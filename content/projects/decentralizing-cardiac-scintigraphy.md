---
title: "Decentralizing Cardiac Scintigraphy in the NHS"
date: 2026-07-01
role: "Customer discovery, Nuclear Medicine"
summary: "Software and NHS information governance block local cardiac amyloid scans more often than isotope supply."
previewImage: "images/decentralizing-cardiac-scintigraphy.png"
membersOnly: false
topic: "Medicine"
tags: ["nuclear-medicine", "cardiology", "nhs", "customer-discovery"]
hideMeta: true
searchHidden: false
showToc: true
---

This started as one of the ideas I explored with my friend S.H., a nuclear engineer who had just finished her PhD at Oxford on fusion materials. I did not want to waste it, so I kept pulling the thread.

### How This Started
{.reflection-heading}

At {{< cross-link href="projects/entrepreneur-first-selection-days/" text="Entrepreneur First Selection Days" >}}, S.H. and I spent a day on the logistics behind radiopharmaceuticals. We assumed the problem was getting the isotope to the patient.

Talking to doctors changed my mind. We called Dr S.A., an NHS interventional cardiologist at a district general hospital in Lincolnshire. He runs a 16-cardiologist department in a rural catchment, and he was clear that isotope supply was not his constraint. His constraint was that he could not run one specific scan locally at all. To get it, he sends patients to London. He pointed us to his colleague, Dr Basu, who has reported nuclear cardiology for around 20 years and had been trying to stand up the same scan locally for roughly 18 months without success.

After the calls I kept inquiring. I worked through the published referral pathways and nuclear medicine service pages of NHS trusts that run these scans, along with national guidance from NICE and the British Nuclear Medicine Society, to check whether the Lincolnshire picture matched the rest of the country. It mostly did.

### The Disease and the Diagnostic Gate
{.reflection-heading}

The scan in question is bone scintigraphy for transthyretin amyloid cardiomyopathy, usually written as ATTR-CM. It is a progressive and eventually fatal disease in which misfolded transthyretin protein deposits in the heart muscle and stiffens it. Transthyretin is a transport protein made in the liver. It normally travels as a stable four-part tetramer carrying thyroid hormone and retinol. When it destabilizes, the subunits misfold and aggregate into amyloid fibrils. This happens either through age in wild-type disease, which mostly affects older men, or through inherited variants such as V122I.

{{< reflection-figure src="images/ttr-pathobiology.png" caption="Pathobiology of transthyretin amyloid: TTR tetramers dissociate into monomers, misfold into amyloidogenic intermediates, and aggregate into fibrils that deposit in the myocardium and peripheral nerves. Source: Cleveland Clinic, 2019." >}}

The important clinical fact is that ATTR-CM has to be separated from light-chain cardiac amyloidosis, known as AL, before anyone starts treatment. AL is driven by a blood cancer and is a medical emergency with survival measured in months if it is missed. So the pathway is not one test. It is a bone scan read alongside a blood and urine screen for a monoclonal protein.

The confirmation step is a scan using a technetium-99m labeled bone tracer, most often 99mTc-DPD in the UK and Europe. The reader grades cardiac uptake against rib uptake on a simple visual scale from Perugini Grade 0 to Grade 3. A Grade 2 or Grade 3 heart, combined with a clean monoclonal screen, confirms ATTR-CM without a biopsy at close to 100 percent specificity.[^nonbiopsy] That is why it is a diagnostic gate. It replaces cutting a sample out of the heart muscle.

The gate matters more now because there are drugs behind it. NICE recommends tafamidis[^ta984] and vutrisiran[^ta1115] for ATTR-CM, and both require a confirmed diagnosis first. The disease is also badly underdiagnosed. Screening studies find unrecognized ATTR in roughly 13 percent of older patients admitted with heart failure with preserved ejection fraction and a thick left ventricle.[^epi] The tests exist, the treatments exist, and most of the patients are still invisible.

