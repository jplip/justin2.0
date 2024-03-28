---
toc: true
comments: true
layout: post
title: ML Accomplishments
courses: {compsci: {week: 28}}
type: tangibles
---

# Titanic Frontend
```html
<!-- Inputs -->
<div>
    <form>
        <p><label>
            Name:
            <input type="text" name="name" id="name" required>
        </label></p>
        <p><label>
            Passenger Class:
            <select name="pclass" id="pclass" required>
                <option value=""> </option> <!-- Blank value -->
                <option value="1">1st Class</option>
                <option value="2">2nd Class</option>
                <option value="3">3rd Class</option>
            </select>
        </label></p>
        <p><label>
            Sex:
            <select name="sex" id="sex" required>
                <option value=""> </option> <!-- Blank value -->
                <option value="male">Male</option>
                <option value="female">Female</option>
            </select>
        </label></p>
        <p><label>
            Age:
            <input type="text" name="age" id="age" required>
        </label></p>
        <p><label>
            Number of Siblings/ Spouses:
            <input type="text" name="sibsp" id="sibsp" required>
        </label></p>
        <p><label>
            Number of Parents or Children on Board:
            <input type="text" name="parch" id="parch" required>
        </label></p>
        <p><label>
            Fare:
            <input type="text" name="fare" id="fare" required>
        </label></p>
        <p><label>
            Embarked From:
            <select name="embarked" id="embarked" required>
                <option value=""> </option> <!-- Blank value -->
                <option value="S">Southampton</option>
                <option value="C">Cherbourg</option>
                <option value="Q">Queenstown</option>
            </select>
        </label></p>
            Alone?:
        <p><label>
            <select name="alone" id="alone" required>
                <option value=""> </option> <!-- Blank value -->
                <option value="True">Yes</option>
                <option value="False">No</option>
            </select>
        </label></p>
        <button type="button" onclick="create_user()">Submit</button>
    </form>
</div>

<div id="probabilities">
    <p>Survival Probability: <span id="survivalProbability"></span></p>
    <p>Death Probability: <span id="deathProbability"></span></p>
</div>

<!-- Table -->
<h2>Titanic Records</h2>
<table id="userTable">
    <tr>
        <th>Name</th>
        <th>Pclass</th> <!-- passanger class -->
        <th>Sex</th>
        <th>Age</th>
        <th>Sibsp</th> <!-- siblings/spouses on board -->
        <th>Parch</th> <!-- parent/children on board -->
        <th>Fare</th>
        <th>Embarked</th> <!-- coming from ex: Southampton -->
        <th>Alone?</th>
        <th>Survival Chance</th>
        <th>Death Chance</th>
    </tr>
</table>

<script>
    // User creation
    function create_user() {
        const name = document.getElementById('name').value;
        const pclass = document.getElementById('pclass').value;
        const sex = document.getElementById('sex').value;
        const age = document.getElementById('age').value;
        const sibsp = document.getElementById('sibsp').value;
        const parch = document.getElementById('parch').value;
        const fare = document.getElementById('fare').value;
        const embarked = document.getElementById('embarked').value;
        const alone = document.getElementById('alone').value;
        
        const formData = {
            "name": name,
            "pclass": pclass,
            "sex": sex,
            "age": age,
            "sibsp": sibsp,
            "parch": parch,
            "fare": fare,
            "embarked": embarked,
            "alone": alone
        };
        
        fetch('http://127.0.0.1:8086/api/titanic/create', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(formData)
        })
        .then(response => {
            if (response.ok) {
                return response.json();
            } else {
                throw new Error('User creation failed');
            }
        })
        //pulls data of probability of surviving and dying
        .then(data => {
            const survivalProbability = data.alive_proba;
            const deathProbability = data.dead_proba;
            const survivalProbabilityNumeric = parseFloat(survivalProbability);
            const deathProbabilityNumeric = parseFloat(deathProbability);
            console.log("Survival Probability:", survivalProbabilityNumeric);
            console.log("Death Probability:", deathProbabilityNumeric);
            document.getElementById('survivalProbability').textContent = survivalProbabilityNumeric.toFixed(2);
            document.getElementById('deathProbability').textContent = deathProbabilityNumeric.toFixed(2);

            addRowToTable(formData, survivalProbabilityNumeric, deathProbabilityNumeric);
        })
        .catch(error => {
            console.error('Error:', error);
            alert("User Creation failed. Try again.");
        });
    }
    //adds data to table
    function addRowToTable(data, survivalProbability, deathProbability) {
        const table = document.getElementById('userTable');

        const row = table.insertRow(-1); // Insert a new row at the end of the table

        const cells = ['name', 'pclass', 'sex', 'age', 'sibsp', 'parch', 'fare', 'embarked', 'alone'];
        cells.forEach(cell => {
            const newCell = row.insertCell(-1);
            newCell.textContent = data[cell];
        });
        const survivalCell = row.insertCell(-1);
        survivalCell.textContent = survivalProbability.toFixed(2);
        const deathCell = row.insertCell(-1);
        deathCell.textContent = deathProbability.toFixed(2);
    }
</script>
```

***What I accomplished most was the frontend. I was able to make a system that posted a user based off the create user code I used 2nd trimester. I was able to track the survivability and dealth probability based on this. I then was able to make a table that tracks the inputed data as long as the page isn't reloaded and puts it into the table.***
<!-- Example of frontnend inputs and table -->
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/ML/TitanicFrontend.png" style="border: 1px solid white;">
</center>

