---
license: apache-2.0
configs:
- config_name: Single-CoT
  data_files:
  - split: train
    path: train-single.jsonl
  - split: validation
    path: val-single.jsonl
- config_name: Diverse-CoT
  data_files:
  - split: train
    path: train-diverse.jsonl
  - split: validation
    path: val-diverse.jsonl
- config_name: Test-CoT
  data_files:
  - split: test
    path: Test.jsonl
task_categories:
- summarization
language:
- en
tags:
- medical
- pathology
- histopathology
- chain-of-thoughts
- summarization
- synthetic-data
size_categories:
- 10K<n<100K
---

This repository is collection of synthetic data consisting of histopathology reports on 110 subtopics along with its chain-of-thoughts reasoning for summarization.

### Dataset Division
**Single-CoT:** It provides distinct and unique collection of histopathology report, reasoning and summary. 45 reports per 110 subtopics.

**Diverse-CoT:** It provides distinct and unique collection of different histopathology reasoning and summary for a few reports. 3 reports per 110 subtopics, with 16 different reasoning and summary pairs.

**Test-Dataset:** A diverse dataset created seprately to benchmark and test the models.

| **Subset**          | **Dataset**                    | **# Samples** |
|---------------------|--------------------------------|---------------|
| **Single-CoT**      | train-single                   | 4,400         |
|                     | val-single                     | 550           |
| **Diverse-CoT**     | train-diverse                  | 4,490         |
|                     | val-diverse                    | 792           |
| **Test-Dataset**    | Test                           | 550           |

---
### Subtopics

The dataset uses 110 different subtopics in histopathology - "Gastrointestinal Biopsies", "Breast Carcinoma Resections", "Prostate Core Needle Biopsies", 
            "Skin Excisions for Melanoma", "Lymph Node Resections", "Liver Transplant Evaluations", 
            "Lung Adenocarcinoma Specimens", "Uterine Leiomyoma Hysterectomies", "Renal Cell Carcinomas", 
            "Brain Tumor Craniotomies", "Thyroid Fine Needle Aspirates", "Pancreatic Neuroendocrine Tumors", 
            "Ovarian Serous Carcinomas", "Testicular Seminomas", "Bladder Transitional Cell Carcinomas", 
            "Bone Sarcoma Resections", "Soft Tissue Liposarcomas", "Head and Neck Squamous Cell Carcinomas", 
            "Colorectal Adenocarcinomas", "Endometrial Biopsies", "Salivary Gland Tumors", 
            "Esophageal Adenocarcinomas", "Gallbladder Carcinomas", "Appendiceal Mucinous Neoplasms", 
            "Mediastinal Mass Biopsies", "Peripheral Nerve Sheath Tumors", "Pediatric Wilms Tumors", 
            "Cervical Cone Biopsies", "Parathyroid Adenomas", "Adrenal Cortical Carcinomas", 
            "Mesothelioma Specimens", "Synovial Sarcomas", "Gastrointestinal Stromal Tumors (GIST)", 
            "Cholangiocarcinomas", "Pheochromocytomas", "Meningioma Resections", "Pituitary Adenomas", 
            "Thymic Carcinomas", "Vulvar Squamous Cell Carcinomas", "Penile Carcinomas", 
            "Amyloidosis Specimens", "Tuberculosis Granulomas", "Inflammatory Bowel Disease Biopsies", 
            "Autoimmune Hepatitis Specimens", "Metastatic Melanoma Lymph Nodes", "Recurrent Glioblastoma Specimens", 
            "Frozen Section Intraoperative Consultations", "Sentinel Lymph Node Biopsies", "Bone Marrow Core Biopsies", 
            "Placental Pathology Specimens", "Nasopharyngeal Carcinomas", "Small Intestinal Adenocarcinomas", 
            "Cervical Squamous Cell Carcinomas", "Endocrine Pancreatic Tumors", "Hepatocellular Carcinomas", 
            "Medullary Thyroid Carcinomas", "Follicular Thyroid Carcinomas", "Gastric Signet Ring Cell Carcinomas", 
            "Basal Cell Carcinomas of Skin", "Merkel Cell Carcinomas", "Ewing Sarcomas", "Osteosarcomas", 
            "Chondrosarcomas", "Urothelial Carcinomas in Situ", "Anaplastic Thyroid Carcinomas", "Retinoblastomas", 
            "Cytomegalovirus Colitis", "Herpes Simplex Esophagitis", "Fungal Infections in Lung Biopsies", 
            "Parasitic Infections in Tissue", "Sarcoidosis Lymph Node Biopsies", "Syphilitic Placentitis", 
            "Graft-versus-Host Disease in GI Biopsies", "HIV-associated Lymphadenopathy", "Celiac Disease Biopsies", 
            "Hashimoto Thyroiditis", "Lupus Nephritis Biopsies", "Sjögren Syndrome Salivary Glands", 
            "Autoimmune Gastritis", "Renal Allograft Biopsies", "Cardiac Transplant Biopsies", 
            "Lung Transplant Rejection Specimens", "Diffuse Large B-cell Lymphoma Biopsies", "Follicular Lymphomas", 
            "Chronic Lymphocytic Leukemia Nodes", "Hodgkin Lymphoma Specimens", "Myelodysplastic Syndromes", 
            "Acute Myeloid Leukemia Infiltrates", "Bone Marrow Biopsies for Plasma Cell Myeloma", 
            "Neuroblastoma Resections", "Medulloblastomas", "Rhabdomyosarcomas", 
            "Congenital Pulmonary Airway Malformation (CPAM)", "Teratomas (Pediatric)", "Hydatidiform Moles", 
            "Choriocarcinomas", "Ectopic Pregnancies", "Placental Abruption with Infarcts", 
            "Chronic Villitis of Unknown Etiology (VUE)", "Endoscopic Ultrasound-Guided FNA", 
            "Tru-Cut Biopsies of Retroperitoneal Masses", "Transbronchial Lung Biopsies", 
            "Stereotactic Brain Biopsies", "Punch Biopsies of Skin Rashes", "Fine Needle Aspirations of Salivary Glands", 
            "Carcinoid Tumors of Appendix", "Langerhans Cell Histiocytosis", "Angiosarcomas", 
            "Hemangiopericytomas", "Clear Cell Sarcomas"

