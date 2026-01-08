# MOLE-CHECKER--APP
A mole checker refers to either a clinical skin exam performed by a dermatologist or a digital tool/app that helps individuals monitor their moles. Its primary purpose is to identify suspicious skin lesions that may indicate early stages of skin cancer, including melanoma, basal cell carcinoma, or squamous cell carcinoma

DermaAI: Intelligent Skin Lesion Analyzer

Hackathon Project: Leveraging Computer Vision & Deep Learning for Early Melanoma Detection.

💡 The Problem

Skin cancer is one of the most common cancers globally. Early detection is critical—melanoma survival rates drop significantly if not caught in Stage 1. However, access to dermatologists can be expensive and slow.

🚀 The Solution

DermaAI is a web-based diagnostic tool that acts as a "second pair of eyes." It uses a ResNet50 Convolutional Neural Network (CNN) to analyze images of skin lesions and provide a risk probability score in seconds.

🛠️ Technology Stack (Current)

1. Frontend: Streamlit 🔴

We chose Streamlit for its rapid deployment capabilities. It allows us to turn our Python data scripts into a fully interactive web application without needing a separate frontend team.

2. Preprocessing: OpenCV 👁️

Medical images often contain "noise" like hair or rulers. We implemented a "Digital Shaving" algorithm:

Morphological Blackhat: Detects hair structures.

Inpainting: Mathematically removes the hair and fills the gap with skin texture, ensuring the AI focuses on the lesion, not the hair.

3. AI Model: TensorFlow & ResNet50 🧠

We use Transfer Learning:

Base: ResNet50 (pre-trained on ImageNet) to extract features (edges, textures).

Head: Custom dense layers fine-tuned on dermoscopic datasets (HAM10000).

🗺️ Scalability Roadmap (Enterprise Architecture)

While the current prototype runs the model locally for low-latency demonstration, our production architecture utilizes Google Cloud Vertex AI:

Model Serving: The ResNet50 model will be deployed to a Vertex AI Endpoint. This allows the app to auto-scale from 10 to 10,000 concurrent users without crashing the Streamlit server.

Continuous Training: We will set up a Vertex AI Pipeline to automatically retrain the model as new medical data becomes available, improving accuracy over time.

Global Edge: The Streamlit frontend will be containerized (Docker) and deployed via Google Cloud Run for global accessibility.

📦 Installation

Clone the repo:

git clone [https://github.com/yourusername/derma-ai.git](https://github.com/yourusername/derma-ai.git)


Install Dependencies:

pip install -r requirements.txt


Run the App:

streamlit run app.py
