---
title       : Getting Started with DataFrames in R
description : This chapter explores dataframe basics and provides students with a fundamental understanding of how to house data in R. 
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:r xp:100 skills:1 key:a1f92e28d6
## What is a dataframe

> A data frame is a list of equal length vectors that supports both homogeneous and heterogeneous data. 

In data storage, each row represents a unique instance and each column represents a unique variable.

Data frames are able to store data of different types (numeric, character, boolean) across rows. While data in each column needs to be of the same type.   

`R` as a programming language stores all data as a vector, regardless of how much data is in the vector. This means that a data frame is actually a list of vectors combined to form a table of information. This knowledge will be important when it comes to data manipulating. 


*** =instructions
- Check out the structure of `movie_selection`.
- Select movies with a rating of 5 or higher. Assign the result to `good_movies`.
- Use `plot()` to  plot `good_movies$Run` on the x-axis, `good_movies$Rating` on the y-axis and set `col` to `good_movies$Genre`.

*** =hint
- Use `str()` for the first instruction.
- For the second instruction, you should use `...[movie_selection$Rating >= 5, ]`.
- For the plot, use `plot(x = ..., y = ..., col = ...)`. 

*** =pre_exercise_code
```{r}
# Pre-load a package in the workspace
library(MindOnStats)

# You can prepare the data before the student starts:
data(Movies)
movie_selection <- Movies[Movies$Genre %in% c("action", "animated", "comedy"),c("Genre", "Rating", "Run")]

# You can also clean up data so that it's not available in the student's workspace anymore:
rm(Movies)
```

*** =sample_code
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection


# Select movies that have a rating of 5 or higher: good_movies


# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre

```

*** =solution
```{r}
# movie_selection is available in your workspace

# Check out the structure of movie_selection
str(movie_selection)

# Select movies that have a rating of 5 or higher: good_movies
good_movies <- movie_selection[movie_selection$Rating >= 5, ]

# Plot Run (i.e. run time) on the x axis, Rating on the y axis, and set the color using Genre
plot(good_movies$Run, good_movies$Rating, col = good_movies$Genre)
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

# Test whether the function str is called with the correct argument, object
# If it is not called, print something informative
# If it is called, but called incorrectly, print something else
test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

# Test the object, good_movies
# Notice that we didn't define any feedback here, this will cause automatically 
# generated feedback to be given to the student in case of an incorrect submission
test_object("good_movies")

# Test whether the student correctly used plot()
# Again, we use the automatically generated feedback here
test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

# Alternativeley, you can use test_function() like this
# test_function("plot", args = c("x", "y", "col"))

# It's always smart to include the following line of code at the end of your SCTs
# It will check whether executing the student's code resulted in an error, 
# and if so, will cause the exercise to fail
test_error()

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```