### Prompt used for Synthetic-Data

**Report-Generation**

Generate a clinically accurate, diverse histopathology report (strictly within 100–150 words) for the subtopic: {subtopic}.

Use these diversity parameters:
- Age: {diversity_params['age']} years
- Gender: {diversity_params['gender']}
- Disease severity: {diversity_params['severity']}
- Presentation: {diversity_params['presentation']}
- Specimen size: {diversity_params['specimen_size']}
- Tumor grade: {diversity_params['grade']}
- Margin status: {diversity_params['margin_status']}

Structure the report as a single paragraph, written in formal clinical language, and include all of the following in flowing sentence form:
1. Patient demographics and brief clinical history
2. Imaging/procedure indication
3. Specimen type and anatomical site
4. Gross findings (size, appearance, margin distance)
5. Microscopic features (type, grade, invasion, necrosis)
6. Margin status and distance
7. Lymph node evaluation (number examined/involved, extracapsular spread)
8. IHC panel with marker interpretation
9. Final diagnosis in standard pathology language

Avoid headings, repetition, or excessive detail. Prioritize brevity, clarity, and information density. Do not exceed 150 words under any condition.

**Single-Reasoning-Summary-Generation**

You are a senior pathologist reviewing a histopathology report. Your task is to generate a consistent, concise 3-step chain-of-thought reasoning sequence (plus a final diagnostic summary), strictly within 150–200 words total.

Report: {report}

Follow this exact structure:
1. Histopathological Correlation – Briefly interpret the clinical context, gross specimen characteristics (e.g., lesion size, margin status, nodal involvement), and key microscopic features (architecture, grade, invasion, necrosis).
2. Ancillary Interpretation – Interpret relevant immunohistochemical (IHC) or molecular findings and their diagnostic implications (e.g., tissue origin, differential exclusion).
3. Diagnostic Integration – Integrate clinical, morphologic, and ancillary data to synthesize the final diagnosis.

Then write a concise diagnostic summary (1–2 sentences) based on the above reasoning.

Tone should be formal, clinical, and factual. Avoid speculation or repetition. Keep reasoning direct and informative. Do not exceed 200 words total under any condition.

