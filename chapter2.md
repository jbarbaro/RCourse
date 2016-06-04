---
title       : Indexing with Data Frames
description : This chapter explores the four main ways of indexing data frames in R
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:r xp:100 skills:1 key:a1f92e28d6
## Indexing with a columns's name

A key part of data manipulation is being able to acess values within your data frame. The first technique that you will learn is how to index a column from YOUR data frame. Recall that a column in a data frame is simply one of many vectors within a list that is the data frame. This allows us to easily index a column by using it's name. 

To perform this operation we use the following notation:

> data.frame$columnname

The magic is in the "$" operator. This tells R to only return values from the column specified.

When R returns the values from this call it will return them in the form of a vector and not a column. Why? Because every column is a vector!

Now it's your turn to give it a try 

*** =instructions
- index the Sepal.Length column in iris and assign it to its own variable called s_length
- print the new variable s_length
*** =hint
- The notation should be data.frame$columnname

*** =pre_exercise_code
```{r}
# recall iris data
data(iris)
```

*** =sample_code
```{r}
# index Sepal.Length

# Print s_length
```

*** =solution
```{r}
# index Sepal.Length

s_length <- iris$Sepal.Length

# Print s_length

s_length

```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("s_length")
test_output_contains("s_length")

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
--- type:NormalExercise lang:r xp:100 skills:1 key:420999c15f
## Creating a simple Data Frame

In this first exercise you will learn how to create a simple data frame. 

To create a data frame you will first need to create vectors of information with equal lengths and then call those objects into the function data.frame.

Note: When using the data.frame() function, character variables are imported as factors or categorical variables. Use the str() function to get to know more about your data frame.


*** =instructions
- Create a variable called "Letters" with the letters A:E
- Create a variable called "Numbers" with the numbers 1:5
- Create a data frame named `my_first_dataframe` using the objects Letters and Numbers
- Print `my_first_dataframe`
- Use the `str()` function to learn more about your data frame
*** =hint
- Use the c() function to create a vector of letters

*** =pre_exercise_code
```{r}
# Create data frame

```

*** =sample_code
```{r}

# Create the object Letters


# Create the object Numbers


# Create a data frame using the objects Letters and Numbers


# Use str() to see data table attributes

```

*** =solution
```{r}

# Create the object Letters
Letters <- c("A","B","C","D","E")

# Create the object Numbers

Numbers <- 1:5

# Create a data frame using the objects Letters and Numbers

my_first_dataframe <- data.frame(Letters,Numbers)

my_first_dataframe

# Use str() to see data table attributes

str(my_first_dataframe)


```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("Letters")
test_object("Numbers")
test_output_contains("my_first_dataframe")

test_function("data.frame")
test_function("str")

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

--- type:NormalExercise lang:r xp:100 skills:1 key:420999c15f
## Changing column and row names in a Data Frame

For a majority of the tutorials in this chapter we will be leveraging the `iris` data set. This simple data set has 5 columns and 150 rows of data which contain attributes for three different species of flowers: Setosa, Versicolor and Virginica. 

We will begin this exercise by looking at the `names()` function. This function allows us to see the current column names in our data set. 

To view the current column names we call our data frame into the `names()` function. In this case `names(iris)`.

We can reassign column names by assigning a string of new column names to the object `names(iris)`. For example:

> names(iris) <- c("Column1", "Column2", "Column3", "Column4", "Column5")

We can also use `colnames` and `rownames` to access the names of columns and rows respectively. In both cases the functions work the same as the `names` function shown above. 

Note: For most data sets the row name will simply be the row number. 


Renaming columns is an important skill to have in your data manipulation tool kit. Now its your turn to try out the `names()` function.

*** =instructions
- Use the `names` function to view the current columns in iris
- Use the `colnames` function to view the current columns in iris
- Use the `rownames` function to view the current row names in iris
- Replace the "." in each column names with "_" using `colnames`
- Print `iris` 

*** =hint
- Call the iris data frame into the function `names()`
- Use c() function to create a vector of new column names
- Make sure the replacement vector is the same length as the number of columns

*** =pre_exercise_code
```{r}


```

*** =sample_code
```{r}

# Use names() to determine the current column names in iris


# Use colnames() to determine the current column names in iris


# Use rownames() to determine the current row names in iris


# Change the column names in iris to use "_" for name breaks using colnames


# Print iris

```

*** =solution
```{r}

# Use names() to determine the current column names in iris

names(iris)

# Use colnames() to determine the current column names in iris

colnames(iris)

# Use rownames() to determine the current row names in iris

rownames(iris)

# Change the column names in iris to use "_" for name breaks 

colnames(iris) <- c("Sepal_Length", "Sepal_Width", "Petal_Length", "Petal_Width", "Species")

# Print iris
iris

```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("iris")
test_output_contains("iris")
test_function("names")
test_function("colnames")
test_function("rownames")

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

--- type:NormalExercise lang:r xp:100 skills:1 key:420999c15f
## Dimension checking in Data Frames

As we discussed in the first exercise a data frame is similar to a matrix. This means that the size of a data frame is dependent on the number of rows and columns. We can quickly check the dimensions of a data frame using the `dim()` function.

The output from the `dim()` function tells us the number of rows followed by the number of columns.

Alternatively, we can explicitly call the number of rows and the number of columns using `nrow()` and `ncol()` respectively. 

The `length()` function is similar to `nrow()` and `ncol()`, but will instead return the number of objects within an object. For example `length` will return "5" for the object x shown below:

x <- c("A","B","C","D","E")


Why? Because there are 5 objects (A,B,C,D,E) within the object x.

With this knowledge what do you think the function `length` will return for the data frame iris?

Most people might say the number of rows, but this would be incorrect. The actual answer is the number of columns, but why?

The reason goes back to the R fundamentals we discussed in the first exercise pertaining to the composition of a data frame. Remember that a data frame is simply a list of vectors where each column represents a vector and the list in aggregate creates the data frame. In this case the data frame, iris, is made up of five vector objects: Sepal_Length, Sepal_Width, Petal_Length, Petal_Width and Species. 
The function `length()` counts the number of objects within an object and in the case of iris there are 5.

Now it's your turn to work with these four functions.


*** =instructions
- Use the `dim()` function to find the number of rows and columns within iris
- Use the `nrow()` function to find the number of rows within iris
- Use the `ncol()` function to find the number of columns within iris
- Use the `length()` function to confirm the answer is 5

*** =hint

*** =pre_exercise_code
```{r}


```

*** =sample_code
```{r}

# Use the `dim()` function to find the number of rows and columns within iris


# Use the `nrow()` function to find the number of rows within iris


# Use the `ncol()` function to find the number of columns within iris


# Use the `length()` function to confirm the answer is 5

```

*** =solution
```{r}

# Use the `dim()` function to find the number of rows and columns within iris
dim(iris)

# Use the `nrow()` function to find the number of rows within iris
nrow(iris)

# Use the `ncol()` function to find the number of columns within iris
ncol(iris)

# Use the `length()` function to confirm the answer is 5
length(iris)

```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_function("dim")
test_function("nrow")
test_function("ncol")
test_function("length")

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