{{< reflection-figure src="images/attr-treatment-landscape.png" caption="Therapeutic landscape for ATTR-CM: drugs target TTR production (RNA silencing, gene editing), tetramer stabilization (tafamidis), or fibril degradation. All require a confirmed diagnosis first. Source: PMC." >}}

{{< reflection-figure src="images/dpd-perugini-grades.png" caption="99mTc-DPD scintigraphies showing Perugini Grade 0 (a) through Grade 3 (d), with increasing cardiac uptake relative to bone. Panel (e) shows thoracic SPECT short-axis and long-axis slices with the corresponding polar plot. Grade 2 or 3 combined with a negative monoclonal screen confirms ATTR-CM non-invasively." >}}

| Modality | Role | Invasiveness | NHS access |
| --- | --- | --- | --- |
| Echocardiography | First-line screening, wall thickness and strain | Non-invasive | High, available at every trust |
| Cardiac MRI | Tissue characterization, late gadolinium, ECV (sensitivity ~0.83) | Non-invasive, needs contrast | Moderate, limited by scanner time |
| 99mTc-DPD scintigraphy | Non-invasive confirmation of ATTR-CM (sensitivity ~0.93) | Minimal, IV tracer | Low, roughly 30 specialized sites |
| Endomyocardial biopsy | Gold-standard tissue typing | Highly invasive | Low, tertiary centers only |

Sensitivity figures above are drawn from a pooled imaging meta-analysis.[^meta]

### The Diagnostic Pathway
{.reflection-heading}

Written out, the logic is short. Two branches run in parallel, and only one combination clears the patient for treatment.

```
Suspected cardiac amyloidosis (echo or CMR red flags)
        |
        +--> Hematology screen: serum free light chains,
        |    serum and urine immunofixation
        |         |
        |         +--> Monoclonal protein present --> biopsy, refer hematology
        |
        +--> 99mTc-DPD scintigraphy (planar at 3h, then thoracic SPECT/CT)
                  |
        +---------+---------+
     Grade 0/1          Grade 2/3
        |                   |
  ATTR-CM unlikely   If AL excluded: ATTR-CM confirmed
                            |
                     TTR genotyping, start therapy
```

### What I Found Inquiring Across Hospitals
{.reflection-heading}

The Lincolnshire department orders effectively zero of these scans per year today because it cannot run them. The cardiologist estimated that with local access the department would order 30 to 40 per year, which lines up with 3 to 5 requests per cardiologist across 16 of them. The hardware was not the blocker. The gamma cameras were there. The scan was not.

The national picture explains why that gap is normal rather than unusual.

| Inquiry | What it showed |
| --- | --- |
| Lincolnshire DGH (calls) | ~0 scans now, ~30 to 40 per year if local, cameras present, sends patients to London |
| National Amyloidosis Centre, UCL | National hub, DPD plus SAP plus echo plus CMR, planar at 3h then thoracic SPECT/CT[^nac] |
| Castle Hill, Hull | Local DPD since 2012, 426 scans across 421 patients over ten years, 211 in 2021 to 2022 alone[^castlehill] |
| Mid Cheshire | District general hospital that built a local pathway and tracked delayed-diagnosis mortality[^midcheshire] |
| Leeds, Royal Brompton, Frimley | Trusts with published local cardiac amyloid scanning services[^trusts] |

Two numbers frame the whole opportunity. Only around 30 of roughly 252 UK nuclear medicine departments run cardiac DPD locally, and the estimated national volume is somewhere between 3,500 and 5,000 scans per year.[^bnms] The Castle Hill data is the clearest signal of latent demand. Once tafamidis became available, local referrals jumped, and half of a decade of scans landed in the final two years.[^castlehill]

### The Real Bottleneck
{.reflection-heading}

Putting the calls next to the published requirements, the blocker resolves into a short list, and isotope supply is not on it.

