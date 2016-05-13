---
title       : Population modeling. From 1202 to 1920's.
description : How are populations growing? This lecture start in 1202 in Pisa, the middle age in Italy. There, Leonardo Bonacci, best knwon as Fibonacci, is going to teach us how to figure out the growth of a rabbit population. This incredible figure of medieval science will also provide us a troubling number named the Golden Ratio, that we are going to explore during the Renaissance. Then in 1798, we migrate nothward in England to meet Thomas Robert Malthus who will introduce us with the exponential growth of populations. Crossing the North Sea in 1838, we visit Pierre-François Verhulst, a Belgian mathematician, that revist the Malthus's model with finite resources. Here, he'll give us some very interesting ideas on "r" and "K" strategies... also, keep an eye on a young english naturalist/physician named Charles Darwin, he's just returning from a travel on the Beagle... In the early XXth century, after the First World War, scientists formalize the interaction between populations. Well, of course, it's well known, at least since 30,000 years (this lecture could have started much more earlier to meet cave painter in the Chauvet-Pont-d'Arc cave), that some species are predators preying on... prey! But according to Alfred James Lotka and Vito Volterra, a simple modeling of a predator-prey system can lead to very unexpected dynamics. Sorry? What about programming with R? Oh, it's just our DeLorean...
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:r xp:100 skills:1 key:66e52f467d
## Fibonacci sequence

So we are in 1202, and the mathematician Leonardo of Pisa is publishing *Liber Abaci*.

NOTE: add pictures, and context

Start simply. Just imagine one heterosexual couple of rabbit, giving birth to two rabbits, a male and a female. They are the second generation.

NOTE: explantation of how to build the sequence. The biological hypothesis! and giving a picture named the `fibonacci_sequence`.

We name the sequence $Fibo_n$. *Fibo* for Fibonacci, and the underscore $n$ give the generation. $Fibo_n$ is a sequence of the number of couple.
Example: $Fibo_0=1$ is the initial couple. $Fibo_1=1$ is the number of couple at the first generation. $Fibo_2=2$, $Fibo_2=3$, $Fibo_4=5$, $Fibo_5=8$, ...

*** =instructions
- Check out the picture `fibonacci_sequence`.
- Start by create a `vector` object named `fibo_seq` and give a number to the two first terms of the sequence.
- Use the loop `for` to produce the sequence.
- Use `plot()` to  plot `generation` on the x-axis and `number_couple` on the y-axis.

*** =hint
- Use `c()` for the second instruction.
- For the third instruction, the writing of a for loop is: `for (i in 3:n) { }`.
- For the plot, use `plot(x = ..., y = ...)`.

*** =pre_exercise_code
```{r}
generation = 10

# vector object and 2 firs elements of the sequence
fibo_seq = 
fibo_seq[1] = 
fibo_seq[2] = 

# make a loop for

# Print the sequence

```

*** =sample_code
```{r}
generation = 10

# vector object and 2 firs elements of the sequence
fibo_seq = 
fibo_seq[1] = 
fibo_seq[2] = 

# make a loop for
for ( ) { 

}
# Print the sequence

```

*** =solution
```{r}
generation = 10

# vector object and 2 firs elements of the sequence
fibo_seq = c()
fibo_seq[1] = 1
fibo_seq[2] = 1

# make a loop for
for (i in 3:generation){
  fibo_seq[i] = fibo_seq[i-1]+fibo_seq[i-2]
}

# Print the sequence
fibo_seq
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

--- type:VideoExercise lang:r xp:50 skills:1 key:59af007e54
## Analyze movie ratings

*** =video_link
//player.vimeo.com/video/154783078

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:d1fb2032c1
## A really bad movie

Have a look at the plot that showed up in the viewer to the right. Which type of movie has the worst rating assigned to it?

*** =instructions
- Adventure
- Action
- Animation
- Comedy

*** =hint
Have a look at the plot. Which color does the point with the lowest rating have?

*** =pre_exercise_code
```{r}
# The pre exercise code runs code to initialize the user's workspace. You can use it for several things:

# 1. Preload a dataset. The code below will read the csv that is stored at the URL's location.
# The movies variable will be available in the user's console.
movies <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

# 2. Pre-load packages, so that users don't have to do this manually.
library(ggplot2)

# 3. Create a plot in the viewer, that students can check out while reading the exercise
ggplot(movies, aes(x = runtime, y = rating, col = genre)) + geom_point()
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package

msg_bad <- "That is not correct!"
msg_success <- "Exactly! There seems to be a very bad action movie in the dataset."

# Use test_mc() to grade multiple choice exercises. 
# Pass the correct option (Action, option 2 in the instructions) to correct.
# Pass the feedback messages, both positive and negative, to feedback_msgs in the appropriate order.
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad)) 
```
