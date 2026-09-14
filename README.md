# gnn-music-recommender-reproducibility
Reproducibility materials for MSc Extended Research Project on Graph Neural Networks for Music Recommender Systems

# Graph Neural Networks for Music Recommender Systems

## Reproducibility Materials

This repository contains the reproducibility materials for the MSc Extended Research Project:

**Graph Neural Networks for Music Recommender Systems: Do Social and Semantic Graphs Improve Recommendation Quality?**

The implementation reproduces the analyses reported in the project, including:

- preprocessing of the HetRec 2011 Last.fm dataset;
- per-user train/validation/test splitting;
- popularity baselines;
- tuned User-CF;
- LightGCN hyperparameter selection;
- tuned LightGCN;
- Social LightGCN;
- preference-weighted Social LightGCN;
- Semantic LightGCN;
- matched shrinkage control;
- mixing-weight sweeps;
- three-seed final evaluation;
- paired Wilcoxon signed-rank tests;
- bootstrap confidence intervals;
- reported analytical figures.

## Main notebook

`GNN_Reproducible.ipynb`

The notebook should be executed sequentially from top to bottom from a fresh runtime.

## Dataset

The project uses the **HetRec 2011 Last.fm 2K dataset**.

The raw dataset is not redistributed in this repository.

Download the Last.fm HetRec 2011 dataset from the original GroupLens source.

The following files are required:

- `user_artists.dat`
- `artists.dat`
- `user_friends.dat`
- `tags.dat`
- `user_taggedartists.dat`

Place these files in the same working directory as `GNN_Reproducible.ipynb` before running the notebook.

## Experimental protocol

- Per-user split: 80% training / 10% validation / 10% test
- Split seed: 42
- Recommendation cutoff: K = 10
- Full-catalogue ranking over 17,632 artists
- Validation masks training interactions
- Test masks training and validation interactions
- Loss: Bayesian Personalised Ranking
- Batch size: 2048
- Final models: 3 random seeds
- Maximum final-training epochs: 400
- Validation interval: 10 epochs
- Early-stopping patience: 60
- Sweep budget: 150 epochs
- Sweep patience: 30

### Selected LightGCN configuration

- Embedding dimension: 128
- Propagation layers: 2
- Learning rate: 0.001
- L2 regularisation: 1e-5

### Side-information grids

- Social alpha: {0, 0.05, 0.25, 1.0}
- Selected alpha: 0.05
- Semantic beta: {0, 0.25, 1.0, 2.0, 4.0}
- Selected beta: 1.0

## Software

The principal dependencies are:

- Python
- PyTorch
- PyTorch Geometric
- pandas
- NumPy
- SciPy
- scikit-learn
- matplotlib
- tqdm

Exact package versions used for the submitted run are provided in `requirements.txt`.

## Outputs

The `outputs/` directory contains the principal numerical outputs and figures from the submitted execution.

Small numerical differences may occur across hardware and software environments, particularly when GPU execution is used.
