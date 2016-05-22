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
