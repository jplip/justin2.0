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
-->

## A little about the project
***This project is based off a user database. The table is formed based off getting the data from the api which will then post onto the table. There are then features like update and delete for the users.***


## Collections
<!-- 2 questions -->
<center>
    <img src="{{site.baseurl}}/images/SQL.png" width="800">
    <br>
    <img src="{{site.baseurl}}/images/ModelSQLdata.png" width="800">
</center>

***Uses the set of users to show on a table with their data.***


## Lists and Dictonaries
<!-- 2 questions -->
<center>
    <img src="{{site.baseurl}}/images/pythonVarJST.png" width="600">
</center>

***This uses the python object and grabs the uid and the password for the system to pass to the update page.***
<!-- This small sentence makes up both questions. -->


## API and JSON
<!-- 6 questions -->
<center>
    <img src="{{site.baseurl}}/images/GET-POST-UPDATE.png" width="700">
</center>
<center>
    <img src="{{site.baseurl}}/images/updatepagePOST.png" width="700">
</center>

***This fetch command fetches from a defined constant that is used in other parts of other fetches. This fetch in particular will post the data from a get above this fetch which will throw the data into a table to be able to analyze cleanly.***

<center>
    <img src="{{site.baseurl}}/images/urlYbodyReq.png" width="800">
</center>

***The get to fetch the data for the table will only work after authenticating with a user from the database. This user will also show up on the table.***
<center>
    <img src="{{site.baseurl}}/images/JSON200.png" width="600">
    <br>
    <img src="{{site.baseurl}}/images/failedpostUser.png" width="600">
</center>

***This is what shows up when the account is inputed correctly and the one under is a failed to get the data because of the wrong cridentials.***


## Frontend
<!-- 3 questions, 4 sub questions -->
<center>
    <img src="{{site.baseurl}}/images/chromeVarJST.png" width="500">
    <br>
    <img src="{{site.baseurl}}/images/userTable.png">
</center>

***I have features of a update/put and a delete feature. They will do exactly as the name says. The update will change the data of the user that is selected to edit and the delete feature will delete whoever was chosen. The user selected is the user coinciding in the same row.***
<center>
    <img src="{{site.baseurl}}/images/function_editUser.png" width="800">
</center>

***When there is a success, the page will have a popup with a success tag. If there is a failure, the feature will just close as if nothing has happened. The two processes of either success or failure will be in the cosole log to see.***
<br>

```bash
net::ERR_FAILED
```
***Currently my code can't properly work with the update and delete feature. I've looked into it and it looks like I have a CORS problem. I get this error whenever I try using the update feature and looked it up online. I'm still trying to fix it but haven't really got to it. This is something that is very needed to be fixed.***


## Optional/Extra, Algorithm Analysis
<!-- 4 questions -->
<center>
    <img src="{{site.baseurl}}/images/MLpreperations.png" width="600">
</center>

***The prep work for the model of the ML to run.***

<center>
    <img src="{{site.baseurl}}/images/MLcalculations.png" width="800">
</center>

***The Linear Regression predicts if someone has sleep disorders based on various features such as age, gender, daily steps, sleep, heart rate, etc. This way of prediction is for continuous outcomes. The goal of the Linear Regression is to find the best straight line through the data points, which can then be used to predict the value of the dependent variable for new data points.***
***The Decision Tree does the same thing as the Linear with the data except it's used for classification problems than linear. The model is represented as a tree structure, where there are branches and then there are leaves to different outcomes.***


## Summary
***Overall I think that the base line is there but there isn't a complete build. There are definetely things that I need to fix and get working to better improve user interactions such as the update and delete features not fully functioning. ML still needs a little work to get running as well.***