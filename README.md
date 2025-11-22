# Rare_Skin_Diseases

In this study, we present the first comprehensive implementation and evaluation of machine learning approaches for rare skin disease classification using MIMIC-IV EHR data, guided by the high-level roadmap proposed in Banerjee et al. (2023). Our contributions are as follows:

1. Dataset construction based on Orphanet + MIMIC-IV + FDA drug database integration. We combine structured EHR data from MIMIC-IV with classification data from Orphanet and drug-level information from the FDA drug database to construct a clinically validated rare skin disease cohort. 
2. Evaluation of negative class selection on model performance. We construct four separate datasets with varying negative class definitions (common diseases, rare non-skin diseases, common skin diseases, and a mixed group), allowing us to quantitatively demonstrate the impact of negative class selection on model performance, an issue largely overlooked in the rare disease ML literature.
3. Thorough Interpretability and Robust Error Analysis. We conduct in-depth post hoc model interpretability and error analysis using SHAP, counterfactual explanations, and anchor-based rule generation. We identify key feature drivers, highlight high-confidence misclassifications, analyze decision boundaries, and extract rules that explain up to 80\% of correctly classified rare skin disease cases
4. Fairness Evaluation for Demographically Sensitive Diseases. Recognizing the importance of racial and demographic variation in skin disease manifestation, we conduct a subgroup fairness analysis using DALEX and SHAP. We demonstrate that model performance variation across racial groups may reflect true clinical differences 

## Data

We used the https://mimic.mit.edu/docs/iv/ - MIMIC-IV dataset which contains real hospital stays for patients admitted to a tertiary academic medical center in Boston, MA, USA. MIMIC-IV contains comprehensive information for each patient while they were in the hospital. We used the hosp and icu modules which are the most comprehensive modules publicly available. To the patient data, we combined the rare diseases data from https://www.orpha.net/ - Orphanet. It is a database dedicated to providing information on rare diseases and orphan drugs. We essentially used the rare skin diseases classification data from https://github.com/orphanet-rare-diseases-issues/RD-CODE/tree/master/Classifications/en - Orphanet Classification. It has .xml files which were converted to dataframes for better usage. See Data_Extraction_Orphanet_and_MIMIC.ipynb. We used the ICD-10 disorders codes from orphanet classification files and mapped them to the ICD-10 diagnosis codes in diagnosis_icd table of the MIMIC dataset. Apart from this we also mapped the prescribed drugs from the prescriptions table, based on their ndc code to https://www.fda.gov/drugs/investigational-new-drug-ind-application/general-drug-categories - FDA drug codes. This was done to club the medications into sub groups of their types and generate features like, has_antihistamine, has_immunosuppressant, has_moisturiser, to name a few. I have only uploaded Orphanet data that has been used, MIMIC IV data can be acquired from https://mimic.mit.edu/docs/iv/


## The order of files and data to be followed.
Data_Extraction_Orphanet_and_MIMIC.ipynb

Data_Combination.ipynb

Data_Preprocessing.ipynb

Data_Analysis.ipynb

Model_Building.ipynb

Model_Training_&_Testing.ipynb

ML_Interpretability.ipynb

Model_Fairness.ipynb

Explaining_CSD_vs_RSD.ipynb
