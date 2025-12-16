# 🚨 Anomaly Detection in Network Traffic using Agglomerative Hierarchical Clustering

A modular **Unsupervised Anomaly Detection System** built using:

- **Agglomerative Hierarchical Clustering**
- **Statistical network flow features**
- **UNSW-NB15 intrusion detection dataset**
- **PCA-based visualization** for interpretability

---

## 📝 Project Description

This project demonstrates an **end-to-end unsupervised anomaly detection pipeline** for network traffic analysis.

- The system uses the **UNSW-NB15 dataset**, a modern benchmark dataset containing normal traffic and multiple cyber-attack patterns.
- Network flows are represented using **statistical, temporal, and TCP-level features**.
- **Agglomerative Hierarchical Clustering (Ward linkage)** is applied to group similar traffic behaviors.
- **Rare clusters** (clusters with very low population) are treated as **anomalies**.
- The approach does **not rely on attack labels**, making it suitable for **unknown or evolving threats**.

---

## 📊 Dataset

The dataset is downloaded **automatically at runtime** using **KaggleHub**.

```python
import kagglehub
path = kagglehub.dataset_download("dhoogla/unswnb15")
```

- Dataset used: **UNSW-NB15**
- Training and testing splits are combined for unsupervised learning
- No dataset files are stored in this repository
- Data is cached locally by KaggleHub

---

## 🧠 Methodology

### 🔹 Feature Selection

The following network flow features are used to capture traffic volume, timing behavior, and TCP characteristics:

- **Packet & Byte Statistics:** `spkts`, `dpkts`, `sbytes`, `dbytes`
- **Traffic Rate & Load:** `rate`, `sload`, `dload`
- **Timing & Jitter:** `sinpkt`, `dinpkt`, `sjit`, `djit`
- **TCP Metrics:** `tcprtt`, `synack`, `swin`, `dwin`
- **Duration & Loss:** `dur`, `sloss`, `dloss`

---

### 🔹 Preprocessing
- Random sampling of **10,000 network flows** for scalability
- Feature normalization using **StandardScaler**

---

### 🔹 Clustering
- Algorithm: **Agglomerative Hierarchical Clustering**
- Linkage Method: **Ward**
- Distance Metric: **Euclidean**
- Number of clusters: **12**
- **Dendrogram** used to analyze cluster hierarchy

---

### 🔹 Anomaly Detection Logic
- Clusters containing **less than 2%** of total samples are labeled as **anomalies**
- Rare clusters correspond to **unusual or suspicious traffic behavior**

---

## 📈 Evaluation & Visualization

- **Silhouette Score** used to evaluate cluster quality
- **PCA (2D projection)** used for dimensionality reduction
- Scatter plots visualize:
  - Normal vs anomalous traffic
  - Cluster separation

---

## 🚀 Features

✅ Fully unsupervised anomaly detection  
✅ No dependency on labeled attack data  
✅ Handles unknown and zero-day attacks  
✅ PCA-based visual interpretability   

---

## 📂 Project Structure

```
Anomaly-Detection-Network-Traffic/
├── AgglomerativeClustering.ipynb
├── requirements.txt
├── README.md
├── LICENSE
└── .gitignore
```

---

## 🛠️ Setup & Installation

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/yourusername/Anomaly-Detection-Network-Traffic.git
cd Anomaly-Detection-Network-Traffic
```

### 2️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Project

```bash
jupyter notebook AgglomerativeClustering.ipynb
```

Run all cells in sequence to:
- Download the dataset
- Preprocess features
- Perform clustering
- Detect anomalies
- Visualize results

---

## 📊 Results

- **Silhouette Score:** ~0.55 (on sampled data)
- Clear separation between dense normal traffic clusters and sparse anomalous clusters
- PCA visualization confirms isolation of anomalous traffic regions

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🙌 Acknowledgements

- UNSW Canberra Cyber – UNSW-NB15 Dataset
- KaggleHub
- scikit-learn
- pandas
- numpy
- matplotlib & seaborn

---

## ⭐️ How to Contribute

Pull requests are welcome.  
For major changes, please open an issue to discuss the proposed updates.

---

## Author

**Shuvrajyoti Nath Mohajohn**  
[GitHub](https://github.com/ShuvrajyotiN)