**Diverse-Reasoning-Summary-Generation**

*Different-approach*

{
                "name": "clinical_correlation",
                "description": "Clinical Correlation Analysis",
                "approach": "Focus on correlating pathological findings with clinical presentation, patient history, and imaging results to reach a diagnosis."
            },
            {
                "name": "differential_diagnosis",
                "description": "Differential Diagnosis Approach",
                "approach": "Systematically consider and exclude alternative diagnoses based on morphological and clinical features."
            },
            {
                "name": "morphological_pattern",
                "description": "Morphological Pattern Recognition",
                "approach": "Analyze architectural patterns, cellular morphology, and tissue organization to identify characteristic features."
            },
            {
                "name": "immunohistochemical",
                "description": "Immunohistochemical Interpretation",
                "approach": "Emphasize the role of immunohistochemical markers in confirming diagnosis and determining tissue origin."
            },
            {
                "name": "molecular_pathology",
                "description": "Molecular Pathology Reasoning",
                "approach": "Integrate molecular findings, genetic alterations, and biomarker expression in diagnostic reasoning."
            },
            {
                "name": "staging_grading",
                "description": "Staging and Grading Assessment",
                "approach": "Focus on tumor staging, histological grading, and prognostic factor evaluation."
            },
            {
                "name": "prognostic_analysis",
                "description": "Prognostic Factor Analysis",
                "approach": "Evaluate prognostic indicators, survival markers, and factors affecting patient outcomes."
            },
            {
                "name": "treatment_planning",
                "description": "Treatment Planning Perspective",
                "approach": "Consider therapeutic implications, treatment response predictors, and surgical planning aspects."
            },
            {
                "name": "comparative_pathology",
                "description": "Comparative Pathology Approach",
                "approach": "Compare findings with similar cases, reference standards, and published literature."
            },
            {
                "name": "evidence_based",
                "description": "Evidence-Based Reasoning",
                "approach": "Base diagnostic reasoning on established criteria, guidelines, and evidence-based medicine principles."
            },
            {
                "name": "systematic_workup",
                "description": "Systematic Diagnostic Workup",
                "approach": "Follow a structured, step-by-step diagnostic approach from gross examination to final diagnosis."
            },
            {
                "name": "risk_stratification",
                "description": "Risk Stratification Analysis",
                "approach": "Assess risk factors, tumor behavior prediction, and stratify patients based on pathological findings."
            },
            {
                "name": "biomarker_driven",
                "description": "Biomarker-Driven Reasoning",
                "approach": "Emphasize the role of specific biomarkers, molecular signatures, and targeted therapy implications."
            },
            {
                "name": "multidisciplinary",
                "description": "Multidisciplinary Correlation",
                "approach": "Integrate pathological findings with radiology, clinical, and laboratory data for comprehensive diagnosis."
            },
            {
                "name": "quality_assurance",
                "description": "Quality Assurance Perspective",
                "approach": "Focus on diagnostic accuracy, quality control measures, and potential diagnostic pitfalls."
            },
            {
                "name": "educational_case",
                "description": "Educational Case Analysis",
                "approach": "Present findings in a teaching format, highlighting key learning points and diagnostic pearls."
            }

*Reasoning-Summary Prompt*

You are a senior pathologist analyzing a histopathology report using a {reasoning_type['description']} approach. 

Reasoning Approach: {reasoning_type['approach']}

Report: {report}

Generate a concise 3-step chain-of-thought reasoning sequence (plus a final diagnostic summary), strictly within 150–200 words total, using the specified reasoning approach.

Follow this exact structure:
1. Step 1 – Apply the specific reasoning approach to interpret the clinical context, gross specimen characteristics, and key microscopic features.
2. Step 2 – Continue with the reasoning approach to analyze ancillary findings, immunohistochemical results, and their diagnostic implications.
3. Step 3 – Complete the reasoning approach by integrating all findings to synthesize the final diagnosis.

Then write a concise diagnostic Summary (1–2 sentences) based on the above reasoning.

Ensure your reasoning clearly reflects the {reasoning_type['description']} methodology throughout. Be formal, clinical, and factual. Avoid speculation or repetition. Do not exceed 200 words total under any condition.