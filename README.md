# Distributed_ML_Sagemaker_Pipelines
An end-to-end machine learning pipeline built on **AWS SageMaker Pipelines**, designed to support **parallel model development** and **batch scoring** on distributed, containerized infrastructure.

## Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Pipeline Stages](#pipeline-stages)
- [How to Run](#how-to-run)
- [Key Takeaways](#key-takeaways)

## Overview

This project demonstrates the use of **SageMaker Pipelines** to operationalize a machine learning workflow that includes:

- Feature engineering
- Model training with XGBoost
- Model evaluation based on MSE threshold
- Conditional model registration
- Offline batch scoring using SageMaker Batch Transform

Ideal for MLOps teams looking to streamline experimentation, ensure consistency in deployment workflows, and scale processing across compute instances.

---

### Architecture :

![image](https://github.com/user-attachments/assets/0adca7b6-0745-4f7a-b839-3221d1d79d6e)


* Parameters:

![image](https://github.com/user-attachments/assets/3312dabb-84be-407c-8b9c-b2e4f7469c58)

## ⚙️ Pipeline Stages

| Stage       | Description |
|-------------|-------------|
| `Processing` | Executes `preprocessing.py` to clean and split data |
| `Training`   | Trains XGBoost model on training set |
| `Evaluation` | Evaluates model against validation set using MSE |
| `Register Model` | Saves model if MSE < threshold |
| `Batch Transform` | Scores batch data using newly trained model |

---

    
## Take Aways:
   
   With the learnings from this experiment, we successfully implemented parallel model development and scoring pipelines for four models—supporting both Purchase and Refinance scenarios in production.
   
  ![image](https://github.com/user-attachments/assets/bf438d9f-2f86-48fb-aef7-5194f169949f)

## ▶️ How to Run
 -->Clone the repo: git clone https://github.com/krishnamami/Distributed_ML_Sagemaker_Pipelines.git
 
 -->pip install -r requirements.txt
 
 -->python sage_maker_pipeline.py



   

