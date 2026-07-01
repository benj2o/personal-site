---
title: "How I Gave AI Hands"
date: 2026-06-30
role: "Side Project, Medical Imaging"
summary: "A close friend started medical school, so I built her a tool to make learning to read scans easier."
previewImage: "images/medstudy-chest-ct.png"
membersOnly: false
topic: "Medicine"
tags: ["medical-ai", "segmentation", "sam"]
hideMeta: true
searchHidden: false
showToc: true
---

A close friend of mine, Melissa, started medical school last year. To surprise her, I wanted to build a small tool to aid with her studies.

So much of learning is visual. In academics alone this ranges from reading diagrams and graphs to following lecture videos. In my own degree it was truss analysis, spotting the single wrong step on a sheet of equations, or working through the interpretation of a diagram. In medical school it is chest CT, head CT, and the occasional MRI. For my parents it might be checking the health of our plants, with the model pointing to the exact spots where symptoms appear. Giving a model spatial orientation and the ability to interpret what it is looking at felt like a natural and simple extension.

### Where Medical Segmentation Stands
{.reflection-heading}

MedSAM is the reference point for segmentation in medical imaging. A single promptable model outlines structures across CT, MRI, ultrasound, and more, without a separate network for each organ. Given a box or point prompt, it returns a clean mask.

What it does not do is interpret. MedSAM can outline a cell, a bacterium, or a region of tissue, but it cannot tell you the cell is malignant, the flagellum is broken, or that a scan shows metastasis. Locating a structure and understanding its clinical meaning are different problems.

{{< reflection-figure src="images/medsam-architecture.png" caption="MedSAM produces segmentation masks from simple box prompts across many imaging modalities." >}}

Applying that rough concept to newer models is where it gets interesting. General multimodal systems like gemini-3.1-pro-preview and GPT-5.5 are already strong enough that the interpretation half is largely handled. Pairing that reasoning with a segmentation backbone gives you both the location and the meaning in a single loop. The remaining work was wiring the two together into something a student could click through.

### How I Built It
{.reflection-heading}

Segmentation runs on SAM 3 as the backbone, adapted with a small LoRA fine-tune on a few hundred slices I annotated so the masks snap to the structures Melissa studies. It takes coordinate and bounding-box prompts and returns masks, and a multimodal model labels each region with a one-line note and a confidence score. The token-pruning idea from my earlier research drops the irrelevant background before the language model runs, which keeps it responsive inside a chat. On a held-out set the segmentation sat around a mean IoU of 0.85.

{{< reflection-figure src="images/medstudy-avm-chat.png" caption="The user presents a case and asks a question, and the model answers while marking the arteriovenous malformation and its feeding vessels inline." >}}

I also added interactive 3D anatomy models. Melissa could click a specific bone or muscle fiber, ask a targeted question, and get the answer visualized directly on the model.

The labels can be wrong and the confidence scores are estimates, so a low score is a cue to check the textbook. What it does well is lower the friction of studying, and the same idea extends well beyond medicine to almost any use case. I hope a product team at Claude or OpenAI builds something like this in. It looks like a simple change that would be broadly useful.
