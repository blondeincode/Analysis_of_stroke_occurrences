# Analysis of an anonymized sample of the National Health Fund data on the occurrence of ischemic stroke

There are two files in this repository: :v:
* [Analysis_of_stroke_occurrences(plotly_visualizations).ipynb - Link to Google Colab](https://colab.research.google.com/drive/1Yn3vBmymkZj0rSCD8Wj-bvJQcAw2ehXn?usp=sharing)
* [Analysis_of_stroke_occurrences(matplotlib_visualizations).ipynb - Link to Google Colab](https://colab.research.google.com/drive/1eZ4wrMlIC0K01a2RsZx-hbGxfjPHrADM?usp=sharing)

## Data was downloaded from the website [dane.gov.pl](https://dane.gov.pl/pl/dataset/1711,zanonimizowana-probka-danych-nfz-dotyczaca-wystapienia-udaru-niedokrwiennego-mozgu)

The National Health Fund has reporting data provided by medical entities. The dataset concerns reimbursed services and medications for patients, some of whom have suffered from ischemic stroke. The collection was prepared in such a way that the data on services and medications come from the period of two years (t, t + 1), while the information on the occurrence of a stroke concerns the period of the next two years (t + 2, t + 3). The provided data set consists of 6 tables containing actual, anonymised data of the National Health Fund. The "patients" table (500,000 IDs) contains data defining whether a patient had an ischemic stroke over the two-year period under review. In order to ensure anonymization of the data, it was not stated what period the data came from. The remaining tables contain information on the history of services and the fulfillment of prescriptions for patients in the table "patients" from the previous two years.

## Description of individual tables:
1. patients - information on the occurrence of first-time ischemic stroke in the analyzed time period (2 years). Patients who experienced ischemic stroke before the analyzed time interval were excluded from the analysis. It consists of the following columns:

   a) PATIENT_ID - unique identifier of the patient.
   
   b) WAS_THERE_A_STROKE? - binary information on whether a disease entity under analysis occurs in the case of a person with a given identifier.
   
2. health_benefits - information on the benefits provided. It consists of the following columns:

   a) PATIENT_ID - unique identifier of the patient.
   
   b) EPISODE_ID - episode identifier allowing to combine services with procedures.
   
   c) CONTACT_ID - identifier allowing to combine services with diagnoses.
   
   d) RANGE_CODE - anonymized code of the scope of the service.
   
   e) TYPE_OF_SERVICES - a text variable that defines the type of the place where the service is provided (hospital treatment, primary healthcare, emergency medical services, etc.).
   
   f) SETTLED_AMOUNT - the amount that the fund paid to the entity for the service provided. In the case of benefits settled under the capitalization rate or as a lump sum, this amount is 0.
   
3. procedures - a table containing information on medical procedures performed. It consists of the following columns:

   a) EPISODE_ID - ID of the episode allowing to combine services with procedures.

   b) CODE_PROCEDURES - anonymised code of the procedure according to the ICD-9 classification.

4. prescriptions - the table contains information on completed prescriptions for reimbursed drugs:

   a) PATIENT_ID - unique identifier of the patient.

   b) PRESCRIPTION_ID - prescription ID.

   c) NUMBER_OF_PACKAGES - the purchased number of packages of a drug with a given ATC code (3 code characters according to the anatomical-therapeutic-chemical classification).

5. diagnosis - the table contains information on the reported diagnoses according to the ICD-10 classification:

   a) CONTACT_ID - identifier that allows you to combine services with diagnoses.

   b) DIAGNOSIS_CODE - encrypted recognition code according to the International Classification of Diseases and Health Problems ICD10. The original code may consist of 3 or 5 characters, which makes the diagnosis more detailed.
   
   c) IS_THIS_THE_MAIN_DIAGNOSIS? - binary variable with levels 'N' - coexisting recognition and 'T' - main recognition.

6. patient_parameters - the table contains information about patient parameters:

   a) PATIENT_ID - unique identifier of the patient.

   b) AGE_GROUP - patient's age presented in five-year age ranges.

   c) GENDER - patient's gender.

   d) DISTRICT_TERRITORY - the territorial code of the patient's place of residence, presented to the poviat level.

## The analysis was conducted in order to answer the following questions:

* How many unique patients and for what total amount have dental services been used?
* How many patients received dental treatment?
* What was the settled amount for all patients who received dental treatment?
* What unique diagnoses were diagnosed in patients settled by the range code 3103275?
* How many unique episodes do patients who have not been diagnosed with a stroke have in their history?
* How many drug packages were issued in total? 
* What percentage are patients who have been diagnosed with a stroke? 
* How many patients in each age group have had a stroke?
* How many patients in each age group have not had a stroke?
* What was the gender breakdown of patients diagnosed with a stroke?
* What was the gender breakdown of patients not diagnosed with a stroke?
* How many patients have been diagnosed with a stroke according to the district territory code?
* Which health services were used by patients diagnosed with a stroke?
* How many patients diagnosed with stroke benefited from each health service?
* Was the diagnosis a primary one or a concomitant diagnosis?

