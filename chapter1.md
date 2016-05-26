---
title       : Insert the chapter title here
description : Insert the chapter description here
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:VideoExercise lang:python xp:50 skills:1 key:a81d6b7d40
## Analyze movie ratings

*** =video_link
//player.vimeo.com/video/154783078

--- type:MultipleChoiceExercise lang:python xp:50 skills:1 key:009ec13c0d
## A really bad movie

Have a look at the plot that showed up in the viewer to the right. Which type of movies have the worst rating assigned to them?

*** =instructions
- Long movies, clearly
- Short movies, clearly
- Long movies, but the correlation seems weak
- Short movies, but the correlation seems weak

*** =hint
Have a look at the plot. Do you see a trend in the dots?

*** =pre_exercise_code
```{python}
# The pre exercise code runs code to initialize the user's workspace. You can use it for several things:

# 1. Pre-load packages, so that users don't have to do this manually.
import pandas as pd
import matplotlib.pyplot as plt

# 2. Preload a dataset. The code below will read the csv that is stored at the URL's location.
# The movies variable will be available in the user's console.
movies = pd.read_csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

# 3. Create a plot in the viewer, that students can check out while reading the exercise
plt.scatter(movies.runtime, movies.rating)
plt.show()
```

*** =sct
```{python}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the
# pythonwhat Python package

msg_bad = "That is not correct!"
msg_success = "Exactly! The correlation is very weak though."

# Use test_mc() to grade multiple choice exercises.
# Pass the correct option (option 4 in the instructions) to correct.
# Pass the feedback messages, both positive and negative, to feedback_msgs in the appropriate order.
test_mc(4, [msg_bad, msg_bad, msg_bad, msg_success])
```

--- type:NormalExercise lang:python xp:100 skills:1 key:c3f846a154
## Plot the movies yourself

Do you remember the plot of the last exercise? Let's make an even cooler plot!

A dataset of movies, `movies`, is available in the workspace.

*** =instructions
- The first function, `np.unique()`, uses the `unique()` function of the `numpy` package to get integer values for the movie genres. You don't have to change this code, just have a look!
- Import `pyplot` in the `matplotlib` package. Set an alias for this import: `plt`.
- Use `plt.scatter()` to plot `movies.runtime` onto the x-axis, `movies.rating` onto the y-axis and use `ints` for the color of the dots. You should use the first and second positional argument, and the `c` keyword.
- Show the plot using `plt.show()`.

*** =hint
- You don't have to program anything for the first instruction, just take a look at the first line of code.
- Use `import ___ as ___` to import `matplotlib.pyplot` as `plt`.
- Use `plt.scatter(___, ___, c = ___)` for the third instruction.
- You'll always have to type in `plt.show()` to show the plot you created.

*** =pre_exercise_code
```{python}
# The pre exercise code runs code to initialize the user's workspace. You can use it for several things:

# 1. Preload a dataset. The code below will read the csv that is stored at the URL's location.
# The movies variable will be available in the user's console.
import pandas as pd
movies = pd.read_csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

# 2. Preload a package
import numpy as np
```

*** =sample_code
```{python}
# Get integer values for genres
_, ints = np.unique(movies.genre, return_inverse = True)

# Import matplotlib.pyplot


# Make a scatter plot: runtime on  x-axis, rating on y-axis and set c to ints


# Show the plot

```

*** =solution
```{python}
a = 10
while a > 5:
  print("%s is bigger than 5" % a)
  a -= 1
```

*** =sct
```{python}
def sct_on_condition_test():
  test_expression_result({"a": 4})
  test_expression_result({"a": 5})
  test_expression_result({"a": 6})

test_while_loop(index = 1,
                test = sct_on_condition_test,
                body = lambda: test_expression_output({"a":4}))   
```

--- type:NormalExercise lang:python xp:100 skills:2 key:9ffb8737d71ff0554a593086ccda71ab8fa1fe0f
## Importing entire text files

In this exercise, you'll be working with the file `moby_dick.txt`.
It is a text file that contains the opening sentences of Moby Dick,
one of the great American novels! Here you'll get experience
opening a text file, printing its contents to the console and, finally,
closing it.


*** =instructions
- Open the file `moby_dick.txt`. Make sure to open it as
read-only and to store it in the variable `'file'`.
- Print the contents of the file to the console using the `print()` function.
As Hugo showed in the video, you'll need to apply the method `read` to the
object `file`.
- Check whether the file is closed.
- Close the file using the `close` method and check again that the file 
is closed.

*** =hint
- Pass the filename to the 1st argument of `open`; the 2nd argument
should be `'r'` for 'read-only'.
- To read a file, use the method `read` and, to close it, the
method `close`.

*** =pre_exercise_code
```{python}
fn = 'https://s3.amazonaws.com/assets.datacamp.com/production/course_998/datasets/moby_opens.txt'
from urllib.request import urlretrieve
urlretrieve(fn, 'moby_dick.txt')
```

*** =sample_code
```{python}
# Open a file
file = open(___, ___ ) 

# Print it to console
print(___)

# Check whether file is closed
print(file.closed)

# Close file


# Check whether file is closed

```

*** =solution
```{python}
def to_decimal(number, base = 2):
    print("Converting %d from base %s to base 10" % (number, base))
    number_str = str(number)
    number_range = range(len(number_str))
    multipliers = [base ** ((len(number_str) - 1) - i) for i in number_range]
    decimal = sum([int(number_str[i]) * multipliers[i] for i in number_range])
    return decimal
```

*** =sct
```{python}
# All of the following test_function_definition() functions are done on the same
# function definition.

# Test the function, see that the defaults of the arguments are the same.
# For this function, we don't care about the argument names of the function. 
# Note: generally, we DO care about the names of the arguments, since they can
# be used as keywords. arg_defaults and arg_names will be set to True by default.

test_function_definition("to_decimal", arg_defaults = True, arg_names = False)

# Here, a feedback message will be generated. You can overwrite this feedback
# message by using:
# test_function_definition("to_decimal", arg_defaults = True, arg_names = False,
#     arg_defaults_msg = "Use the correct default argument values!")
# In the following tests, I'll always use the standard feedback messages, remember they
# can almost always be overwritten.

# We want to test whether the function returns the correct things with certain inputs.

test_function_definition("to_decimal", arg_names = False, arg_defaults = False, # Already tested this
    results = [
        (1001101, 2),
        (1212357, 8)]
)

# This will run to_decimal(1001101, 2) and to_decimal(1212357, 8) in student and solution
# environment, and match the results. If they don't match, a feedback message will be generated.
# Note: here we've set arg_defaults to False, because we already tested this in the first
# test_function_definition.

# We want to test the output of the function with certain inputs.

test_function_definition("to_decimal", arg_names = False, arg_defaults = False, # Already tested this
    outputs = [
        (1234, 6),
        (8888888, 9)]
)

# This will run to_decimal(1234, 6) and to_decimal(8888888, 9) in solution and student
# environment and compare their printed output.

# Finally, we might want them to use a certain function. For this we can do tests specifically
# on the body of the function. Remember you can use lambda functions or custom functions for this
# (also see wiki about test_if_else(), test_for_loop() and test_while_loop().

test_function_definition("to_decimal", arg_names = False, arg_defaults = False, # Already tested this 
    body = lambda: test_function("sum", args = [], incorrect_msg = "you should use the `sum()` function."))

# This will test the body of the function definition, and see if the function sum() is used.
# Note that the generated feedback will be preceded by: 'In your definition of `to_decimal()`, ...'
# So if the last test doesn't pass, this feedback will be generated:
#     In your definition of `to_decimal()`, you should use the `sum()` function.
```

