---
toc: true
comments: true
layout: post
title: CPT Individual
courses: {compsci: {week: 24}}
type: tangibles
---
<!-- 
https://raw.githubusercontent.com/jplip/justin2.0/main
{{site.baseurl}}
-->
Link to [College Board Requirements](https://apcentral.collegeboard.org/media/pdf/ap-csp-student-task-directions.pdf)

## Component A: Program Code
<!-- Has 6 questions -->

- ### Q1: ***Instructions for input from one of the following: the user, a device, an online data stream, a file.***
    - The user will click on answers that resonate the most with them and get scored based on the values associated with the answers to get a final score.
    ![A1-1](https://raw.githubusercontent.com/jplip/justin2.0/main/images/A1-1.png)


- ### Q2: ***Use of at least one list (or other collection type) to represent a collection of data that is stored and used to manage program complexity and help fulfill the program’s purpose.***
    - Concept was not fully finished.
        - Concept: Added the jwt token to our users so that whichever user is connected to the website, can go onto the stress test and add their stress values to get their data for the day.
    ![A2-1](https://raw.githubusercontent.com/jplip/justin2.0/main/images/A2-1.png)


- ### Q3: ***At least one procedure that contributed to the program’s intended purpose where you have defined: the name, return type, one or more parameters.***
    - The update function used to calculate the values of the answers chosen to then update the stress bar total.
    ![A3-1](https://raw.githubusercontent.com/jplip/justin2.0/main/images/A3-1.png)


- ### Q4: ***An algorithm that includes sequencing, selection, and iteration that is in the body of the selected procedure.***
    - I used a selection of questions with a range of 1-4 to add to the total value of stress on the bar which at the end will be calculated.
    ![A4-1](https://raw.githubusercontent.com/jplip/justin2.0/main/images/A4-1.png)


- ### Q5: ***Calls to your student-developed procedure.***
    - Calls the update function after every time pressing the next or back button.
    ![A5-1](https://raw.githubusercontent.com/jplip/justin2.0/main/images/A5-1.png)
    <br>
    ![A5-2](https://raw.githubusercontent.com/jplip/justin2.0/main/images/A5-2.png)


- ### Q6: ***Instructions for output (tactile, audible, visual, or textual) based on input and program functionality.***
    - The final score after reaching the end of the test can be changed by going back with the 'back' button and selecting a different answer.
    ![A6-1](https://raw.githubusercontent.com/jplip/justin2.0/main/images/A6-1.png)
    <br>
    ![A6-2](https://raw.githubusercontent.com/jplip/justin2.0/main/images/A6-2.png)


## Component B: Video
<!-- Has 8 questions. Personally made question 4 and 5 combine some questions. -->

| Requirements | My Answers |
| - | - |
| Input to your program | Video has cursor click on answers to proceed to the next quesion. |
| At least one aspect of the functionality of your program | Has differnt values depending on the answer to the question. |
| Output produced by your program | At the end of the test, finalaizes the total value and then has it shown on the stress bar. |
| Your video may NOT contain: any distinguishing information about yourself and/or voice narration (though text captions are encouraged) | The video is kept strictly on the code and the test. There is nothing about me personally in it. The video has no audio but there is text captions that can be read. |
| Your video must be: either .webm, .mp4, .wmv, .avi, or .mov format; no more than 1 minute in length; no more than 30MB in file size | My video is shot as a .mp4 and is 59.6 seconds. The file is 2.9MB after downloading it from the website it was made on. |

## Video
<center>
    <iframe src="https://www.veed.io/embed/61a3bbd8-904f-480f-930a-24d13b9ad909" width="744" height="504" frameborder="0" title="Stress Test" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
</center>

## Reflection
<p>
    I do think that there could've been more done on this project. While the concept and frame for everything are there, the only thing that was missing was the integration with the backend. I want the data from the daily test taking to be put onto the user's account and then show a graph or data chart from low to high stress with the data throughout the days, weeks, months, and years. There was also a problem with the math that I've had trouble with for a while, but I was able to get the ending result with the right color and the right calculation. In the end, I might not have been able to finish it all, but at least I know where to start if I were to do it all over again.
</p>