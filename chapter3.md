---
title       : Beyond the Basics with Data Frames
description : This chapter explores the three main ways of indexing data frames in R. We will look at indexing with a column name using the "$" notation, indexing using square bracket notation and indexing using the attach function. 
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:r xp:100 skills:1 key:a1f92e28d6
## Creating Empty Data Frames 

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
## Changing information within a Data Frame

Square Bracket indexing is probably the most commonly used form of indexing in R. The reason for this has to do with the fact that it allows the user to index both rows and columns simulataneously. This allows you to extract values, entire columns, entire rows and any combination of rows and columns.

**Square Bracket Indexing Notation**

> data.frame[rows,columns]

For instance if you wanted to index the first column from iris the notation would be:

iris[ , 1 ]

*First Row only?*

iris[ 1, ] Note: The comma is important!

*First row and first column?*

iris[ 1 , 1 ]

*How about the first column and first 5 rows?*

iris[ 1 : 5 , 1 ]

*Column 1 and 3 and rows 5 through 10?*

iris[ 5: 10 , c( 1 , 3 ) ]

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

Index_One <- iris[5, 1]

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

--- type:NormalExercise lang:r xp:100 skills:1 key:353e5b5e5d
## Creating New Columns in DataFrames

Now that you have a sense for how to index a data frame there are a few other tricks you might find useful for your tool kit.

For instance, when you index a data frame using a column name you can also index the rows using square brackets.The notation would look something like this:

> data.frame$column_name[ rows ]

Alternatively, when using square bracket notation to index a column you can also use the column name not just it's numbered position in the data frame.

> data.frame[, " column_name " ]

As you might have noticed when you index a data frame on only one column, R will return the output as a vector of values and not a column. In some instances, however, it is useful to have R return a column. You can do this by specifying the column position or column name in the square bracket without any commas. For instance:

> data.frame["column_name"]

This can be limiting though because you are not able to index rows simulataneously. To do this we need to set drop = FALSE. 

> data.frame[ 1 : 5 , 1, drop = FALSE ]

You can also exclude columns and rows when indexing by using a negative sign before the column or row you want to remove. For instance:

> data.frame[ , -1 ] 

This will produce all columns but the first.


*** =instructions
- Index the first five rows of the column Sepal.Width from iris using the `$` and bracket notation, assign it to a variable named index_one and print the new variable in the console
- Index the column Petal.Width from iris with the column name using square bracket notation, assign it to a variable named index_two and print the new variable in the console
- Return only the second column from iris in column form, assign it to a variable named index_three and print the new variable in the console 
- Return only the second column from iris in column form, indexed on rows 1 to 5, assign it to a variable named index_four and print the new variable in the console
- Return all but the first two columns from iris, assign it to a variable named index_five and print the new variable in the console

*** =hint


*** =pre_exercise_code
```{r}


```

*** =sample_code
```{r}

# Index the first five rows of column Sepal.Width from iris using the `$` and bracket notation, assign it to a variable named index_one

# Print index_one


#Index the column Petal.Width from iris with the column name using square bracket notation, assign it to a variable named index_two 

# Print index_two


# Return only the second column from iris in column form, assign it to a variable named index_three

# Print index_three


# Return only the second column from iris in column form, indexed on rows 1 to 5, assign it to a variable named index_four and print the new variable in the console

# Print index_four


# Return all but the first two columns from iris, assign it to a variable named index_five

# Print index_five


```

*** =solution
```{r}

# Index the first five rows of column Sepal.Width using the `$` and bracket notation, assign it to a variable named index_one

index_one <- iris$Sepal.Width[1:5]

# Print index_one

index_one

#Index the column Petal.Width from iris with the column name using square bracket notation, assign it to a variable named index_two 

index_two <- iris[,"Petal.Width"]
# Print index_two
index_two

# Return only the second column in column form, assign it to a variable named index_three

index_three <- iris[ 2 ]

# Print index_three

index_three

# Return only the second column from iris in column form, indexed on rows 1 to 5, assign it to a variable named index_four

index_four <- iris[1:5,2, drop = F]

# Print index_four

index_four

# Return all but the first two columns in iris, assign it to a variable named index_five

index_five <- iris[,-c(1,2)]

# Print index_five

index_five

```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("index_one")
test_object("index_two")
test_object("index_three")
test_object("index_four")

test_output_contains("index_one")
test_output_contains("index_two")
test_output_contains("index_three")
test_output_contains("index_four")

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

--- type:NormalExercise lang:r xp:100 skills:1 key:751023a015
## Applying Functions with Data Frames

The $ notation is pretty handy, but it can become very annoying when you have to type it each time that you want to work with your data. The `attach()` function offers a solution to this. When you pass a data frame through the attach function you are then able to call the columns of the data frame without explicitely calling the data frame first.

The notation for attach looks as follows

> attach(data.frame) 
<br>column_name</br>


*** =instructions
- Call the variable Petal.Width from the iris data frame using the attach function

*** =hint
- You first need to pass the data frame through the attach function
*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

# Call the variable Petal.Width from the iris data frame using the attach function

```

*** =solution
```{r}

# Call the variable Petal.Width from the iris data frame using the attach function
attach(iris)

Petal.Width
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_function("attach")
test_output_contains("Petal.Width")

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





