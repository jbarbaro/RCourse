---
title       : Getting Started with Data Frames in R
description : This chapter explores dataframe basics and provides students with a fundamental understanding of how to house data in R. 
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:r xp:100 skills:1 key:a1f92e28d6
## What is a dataframe

> A data frame is a list of equal length vectors that supports both homogeneous and heterogeneous data. 

In data storage, each row represents a unique instance and each column represents a unique variable.

Data frames are able to store data of different types (numeric, character, boolean) across rows. Conversly, data in each column need to be of the same type.   

`R` as a programming language stores all data as a vector, regardless of how much data is in the vector. This means that a data frame is actually a list of vectors combined to form a table of information. This knowledge will be important when it comes to data manipulation. 

You will begin by getting a sense for what a data frame looks like in R and what it means for data to be stored as vectors.

*** =instructions
- Check out the data frame Easy_Data.
*** =hint
- Type Easy_Data into the R consol 

*** =pre_exercise_code
```{r}
# Create data frame
Easy_Data <- data.frame(Letter = c("A","B","C","D","E"), Numbers = 1:5, Is.True = as.logical((c(1,1,0,1,0))))
```

*** =sample_code
```{r}
# Easy_Data is available in your workspace

# Check out the data frame Easy_data by typing the variable name into your workspace
```

*** =solution
```{r}
# Easy_Data is available in your workspace

# Check out the data frame Easy_data by typing the variable name into your workspace
Easy_Data
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("Easy_Data")

# Test whether the student correctly used plot()
# Again, we use the automatically generated feedback here
#test_function("plot", args = "x")
#test_function("plot", args = "y")
#test_function("plot", args = "col")

# Alternativeley, you can use test_function() like this
# test_function("plot", args = c("x", "y", "col"))

# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```
