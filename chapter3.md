---
title       : Beyond the Basics with Data Frames
description : In this chapter we look at other commonly used techniques with data frames that will assist you in data analytics.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:r xp:100 skills:1 key:a1f92e28d6
## Creating Empty Data Frames 

In some instances it is useful to create an empty data frame. Think of a situation where the data being populated in a data frame is done so using a loop, in this scenario having an empty data frame is nessissary.

You can easily create an empty data frame by assigning `dataframe()` to a variable, for instance

> x <- data.frame()

In some instances you may already know the column names you want for the data table but not the data. In this case you can prepopulate the data frame with empty columns by passing a call for the type of variable you want the column to be. For instance:

> number_column <- numeric() 
<br> x <- data.frame(number_column) </br>

As shown above, you can then create an empty data frame by passing the empty variable vectors through the data frame function like you did when creating a data frame with values.



*** =instructions
- Create an empty data frame named `df_empty` that has a column named `numeric_col` which is of type numeric and a second column named `char_col` which is of type character
- Print `df_empty`
*** =hint
- First create `numeric_col` and `char_col` then pass them through `data.frame()`
- To set a empty vector of type character use `character()`

*** =pre_exercise_code
```{r}
# recall iris data
data(iris)
```

*** =sample_code
```{r}
# Create numeric_col

# Create char_col

# Create a new empty data frame named df_empty

# Print df_empty
```

*** =solution
```{r}
# Create numeric_col

numeric_col <- numeric()

# Create char_col

char_col <- character()

# Create a new empty data frame named df_empty

df_empty <- data.frame(numeric_col,char_col)

# Print df_empty

df_empty


```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("numeric_col")
test_object("char_col")
test_object("df_empty")
test_output_contains("df_empty")

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

In some instances you may need to change values or add values into an existing data frame. Think of an istance where a value is set as NA but you know the value and need to replace the NA. 

The technique for replacing/ adding values in data frame is simple. First you index the data frame to the position you want to change, and then you assign it a value. 

For instance:

> data.frame[1,2] <- new_value

You can also replace an entire column or row as long as the vector you are replacing with is the same length

> data.frame[,2] <- new_vector_of_values


*** =instructions
- `test_df` is a pre populated data frame with two columns. The first column is numeric and the second is a character vector. Begin by viewing `test_df`
- Replace the `NA` value in `test_df` with the number 3
- Change the character column to values `f,g,h,i,j` in one call
- Print `test_df`

*** =hint
- To assign the character vector new values in one call you must first create a vector of new values

*** =pre_exercise_code
```{r}
# Create data frame

test_df <- data.frame(numeric = c(1:2,NA,4:5), character = c("a","b","c","d","e"))

```

*** =sample_code
```{r}

# View test_df

# Replace the NA value in test_df

# Change the values in the character column

# Print test_df

```

*** =solution
```{r}

# View test_df

test_df

# Replace the NA value in test_df

test_df[3,1] <- 3

# Change the values in the character column

test_df[,2] <- c("f","g","h","i","j")

# Print test_df

test_df

```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("test_df")
test_output_contains("test_df")



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
## Creating New Rows and Columns in DataFrames

Some instance you might need to create a whole new row or a whole new column of information. Doing this is quite easy and only takes a couple steps 

**Creating a new column**

> data.frame$new_column_name <- new_vector_of_values

Adding a new column begins as though you were going to index a column already in the data frame using the "$" notation. Instead, however, you type the new column name and assign that new column a vector of values associated with it.

**Creating a new row **

Creating a new row is a little different. In this case we use the function `rbind` and pass through it the original data frame and the new row we want to add.

For example:

> data.frame <- rbind( data_frame , new_row )



*** =instructions
- Using the data frame `test_df` from the last exercise add a new column of letters g:k, name the column character_2
- Using the data frame `test_df` add a new row sequentially expanding on the columns numeric, character and character_2

*** =hint
- Make sure to assign the output to `test_df`
- When creating a vector of new values for a column do not include the column name
- You first need to create a new vector of values for the new row/coloumn before adding it to the existing data frame
- Print test_df

*** =pre_exercise_code
```{r}
test_df <- data.frame(numeric = c(1:2,NA,4:5), character = c("a","b","c","d","e"))
```

*** =sample_code
```{r}

# View the data frame test_df

# Create a new vector of values for the column character_2

# Combine the column vector character_2 with the original data frame test_df

# Create a new vector of values for the new row

# Combine the row vector with the original data frame test_df

# Print test_df

```

*** =solution
```{r}

# View the data frame test_df

test_df

# Create a new vector of values for the column character_2

character_2 <- c("g","h","i","j","k")

# Combine the column vector character_2 with the original data frame test_df

test_df$character_2 <- character_2

# Create a new vector of values for the new row

new_row <- c(6, "f","l")

# Combine the row vector with the original data frame test_df

test_df <- rbind(test_df, new_row)

# Print test_df

test_df

```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_object("test_df")
test_output_contains("test_df")


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
## Applying Functions with Data Frames

The last topic we will discuss with regards to data frames is applying functions to preform calculations with the data held in the data frame. We can use the `apply` function to perform different operations accross both the columns and rows in our data frame. 

The first argument in the `apply` function is the data.frame, the second is an indicator for how the calcuations will be preformed. A "1" indicates across rows while a "2" indicates across columns. The final input is the calculation you want done (mean, median, ect.)


For our excerises we will take a look at the iris data set once again.


*** =instructions
- Create a new dataset named iris2 with only numeric information 
- Calculate the sum of each column and assign the output to a variable called sum_df, print sum_df
- Determine the mean of each row and assign the output to a variable called mean_df, print mean_df

*** =hint
- Only the first four columns are numeric
- You need to index the first four columns before preceding
- the function for mean is `mean` and for sum is `sum`
*** =pre_exercise_code
```{r}
data(iris)
```

*** =sample_code
```{r}

# Create a new dataset named iris2 with only numeric information 

# Calculate the sum for each column

# Print sum_df

# Calculate the mean of each row

# Print mean_df

```

*** =solution
```{r}

# Create a new dataset named iris2 with only numeric information 

iris2 <- iris[,1:4]

# Calculate the sum for each column

sum_df <- apply(iris2,2,sum)

# Print sum_df

sum_df

# Calculate the mean of each row

mean_df <- apply(iris2,1,mean)

# Print mean_df

mean_df

```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

test_function("apply")
test_object("iris2")
test_output_contains("sum_df")
test_output_contains("mean_df")

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





