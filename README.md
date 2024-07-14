# JPX Tokyo Stock Exchange Prediction AWS Pipeline

---

## Project Overview
This project aims to build an end-to-end machine learning pipeline to predict stock prices using data from the JPX Tokyo Stock Exchange. The project involves data collection, preprocessing, model training, evaluation, and deployment using AWS services.

---

## Table of Contents
1. [Project Structure](#project-structure)
2. [Dataset](#dataset)
3. [AWS Setup](#aws-setup)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Model Training](#model-training)
7. [Evaluation](#evaluation)
8. [Deployment](#deployment)
9. [Contributing](#contributing)
10. [License](#license)
---

## Project Structure
```plaintext
jpx-stock-prediction/
├── data/
│   ├── raw/
│   ├── processed/
├── notebooks/
├── src/
│   ├── data_preprocessing.py
│   ├── feature_engineering.py
│   ├── model_training.py
│   ├── evaluation.py
│   ├── deployment.py
├── requirements.txt
├── README.md
└── .gitignore
```


---

## Dataset
The dataset used for this project is obtained from the [JPX Tokyo Stock Exchange Prediction](https://www.kaggle.com/c/jpx-tokyo-stock-exchange-prediction) competition on Kaggle. It contains historical stock prices and other relevant financial data.

---

## AWS Setup
### Services Used
1. **S3**: For storing raw and processed data, as well as the trained model.
2. **EC2**: For running data preprocessing and model training scripts.
3. **SageMaker**: For managing Jupyter notebooks and training models.
4. **Lambda**: For deploying the model as a serverless function.
5. **API Gateway**: For creating a RESTful API to interact with the deployed model.

### Setup Instructions
1. **Create an S3 Bucket**:
    - Go to the S3 service in the AWS console.
    - Create a new bucket (e.g., `jpx-stock-data`).
    - Upload your dataset to this bucket.

2. **Launch an EC2 Instance**:
    - Choose an appropriate instance type (e.g., `t2.medium`).
    - Set up security groups to allow SSH access.
    - Install necessary packages and clone the repository.

3. **Set Up SageMaker**:
    - Create a new notebook instance.
    - Attach the appropriate IAM role with S3 access.
    - Open the notebook and clone the repository.

4. **Lambda Function and API Gateway**:
    - Write a Lambda function to load the model from S3 and handle inference requests.
    - Create a new API Gateway and integrate it with the Lambda function.

---

## Installation
To set up the project locally, follow these steps:
1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/jpx-stock-prediction.git
    cd jpx-stock-prediction
    ```
2. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

---

## Usage
1. **Data Preprocessing:** Run the data preprocessing script to clean and prepare the data:
    ```bash
    python src/data_preprocessing.py
    ```
2. **Feature Engineering:** Generate features for the model:
    ```bash
    python src/feature_engineering.py
    ```
3. **Model Training:** Train the model using the processed data:
    ```bash
    python src/model_training.py
    ```
4. **Evaluation:** Evaluate the trained model:
    ```bash
    python src/evaluation.py
    ```

---

## Model Training
The model training script includes the following steps:
1. Loading the processed data
2. Splitting the data into training and validation sets
3. Training a linear regression model (or any other chosen model)
4. Saving the trained model to S3

---

## Evaluation
The evaluation script calculates performance metrics like Mean Absolute Error (MAE), Mean Squared Error (MSE), and R-squared (R²) to assess the model's accuracy.

---

## Deployment
To deploy the model using AWS services, follow these steps:
1. **Upload the Trained Model to S3**:
    - Save the trained model to your local system.
    - Upload the model to your S3 bucket (e.g., `s3://jpx-stock-data/model/`).

2. **Set Up AWS Lambda**:
    - Create a new Lambda function.
    - Write the function code to load the model from S3 and handle inference requests.
    - Configure the function's execution role to allow S3 access.

3. **Create an API Gateway**:
    - Create a new RESTful API.
    - Integrate the API with the Lambda function.
    - Deploy the API to make it accessible.

---

## Contributing
Contributions are welcome! Please follow these steps to contribute:
1. Fork the repository
2. Create a new branch (`git checkout -b feature-branch`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature-branch`)
5. Open a Pull Request

---

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
