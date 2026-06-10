🔍 Just completed a workforce diversity analysis using unsupervised ML — and the findings were eye-opening.

For a recent data visualisation project, I applied K-Means clustering and PCA to U.S. workforce data to uncover how gender and ethnicity are distributed across economic sectors.

Here's what stood out:

📌 Construction is a demographic outlier — 93.7% white representation, making it the most ethnically homogeneous sector in the dataset. PCA confirmed it sits completely apart from every other industry.

📌 The Elbow Method pointed clearly to k=4 as the optimal cluster count for gender-based segmentation — a clean inflection that held across both gender and ethnicity clustering.

📌 High ethnic diversity isn't just a small-sector story. Sectors like Professional & Business Services and Leisure & Hospitality show strong demographic balance even at scale — meaning size alone doesn't predict homogeneity.

📌 Education & Health Services clustered separately from most other industries — consistent internal structure across both gender and ethnicity metrics.

🛠 Tech stack: Python · scikit-learn · pandas · seaborn · PCA · Shannon entropy

This project reinforced something I think about a lot in data work: unsupervised methods don't just find patterns — they surface the structural assumptions baked into an industry's workforce, ones that often go unquestioned.
