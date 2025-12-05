🌿 Plant Disease Detection (Deep Learning + FastAPI + Streamlit)

An end-to-end Plant Disease Detection System using PyTorch, ResNet-18, FastAPI REST backend, and Streamlit UI.
The model classifies leaf images into diseases and returns description + chemical treatments + bio-organic treatments from a curated dataset.

📺 Live Demo (GIF)

<p align="center"> <img src="assets/plant_disease_demo.gif" alt="Plant Disease Detection Demo" width="700"> </p>

✨ Features
🔍 Deep Learning Model

Trained on a cleaned custom dataset (loaded & processed in Colab).

ResNet-18 with custom classifier head (fine-tuned on your classes) — page 5 shows the ResNet model setup and classifier replacement 

plant_disease_detection_colab f…

Normalization, augmentations & resizing pipeline (page 3–4 of the notebook) 

plant_disease_detection_colab f…

Softmax probability with confidence score.

🚀 FastAPI Backend

/predict/ endpoint accepts an uploaded image.

Returns:

Disease name

Disease description

List of recommended treatments

Bio/organic solutions

Confidence score

🎨 Streamlit Frontend

Upload leaf image

Get prediction with confidence

Beautiful UI with treatment list formatting

Works locally or deployed on Streamlit Cloud

📄 Treatment Dataset Integration

CSV (Treatment_dataset.csv) is parsed to fetch:

disease description

chemical treatment recommendations

bio/organic options

String cleaning logic ensures clean bullet-point output.

🧠 Model Training Overview (Colab)

Your PDF notebook clearly documents the training process. Here is a summary extracted from it:

Dataset Loading

Dataset path defined on page 1, listing all disease class folder names (page 1 image) 

plant_disease_detection_colab f…

Automatic mapping of folder → class index.

Exploration & Visualization

Page 3 shows sample leaf images before processing (grid of preview images) showing dataset quality 

plant_disease_detection_colab f…

Train / Test / Validation Splits

Stratified splits shown on page 3 using train_test_split with fixed seeds.

Image Transformations

Defined on page 4:

Resize

Random Horizontal Flip

Random Rotation

Random ResizedCrop

Tensor conversion + normalization (same used in app) 

plant_disease_detection_colab f…

Model Architecture

On page 5:

Imported pretrained ResNet18

Replaced final FC layer with Linear(in_features, num_classes)

Set required parameters for training

Training Loop

Page 6 shows the full training loop:

Forward → loss → backward → optimizer step

Validation loss

Accuracy calculation per epoch


plant_disease_detection_colab f…

📁 Project Structure
📦 plant-disease-detection
├── backend/
│   ├── main.py                 # FastAPI server
│   ├── plant_disease_model.pth # Trained PyTorch model
│   ├── Treatment_dataset.csv   # Treatment details
├── frontend/
│   ├── app.py                  # Streamlit UI
├── notebooks/
│   ├── plant_disease_training.pdf  # Your Colab training PDF
├── README.md

🧪 API Usage (FastAPI)
POST /predict/

Upload an image to get prediction.

Request
multipart/form-data
file: image.jpg

Response
{
  "prediction": {
    "disease": "Strawberry - Leaf Scorch",
    "description": "Fungal disease causing purple-brown spots...",
    "treatments": [
      "Apply Copper oxychloride 50% WP",
      "Use Thiophanate methyl 70% WP"
    ],
    "bio_treatments": [
      "Neem oil 5ml/liter",
      "Trichoderma viride 2g/liter"
    ]
  },
  "confidence": 0.96
}


Run backend:

cd backend
uvicorn main:app --host 0.0.0.0 --port 8000

🎨 Streamlit UI

Run the frontend:

cd frontend
streamlit run app.py

UI Features

Displays uploaded leaf image

Shows disease prediction

Confidence score

Treatment recommendations

Clean bullet list formatting

🛠 Tech Stack
Component	Technology
Model Training	Python, PyTorch
Backend	FastAPI
Frontend	Streamlit
Deployment	Uvicorn / Streamlit Cloud
Dataset	Custom Plant Disease Dataset + Treatment CSV
📦 Installation
1️⃣ Clone repository
git clone https://github.com/your-username/plant-disease-detection.git
cd plant-disease-detection

2️⃣ Install dependencies
pip install -r requirements.txt


Typical requirements:

fastapi
uvicorn
torch
torchvision
pandas
pillow
streamlit

🤖 Model Details

Architecture: ResNet-18

Input size: 224 × 224

Loss: CrossEntropyLoss

Optimizer: Adam

Accuracy: ~High accuracy during validation 
