# VerdictEye – Predict Court Judgements  

VerdictEye is an AI-driven legal text classification project that predicts relevant **Indian Penal Code (IPC) sections** based on criminal incident descriptions. The system also generates possible verdict statements using predefined templates, making the outputs easier to interpret in a legal context.  

This repository contains the Kaggle notebook implementation, where a **BERT-based classifier** is fine-tuned to automate IPC prediction and provide transparent results.  

---

## Project Overview  
- **Problem Statement:** Legal professionals often spend significant time mapping case details to IPC sections. Manual analysis is slow, complex, and error-prone.  
- **Solution:** VerdictEye leverages Natural Language Processing (NLP) to automate the mapping of incidents to IPC sections, with confidence scores and verdict-like statements to assist understanding.  
- **Key Features:**  
  - Preprocessing and cleaning of incident descriptions  
  - Fine-tuning of **BERT (bert-base-uncased)** for multi-class classification  
  - IPC predictions with associated confidence levels  
  - Human-readable verdict templates for better interpretability  
  - Support for both single predictions and top-k predictions  

---

## Workflow  
1. **Training (`train_bert.py`)**  
   - Loads and validates the dataset  
   - Handles class imbalance by removing IPC sections with fewer than two samples  
   - Encodes IPC labels numerically and saves the encoder  
   - Tokenizes text using the BERT tokenizer  
   - Fine-tunes BERT for three epochs with AdamW optimizer and learning rate scheduling  
   - Achieved around **89.5% validation accuracy** across 311 IPC classes  

2. **Inference (`verdict_bert.py`)**  
   - Loads the trained model, tokenizer, and label encoder  
   - Accepts new case descriptions and predicts the most relevant IPC section  
   - Provides confidence scores and generates verdict statements using templates  
   - Supports top-k predictions to reflect cases with multiple possible IPC sections  
   - Includes predefined test cases and an interactive mode for experimentation  

---

## Results  
- **Best Validation Accuracy:** 89.49%  
- **Dataset Size:** 10,968 samples across 311 IPC classes  
- **Training Samples:** 8,774  
- **Validation Samples:** 2,194  

**Example Prediction**  
- **Input:** “A person was found with illegal drugs in their possession”  
- **Output:**  
  - IPC Section: 21 (NDPS Act)  
  - Confidence: 96.73%  
  - Verdict: “NDPS Act 21 states that whosoever sells drugs for any cause other than medical will be held under the NDPS Act 21 for drug peddling.”  

---

## How to Use  
- Open the notebook `verdicteye-predict-court-judgements.ipynb` in Jupyter or Kaggle.  
- Run the training pipeline to fine-tune the model (or load the pre-saved model).  
- Use the inference script to test predictions on new incident descriptions.  

---

## Future Work  
- Expanding the dataset with more IPC-labeled cases  
- Introducing **multi-label classification** for cases involving multiple IPC sections  
- Exploring domain-specific models such as Legal-BERT for improved accuracy  
- Adding support for multiple languages, including Hindi and regional dialects  
- Deploying the model as a web application with a front-end interface for real-time usage  

---

## License  
This project is intended for educational and research purposes. It should not be used for real-world legal decision-making without expert review.  

---

## Author  
**Abhishek Kumar Singh**  
- Kaggle: [VerdictEye Notebook](https://www.kaggle.com/code/abhishekkumarsingh17/verdicteye-predict-court-judgements)  
- GitHub: [abhishekkumarsingh17](https://github.com/abhishekkumarsingh17)  
