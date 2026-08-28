# Results

## Study Overview

The project analysed a Planet Tanager surface-reflectance hyperspectral scene covering coastal waters of Corozal Bay, Belize.

The scene contained 426 native hyperspectral bands. After applying the product's wavelength-quality information and inspecting the upper spectral edge, 365 bands were retained for the final spectral analysis, covering approximately 376.44–2484.13 nm.

---

## Coastal Water Extraction

The initial coastal-water mask contained:

**103,239 water pixels**

Connected-component analysis identified the main contiguous water body:

**94,550 pixels**

This main water body was used for the subsequent spectral feature and clustering analysis.

---

## Relative Spectral Indicators

Three relative spectral indicators were investigated:

- Green / Blue
- Red / Green
- NIR / Red

The indicators showed different spatial behaviour across the coastal water body.

Pearson correlation results were:

| Indicator Pair | Correlation |
|---|---:|
| Green / Blue vs Red / Green | -0.6169 |
| Green / Blue vs NIR / Red | -0.1304 |
| Red / Green vs NIR / Red | 0.0235 |

The low correlation between Red / Green and NIR / Red indicates that these indicators captured substantially different aspects of spectral variability in the scene.

---

## PCA

The reliable hyperspectral data were standardized before PCA.

The first six principal components retained:

**96.93% of the total spectral variance**

Variance explained:

| Components | Cumulative variance |
|---|---:|
| PC1 | 80.49% |
| PC1–PC2 | 90.04% |
| PC1–PC3 | 94.81% |
| PC1–PC6 | 96.93% |
| PC1–PC20 | 99.07% |

The first six PCs were therefore selected as the feature space for K-means clustering.

---

## K-Means Clustering

Candidate cluster counts from K = 2 to K = 8 were evaluated using inertia and a sampled silhouette score.

The best sampled silhouette score occurred at:

**K = 3**

with a silhouette score of:

**0.4022**

The three spectral classes contained:

| Spectral Class | Pixels | Share |
|---|---:|---:|
| Class 1 | 60,549 | 64.04% |
| Class 2 | 32,650 | 34.53% |
| Class 3 | 1,351 | 1.43% |

---

## Spectral Characteristics

Mean reflectance across the final spectral dataset was:

| Spectral Class | Mean Reflectance |
|---|---:|
| Class 1 | 0.1154 |
| Class 2 | 0.1322 |
| Class 3 | 0.0607 |

This produced three overall reflectance regimes:

- **Class 2:** highest overall reflectance
- **Class 1:** intermediate reflectance
- **Class 3:** lowest overall reflectance

The strongest reliable separation in the visible region occurred at:

**570.83 nm**

Reflectance at 570.83 nm:

| Spectral Class | Reflectance |
|---|---:|
| Class 1 | 0.1867 |
| Class 2 | 0.2255 |
| Class 3 | 0.1176 |

Across approximately 401–696 nm, the same general ordering was observed:

**Class 2 > Class 1 > Class 3**

---

## Spatial Distribution

Three exploratory image-row-based zones were used to compare spectral-class composition.

| Zone | Pixels | Dominant Class | Dominant Percentage | Shannon Diversity |
|---|---:|---|---:|---:|
| Zone 1 | 21,059 | Class 2 | 58.26% | 0.6795 |
| Zone 2 | 45,978 | Class 1 | 81.53% | 0.4845 |
| Zone 3 | 27,513 | Class 1 | 51.88% | 0.8475 |

### Main spatial observations

**Zone 1**

Spectral Class 2 was dominant at 58.26%.

**Zone 2**

Spectral Class 1 strongly dominated at 81.53%, making this the most spectrally homogeneous zone.

**Zone 3**

Zone 3 had the highest Shannon diversity (0.8475), indicating the greatest mixture of spectral classes.

Most notably, **96.74% of all Spectral Class 3 pixels occurred in Zone 3**.

---

## Interpretation

The analysis demonstrates substantial spatial and spectral heterogeneity within the mapped coastal waters.

The clustering results identify three data-driven spectral regimes with different reflectance characteristics and spatial distributions.

Spectral Class 3 is particularly notable because it is:

- the smallest class,
- the darkest class in overall mean reflectance,
- spectrally distinct from the other classes,
- and highly concentrated in Zone 3.

However, the available analysis does not provide sufficient evidence to assign these classes directly to specific physical water-quality parameters.

They should therefore be interpreted as **spectral regimes**, not as validated categories such as:

- high turbidity,
- low turbidity,
- suspended sediment,
- chlorophyll-a,
- or polluted water.

---

## Validation Requirements

Quantitative interpretation would require additional information such as:

- coincident field water-quality measurements,
- laboratory observations,
- validated empirical relationships,
- or a physically based / statistically validated retrieval model.

Future observations could therefore be used to determine whether the spectral classes correspond to specific water-quality conditions.

---

## Overall Conclusion

Planet Tanager hyperspectral imagery provided sufficient spectral information to identify clear spatial and spectral variability within the Corozal Bay coastal-water scene.

The combination of water masking, spectral feature analysis, PCA, and unsupervised K-means clustering produced a reproducible framework for identifying distinct coastal-water spectral regimes.

The results provide a foundation for future quantitative water-quality retrieval and validation using additional Tanager acquisitions and field observations.