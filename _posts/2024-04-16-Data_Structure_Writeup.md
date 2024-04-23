---
toc: true
comments: true
layout: post
title: Data Structure Writeup
courses: {compsci: {week: 28}}
type: tangibles
---
<!-- Assignment
https://github.com/orgs/nighthawkcoders/projects/12/views/1?pane=issue&itemId=59083840

{{site.baseurl}}
https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/
-->

## A little about the project
***This code and screenshots will be about the CRUD operations for my team's trimester project.***


## Collections
<!-- 2 questions -->
<!-- Replace this image eventually because TANG -->
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/SQL.png" width="800">
</center>

***This is a screenshot of SQLite3 Editor with the database of users.***
<center>
    <img src="{{site.baseurl}}/images/Data%20Structure%20Writeup/initalizeModel.png" width="800">
</center>

***This screenshot is about the initialization of the variables put into the database's table columns above.***
<center>
    <img src="{{site.baseurl}}/images/Data%20Structure%20Writeup/ModelSQLdata.png" width="800">
</center>

***This is the test data in the model that will create when the table is first initialized.***


## Lists and Dictonaries
<!-- 2 questions -->
<center>
    <img src="{{site.baseurl}}/images/Data%20Structure%20Writeup/securityBreakpoint.png" width="700">
</center>

***When logging into a user, this breakpoint while debuging will grab the body of the uid and will show the objects grabbed in the python object screenshot below.***
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/pythonVarJST.png" width="600">
</center>

***This image is holding the uid and password needed to login to the site.***


## API and JSON
<!-- 6 questions -->
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/GET-POST-UPDATE.png" width="700">
</center>
***The use of the framework Flask in our code provides built-in routing mechanisms and handle request dispatching for CRUD operations. The method is then identified in the frontend code to use the method needed.***
<!-- Discuss algorithmic condition used to direct request to appropriate Python method based on request method. -->
<br>
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/updatepagePOST.png" width="700">
</center>

***This fetch command fetches from a defined constant that is used in other parts of other fetches. This fetch in particular will post the data from a get above this fetch which will throw the data into a table to be able to analyze cleanly.***

<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/urlYbodyReq.png" width="800">
</center>

***The get to fetch the data for the table will only work after authenticating with a user from the database. This user will also show up on the table.***
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/JSON200.png" width="600">
</center>

***This is what is a part of the user data that is shown when doing a get method after successfully authorizing from a user in the database.***
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/failedpostUser.png" width="600">
</center>

***This is what shows up when the account authoizing is inputed uncorrectly and this message shows up after the failed attempt.***


## Frontend
<!-- 3 questions, 4 sub questions -->
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/userTable.png">
</center>

***I have features of a update/put and a delete feature on the table. They will do exactly as the name says. The update will change the data of the user that is selected to edit and the delete feature will delete whoever was chosen. The user selected for these functions are the user coinciding in the same row.***
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/chromeVarJST.png" width="500">
</center>

***This is the JSON object shown in the chrome inspect tool that is grabbing the variables of the user from a onclick function onto the edit feature.***
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/function_editUser.png" width="800">
</center>

***When there is a success, the page will have a popup with a success tag. If there is a failure, the feature will just close as if nothing has happened. The two processes of either success or failure will be in the cosole log to see.***


## Optional/Extra, Algorithm Analysis
<!-- 4 questions -->
<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/MLpreperations.png" width="600">
</center>

***The prep work for the model of the ML to run. It will initialize, load, preprocess, and train the dataset we have in the repository.***

<center>
    <img src="https://raw.githubusercontent.com/jplip/justin2.0/main/images/Data%20Structure%20Writeup/MLcalculations.png" width="800">
</center>

***This code is for the prediction and will train and then evaluate which will then lead up to the prediction of whatever we are predicting which in this case would be sleep disorder.***
<br>

***The Linear Regression predicts if someone has sleep disorders based on various features such as age, gender, daily steps, sleep, heart rate, etc. This way of prediction is for continuous outcomes. The goal of the Linear Regression is to find the best straight line through the data points, which can then be used to predict the value of the dependent variable for new data points.***
<br>

***The Decision Tree does the same thing as the Linear with the data except it's used for classification problems than linear. The model is represented as a tree structure, where there are branches and then there are leaves to different outcomes.***


## Summary
***Overall I think that the base line is there but there isn't a complete build. There are definetely things that I need to fix and get working to better improve user interactions such as the update and delete features not fully functioning. ML still needs a little work to get running as well.***