1. Not tracer supply. DPD is a routine bone tracer already stocked daily for skeletal scans in most departments.
2. Software. Quantitative SPECT/CT reconstruction needs platform-specific tools such as Hermes Hermia or the Siemens xSPECT pipeline.[^hermes] The visual Perugini grade is standardized. The quantitative SUV metrics that sit on top of it are not standardized across sites, which makes a shared reporting workflow harder than it looks.
3. Hardware detail. Planar-only cameras are not enough. Reading planar images without SPECT/CT carries roughly a 15 percent false-positive rate from blood pool and overlying bone. Many district cameras are now SPECT/CT capable but sit underused as nuclear perfusion work declines.
4. Information governance. A local-acquisition, remote-reporting model means moving images across trust boundaries. That triggers National Imaging Registry onboarding, a data protection impact assessment, the security toolkit, and clinical safety sign-off under DCB0129 and DCB0160.[^nir] In the NHS this is usually where months disappear.
5. Concentrated expertise. Reporting skill and the specific licensing to run the cardiac indication tend to sit at tertiary hubs, not district hospitals.

The model the Lincolnshire team actually wanted is the obvious one. Acquire the scan locally, where the camera and the patient already are, and report it remotely, where the expertise is. Castle Hill shows a district service can run end to end. The National Amyloidosis Centre shows the referral hub still makes sense for complex cases. The missing piece is the software and governance layer that would let an average department do the acquisition without standing up a full specialist service.

| Metric | Standardization | Main limitation |
| --- | --- | --- |
| Perugini grade (0 to 3) | High, used worldwide | Subjective at Grade 1 |
| Heart-to-contralateral-lung ratio | Moderate | False positives from blood pool or rib uptake |
| SPECT/CT SUV | Low, tied to vendor software | Skeletal muscle competition, needs hybrid hardware |

{{< reflection-figure src="images/dpd-spect-ct-fusion.png" caption="SPECT/CT fusion with freehand VOI delineation over the myocardium (blue) for two cases: (A) AL amyloidosis with Perugini 0 and low SUVmax, (B) wtATTR with Perugini 3 and high SUVmax. Panel (C) shows the SUVmax separation between amyloid subtypes. This is the reconstruction step that depends on vendor-specific software. Source: PMC, DPD quantification in cardiac amyloidosis." >}}

### The Economics
{.reflection-heading}

The procedure itself is cheap. NHS unbundled tariffs put a SPECT scan at £78 and a SPECT/CT at £92.[^tariff] The cost is not the scan. It is everything around sending a frail patient to London. Median age at ATTR-CM diagnosis sits between 75 and 86. Many patients cannot travel by public transport, so non-emergency transport runs £250 to £400 round trip, and the one to two day assessment adds accommodation for a patient and a carer at £150 to £300 a night. The regional hospital also loses the diagnostic activity and delays starting therapy.

There is a useful precedent for how new cardiac imaging software scales inside the NHS. HeartFlow, which models blood flow from a CT scan, went from a 2017 NICE recommendation to central Innovation Technology Payment funding in 2018 and 2019, and then to the MedTech Funding Mandate in April 2021, with a modeled saving of about £214 per patient against invasive angiography.[^heartflow] The lesson is not that a DPD product would follow the same path. It is that guidance, then central funding, then a reimbursement mandate is the sequence that actually moves adoption across district hospitals.

### Perfusion Imaging, Briefly
{.reflection-heading}

This all sits next to a larger shift. UK nuclear myocardial perfusion imaging has fallen sharply since NICE moved CT angiography to the first line for stable chest pain, which is part of why so many gamma cameras have spare capacity. In the US, perfusion imaging is still dominant, supported by office-based nuclear cardiology and fee-for-service reimbursement. The reporting for perfusion is heavily software-driven, and the failure modes are real. If the software is wrong and the reader is not experienced enough to override it, the error propagates.

### Where This Leaves Me
{.reflection-heading}