<br>
<br>

# Sleep Disorder Model

```python
import pandas as pd
from sklearn.preprocessing import OneHotEncoder
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.linear_model import LinearRegression
from sklearn.metrics import accuracy_score
import numpy as np
import logging


class SleepHealthPredictor: # initializes class instance
    def __init__(self):
        self.data = None
        self.encoder = None
        self.model_dt = None
        self.model_logreg = None
        self.X_test = None
        self.y_test = None

    def load_data(self, file_path): #responsible for loading the dataset from a specified file path
        self.data = pd.read_csv(file_path)

    def preprocess_data(self): # responsible for preprocessing the data
        if self.data is None:
            raise ValueError("Data not loaded. Call load_data() first.")

    def train_models(self): # responsible for training the models
        X = self.data.drop('Sleep Disorder', axis=1)
        y = self.data['Sleep Disorder']
        X_train, self.X_test, y_train, self.y_test = train_test_split(X, y, test_size=0.3, random_state=42)

        self.model_dt = DecisionTreeClassifier()
        self.model_dt.fit(X_train, y_train)

        self.model_logreg = LinearRegression()
        self.model_logreg.fit(X_train, y_train)

    def evaluate_models(self): # responsible for evaluating the models
        if self.model_logreg is None:
            raise ValueError("LinearRegression model not trained successfully.")

        y_pred_dt = self.model_dt.predict(self.X_test)
        accuracy_dt = accuracy_score(self.y_test, y_pred_dt)
        print('DecisionTreeClassifier Accuracy: {:.2%}'.format(accuracy_dt))

        y_pred_logreg = self.model_logreg.predict(self.X_test)
        accuracy_logreg = accuracy_score(self.y_test, y_pred_logreg)
        print('LinearRegression Accuracy: {:.2%}'.format(accuracy_logreg))

    def predict_sleep_disorder(self, patient_data): # responsible for making predictions
        if self.model_logreg is None:
            logging.error("LinearRegression model is not initialized.")
            return None # or handle the error appropriately
        # Your prediction logic here, using patient_data
        # For example:
        prediction = self.model_logreg.predict(patient_data)
        return prediction

# Usage
sleep_health_predictor = SleepHealthPredictor()

def initSleep(): # initializes the sleep disorder model
    logging.info("Initializing sleep data and training models...")
    sleep_health_predictor.load_data('Sleep_health_and_lifestyle_dataset.csv')
    sleep_health_predictor.preprocess_data()
    sleep_health_predictor.train_models()
    logging.info("Models trained successfully.")
    sleep_health_predictor.evaluate_models()
    # Example of defining patient_data
    patient_data = pd.DataFrame({
        'Age': [25],
        'Gender': ['Male'],
        'Daily Steps': [10],
        'Sleep Duration': [1],
        'BMI Category': ['Overweight'],
        'Heart Rate': [76],
        'Stress Level': [50],
        'Quality of Sleep': [3]
        # Add other relevant features here
    })
    # Now you can use patient_data in your prediction
    prediction = sleep_health_predictor.predict_sleep_disorder(patient_data)
    return('Predicted Sleep Disorder:', prediction)
```
***This is my model that I used and I was able to get the prediction to post if a person has a sleep disorder. The problem is is that I couldn't find the reason on why the prediction for 'sleep disorder' couldn't switch from the value of 'none' no matter what values I put for the calculations. I'm guessing it's something to do with the values not having the right definement and I couldn't find the right ones. I struggled to finish the model and still haven't fully completed it because of this reason. I think maybe the prediction might not be right as well but I honestly don't know since I think it's fine with the other model we done.***
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/ML/ConsoleSleepDisorderNone.png" style="border: 1px solid white;">
</center>

# Sleep Disorder API

```python
from flask import Blueprint, jsonify, request
from flask_restful import Api, Resource
from model.sleep_disorder import SleepHealthPredictor
import pandas as pd

sleep_health_api = Blueprint('sleep_health_api', __name__, url_prefix='/api/sleep')
api = Api(sleep_health_api)

class SleepHealthAPI(Resource):
    def post(self):
        # Get patient data from the API request
        data = request.get_json()

        # Create a DataFrame from the JSON data
        patient_data = pd.DataFrame(data)

        # Initialize the predictor and load the data
        sleep_health_predictor = SleepHealthPredictor()
        sleep_health_predictor.load_data('Sleep_health_and_lifestyle_dataset.csv')
        data.pop('Person ID') # drop data
        data.pop('Occupation')
        data.pop('Physical Activity Level')
        data.pop('Blood Pressure')
        
        sleep_health_predictor.preprocess_data()
        sleep_health_predictor.train_models()

        # Make a prediction
        prediction = sleep_health_predictor.predict_sleep_disorder(patient_data)

        # Prepare the response
        response = {
            'prediction': prediction.tolist()
        }

        return jsonify(response)

# Add resource to the API
api.add_resource(SleepHealthAPI, '/predict')
```
***From what I know this api works fine and pulls the necessary data to work. No difficulties with this.***

# Summary
***I think that the frontend was easy work but the backend was something that I need to look more into. I think that the model was definetly something that I struggled with and getting the values. I think the problem was human error where I just didn't know how to define the values as they were not just one word. All together I was kinda lost when doing the code for the model.***