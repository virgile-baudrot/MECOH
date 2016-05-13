---
title       : Population modeling. From 1202 to 1920's.
description : How are populations growing? This lecture start in 1202 in Pisa, the middle age in Italy. There, Leonardo Bonacci, best knwon as Fibonacci, is going to teach us how to figure out the growth of a rabbit population. This incredible figure of medieval science will also provide us a troubling number named the Golden Ratio, that we are going to explore during the Renaissance. Then in 1798, we migrate nothward in England to meet Thomas Robert Malthus who will introduce us with the exponential growth of populations. Crossing the North Sea in 1838, we visit Pierre-François Verhulst, a Belgian mathematician, that revist the Malthus's model with finite resources. Here, he'll give us some very interesting ideas on "r" and "K" strategies... also, keep an eye on a young english naturalist/physician named Charles Darwin, he's just returning from a travel on the Beagle... In the early XXth century, after the First World War, scientists formalize the interaction between populations. Well, of course, it's well known, at least since 30,000 years (this lecture could have started much more earlier to meet cave painter in the Chauvet-Pont-d'Arc cave), that some species are predators preying on... prey! But according to Alfred James Lotka and Vito Volterra, a simple modeling of a predator-prey system can lead to very unexpected dynamics. Sorry? What about programming with R? Oh, it's just our DeLorean...
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:NormalExercise lang:r xp:100 skills:1 key:66e52f467d
## Fibonacci sequence

NOTE: ADD a slide : So we are in 1202, and the mathematician Leonardo of Pisa is publishing *Liber Abaci*.
NOTE: Pictures, and context in the slides !!!

Start simply. Just imagine one heterosexual couple of rabbit, giving birth to two rabbits, a male and a female. They are the second generation.

NOTE: explantation of how to build the sequence. The biological hypothesis! and giving a picture named the `fibonacci_sequence`.

*** =instructions
- Check out the picture `fibonacci_sequence`.
- Start by create a `vector` object named `fibo_seq` and give a number to the two first terms of the sequence.
- Use the loop `for` to produce the sequence.
- Use `plot()` to  plot `generation` on the x-axis and `number_couple` on the y-axis.

*** =hint
- Use `c()` for the second instruction.
- For the third instruction, the writing of a for loop is: `for (i in 3:n) { }`.
- For the plot, use `plot(x = ..., y = ...)`.

*** =sample_code
```{r}
# Let 10 generations
generation = 10

# vector object and 2 first elements of the sequence

# Make a loop for

```

*** =solution
```{r}
# Let 10 generations
generation = 10

# vector object and 2 first elements of the sequence
fibo_seq = c(1,1)

# make a loop for
for (i in 3:generation){
  fibo_seq[i] = fibo_seq[i-1]+fibo_seq[i-2]
}
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package. Documentation can also be found at github.com/datacamp/testwhat/wiki

# Test if student as called the function c()
#test_function("c", args = "x",
#              not_called_msg = "You didn't call `c()`!")


# Test the output of the sequence
test_output_contains("fibo_seq")

# Test whether the student correctly used plot()
# Again, we use the automatically generated feedback here
#test_function("plot", args = "x")
#test_function("plot", args = "y")

# Checks whether the student's submission generated an error.
test_error()  

# Final message the student will see upon completing the exercise
success_msg("Good work!")
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:d1fb2032c1
## The Golden Ratio

Have a look at the plot that showed up in the viewer to the right.
The sequence of point is converging toward the value of golden ratio `(1+5^(1/2))/2=1.618...`.
Which sequence using the Fibonacci's sequence `Fib[n]` converge toward the golden ratio?

*** =instructions
- `Fib[n]/Fib[n-1]`
- `Fib[n]/Fib[n-1]^(1/2)`
- `(1+Fib[n]^(1/2))/2`
- `Fib[n]/(Fib[n-1]+Fib[n-2])`

*** =hint
Remember the Fibonacci's sequence: 1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,1597,2584,4181,6765

*** =pre_exercise_code
```{r}
# The pre exercise code runs code to initialize the user's workspace. You can use it for several things:

# 1. Preload a dataset. The code below will read the csv that is stored at the URL's location.
# The movies variable will be available in the user's console.
#movies <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")
generation = seq(1,20,1)
fibo_seq=c(1,1) ; golden_ratio=c(1,1)
for (i in 3:length(generation)){
  fibo_seq[i] = fibo_seq[i-1]+fibo_seq[i-2]
  golden_ratio[i]=fibo_seq[i]/fibo_seq[i-1]
}

# 2. Pre-load packages, so that users don't have to do this manually.
library(ggplot2)

# 3. Create a plot in the viewer, that students can check out while reading the exercise
ggplot()+theme_bw()+
  geom_point(aes(x=generation,y=golden_ratio))+
  geom_hline(yintercept = (1+sqrt(5))/2)
```

*** =sct
```{r}
# The sct section defines the Submission Correctness Tests (SCTs) used to
# evaluate the student's response. All functions used here are defined in the 
# testwhat R package

msg_bad <- "That is not correct!"
msg_success <- "Exactly!"

# Use test_mc() to grade multiple choice exercises. 
# Pass the correct option (Action, option 1 in the instructions) to correct.
# Pass the feedback messages, both positive and negative, to feedback_msgs in the appropriate order.
test_mc(correct = 1, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad)) 
```

--- type:VideoExercise lang:r xp:50 skills:1 key:59af007e54
## Analyze movie ratings

*** =video_link
//player.vimeo.com/video/154783078
