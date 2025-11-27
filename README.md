Multi-Model Self-Supervised Learning Framework for Pancreatic Cancer Detection and Stage Prediction

This repository contains a complete end-to-end medical AI framework designed for automated pancreas segmentation, tumor–vessel proximity analysis, and pancreatic cancer stage prediction from 3D abdominal CT scans.
The system is built using a combination of:

Self-Supervised Learning (SimCLR)

3D UNet segmentation

Vessel extraction and distance-transform analysis

Machine-learning–based staging

Streamlit application for real-time inference

🔬 Dataset Used: CURVAS-PDAC (multi-center CT dataset for pancreatic cancer vascular analysis)

🚀 Key Features
1️⃣ Self-Supervised Encoder (SimCLR)

Trains on unlabeled CT scans

Learns anatomical structure features

Reduces dependence on large annotated datasets

2️⃣ Pancreas Segmentation (3D UNet)

Fine-tuned using SSL encoder

Produces high-quality pancreas masks

Works with low-contrast abdominal CTs

3️⃣ Vessel Isolation

Extracts SMA, SMV, PV, hepatic artery regions

Computes spatial proximity using distance transforms

Used for cancer resectability prediction

4️⃣ Tumor–Vessel Feature Engineering

Extracted metrics include:

Min tumor–vessel distance

Vessel encasement ratio

Contact fraction

Overlap percentage

Distance transform statistics

5️⃣ Stage Prediction

A classical ML classifier assigns cancer stages:

Resectable

Borderline

Locally Advanced

6️⃣ Streamlit Web Application

Upload CT (DICOM ZIP) → automatic:
✔ Segmentation
✔ Vessel analysis
✔ Stage prediction
✔ Visualization

🧠 Project Architecture
PancreasProject/
│
├── data/
│   ├── training_set/
│   └── tumor_data/
│
├── src/
│   ├── pretrain_ssl_simclr.py
│   ├── finetune_unet_ssl.py
│   ├── infer_unet_ssl.py
│   ├── extract_vessels.py
│   ├── extract_tumor_vessel_features.py
│   ├── train_stage_classifier.py
│   ├── app_streamlit.py
│   └── ...
│
├── outputs/
│   ├── checkpoints_ssl/
│   ├── pseudo_tumor_masks/
│   ├── vessel_masks/
│   ├── stage_features.csv
│   ├── tumor_vessel_features.csv
│   └── unet_tumor.pth
│
└── README.md

🔧 Installation
Clone Repository
git clone https://github.com/<your-username>/PancreasProject.git
cd PancreasProject

Create Virtual Environment
python -m venv venv
source venv/bin/activate  # (Linux/Mac)
venv\Scripts\activate     # (Windows)

Install Dependencies
pip install -r requirements.txt

🏋️‍♂️ Training the Models
1. Self-Supervised Pretraining
python src/pretrain_ssl_simclr.py

2. Fine-tune 3D UNet
python src/finetune_unet_ssl.py

3. Train Stage Classifier
python src/train_stage_classifier.py

🔍 Inference Pipeline
Segment Pancreas
python src/infer_unet_ssl.py --input scan.nii.gz

Extract Vessels
python src/extract_vessels.py

Compute Tumor–Vessel Features
python src/extract_tumor_vessel_features.py

Stage Prediction
python src/predict_stage.py

🌐 Run Streamlit App
streamlit run src/app_streamlit.py


Upload DICOM (.zip) → View segmentation, vessels, and stage output.

📊 Results
Task	Score
Pancreas Segmentation	Dice: 0.74–0.81
Pseudo Tumor Mask	Dice: 0.62–0.70
Stage Prediction	Accuracy: ~88%
🧬 Novelty of the Project

Combines Self-Supervised Learning + Medical Segmentation + Vessel Analytics

Developed fully using CURVAS-PDAC, rare and specialized dataset

End-to-end automated clinical pipeline

Vessel-aware staging (clinically meaningful)

Real-time deployable using Streamlit
