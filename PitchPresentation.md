" Guess the Number" - My First Shiny App
========================================================
author: Ruby Annette
date: 23.5.2016

Course Project
========================================================


* This App was developed using " Shiny" for the course project of "Developing Data Products" course which is a part of "Data Science" specialisation.

* This presentation is created using the Rstudio Presenter

* The objective of the presentation is to explain or pitch the " Guess the Number" app

About the App "Guess the Number""
========================================================

* The objective of this app game is to guess a number between 1 and 100 and try to match it with the computer's selection.
* When you enter a number that you guess should be the right no, it tell you whether the no is correct or whether it above or below the limit as a clue to you

Some sample Code for you
========================================================

#the computer guesses an integer between
number <- floor(runif(1,1,101))
#print(number)
numberGuessed <- function(guess, number) {
       returnValue <- "Nothing entered yet."
       if (guess > 100) {
               #print(guess)
               #print(class(guess))                #print(class(100))
                returnValue <- 'Above 100.\nPlease make a selection between 1 and 100.'
       }
       else if (guess < 1) {
               #print(guess)
               returnValue <- 'Below 1.\nPlease make a selection between 1 and 100.'
       }
        else if (guess > number) {
                returnValue <- 'Higher than the number.'
        }
        else if (guess < number) {
                returnValue <- 'Lower than the number.'
       }
       else if (guess == number) {
                returnValue <- 'Correct!'
        }
        returnValue
}
shinyServer( 
        function(input, output) {
                output$inputValue <- renderPrint({as.numeric(input$guess)})
                #output$outputValue <- renderText({numberGuessed(input$guess, number)})
                output$outputValue <- renderText({
                        if (input$goButton == 0) "You have not guessed a number yet"
                        else if (input$goButton >= 1) numberGuessed(as.numeric(input$guess), number)
                })
        }
) 

The "Guess the Number" App
========================================================

Find the app in the URL given below: 

http://127.0.0.1:5062/

![alt text](GuessNumber.png)





```
