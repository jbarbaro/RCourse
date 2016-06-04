---
title       : Indexing with Data Frames
description : This chapter explores the four main ways of indexing data frames in R
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:r xp:100 skills:1 key:a1f92e28d6
## Indexing with a column's name

A key part of data manipulation is being able to acess values within your data frame. The first technique that you will learn is how to index a column from YOUR data frame. Recall that a column in a data frame is simply one of many vectors within a list that is the data frame. This allows us to easily index a column by using it's name. 

**Column Name Indexing Notation:**

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
## Introduction to indexing using Square Brackets

Square Bracket indexing is probably the most commonly used form of indexing in R. The reason for this has to do with the fact that it allows the user to index both rows and columns simulataneously. This allows you to extract values, entire columns, entire rows and any combination of rows and columns.

**Square Bracket Indexing Notation**

> data.frame[rows,columns]

For instance if you wanted to index the first column from iris the notation would be:

iris[, 1]

First Row only?

iris[1, ] Note: The comma is important!

First row and first column?

iris[1, 1]

How about the first column and first 5 rows?

iris[1:5, 1]

Column 1 and 3 and rows 5 through 10?

iris[5:10, c(1, 3)]

Any combination of rows and columns are possible using square bracket notation

*** =instructions
- Index the 1st column and 5th row in the data frame iris, assign it to a variable named Index_One and print the output
- Index just the 3rd and 4th column from iris, assign it to a variable named Index_Two and print the output
- Challenge: Index row 1, 5 and 10 from iris, assign it to a variable named Index_Three and print the output
- Challenge: Index column 5 and column 1 from iris in that order assign it to a variable named Index_Four and print the output

*** =hint
- You can use the c() function to explicitly call individual columns
- data.frame[c(2,5),] would return rows 2 and 5
- data.frame[c(5,2),] would return rows 5 and 2 in that order

*** =pre_exercise_code
```{r}
# Create data frame

```

*** =sample_code
```{r}

# Index the 1st column and 5th row in the data frame iris and assign it to a variable named Index_One

# Print Index_One

# Index just the 3rd and 4th column from iris and assign it to a variable named Index_Two

# Print Index_Two

# Challenge: Index row 1, 5 and 10 from iris and assign it to a variable named Index_Three

# Print Index_Three

# Challenge: Index column 5 and column 1 from iris in that order and assign it to a variable named Index_Four

# Print Index_Four
```

*** =solution
```{r}

# Index the 1st column and 5th row in the data frame iris and assign it to a variable named Index_One

Index_One <- iris[ ,c(1,5)]

# Print Index_One

Index_One

# Index just the 3rd and 4th column from iris and assign it to a variable named Index_Two

Index_Two <- iris[,3:4]

# Print Index_Two

Index_Two

# Challenge: Index row 1, 5 and 10 from iris and assign it to a variable named Index_Three

Index_Three <- iris[c(1,5,10),]

# Print Index_Three

Index_Three

# Challenge: Index column 5 and column 1 from iris in that order and assign it to a variable named Index_Four

Index_Four <- iris[, c(5,1)]

# Print Index_Four

Index_Four


```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("Index_One")
test_object("Index_Two")
test_object("Index_Three")
test_object("Index_Four")

test_output_contains("Index_One")
test_output_contains("Index_Two")
test_output_contains("Index_Three")
test_output_contains("Index_Four")


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

--- type:NormalExercise lang:r xp:100 skills:1 key:5e2f573a7d
## Expanded topics in Square Bracket Indexing Notation

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

--- type:NormalExercise lang:r xp:100 skills:1 key:4b6f7d13c4
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





