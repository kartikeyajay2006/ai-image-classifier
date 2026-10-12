<div align="center">

# 🧠 AI Image Classifier

**Drop in a photo and see what it is in about a second, with the top 3 guesses and a confidence score for each.**

[![Live demo](https://img.shields.io/badge/live_demo-Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)](https://ai-image-classifier-yw8jmptfdt64yxxyxprabj.streamlit.app/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.17-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![MobileNetV2](https://img.shields.io/badge/model-MobileNetV2_·_ImageNet-4285F4?style=flat-square)](https://keras.io/api/applications/mobilenet/)
[![OpenCV](https://img.shields.io/badge/OpenCV-preprocessing-5C3EE8?style=flat-square&logo=opencv&logoColor=white)](https://opencv.org/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)

**[▶ Try it live](https://ai-image-classifier-yw8jmptfdt64yxxyxprabj.streamlit.app/)**

</div>

---

## What it does

Upload a JPG or PNG and the app tells you what is in it (a dog, a car, a coffee mug) using **MobileNetV2**, a convolutional network pre-trained on the **1,000 ImageNet classes**.
You get the **top 3 predictions** with confidence scores, in a clean dark interface.

MobileNetV2 was chosen because it is small (about 3.5M parameters) and fast on a CPU. That is what lets it run on Streamlit Community Cloud's free tier with no GPU.

## How it works

```mermaid
flowchart LR
    U[Upload JPG / PNG] --> P[Pillow → NumPy]
    P --> R[OpenCV resize<br/>224 × 224]
    R --> N[preprocess_input<br/>scale to −1…1]
    N --> M[MobileNetV2<br/>ImageNet weights]
    M --> D[decode_predictions<br/>top 3]
    D --> UI[Labels + confidence]
```

The model is loaded once and cached, so every prediction after the first is fast.

## Run locally

```bash
git clone https://github.com/kartikeyajay2006/ai-image-classifier.git
cd ai-image-classifier
pip install -r requirements.txt
streamlit run model.py
```

Then open http://localhost:8501.

## Tech stack

| | |
|---|---|
| Model | TensorFlow / Keras MobileNetV2 (ImageNet) |
| Image processing | OpenCV (headless), Pillow, NumPy |
| UI and hosting | Streamlit, Streamlit Community Cloud |

## Ideas for next steps

- Fine-tune on a custom dataset (for example, Indian street food) with transfer learning
- Grad-CAM heat-maps to show *where* the model is looking
- Camera input for live classification

## Author

Built by **[Kartikeya Yadav](https://github.com/kartikeyajay2006)**.
[LinkedIn](https://www.linkedin.com/in/kartikeya2006/) · [Portfolio](https://kartikeya-portfolio-rx7w.vercel.app/)