The Lincolnshire estimate of 30 to 40 scans a year is credible. Comparable district services such as Castle Hill and Mid Cheshire run roughly 40 to 100 scans a year once established. The demand is real, the tracer is not scarce, and the hardware is largely already installed.

Some things I could not verify and would want before doing anything serious. The licensing cost of the reconstruction software is commercially sensitive and not published. I could not confirm how many of the 252 departments hold the specific cardiac indication licensing rather than a general bone-scan license. And I do not yet know whether a remote-reporting product already exists inside an NHS trust that could simply be extended.

I did not turn this into a company. The point of the exercise was to find where the system actually breaks, and the answer here was software and governance rather than physics or supply. That connects to my interest in {{< cross-link href="projects/medical-imaging-study-tool/" text="clinical imaging tools" >}}, which is why I wrote it up instead of letting the thread go.

*This is a research and product write-up, not medical advice. For diagnosis or treatment, consult a clinician.*

[^nonbiopsy]: [Nonbiopsy diagnosis of cardiac transthyretin amyloidosis, Circulation 2016](https://www.ahajournals.org/doi/10.1161/circulationaha.116.021612)
[^ta984]: [NICE TA984, tafamidis for transthyretin amyloidosis with cardiomyopathy](https://www.nice.org.uk/guidance/ta984)
[^ta1115]: [NICE TA1115, vutrisiran for transthyretin amyloidosis with cardiomyopathy](https://www.nice.org.uk/guidance/ta1115)
[^epi]: [Cardiac amyloidosis epidemiology, diagnosis and therapy, ESC](https://www.escardio.org/Councils/Council-for-Cardiology-Practice-(CCP)/Cardiopractice/cardiac-amyloidosis-epidemiology-diagnosis-and-therapy)
[^nac]: [National Amyloidosis Centre, information for referring physicians, UCL](https://www.ucl.ac.uk/medical-sciences/divisions/national-amyloidosis-centre/information-referring-physicians)
[^castlehill]: [Impact of increased DPD scintigraphy on timing of diagnosis and prognosis over ten years, Hull](https://www.researchgate.net/publication/375591458_Impact_of_increased_DPD_scintigraphy_on_timing_of_diagnosis_and_prognosis_of_transthyretin_cardiac_amyloidosis_over_the_course_of_ten_years)
[^midcheshire]: [Pathways for ATTR-CM from a district general hospital perspective, MDPI](https://www.mdpi.com/2308-3425/13/6/248)
[^trusts]: Local cardiac amyloid services: [Leeds Teaching Hospitals](https://www.leedsth.nhs.uk/services/cardiology/cardiac-amyloidosis-service/), [Royal Brompton and Harefield](https://www.rbht.nhs.uk/our-services/cardiac-amyloidosis-99mtc-dpd-scan), [Frimley Health](https://www.fhft.nhs.uk/patients-and-visitors/patient-information-library/cardiac-amyloid-study)
[^bnms]: [Recommendations for good clinical practice for DPD bone scintigraphy for cardiac amyloidosis, BNMS](https://www.researchgate.net/publication/377703140_Guidelines_Recommendations_for_good_clinical_practice_for_DPD_bone_scintigraphy_for_cardiac_amyloidosis)
[^hermes]: [Hermes Medical Solutions, cardiology software](https://www.hermesmedical.com/our-software/cardiology/)
[^nir]: [National Imaging Registry and its governance framework, NHS England Digital](https://digital.nhs.uk/services/national-imaging-registry/governance)
[^tariff]: [Nuclear medicine tariffs, British Society of Cardiovascular Imaging](https://bsci.org.uk/standards-and-guidelines/tariffs/)
[^heartflow]: [NICE MTG32, HeartFlow FFRCT for coronary CT angiography](https://www.nice.org.uk/guidance/mtg32)
[^meta]: [Cardiac MRI and scintigraphy in cardiac amyloidosis, a meta-analysis of 4,866 patients, PMC](https://pmc.ncbi.nlm.nih.gov/articles/PMC12557567/)
