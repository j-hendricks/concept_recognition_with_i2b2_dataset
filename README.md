# concept_recognition_with_i2b2_dataset
Concept recognition on clinical notes provided by i2b2 dataset, used for academic purposes only

## Datset Options
Each dataset option can be found at the following link but can only be accessed upon request from Harvard Medical School: https://portal.dbmi.hms.harvard.edu/projects/n2c2-nlp/

1) Concept relations (the one I have chosen for my capstone): The data consists of clinical discharge notes and annotations identifying the treatments, conditions, and tests, e.g. "diabetes" would be a "condition" and "x-ray" would be a "test". The goal is to perform this token classification with clinicalBERT from Hugging Face.
2) Temporal relations (not chosen for capstone): data consists of medical events with time stamps. Goal would be to forecast medical events based on previous timestamps.
3) Medical events (not chosen for capstone): describes adverse medical reactions to various pharmaceuticals. The goal would be to extract the medications in the notes and potentially forecast adverse reactions.

## Code for data extraction
I have only uploaded the code for extracting text from dataset 1 because part of the agreement was that I would not share this data with anyone. In summary, I used Python's "with open()" function to read the text files into a dataframe, and then preprocessed the data such that each token has a concept tag (e.g. B-test, I-treatment and O).



