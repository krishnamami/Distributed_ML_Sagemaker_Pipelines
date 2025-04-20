# Distributed_ML_Sagemaker_Pipelines
This project demonstrates how to leverage Amazon SageMaker Pipelines to enable parallel model development and distributed scoring using containerized compute nodes. The pipeline is designed to streamline end-to-end ML workflows, from data processing to batch inference, while accelerating experimentation and production deployment.

### Architecture :

![image](https://github.com/user-attachments/assets/0adca7b6-0745-4f7a-b839-3221d1d79d6e)


* Parameters:

![image](https://github.com/user-attachments/assets/3312dabb-84be-407c-8b9c-b2e4f7469c58)
# Pipeline Steps:
* Processing Step:
   * Executes a Python-based feature engineering script using frameworks like Scikit-learn.
   * Outputs are stored in S3 as training, testing, and validation datasets.
   * These outputs are passed to the training step as dependencies.
   * Output of feature engineering is stored in S3 buckets as train,test and validation data sets
* Training step:
   * Depends on the output of the processing step.
   * Uses frameworks such as XGBoost and runs on instance types specified via Instance_type.
   * Outputs include trained model artifacts stored in S3.
* Model Evaluation:
     * A standalone evaluation script compares the model’s performance against the defined mse_threshold.
     * Step depends on outputs from the training step.
     * Determines whether the model should proceed to registration.
 * Model Creation :
    * If the evaluation criteria are met, a model is created and registered using:
        * The trained artifacts from the training step.
        * The appropriate container image (e.g., XGBoost container).
 * Batch Transform :
    * Performs offline scoring using the batch data located in S3.
    * Leverages the registered model to generate predictions in batch mode.
    
   Production Use:
   
   With the learnings from this experiment, we successfully implemented parallel model development and scoring pipelines for four models—supporting both Purchase and Refinance scenarios in production.
   
  ![image](https://github.com/user-attachments/assets/bf438d9f-2f86-48fb-aef7-5194f169949f)

# How To Run
 -->Clone the repo: git clone https://github.com/krishnamami/Distributed_ML_Sagemaker_Pipelines.git
 -->pip install -r requirements.txt
 -->python sage_maker_pipeline.py



   

