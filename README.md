# GeoSpectra AI

## Hyperspectral Assessment of Coastal Water Quality in Corozal, Belize Using Planet Tanager Open Data

An independent geospatial research project developed for the **Planet Tanager Open Data Competition 2026**.

This project investigates how high-dimensional hyperspectral surface-reflectance data from Planet Tanager can be used to characterize spatial variability in coastal waters and identify distinct spectral water regimes in **Corozal Bay, Belize**.

> **Important:** The current analysis is exploratory. The spectral classes and indices produced by this project represent relative optical/spectral variability and are **not calibrated measurements** of turbidity, chlorophyll-a, suspended sediment concentration, or other water-quality parameters.

---

## Study Area

**Corozal, Belize**

The analysis focuses on coastal waters within Corozal Bay using a Planet Tanager hyperspectral scene acquired on **24 August 2025**.

---

## Dataset

- **Satellite / Sensor:** Planet Tanager
- **Product:** Surface Reflectance
- **Native spectral bands:** 426
- **Bands retained for analysis:** 365
- **Approximate final spectral range:** 376.44–2484.13 nm
- **Native spatial resolution:** 32.86 m
- **Coordinate Reference System:** EPSG:32616 — WGS 84 / UTM Zone 16N
- **Scene acquisition date:** 24 August 2025
- **File format:** HDF5 / HDF-EOS

---

## Research Objectives

1. Explore and document the Tanager hyperspectral data structure and metadata.
2. Visualize the hyperspectral scene using RGB composites and individual spectral bands.
3. Investigate representative hyperspectral signatures.
4. Develop a coastal-water mask and isolate the main connected water body.
5. Calculate relative spectral indicators and examine their spatial variability.
6. Apply dimensionality reduction and unsupervised machine learning to identify spectrally distinct coastal-water regimes.
7. Evaluate the spatial distribution and spectral characteristics of the resulting classes.

---

## Methodology

```text
Planet Tanager Surface Reflectance
              │
              ▼
      HDF5 Data Exploration
              │
              ▼
      RGB & Spectral Visualization
              │
              ▼
     Spectral Signature Analysis
              │
              ▼
       Coastal Water Masking
              │
              ▼
 Relative Spectral Feature Mapping
              │
              ▼
   Spectral Quality Screening
              │
              ▼
     PCA Dimensionality Reduction
              │
              ▼
      K-Means Unsupervised Clustering
              │
              ▼
     Spatial Spectral-Class Mapping
              │
              ▼
     Statistical & Spatial Analysis

```

---

## Key Visual Results

### Full Hyperspectral Class Signatures

Mean hyperspectral signatures for the three data-driven coastal-water spectral classes identified through the analysis.

![Full hyperspectral class signatures](outputs/figures/full_hyperspectral_class_signatures.png)

### Visible-Region Spectral Signatures

The visible region shows clear differences in reflectance between the three spectral classes, with the strongest reliable visible separation occurring near 570.83 nm.

![Visible spectral class signatures](outputs/figures/visible_spectral_class_signatures.png)

### Spatial Distribution of Spectral Classes

K-means clustering reveals spatially distinct hyperspectral spectral regimes across the main connected coastal-water body.

![Spatial distribution of hyperspectral coastal water classes](outputs/maps/spatial_spectral_class_map.png)

---

## Notebook Pipeline

| Notebook | Description | Status |
|---|---|---|
| `01_Data_Exploration.ipynb` | HDF5 structure, metadata and spectral information | ✅ Complete |
| `02_Data_Visualization.ipynb` | RGB and hyperspectral visualization | ✅ Complete |
| `03_Spectral_Signature_Analysis.ipynb` | Representative hyperspectral signatures | ✅ Complete |
| `04_Coastal_Water_Mask_and_Analysis.ipynb` | Coastal-water masking and analysis | ✅ Complete |
| `05_Coastal_Water_Quality__Feature_Mapping.ipynb` | Relative spectral feature mapping | ✅ Complete |
| `06_Hyperspectral_Coastal_Water_Clustering.ipynb` | PCA and unsupervised spectral clustering | ✅ Complete |

---

## Key Results

### Coastal Water Extraction

The original coastal-water mask identified **103,239 water pixels**. Connected-component analysis isolated the main contiguous coastal-water body containing **94,550 pixels**.

### Relative Spectral Indicators

Three exploratory spectral indicators were evaluated:

- Green / Blue
- Red / Green
- NIR / Red

Their Pearson correlations were:

| Indicator Pair | Pearson Correlation |
|---|---:|
| Green / Blue vs Red / Green | -0.6169 |
| Green / Blue vs NIR / Red | -0.1304 |
| Red / Green vs NIR / Red | 0.0235 |

