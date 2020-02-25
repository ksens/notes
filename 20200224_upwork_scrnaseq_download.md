# Deliverable

## Summary

Python script to download metadata from all subpages of https://support.10xgenomics.com/single-cell-gene-expression/datasets

## Details

The website linked above hosts publicly available single cell gene expression datasets. I want someone to develop a web-scraping project to download metadata and data files and store them locally wherever the script is being run. 

### Metadata categories

This is the data hierarchy on the website linked above:

Single Cell Gene Expression Datasets:

```
- category
   - cell_ranger_version
      - dataset
```

For example, if I annotate the snapshot used below:

```
- [category] Chromium Next GEM Demonstration (v3.1 Chemistry)
   - [cell_ranger_version] Cell Ranger 3.0.2
      - [dataset] 5k Peripheral blood mononuclear cells (PBMCs) from ...
      - ...
   - [cell_ranger_version] Cell Ranger 3.1.0
      - [dataset] 5k Peripheral blood mononuclear cells (PBMCs) from ...
- [category] Chromium Demonstration (v3 Chemistry)
   - [cell_ranger_version] Cell Ranger 3.0.0
      - ...
```

### Metadata download format

The script should visit each `dataset` URL within each `category/cell_ranger_version` and download the metadata into a YAML format

e.g. in the attachment `10x_dataset_metadata_example.png`, the YAML should be something like:

```
3.0.2/5k_pbmc_v3: 
  dataset_num: 1
  category: Chromium Next GEM Demonstration (v3.1 Chemistry)
  cell_ranger_version: Cell Ranger 3.0.2
  cell_ranger_version_shortcode: 3.0.2,
  dataset: 5k Peripheral blood mononuclear cells (PBMCs) from a healthy donor (v3 chemistry),
  url: https://support.10xgenomics.com/single-cell-gene-expression/datasets/3.0.2/5k_pbmc_v3,
  url_shortcode: 3.0.2/5k_pbmc_v3,
  dataset_page_fulltext: >
     Peripheral blood mononuclear cells (PBMCs) from a healthy donor (the same cells were used to generate 5k_pbmc_v3_nextgem).

     PBMCs are primary cells with relatively small amounts of RNA (~1pg RNA/cell).

     Libraries were prepared following the  Chromium Single Cell 3ʹ Reagent Kits v3 User Guide (CG000183 RevA).

     5,025 cells detected
     Sequenced on Illumina NovaSeq with approximately 76,406 reads per cell
     28bp read1 (16bp Chromium barcode and 12bp UMI), 91bp read2 (transcript), and 8bp I7 sample barcode
     run with --expect-cells=5000
  bulleted_list_in_fulltext:
     - 5,025 cells detected
     - Sequenced on Illumina NovaSeq with approximately 76,406 reads per cell
     - 28bp read1 (16bp Chromium barcode and 12bp UMI), 91bp read2 (transcript), and 8bp I7 sample barcode
     - run with --expect-cells=5000
  num_cells_approx: 5025
3.0.2/5k_pbmc_v3_nextgem: 
  dataset_num: 2
  # ...
```

The script should download metadata from all subpages of the parent URL into one large YAML file.


# Type of freelancer

Individual
