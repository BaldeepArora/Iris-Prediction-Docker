# Iris Prediction Dockerized ML App

A simple machine learning application that predicts the species of an Iris flower based on input features. This project demonstrates the complete pipeline of developing a machine learning model, creating an API using Flask, containerizing the application using Docker, and deploying it to the cloud.

## Table of Contents
- [Overview](#overview)
- [Technologies Used](#technologies-used)
- [Dataset](#dataset)
- [Prerequisites](#prerequisites)
- [Setup and Installation](#setup-and-installation)
- [Running the Application](#running-the-application)
- [Usage](#usage)
  - [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)

## Overview
This project trains a machine learning model to classify Iris flower species based on the features: sepal length, sepal width, petal length, and petal width. It uses a Decision Tree classifier to predict the species of the Iris flower. The model is exposed via a Flask API, which is containerized using Docker, making it easy to deploy and run the application on any system.

## Technologies Used
- **Python 3.9**
- **Flask** - For creating the web API
- **scikit-learn** - For the machine learning model
- **Docker** - For containerizing the application
- **NumPy and Pandas** - For numerical operations

## Dataset
The dataset used in this project is the [Iris dataset](https://en.wikipedia.org/wiki/Iris_flower_data_set), which is a famous dataset for machine learning classification problems and contains 150 samples of Iris flowers, with 3 classes: Setosa, Versicolor, and Virginica.

## Prerequisites
- **Docker** installed on your machine.
- **Git** for version control.

## Setup and Installation
Follow these steps to set up the project locally:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/BaldeepArora/Iris-Prediction-Docker.git
2. Install Dependencies: Make sure you have Python 3.9 installed. Install the required packages listed in requirements.txt:
   ```bash
   pip install -r requirements.txt
3. Train the Model: Run the train_model.py script to train the Decision Tree model and save it as model.pkl:
   ```bash
   python train_model.py

## Running the Application 
The application is containerized with Docker, so you can run it easily in a Docker container.
1. Build the Docker Image:
   ```bash
   sudo docker build -t iris-prediction-app .
2. Run the Docker Container:
   ```bash
   sudo docker run -p 4000:80 iris-prediction-app
The application will be available at http://localhost:4000 or http://<YOUR_VM_EXTERNAL_IP>:4000.

## Usage

### API Endpoints

#### `GET /`
- **Description**: A simple endpoint that returns a welcome message.
- **Response**:
  ```html
  Hello, Docker!
#### POST /predict
- Description: Predicts the species of an Iris flower based on the input features.
- Request Body (JSON):
  ```json
  {
  "input": [sepal_length, sepal_width, petal_length, petal_width]
}
- Example:
  ```json
  {
  "input": [5.1, 3.5, 1.4, 0.2]
}
- Response:
  ```json
  {
  "prediction": <predicted_class>
}
The prediction will be 0, 1, or 2, representing the Iris species (Setosa, Versicolor, Virginica).

#### Testing the API
- Use curl to test the /predict endpoint:
  ```bash
  curl -X POST http://localhost:4000/predict -H "Content-Type: application/json" -d '{"input": [5.1, 3.5, 1.4, 0.2]}'
- Alternatively, use Postman to send a POST request with JSON input to http://localhost:4000/predict.

## Project Structure
```bash
Iris-Prediction-Docker/
│
├── Dockerfile
├── requirements.txt
├── train_model.py          # Script to train and save the model
├── app.py                  # Flask application to serve the model
├── model.pkl               # Saved machine learning model
└── README.md               # Project documentation
```
## Contributing
- Contributions are welcome! Please fork the repository, make your changes, and submit a pull request.
