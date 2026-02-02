# Contactless Fingerprint Recognition using Prototypical Networks

## Table of Contents
1. Introduction  
2. Background and Motivation  
3. Problem Definition  
4. Key Challenges  
5. Proposed Approach  
6. Model Architecture  
7. Few-Shot Learning with Prototypical Networks  
8. Training Methodology  
9. Inference Methodology  
10. Distance Metric and Decision Threshold  
11. Results and Observations  
12. Advantages of the Proposed System  
13. Limitations  
14. Future Scope  
15. Technology Stack  
16. Use Cases  
17. Author and Guide  
18. License  

---

## 1. Introduction
Fingerprint recognition is one of the most widely used biometric authentication techniques due to its uniqueness and permanence. Traditional fingerprint recognition systems rely on **physical contact** with sensors, which introduces hygiene concerns, sensor wear, and distortions caused by finger pressure.

This project focuses on **Contactless Fingerprint Recognition**, where fingerprint images are captured using camera-based or optical systems without physical contact. To address the challenge of limited labeled data in such systems, the project employs **Few-Shot Learning using Prototypical Networks**.

---

## 2. Background and Motivation
In real-world biometric systems:
- Collecting large labeled fingerprint datasets is expensive
- Contactless fingerprints suffer from variations in pose, illumination, and scale
- Conventional deep learning models overfit when trained on small datasets

Few-shot learning provides a solution by enabling models to **generalize from very few examples per class**.  
Prototypical Networks are particularly well-suited for biometric recognition because they rely on **metric learning** rather than large-scale classification.

---

## 3. Problem Definition
The goal of this project is to design a fingerprint recognition system that:
- Works reliably with **very limited labeled samples per identity**
- Can classify unseen fingerprints accurately
- Supports **unknown identity detection**
- Is computationally efficient during inference

---

## 4. Key Challenges
- Limited training samples per fingerprint class
- High intra-class variation in contactless fingerprints
- Inter-class similarity among fingerprint patterns
- Overfitting in traditional deep learning models

---

## 5. Proposed Approach
The system uses **Prototypical Networks**, a metric-based few-shot learning approach.

Core idea:
- Learn an embedding space where fingerprints of the same class cluster together
- Represent each class using a **prototype** (mean embedding)
- Perform classification by comparing distances to prototypes

---

## 6. Model Architecture
The architecture consists of the following components:

### 6.1 CNN Encoder
- Extracts high-level spatial features from fingerprint images
- Converts raw images into fixed-dimensional embedding vectors

### 6.2 MLP Layer
- Further refines CNN embeddings
- Helps in learning better class representations for prototype computation

### 6.3 Prototypical Network
- Computes one prototype per class
- Performs distance-based classification

---

## 7. Few-Shot Learning with Prototypical Networks
In Prototypical Networks:
- Each class is represented by a prototype
- A prototype is computed as the **mean of support embeddings**
- Classification is done using a distance metric (Euclidean distance)

This approach is similar to KNN but is:
- Faster during inference
- More robust in low-data scenarios
- Optimized end-to-end during training

---

## 8. Training Methodology (Episodic Training)
Training is performed using **episodes**, each simulating a few-shot classification task.

### Steps:
1. Sample N classes
2. Select K support samples per class
3. Select Q query samples per class
4. Pass all images through CNN encoder
5. Compute embeddings
6. Generate class prototypes from support embeddings
7. Compute distances between query embeddings and prototypes
8. Compute cross-entropy loss
9. Update model parameters using backpropagation

---

## 9. Inference Methodology
During inference:
1. Input a fingerprint image
2. Extract its embedding using the trained CNN
3. Compute distance to all class prototypes
4. Assign the class with minimum distance

---

## 10. Distance Metric and Decision Threshold
- **Euclidean Distance** is used to measure similarity
- A predefined threshold is applied:
  - Distance < threshold → Known identity
  - Distance ≥ threshold → Classified as unknown

This enables **open-set recognition**, which is crucial in biometric systems.

---

## 11. Results and Observations
- The model performs well even with very limited training data
- Metric-based learning improves generalization
- Faster inference compared to traditional KNN
- Robust to variations in contactless fingerprint images

---

## 12. Advantages of the Proposed System
- Requires minimal labeled data
- Contactless and hygienic
- Reduced sensor wear
- Efficient and scalable
- Suitable for real-world deployment

---

## 13. Limitations
- Performance depends on embedding quality
- Sensitive to threshold selection
- Requires careful episode design during training

---

## 14. Future Scope
- Integration of larger and diverse datasets
- Hyperparameter optimization
- Use of advanced encoders (Vision Transformers)
- Domain adaptation for cross-sensor fingerprints
- Real-time system deployment

---

## 15. Technology Stack
- **Programming Language**: Python  
- **Frameworks**: PyTorch / TensorFlow  
- **Model Type**: Prototypical Network  
- **Encoder**: CNN  
- **Distance Metric**: Euclidean  

---

## 16. Use Cases
- Touchless access control systems
- Secure authentication in healthcare
- Public security systems
- Remote biometric verification

---

## 17. Author and Guide
**Author:**  
Shristi Raushan  
Indian Institute of Technology Kharagpur  