These results indicate that the three indicators capture different aspects of spectral variability within the coastal-water scene.

### PCA and Clustering

After spectral quality screening, **365 spectral bands** were retained for the final analysis.

The first **6 principal components retained 96.93% of the spectral variance**.

K-Means clustering was evaluated for K = 2-8, with **K = 3 producing the highest sampled silhouette score of 0.4022**.

The final spectral classes were:

| Spectral Class | Pixels | Percentage |
|---|---:|---:|
| Class 1 | 60,549 | 64.04% |
| Class 2 | 32,650 | 34.53% |
| Class 3 | 1,351 | 1.43% |

### Spectral Characteristics

The mean reflectance of the three classes was:

| Spectral Class | Mean Reflectance |
|---|---:|
| Class 1 | 0.1154 |
| Class 2 | 0.1322 |
| Class 3 | 0.0607 |

Class 2 had the highest overall reflectance, Class 1 was intermediate, and Class 3 had the lowest overall reflectance.

The strongest reliable visible-region separation occurred near **570.83 nm**.

### Spatial Distribution

Three exploratory spatial zones were compared with the K-Means classes.

Zone 2 was strongly dominated by **Spectral Class 1 (81.53%)**, while Zone 3 showed the highest spectral diversity and contained **96.74% of all Spectral Class 3 pixels**.

These results demonstrate clear spatial heterogeneity within the analysed coastal-water body.

---

## Scientific Interpretation

The analysis demonstrates substantial spatial and spectral heterogeneity within the mapped coastal waters of Corozal Bay.

The combination of hyperspectral surface reflectance, spectral quality screening, relative spectral indicators, PCA dimensionality reduction, and unsupervised K-Means clustering provided a reproducible framework for identifying distinct spectral regimes within the main coastal-water body.

The three spectral classes showed different reflectance characteristics and spatial distributions. Spectral Class 2 exhibited the highest overall mean reflectance, Spectral Class 1 showed intermediate reflectance, and Spectral Class 3 had the lowest mean reflectance and was strongly localized within Zone 3.

These classes should be interpreted as **data-driven spectral regimes**, not as directly measured water-quality categories.

Without coincident field observations or a validated retrieval model, the current analysis cannot establish whether a particular spectral class corresponds to high or low turbidity, suspended sediment concentration, chlorophyll-a, or another specific water-quality parameter.

The results therefore provide an exploratory hyperspectral characterization of coastal-water variability and a foundation for future quantitative water-quality retrieval and validation.

---

## Limitations

This project has several important limitations:

1. **Single-scene analysis:** The study is based on one Planet Tanager acquisition from 24 August 2025, so the results describe spectral variability for this scene and date rather than long-term coastal-water conditions.

2. **No coincident field measurements:** No in-situ water-quality observations were available for calibration or independent validation.

3. **Relative indicators:** The Green / Blue, Red / Green, and NIR / Red features are exploratory spectral indicators and are not validated retrieval algorithms for specific water-quality constituents.

4. **Unsupervised classes:** K-Means identifies spectral similarity groups. The resulting classes do not automatically represent physical categories such as clear water, turbid water, suspended sediment, or high/low chlorophyll-a.

5. **Exploratory spatial zones:** Zones 1–3 were defined using image-row positions. They should not be interpreted as measured distance-from-shore or hydrological zones.

6. **Spectral edge effects:** Additional inspection identified instability in the upper spectral edge, requiring removal of three wavelengths beyond the product's `good_wavelengths` screening.

7. **Validation requirement:** Quantitative water-quality interpretation requires independent field observations, laboratory measurements, or a validated remote-sensing retrieval model.

---

## Reproducibility

The project was developed using Python, Jupyter Notebook, GIS tools, and machine-learning libraries.

The required Python dependencies are listed in `requirements.txt`.

Create a virtual environment:

```bash
python -m venv geospectra_env
geospectra_env\Scripts\activate
pip install -r requirements.txt
01 → 02 → 03 → 04 → 05 → 06

```
---

## Future Work

Future development of this project could focus on:

- Integrating coincident field water-quality measurements for validation.
- Developing quantitative turbidity and total suspended solids (TSS) retrievals.
- Investigating chlorophyll-sensitive hyperspectral features.
- Incorporating additional Planet Tanager acquisitions for temporal analysis.
- Testing supervised machine-learning approaches using validated field observations.
- Developing distance-to-coast and hydrodynamic spatial gradients.
- Performing uncertainty and sensitivity analysis.
- Comparing Tanager-derived spectral features with other open satellite datasets.

```
---

## Author

**Keerthivasan S**

GitHub: [Keerthivasan2899](https://github.com/Keerthivasan2899)

---

## Competition

Prepared as an independent research project for the **Planet Tanager Open Data Competition 2026**.
