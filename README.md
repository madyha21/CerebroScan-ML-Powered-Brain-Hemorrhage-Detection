# CerebroScan-ML-Powered-Brain-Hemorrhage-Detection
A deep learning-based web application for automated detection of brain hemorrhages from CT scan images. This project utilizes a combination of Convolutional Neural Networks (CNN) and Long Short-Term Memory (LSTM) networks to analyze sequential CT scan data, providing a tool to assist medical professionals in rapid diagnosis.

📖 Overview

Brain hemorrhages are a critical medical condition requiring immediate intervention. CerebroScan aims to reduce diagnosis time by providing an initial, automated screening of CT scans. The model is trained on a large dataset of over 20,000 images to classify scans as "Hemorrhage" or "Normal."

The core innovation of this project is the use of a TimeDistributed CNN + LSTM architecture, which allows the model to consider the contextual sequence of slices in a CT scan, rather than just a single image, potentially leading to more accurate predictions.

✨ Features

· Advanced Model Architecture: Implements a hybrid CNN-LSTM model for spatio-temporal feature extraction from image sequences.

· User-Friendly Web Interface: A clean React.js frontend for easy upload and visualization of results.

· Robust Backend API: A Flask server that handles image preprocessing, model inference, and result delivery.

· Data Augmentation: Utilizes Keras' ImageDataGenerator to improve model generalization and combat overfitting.

🛠️ Tech Stack

· Backend & ML: Python, TensorFlow/Keras, NumPy, Flask
· Frontend: React.js
· Data Handling & Preprocessing: Keras ImageDataGenerator, OpenCV (implied)

🗂️ Project Structure

```bash
CerebroScan-Proj/
├── brain-ct-hemorrhage-dataset/  # Dataset directory (not in repo, link in setup)
│   ├── Training/
│   └── Testing/
├── ml-model/                     # Machine Learning Code & Training
│   ├── brain-ct-hemorrhage-inceptionv3-mahjoubi-checkpoint.ipynb
│   ├── models/                   # Saved model files (e.g., modelnew.h5, modelnew.keras)
│   └── requirements.txt          # Python dependencies for ML
├── backend/                      # Flask API
│   ├── app.py
│   ├── model_loader.py           # Code to load the saved .h5/.keras model
│   └── requirements.txt
├── frontend/                     # React Application
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── App.js
│   │   └── ...
│   ├── package.json
│   └── ...
└── README.md
```

🚀 Installation & Setup

Prerequisites

· Python 3.8+
· Node.js and npm

1. Clone the Repository

```bash
git clone https://github.com/[YourUsername]/CerebroScan.git
cd CerebroScan
```

2. Backend (Flask API) Setup

```bash
# Navigate to the backend directory
cd backend

# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: `venv\Scripts\activate`

# Install Python dependencies
pip install -r requirements.txt

# Start the Flask server
python app.py
```

The API should now be running on http://localhost:5000.

Backend requirements.txt example:

```
Flask==2.3.3
Flask-CORS==4.0.0
tensorflow==2.13.0
numpy==1.24.3
Pillow==10.0.0
```

3. Frontend (React App) Setup

Open a new terminal window.

```bash
# Navigate to the frontend directory
cd frontend

# Install npm packages
npm install

# Start the React development server
npm start
```

The application should now be running on http://localhost:3000.

🖥️ Usage

1. Ensure Servers are Running: Both the Flask backend (:5000) and React frontend (:3000) must be active.
2. Access the App: Open your web browser and go to http://localhost:3000.
3. Upload a CT Scan: Use the interface to upload a single CT scan image (.jpg or .png).
4. View Results: Click the "Analyze" button. The application will send the image to the backend, which will run it through the trained model and return a prediction (e.g., "Hemorrhage Detected" or "Normal Scan") along with a confidence score.

🧠 Model Architecture

The primary model is a TimeDistributed CNN followed by an LSTM.

· TimeDistributed CNNs: Apply 2D convolutional layers across each frame in an input sequence, extracting spatial features from individual images.

· LSTM Layer: Processes the sequence of feature vectors extracted by the CNN, learning temporal dependencies between consecutive CT scan slices.

· Final Layers: The output from the LSTM is passed through fully connected (Dense) layers with a final sigmoid activation for binary classification.

📊 Dataset

· Source: The dataset was sourced from Kaggle.
· Content: Contains over 20,000+ annotated CT scan images categorized into "Hemorrhage" and "Normal" classes.
· Structure: The data is split into Training and Testing directories for model development and evaluation.

👥 Authors

· Madiha Manzoor
· Haifa Bashir
· Amina Hameed

📜 License

This project is licensed under the MIT License - see the LICENSE file for details.

🙏 Acknowledgments

· Kaggle community for the publicly available brain CT hemorrhage dataset.
· Contributors and maintainers of TensorFlow, Keras, React, and Flask.
