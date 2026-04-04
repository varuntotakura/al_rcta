# AL_RCTA - An Analysis of Active Learning Algorithms using Real-World Crowd-sourced Text Annotations

## Paper and repository
This repository accompanies a recently accepted paper and contains the cleaned datasets, collected annotator files, and scripts to reproduce the experimental splits used in the study.

## Datasets (summary)
We used three benchmark text-classification datasets:

- AG News (4 classes): world, sports, business, science/technology.
- Consumer Complaints (6 classes): debt collection, prepaid card/debit card, mortgage, checking/savings account, student loan, vehicle loan/lease. (Source: https://catalog.data.gov/dataset/consumer-complaint-database)
- Wikipedia Movie Plots (4 classes — movie genres): drama, comedy, horror, action. (Source: https://www.kaggle.com/datasets/jrobischon/wikipedia-movie-plots)

For each dataset we randomly sampled 3,000 examples and collected annotations via Upwork from multiple distinct workers (10 annotators per sampled set, Wikipedia includes 9 annotator files in this repo). Annotators could abstain by entering label 0. The protocol received ethical review and participant consent; no worker identities were recorded.

## Folder structure & key files
AGNewsGroups/
- Cleaned_AG_News_Dataset_3_columns_ALL.xlsx — main cleaned dataset (Index, Description, Class Index).
- Cleaned_AG_News_Dataset_Unlabeled.xlsx — unlabeled subset with ground-truth labels.
- Annotations/ — human annotation files (AG_Upwork_<num>.xlsx).

ConsumerComplaints/
- Cleaned_Dataset_All.xlsx — main cleaned dataset (Index, Consumer complaint narrative, Product).
- Cleaned_Consumer_Complaint_Dataset_Unlabeled.xlsx — unlabeled subset with ground-truth labels.
- Annotations/ — human annotation files (CC_Upwork_<num>.xlsx).

WikipediaMoviePlots/
- Cleaned_Dataset_All.csv — main cleaned dataset (Index, Plot, Genre).
- wiki_unlabeled_with_labels.xlsx — unlabeled subset with ground-truth labels.
- Annotations/ — human annotation files (Wiki_Upwork_<num>.csv) — nine annotator files provided.

All dataset files in this repo use an "Index" column (unique id), a text column standardized as "Description", and a label column standardized as "Labels".

## Directory structure
A concise view of the repository layout:

```
.
├─ README.md
├─ AGNewsGroups/
│  ├─ Cleaned_AG_News_Dataset_3_columns_ALL.xlsx
│  ├─ Cleaned_AG_News_Dataset_Unlabeled.xlsx
│  └─ Annotations/
├─ ConsumerComplaints/
│  ├─ Cleaned_Dataset_All.xlsx
│  ├─ Cleaned_Consumer_Complaint_Dataset_Unlabeled.xlsx
│  └─ Annotations/
├─ WikipediaMoviePlots/
│  ├─ Cleaned_Dataset_All.csv
│  ├─ wiki_unlabeled_with_labels.xlsx
│  └─ Annotations/
.
```

## Usage for experiments (how data was used)
- Initial labelled seed: 500 randomly sampled examples (random_state=42).
- Test set: 10,000 randomly sampled examples from the remaining pool (random_state=42). If fewer than 10k remain, sampling with replacement is used for the test set.
- Unlabeled pool: remaining annotated examples after extracting the seed and test splits; ground-truth labels for these unlabeled examples are included in the *_Unlabeled.* files.
- Annotated pool: 3,000 sampled examples per dataset with crowd annotations.
- Scoring subset: the code samples 500 examples from the annotated pool for scoring (100 used only for some other datasets in related projects).

Use the provided cleaned files and annotation folders to reproduce the splits and experiments described in the paper. Scripts in the codebase expect the file names and columns described above.

## Citation & contact
If you use this repository or the collected annotations, please cite the accompanying paper and acknowledge the dataset sources.  
Author: Varun Totakura

## Paper citation (BibTeX)
The paper has been accepted to WCCI 2026 - IJCNN (to appear). Use the following BibTeX entry:

```bibtex
@InProceedings{al_rcta2026,
  author    = {Varun Totakura and Ankita Singh and Yushun Dong and Shayok Chakraborty},
  title     = {{An Analysis of Active Learning Algorithms using Real-World Crowd-sourced Text Annotations}},
  booktitle = {Proceedings of the IEEE World Congress on Computational Intelligence (WCCI) -- International Joint Conference on Neural Networks (IJCNN)},
  month     = {June},
  year      = {2026},
  note      = {Accepted for publication}
}
```

Creative Commons Attribution 4.0 International (CC BY 4.0)

Copyright (c) 2026 Varun Totakura

This work is licensed under the Creative Commons Attribution 4.0 International License.

You are free to:

* Share — copy and redistribute the material in any medium or format
* Adapt — remix, transform, and build upon the material for any purpose, even commercially

Under the following terms:

* Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
* No additional restrictions — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

Full license text: https://creativecommons.org/licenses/by/4.0/