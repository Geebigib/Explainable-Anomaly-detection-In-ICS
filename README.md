# Explainable-Anomaly-detection-In-Industrial control system


This project use Secure Water Treatment (SWaT) dataset from iTrust Centre for Research in Cyber Security which can be requested from https://itrust.sutd.edu.sg/itrust-labs_datasets/

## Instructions for Running the Code

### Requirements

- Python (version 3.0.0)
- Google Colab and Google Drive
- SWaT dataset
  
### Step 0. Exploratory Data Analysis (EDA) and Data preprocessing
To explore the SWaT dataset through Exploratory Data Analysis (EDA), please refer to the notebook [SWaT_EDA.ipynb](https://github.com/Geebigib/Explainable-Anomaly-detection-In-ICS/blob/81034290a7729452c4232f76b8d0a5724f2e7763/SWaT_EDA.ipynb)

Given that the dataset deviates from the standard normal distribution, standardizing the data is not optimal. Instead, we normalize both continuous and discrete variables to a range of 0–1, aligning them with the typical behavior observed in the training set. The normalization process is implemented in the code within [the Model Training section](#step-2-model-training-threshold-selection-and-prediction-result).


### Step 1. Model hyperparameter tuning

To optimize model performance, fine-tuning was conducted to select the most suitable hyperparameters. To replicate this process:

- For DeepSVDD, execute the notebook [Neural_Network_Base_Model_tuning.ipynb](https://github.com/Geebigib/Explainable-Anomaly-detection-In-ICS/blob/275836ed883315e6ef59074bf4588d3d7026a913/Neural_Network_Base_Model_tuning.ipynb).
- For ECOD, this step is unnecessary as the model does not require hyperparameter tuning.


### Step 2. Model Training, threshold selection, and prediction result

In this study, the models underwent training using normal operational data from each stage in the SWaT system, to enable them to learn typical behavior patterns. When abnormal behavior occurs, the error score spikes significantly, facilitating the detection of anomaly attacks. Following the model training phase, the appropriate threshold was established using data from stage P1 to identify anomalies when the error score exceeds a certain threshold. Subsequently, the data was predicted to identify anomaly points and measure model accuracy. 

To replicate this process:
- For DeepSVDD, execute the notebook [Neural_Network_Base_Model_separate_stage.ipynb](https://github.com/Geebigib/Explainable-Anomaly-detection-In-ICS/blob/275836ed883315e6ef59074bf4588d3d7026a913/Neural_Network_Base_Model_separate_stage.ipynb)
- For ECOD, execute the notebook [Probability_Base_Model_separate_stage.ipynb](https://github.com/Geebigib/Explainable-Anomaly-detection-In-ICS/blob/275836ed883315e6ef59074bf4588d3d7026a913/Probability_Base_Model_separate_stage.ipynb)

### Step 3. XAI result

In this study, XAI techniques were utilized to enhance model transparency and pinpoint anomaly points accurately. Our goal was to identify the XAI method capable of localizing attack points with the highest accuracy and minimal training time. To evaluate the accuracy of each XAI, we calculated Intersection over Union (IOU) scores and Accuracy metrics.

To replicate this process:
- For DeepSVDD, execute the notebook [XAI_from_DeepSVDD.ipynb](https://github.com/Geebigib/Explainable-Anomaly-detection-In-ICS/blob/275836ed883315e6ef59074bf4588d3d7026a913/XAI_from_DeepSVDD.ipynb)
- For ECOD, execute the notebook [XAI_from_ECOD.ipynb](https://github.com/Geebigib/Explainable-Anomaly-detection-In-ICS/blob/275836ed883315e6ef59074bf4588d3d7026a913/XAI_from_ECOD.ipynb)


#### Note
The notebook mentioned above was executed on Google Colab and connected to Google Drive, where the SWaT dataset was stored. Additionally, the trained models and XAI results were saved in Google Drive for easy access and reproducibility.
