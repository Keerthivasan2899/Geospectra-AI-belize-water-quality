# Methodology

## 1. Study Area and Data

The project analyses coastal waters in Corozal Bay, Belize using a Planet Tanager surface-reflectance hyperspectral scene acquired on 24 August 2025. The dataset contains 426 native spectral bands, a native spatial resolution of 32.86 m, and is referenced in EPSG:32616 (WGS 84 / UTM Zone 16N).

## 2. Hyperspectral Data Exploration

The HDF5/HDF-EOS structure was inspected to identify the main hyperspectral data field and associated metadata. The surface-reflectance cube contains 426 spectral bands with a spatial shape of 671 × 763 pixels.

## 3. Spectral Quality Screening

The product's `good_wavelengths` metadata was used to identify reliable spectral bands. This removed 58 bands in two contiguous wavelength regions:

- 1342.41–1437.55 nm
- 1782.58–1967.21 nm

Additional inspection of the upper spectral edge identified instability in the final three retained wavelengths around 2489–2499 nm. These three upper-edge bands were excluded from subsequent spectral-signature analysis, leaving 365 final bands spanning 376.44–2484.13 nm.

## 4. Coastal Water Masking

A previously developed coastal-water mask was applied to the scene. The initial mask contained 103,239 water pixels. Connected-component analysis was then used to isolate the largest contiguous water region, producing a main connected water body containing 94,550 pixels.

## 5. Relative Spectral Indicators

Three exploratory spectral ratios were calculated within the water mask:

- Green / Blue
- Red / Green
- NIR / Red

The ratios were cleaned using percentile-based filtering for exploratory analysis and displayed using a 5th–95th percentile stretch to reduce the influence of extreme values on visualization.

These indicators were treated as relative spectral features rather than calibrated water-quality measurements.

## 6. Exploratory Spatial Zones

The main connected water body was divided into three exploratory image-row-based zones:

- Zone 1: rows < 300
- Zone 2: rows 300–449
- Zone 3: rows ≥ 450

These zones were used to compare relative spectral indicators and spectral-class composition. They are not measured distance-to-coast zones or validated water-quality categories.

## 7. PCA Dimensionality Reduction

The reliable spectral data were standardized across water pixels using `StandardScaler`. Principal Component Analysis was then applied to reduce the dimensionality of the hyperspectral feature space.

The first six principal components retained 96.93% of the total standardized spectral variance and were selected as the feature space for unsupervised clustering.

## 8. Unsupervised K-Means Clustering

K-Means clustering was evaluated for K = 2 through K = 8. Inertia and a sampled silhouette score were used to compare candidate cluster counts. K = 3 produced the highest sampled silhouette score (0.4022) among the tested solutions.

The final three data-driven spectral classes contained:

| Class | Pixels | Share |
|---|---:|---:|
| Spectral Class 1 | 60,549 | 64.04% |
| Spectral Class 2 | 32,650 | 34.53% |
| Spectral Class 3 | 1,351 | 1.43% |

## 9. Spectral Class Analysis

Mean hyperspectral signatures were calculated from the original surface-reflectance values for each K-Means class. Overall mean reflectance showed three distinct regimes, with Class 2 having the highest mean reflectance, Class 1 intermediate, and Class 3 the lowest.

The strongest reliable visible-region class separation occurred at 570.83 nm.

## 10. Spatial Class Analysis

Cluster labels were mapped back to their original image positions to examine their spatial distribution. The class composition of the three exploratory zones was then compared.

Zone 2 was strongly dominated by Spectral Class 1, while Zone 3 contained nearly all Spectral Class 3 pixels. Shannon diversity was calculated to characterize the degree of spectral-class heterogeneity within each exploratory zone.

## 11. Interpretation and Validation

The resulting spectral classes describe data-driven spectral regimes within the mapped coastal waters. They should not be assigned directly to physical water-quality parameters such as turbidity, chlorophyll-a, or suspended sediment concentration without independent observations or a validated retrieval model.

The analysis is therefore exploratory and intended to demonstrate how hyperspectral open data can be used to characterize coastal-water optical variability and identify candidate spectral regimes for future validation.