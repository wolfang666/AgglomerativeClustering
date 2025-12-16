# AgglomerativeClustering
Anomaly Detection in Network Traffic Using Agglomerative Hierarchical Clustering

This project implements an unsupervised anomaly detection system for network traffic using Agglomerative Hierarchical Clustering on the UNSW-NB15 intrusion detection dataset. The objective is to identify rare and suspicious network behaviors without relying on labeled attack data.

## 📊 Dataset
The UNSW-NB15 dataset is downloaded automatically at runtime using KaggleHub.

```python
import kagglehub
path = kagglehub.dataset_download("dhoogla/unswnb15")