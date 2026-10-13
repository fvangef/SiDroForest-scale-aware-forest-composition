[README.md](https://github.com/user-attachments/files/33386918/README.md)
# SiDroForest scale-aware forest-composition analysis

Code and manuscript figures accompanying the revised study:

**Geographic generalisation and scale-aware Sentinel-2 forest-composition mapping across selected sites in Eastern Siberia**

Authors: Femke van Geffen, Ronny Hänsch, Begüm Demir, Stefan Kruse, Ulrike Herzschuh, and Birgit Heim.

## What this repository contains

This repository contains the analyses introduced downstream of the previously published SiDroForest Sentinel-2 Random Forest classifier. The classifier itself is **not presented as new here**. The repository covers:

1. abstention-aware independent evaluation using geographically separate reference observations;
2. hard-label contextual mapping of evergreen, summergreen and mixed forest;
3. sensitivity analysis across neighbourhood widths of **100–1000 m** and dominance thresholds of **0.50–0.90**;
4. secondary probability-context, entropy and parameter-stability analyses;
5. scale-matched comparison with **CGLS-LC100** and **GLC_FCS30**, with SiDroForest aggregated by categorical mode/majority to comparison-product support;
6. preparation and quality control of the final contextual forest-composition GeoTIFFs for data publication.

The nominal contextual map definition used in the manuscript is **hard-label spatial composition, nominal 500 m neighbourhood, 0.75 dominance threshold**. At 10 m pixel spacing this is implemented as a centred **51 × 51 pixel** window.

## Repository structure

```text
.
├── notebooks/
│   ├── SiDroForest_v16_final_analysis.ipynb
│   └── SiDroForest_prepare_contextual_maps_dataset.ipynb
├── figures/
│   └── publication and supplementary v16 figures (PNG/PDF)
├── results/
│   └── compact CSV summaries of manuscript results
├── data/
│   └── README.md describing required external inputs
├── requirements.txt
├── CITATION.cff
├── LICENSE
├── .env.example
└── .gitignore
```

## Installation

Create a Python environment and install the dependencies:

```bash
pip install -r requirements.txt
```

The GitHub copies of the notebooks have execution outputs cleared and Google Drive-specific paths removed. Run Jupyter from the repository root. By default the notebooks expect source data under `data/` and write generated analysis files to `outputs/`. Any important path can be overridden using the variables shown in `.env.example`.

## Data availability

Large input and output rasters are not duplicated in this code repository.

- Existing SiDroForest forest-type maps: **PANGAEA, DOI 10.1594/PANGAEA.973410**.
- SiDroForest Sentinel-2 labelled image patches: **PANGAEA, DOI 10.1594/PANGAEA.933268**.
- Previously developed RF classifier/example code: `https://github.com/fvangef/Code-supplement-for-Summer-and-Evergreen`
- New contextual forest-composition maps: **PANGAEA DOI to be added after publication/deposit assignment**.

See `data/README.md` for the expected inputs and provenance notes. The native CGLS-LC100 and GLC_FCS30 products are not redistributed here.

## Class convention

For contextual maps:

- `0` = masked / non-forest (GeoTIFF nodata in the publication product)
- `1` = evergreen needleleaf forest
- `2` = summergreen needleleaf forest
- `3` = mixed forest

The mixed class is a **spatial forest-composition class**, not a direct RF class and not a synonym for classifier uncertainty. A valid forest pixel is labelled evergreen or summergreen if the corresponding local hard-label proportion reaches the dominance threshold; otherwise it is labelled mixed.

## Independent evaluation

Masked outcomes are retained as model abstentions rather than silently discarded. Conditional accuracy is therefore reported together with coverage/abstention. Balanced accuracy and macro-F1 are only used when both reference classes occur in the classified subset.

## Global-product comparison

CGLS-LC100 and GLC_FCS30 are treated as independently developed comparison products, **not as ground truth**. The final analysis aggregates the finer SiDroForest categorical map to the comparison-product support using categorical mode/majority before calculating agreement.

## Reproducing the analysis

1. Install `requirements.txt`.
2. Obtain the required source datasets and configure paths using `.env.example` or the default layout in `data/README.md`.
3. Run `notebooks/SiDroForest_v16_final_analysis.ipynb`.
4. The analysis writes generated rasters/tables/figures to `outputs/`.
5. To stage the final contextual GeoTIFF dataset, run `notebooks/SiDroForest_prepare_contextual_maps_dataset.ipynb` after the main analysis.

## Related publications and datasets

- van Geffen, F., Hänsch, R., Demir, B., Kruse, S., Herzschuh, U., & Heim, B. (2025). *A Benchmark Dataset for Sentinel-2 Based Forest Type Classification in the Siberian Summergreen-Evergreen Forest Transition Zone*. IEEE JSTARS. DOI: **10.1109/JSTARS.2025.3562912**.
- van Geffen, F. et al. (2022). *SiDroForest: a comprehensive forest inventory of Siberian boreal forest investigations including drone-based point clouds, individually labeled trees, synthetically generated tree crowns, and Sentinel-2 labeled image patches*. Earth System Science Data, 14, 4967–4994. DOI: **10.5194/essd-14-4967-2022**.
- Existing map dataset: PANGAEA DOI **10.1594/PANGAEA.973410**.

## License

Code in this repository is provided under the MIT License. Source datasets retain their original licenses and citation requirements.
