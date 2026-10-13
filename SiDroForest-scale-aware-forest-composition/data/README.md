# Input data

Large source datasets are intentionally **not included** in this GitHub repository.
The code repository contains the analysis; raster products and reference datasets should be obtained from their original repositories/publications.

The original analysis used a directory structure equivalent to:

```text
data/
├── Clustered_LS_+9_28nov/
│   └── RF_old_full_sentinel2.pkl
├── Sidroforest/
│   ├── classified_old_full_s2_RF/
│   │   └── sidroforest_old_sentinel_RF_confidence_summary_clean.csv
│   └── FCS30_forest_classes/            # optional mapping audit derivatives
├── FCS30/
│   ├── GLC_FCS30_2020_*.tif             # native FCS30 source tiles
│   ├── siberia_cropped_plots_RAW_RF_no_mixed_NDVI068/
│   │   └── raw_rf_no_mixed_plot_evaluation_summary.csv
│   └── pangaea_shapefiles_RAW_RF_no_mixed_NDVI068/
│       └── pangaea_raw_rf_no_mixed_summergreen_evergreen_masked_excluded_summary.csv
├── globcover_6_classes_named_per_plot/
│   ├── LK.tif
│   ├── LK2.tif
│   └── YA.tif
└── Cropped_Images_6_classes_downsampled/
    ├── LK_Cropped_Image_Downsampled.tif
    └── YA_Cropped_Image_Downsampled.tif
```

You do not need to reproduce this exact folder layout if you set the path environment variables in `.env.example`.

## Published SiDroForest sources

- Previously published 10 m SiDroForest forest-type maps and CGLS derivatives: PANGAEA DOI **10.1594/PANGAEA.973410**.
- Sentinel-2 labelled image patches: PANGAEA DOI **10.1594/PANGAEA.933268**.
- The contextual forest-composition GeoTIFFs generated for the revised study should be cited from the new PANGAEA deposit once its DOI is assigned.

The native global land-cover products (CGLS-LC100 and GLC_FCS30) are not redistributed here.
