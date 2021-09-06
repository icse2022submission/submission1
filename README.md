# ICSE 2022 submission: Domain-Specific Analysis of Mobile App Reviews Using Keyword-Assisted Topic Models (replication package)
This repository contains Python scripts in jupyter notebook format used to replicate the results of our study.

The package contains the following files:
- `food.csv` and `investing.csv` -> user review datasets
- `main_script` -> analysis (summarization, keyword generation, keyATM and LDA training)
- `results_visualization` -> creating plots and running a t-test
- `scores` folder -> results for each keyATM configuration and LDA for each K value in pickle format
- `wiki` -> download wiki dump and generate sparse binary matrix for extrinsic evaluation

To replicate our study use the following steps:
1. Download and install [keyATM](https://keyatm.github.io/keyATM/) and [hybridtfidf](https://pypi.org/project/hybridtfidf/).
2. Save the datasets and all scripts to your preferred folder.
3. Run `wiki` to download a wikipedia dump and generate a sparse binary matrix for extrinsic evaluation. Change the destination folder to your preferred choice.
4. Run `main_script` to (1) load a dataset of your choice (`food.csv` | `investing.csv`); (2) load wiki matrix for evaluation; (3) generate keywords for keyATM; (4) train and evaluate keyATM as well as LDA with the required number of topics; (5) *optionally* filter out keywords with low NPMI score.
5. Run `results_visualization` to generate the results from the paper

Using extrinsic evaluation and training a keyATM model is costly. For that reason, a binary matrix is generated for faster word lookup and the NPMI calculation is optimized to save time and resources. Nevertheless, to comfortably execute all the scripts, you need at least 64GB RAM. However, the training can take hours, especially for a large number of topics. To quickly verify that everything works, use smaller number of topics and limit the dataset size by using `fin_texts[:5000]`, as an example.
