# 🧠 Multimodal Medical Image Synthesis & Cross-Modality Translation using Explainable AI

This project implements a dual GAN-based framework to:
- 🎯 Generate synthetic chest X-rays from radiology reports using a BERT-guided text-to-image GAN
- 🔄 Translate unpaired brain MRI scans into CT images using CycleGAN
- 👁️ Integrate explainable AI (Grad-CAM) to visualize disease-relevant regions in generated outputs

> 📄 You can read our full research paper here:  
> 👉 [ImageSynthesis_final_final_final.docx](./docs/ImageSynthesis_final_final_final.docx)

---

## 📌 Motivation

High-quality multimodal datasets (X-ray + reports, MRI + CT) are limited in size and availability. This restricts the training of robust, generalizable AI models in the medical imaging domain.  
This project aims to **generate synthetic datasets** that are medically valid and useful for downstream disease classification or diagnosis tasks.

---

## 💡 Key Features

- ✅ **Text-to-X-ray Generation:**  
  Synthesizes 256×256 chest X-rays from radiology report text using BERT embeddings and GANs.

- ✅ **Multimodal Fusion Architecture:**  
  Combines BERT-based language embeddings with GANs to create realistic disease-specific images.

- ✅ **MRI-to-CT Translation (CycleGAN):**  
  Converts unpaired MRI to CT scans while preserving anatomical structure via cycle consistency loss.

- ✅ **Explainable AI (Grad-CAM):**  
  Highlights disease-relevant regions in generated images to ensure clinical interpretability.

---

## 🧱 Architecture Overview

### 1️⃣ **X-ray Synthesis (Text → Image)**  
- **Input:** Radiology report (Findings + Impression)
- **Text Encoder:** BERT  
- **Generator:** ResNet-based GAN  
- **Losses:** Adversarial + L1 + Perceptual  
- **Output:** Synthetic X-ray image

### 2️⃣ **MRI → CT (CycleGAN)**  
- **Domains:** Unpaired MRI and CT datasets  
- **Generators:** MRI→CT and CT→MRI  
- **Discriminators:** Real vs fake for both domains  
- **Losses:** Adversarial + Cycle Consistency + Identity

---

## 🧪 Dataset & Preprocessing

- **Chest X-ray Dataset:**
  - 7,000 images paired with XML-based radiology reports
  - Extracted “Findings” and “Impression” sections for semantic input
  - Tokenized reports using BERT tokenizer
  - Resized images to 256×256 and normalized pixel values

- **MRI–CT Dataset:**
  - Unpaired images collected from open-access repositories
  - Images normalized and aligned to same resolution

---

## 📊 Loss Functions Used

- **Adversarial Loss (GAN)**
- **Cycle Consistency Loss (CycleGAN)**
- **Perceptual Loss (VGG-based)**
- **Content Loss (L1/L2 distance)**

---

## 🔍 Explainability (Grad-CAM)

Used Grad-CAM on discriminator and classifier outputs to:
- Visualize which parts of the image influence decisions
- Ensure generated images show relevant disease markers

---

## 🚀 Applications

- 📚 Data augmentation for rare medical cases
- 🧠 Multimodal model training (report + image)
- 👨‍⚕️ Clinical decision support for diagnosis
- 🏥 Radiation-free synthesis of CT from MRI in sensitive scenarios



