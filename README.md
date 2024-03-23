# concept_recognition_with_i2b2_dataset
Concept recognition on clinical notes provided by i2b2 dataset, used for academic purposes only

## Datset Options
Each dataset option can be found at the following link but can only be accessed upon request from Harvard Medical School: https://portal.dbmi.hms.harvard.edu/projects/n2c2-nlp/

1) Concept relations (the one I have chosen for my capstone): The data consists of clinical discharge notes and annotations identifying the treatments, conditions, and tests, e.g. "diabetes" would be a "condition" and "x-ray" would be a "test". The goal is to perform this token classification with clinicalBERT from Hugging Face.
2) Temporal relations (not chosen for capstone): data consists of medical events with time stamps. Goal would be to forecast medical events based on previous timestamps.
3) Medical events (not chosen for capstone): describes adverse medical reactions to various pharmaceuticals. The goal would be to extract the medications in the notes and potentially forecast adverse reactions.

## Code for data extraction
I have only uploaded the code for extracting text from dataset 1 because part of the agreement was that I would not share this data with anyone. In summary, I used Python's "with open()" function to read the text files into a dataframe, and then preprocessed the data such that each token has a concept tag (e.g. B-test, I-treatment and O).

## Preprocessing and Exploratory Analysis
Please view "Data_Processing_and_EDA.ipynb" to understand how I preprocessed the data. This notebook also shows some interseting visulizations of my data, such as TSNE.

## Recreating Previous Results
This dataset was originally a part of the The 2010 i2b2/VA Workshop on Natural Language Processing Challenges for Clinical Records (link: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3168320/). The paper, “2010 i2b2/VA challenge on concepts, assertions, and relations in clinical text” by Uzuner et al. summarized the results of the competition.

![Summary of Results](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3168320/table/tbl2/?report=objectonly)

As seen in the above table from the challenge, contenders achieved exact F1-scores between 0.788 and 0.852. The top contender, deBruijn et al., used a “semi-Markov HMM, trained using passive-aggressive online updates” for concept extraction (https://www.svkir.com/papers/deBruijn-et-al-i2b2-2010.pdf). There is no code currently available from this paper, but I have trained a HMM in the file “baselines_for_concept_recognition_of_clinical_notes.ipynb”. My code achieved an F1-score of 0.17, which is far from the results found by deBruijn. 

Gurulingappa et al. applied conditional random fields (CRF) to obtain a F1-score of 0.818. They used various features such as capitalizations, special characters, and others. Again, code was not available, so I trained my own conditional random field model in the file “baselines_for_concept_recognition_of_clinical_notes.ipynb”. My results were somewhat better than my HMM with an F1-score 0.21.

I would like to point out that BERT and transformers did not come out until 2017, and this competition was in 2010. So for my final code, I will use a BERT model and see if I can achieve similar results to the i2b2 contenders. My hypothesis is that it will be far closer than the previous models since transformers are state-of-the-art.


