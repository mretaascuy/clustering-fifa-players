# FIFA Players Clustering - Unsupervised Learning

Unsupervised learning project clustering FIFA players by skill profile, developed as part of the Data Science Diploma at FaMAF - Universidad Nacional de Córdoba, Argentina.

## Dataset

- FIFA player dataset filtered to field players with OVR >= 70
- Goalkeepers excluded (different skill profile)
- 17 skill attributes selected across 5 categories: defense, attack, creation, speed and physical
- Feature selection based on domain expertise using Liverpool FC (Premier League) as reference via sofifa.com

## Project Structure

- `fifa_players_clustering.ipynb` - Full clustering pipeline: EDA, feature selection, PCA, K-Means and Hierarchical Clustering with t-SNE visualization

## Methodology

### Exploratory Data Analysis
- Analysis of general skill distributions (Pace, Shooting, Passing, Dribbling, Defense, Physical)
- Strong positive correlations found: PAS-DRI (0.85), SHO-DRI (0.77), PAS-SHO (0.68)
- Bimodal distribution in Defense attribute, suggesting clear separation between attacking and defensive players

### Feature Engineering
- Selected 17 attributes across 5 categories:
  - **Defense:** Interceptions, Standing Tackle, Sliding Tackle
  - **Attack:** Finishing, Shot Power
  - **Creation:** Vision, Short Passing, Long Passing
  - **Speed:** Acceleration, Sprint Speed
  - **Physical:** Strength, Stamina

### Dimensionality Reduction
- StandardScaler applied to normalize features
- PCA applied: 9 components retained 95% of variance

### Clustering Methods

**K-Means (5 clusters)**
- Elbow method used to select optimal number of clusters
- Silhouette analysis showed overlapping clusters
- K-Means struggled with non-spherical cluster shapes

**Hierarchical Clustering (Ward method, 6 clusters)**
- Ward linkage minimizes intra-cluster variance
- t-SNE used for 2D visualization
- Better separation than K-Means for most clusters

## Key Findings

- Players cluster by **skill profile rather than playing position** — a fast offensive midfielder may cluster with wingers or forwards
- Hierarchical clustering outperformed K-Means for this dataset
- Clusters 2 and 4 showed overlap, confirming that some players have interchangeable skill profiles
- FIFA positional labels don't always reflect actual playing style or individual capabilities
- Flexible players (e.g. attacking midfielders who can play wide) naturally generate overlapping clusters

## Tools & Libraries

Python, scikit-learn, scipy, pandas, numpy, matplotlib, seaborn, plotly, yellowbrick, VS Code.
