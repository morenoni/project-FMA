# project-FMA

Music genre classification (Rock, Folk, Pop, Electronic) on the Free Music Archive (FMA) dataset, comparing classifiers built on hand-crafted audio features with a fine-tuned pretrained audio model. See [`Deliverables/project_proposal.md`](Deliverables/project_proposal.md) for the full research question and methods.

## Repository structure

```
project-FMA/
├── Data_Cleaning/
│   ├── cleaning.ipynb          # Builds the cleaned track list from the FMA metadata
│   ├── cleaned_data/
│   │   └── tracks_clean.csv    # 3,998 tracks: track_id, genre, split, audio_path
│   ├── fma_small/              # NOT in repo: audio files (download below)
│   └── fma_metadata/           # NOT in repo: metadata CSVs (download below)
├── Feature_Engineering/        # Hand-crafted audio features + classical models
├── Deep_Learning/              # Pretrained audio model fine-tuning
└── Deliverables/
    └── project_proposal.md
```

## Data not included in the repo

The raw FMA data is too large for GitHub, so it is gitignored. Download it from the [FMA GitHub repository](https://github.com/mdeff/fma) and unzip it into `Data_Cleaning/`:

| Folder | Download | Size | Contents |
|---|---|---|---|
| `Data_Cleaning/fma_small/` | [fma_small.zip](https://os.unil.cloud.switch.ch/fma/fma_small.zip) | 7.2 GB | 8,000 30-second MP3 clips |
| `Data_Cleaning/fma_metadata/` | [fma_metadata.zip](https://os.unil.cloud.switch.ch/fma/fma_metadata.zip) | 342 MB | `tracks.csv` (genres, splits) and other metadata |

After unzipping, `Data_Cleaning/` should contain `fma_small/000/000002.mp3`, …, and `fma_metadata/tracks.csv`.

## Running the data cleaning

1. Download and unzip the data as above.
2. Open `Data_Cleaning/cleaning.ipynb` and change `path` to your own `Data_Cleaning` folder.
3. Run the notebook. It writes `Data_Cleaning/cleaned_data/tracks_clean.csv`.

The notebook keeps the fma_small tracks labeled Rock, Folk, Pop, or Electronic and drops two broken (empty) MP3 files, leaving 3,998 tracks with FMA's official train/validation/test split:

| Genre | Training | Validation | Test |
|---|---|---|---|
| Electronic | 799 | 100 | 100 |
| Folk | 800 | 100 | 100 |
| Pop | 800 | 100 | 100 |
| Rock | 799 | 100 | 100 |

## Reference

Defferrard, M., Benzi, K., Vandergheynst, P., & Bresson, X. (2017). FMA: A Dataset for Music Analysis. *18th International Society for Music Information Retrieval Conference (ISMIR)*. https://arxiv.org/abs/1612.01840
