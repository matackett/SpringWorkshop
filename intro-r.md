Introduction for students new to R and RStudio
================
Your Name
Today’s Date

<div class="instructions">

</div>

## Yay we’ve started\!

If you have not ever used GitHub, you will first need to go in and
create an account. Look at the guidlines on Jenny Bryant’s Happy Git
with R website: <https://happygitwithr.com/github-acct.html>

Create your git account and make sure you write down your username and
password.

Now in github.com, search for the repository here:
<https://github.com/matackett/SpringWorkshop> and havd it ready. It’s
okay to go ahead and double click on the md file called intro-r.md and
follow along.

## Introduction

Your 100 level StatSci course this semester will march you through a
thorough introduction to using R for statistical science and data
science purposes, as well as for many other practical applications. You
should already be familiar with the environment you are going to use for
your course, whether it is RStudio in the Cloud, a Docker container, or
software installed on your own computer. Your instructor should have
given you that information and you should be ready to use it. The
materials here are a compilation of advice and instructions from your
professors Curry Hilton, Victoria Ellison, Yue Jiang, Shawn Santo, Bob
Eisinger, and especially Maria Tackett, Mine Cetinkaya-Rundel, and TAs
including Becky Tang, Jennifer Wilson, Frances Hu, and many helpful
resources.

Here are some key ideas:

If you are in the habit of saying you are not a coder, that stops here.

R is an open source programming language for statistical computing
(<http://cran-r-project.org>).

RStudio is the IDE or Interactive Development Environment we use to work
in R. RStudio is available open source, but their company also provides
some cloud-based servers for working in their environment, known as
RStudio in the Cloud.

## RStudio

Your RStudio window generally has four panels. This is customizable so
you might have changed it already. You can also drag the borders to
resize each portion.

  - Source: Where R markdown files are produced and saved

  - Console: Where live R code is run; cannot be saved

  - Environment: Where R objects live and are stored

  - Utility: Where directories, plots, packages, and help can be found

Your R Markdown file (this document) is in the upper left panel. (Note
that the workshop facilitators walked you through getting that file into
your RStudio environment from github)

The panel in the upper right contains your *workspace* as well as a
history of the commands that you’ve previously entered.

Any plots that you generate will show up in the panel in the lower right
corner. This is also where you can browse your files, access help,
manage packages, etc.

## R Packages

R is an open-source programming language, meaning that users can
contribute packages that make our lives easier, and we can use them for
free. For this lab, and many others in the future, we will use the
following R packages:

  - `statsr`: for data files and functions used in this course
  - `dplyr`: for data wrangling
  - `ggplot2`: for data visualization
  - `usethis`: for workflow automation (and eventually, to help write
    your own packages\!)

You should have already installed these packages using commands like
`install.packages` and \`install\_github’. These packages are part of a
modern version of R known collectively as the Tidyverse. Find out more
here: <https://rviews.rstudio.com/2017/06/08/what-is-the-tidyverse/>
When you open this Rmd file in R Studio, it may prompt you to install
these packages, with a yellow warning at the top of the screen. Click
‘Install’ if it asks you. Alternatively, simply uncomment whichever
you need and run this code chunk to install them.

``` r
#library(dplyr)
#library(ggplot2)
#library(statsr)
#library(usethis)
```

Next, you need to load the packages in your working environment. We do
this with the `library` function. Note that you only need to **install**
packages once, but you need to **load** them each time you relaunch
RStudio.

``` r
library(dplyr)
library(ggplot2)
#library(statsr)
library(usethis)
```

To do so, you can

  - click on the green arrow at the top of the code chunk in the R
    Markdown (Rmd) file, or
  - highlight these lines, and hit the **Run** button on the upper right
    corner of the pane, or
  - type the code in the console.

Going forward you will be asked to load any relevant packages at the
beginning of each lab.

## Git and Github

You will use GitHub to obtain the RMarkdown or .Rmd file for this
workshop. If you already have a GitHub account, great\! If not, take a
minute to start one. But first, some user name advice…

Jenny Bryan is an RStudio software engineer who wrote ‘Happy Git and
Github for the useR’. She will be a keynote speaker at the RStudio
Conference later this month, which you’ll hear more about.  
Meanwhile, here is her page of advice on creating a free Github account
and choosing a user name that works.
<https://happygitwithr.com/github-acct.html> Register your free
account.  
You’ll have to confirm the request in email.

Now the workshop facilitators will help you fork the repository that
contains the software you need.

Configure git.

You will use the use\_git\_config() function from the usethis package.

Type the following lines of code in the console in RStudio filling in
your name and email address.

The email address is the one tied to your GitHub account.

``` r
library(usethis)
use_git_config(user.name = "GitHub username", user.email="your email")
```

For example, Joan’s would be

library(usethis) use\_git\_config(user.name=“joan-combs-durso”,
[user.email="joan.durso@duke.edu](mailto:user.email=%22joan.durso@duke.edu)")

Now your facilitators will help you get started with forking the
package.

## Dataset Diamonds can be found in the ggplot2 package\!

We are going to use a dataset called ‘diamonds’. To get you started, run
the following command to load the data and to inspect the first ten rows
of the file.

``` r
data(diamonds)
#That command loaded the file.  The next one shows you the first few rows.

head(diamonds)
```

    ##   carat       cut color clarity depth table price    x    y    z
    ## 1  0.23     Ideal     E     SI2  61.5    55   326 3.95 3.98 2.43
    ## 2  0.21   Premium     E     SI1  59.8    61   326 3.89 3.84 2.31
    ## 3  0.23      Good     E     VS1  56.9    65   327 4.05 4.07 2.31
    ## 4  0.29   Premium     I     VS2  62.4    58   334 4.20 4.23 2.63
    ## 5  0.31      Good     J     SI2  63.3    58   335 4.34 4.35 2.75
    ## 6  0.24 Very Good     J    VVS2  62.8    57   336 3.94 3.96 2.48

To do so, once again, you can

  - click on the green arrow at the top of the code chunk in the R
    Markdown (Rmd) file, or
  - put your cursor on this line, and hit the **Run** button on the
    upper right corner of the pane, or
  - type the code in the console.

This command instructs R to load some data. You should see that the
workspace area in the upper righthand corner of the RStudio window now
lists a data set called `diamonds` that has 53940 observations on 10
variables. As you interact with R, you will create a series of objects.
Sometimes you load them as we have done here, and sometimes you create
them yourself as the byproduct of a computation or some analysis you
have performed.

``` r
#type the following in the console to view the whole dataset.
diamonds
```

However printing the whole dataset in the console is not that useful.
One advantage of RStudio is that it comes with a built-in data viewer.
Click on the name `diamonds` in the *Environment* pane (upper right
window) that lists the objects in your workspace. This will bring up an
alternative display of the data set in the *Data Viewer* (upper left
window). You can close the data viewer by clicking on the *x* in the
upper lefthand corner.

What you should see are eleven columns of data, each row representing a
different diamond: the first entry in each row is simply the row number
(an index we can use to access the data from individual stones if we
want), the second is price in dollars, and the third is the weight in
carats of that gem. Use the scrollbar on the right side of the console
window to examine the complete data set.

Note that the row numbers in the first column are not part of the
‘diamonds’ data. R adds them as part of its printout to help you make
visual comparisons. You can think of them as the index that you see on
the left side of a spreadsheet. In fact, the comparison to a spreadsheet
will generally be helpful. R has stored the ‘diamonds’ data in a kind of
spreadsheet or table called a *data frame*.

You can see the dimensions of this data frame by typing:

``` r
dim(diamonds)
```

    ## [1] 53940    10

This command should output `[1] 53940 10`, indicating that there are
53940 rows or observations and 10 columns or fieldnames. columns (we’ll
get to what the `[1]` means in a bit), just as it says next to the
object in your workspace. You can see the names of these columns (or
variables) by
    typing:

``` r
names(diamonds)
```

    ##  [1] "carat"   "cut"     "color"   "clarity" "depth"   "table"   "price"  
    ##  [8] "x"       "y"       "z"

<div class="question">

How many variables are included in this data set?

  - 2
  - 9
  - 10
  - 82
  - 53940

</div>

<div class="exercise">

What are some of the values for ‘cut" included in this dataset? Hint:
Take a look at the ’cut’ variable in the Data Viewer to answer this
question.

</div>

You should see that the data frame contains the columns `price`,
`carat`, and `cut`. At this point, you might notice that many of the
commands in R look a lot like functions from math class; that is,
invoking R commands means supplying a function with some number of
arguments. The `dim` and `names` commands, for example, each took a
single argument, the name of a data frame.

<div class="boxedtext">

**Tip: ** If you use the up and down arrow keys, you can scroll through
your previous commands, your so-called command history. You can also
access it by clicking on the history tab in the upper right panel. This
will save you a lot of typing in the future.

</div>

### R Markdown

So far we asked you to type your commands in the console. The console is
a great place for playing around with some code, however it is not a
good place for documenting your work. Working in the console exclusively
makes it difficult to document your work as you go, and reproduce it
later.

R Markdown is a great solution for this problem. And, you already have
worked with an R Markdown document – this lab\! Going forward type the
code for the questions in the code chunks provided in the R Markdown
(Rmd) document for the lab, and **Knit** the document to see the
results. Knit should produce an HTML file for you that lets you

### Some Exploration

Let’s start to examine the data a little more closely. To find out more
about this dataset, you could use some help. Tyr typing the name of the
dataset with a ‘?’ in front of it.

``` r
?diamonds
```

    ## Help on topic 'diamonds' was found in the following packages:
    ## 
    ##   Package               Library
    ##   openintro             /usr/local/lib/R/site-library
    ##   ggplot2               /usr/local/lib/R/site-library
    ## 
    ## 
    ## Using the first match ...

You should see the documentation on the dataset in the Help window. Try
out the other tabs there briefly.  
We can access the data in a single column of a data frame separately
using a command
    like

``` r
diamonds$clarity[1:100]
```

    ##   [1] SI2  SI1  VS1  VS2  SI2  VVS2 VVS1 SI1  VS2  VS1  SI1  VS1  SI1  SI2 
    ##  [15] SI2  I1   SI2  SI1  SI1  SI1  SI2  VS2  VS1  SI1  SI1  VVS2 VS1  VS2 
    ##  [29] VS2  VS1  VS1  VS1  VS1  VS1  VS1  VS1  VS1  SI1  VS2  SI2  SI2  SI1 
    ##  [43] VS2  VS1  SI2  SI1  SI2  SI2  VS2  SI2  SI1  VS1  SI1  VS2  VS2  SI2 
    ##  [57] SI2  SI1  SI1  SI1  VS1  SI1  SI1  SI1  SI2  VVS2 VVS1 SI1  SI1  VVS1
    ##  [71] VVS1 SI1  SI1  SI1  SI1  VVS2 VVS2 VVS2 VVS2 VVS1 VVS1 VVS1 VVS2 SI2 
    ##  [85] VVS1 VVS1 VVS1 VVS1 VVS2 SI1  SI1  SI2  VS2  VS2  SI2  VS2  VS1  SI2 
    ##  [99] SI1  SI1 
    ## Levels: I1 IF SI1 SI2 VS1 VS2 VVS1 VVS2

This command will only show the value of clarity of the diamonds
measured in this dataset. The dollarsign basically says “go to the data
frame that comes before me, and find the variable that comes after me”.
Note that it should have given you a message in the data viewer window
that you have exceeded the maximum print length so it has stopped before
it has shown you more than 1000 values.

<div class="question">

What command would you use to extract just the data on diamond length?

  - `diamonds$x`
  - `x`
  - `diamonds[x]`
  - `$x`

</div>

``` r
# type your code for the Question 2 here, and Knit
diamonds$x[1:10]
```

    ##  [1] 3.95 3.89 4.05 4.20 4.34 3.94 3.95 4.07 3.87 4.00

Notice that the way R has printed these data is different. When we
looked at the complete data frame, we could have seen 53940 rows, one on
each line of the display. These data are no longer structured in a table
with other variables, so they are displayed one right after another.
Objects that print out in this way are called vectors; they represent a
set of numbers. R has added numbers in \[brackets\] along the left side
of the printout to indicate locations within the vector. For example,
3.95 follows \[1\], indicating that 3.95 is the first entry in the
vector. And if \[801\] starts a line, then that would mean the first
number on that line would represent the 801st entry in the vector.

R has some powerful functions for making graphics. We can create a
simple plot of the price of diamonds by their weight measured in carats
with the command

``` r
ggplot(data = diamonds, aes(x = carat, y = price)) +
  geom_point()
```

![](intro-r_files/figure-gfm/plot-price-vs-carat-1.png)<!-- -->

Before we review the code for this plot, let’s summarize the trends we
see in the data.

<div class="question">

Which of the following best describes the relationship between price and
diamond weight on stones included in this dataset?

  - There are so many dots it is hard to see a trend\!
  - Price and diamond weight in carats are positively related.
  - The heavier the rock, the pricier it is\!
  - Who wants to buy diamonds anyway?
  - This is a really ugly plot; there must be more to learn\!

</div>

Back to the code… We use the `ggplot()` function to build plots. If you
run the plotting code in your console, you should see the plot appear
under the *Plots* tab of the lower right panel of RStudio. Notice that
the command above again looks like a function, this time with arguments
separated by commas.

  - The first argument is always the dataset.
  - Next, we provide the variables from the dataset to be assigned to
    `aes`thetic elements of the plot, e.g. the x and the y axes.
  - Finally, we use another layer, separated by a `+` to specify the
    `geom`etric object for the plot. Since we want to scatterplot, we
    use `geom_point`.

You might wonder how you are supposed to know the syntax for the
`ggplot` function. Thankfully, R documents all of its functions
extensively. To read what a function does and learn the arguments that
are available to you, just type in a question mark followed by the name
of the function that you’re interested in. Try the following in your
console:

``` r
`?`(ggplot)
```

Notice that the help file replaces the plot in the lower right panel.
You can toggle between plots and help files using the tabs at the top of
that panel.

<div class="boxedtext">

More extensive help for plotting with the `ggplot2` package can be found
at <http://docs.ggplot2.org/current/>. The best (and easiest) way to
learn the syntax is to take a look at the sample plots provided on that
page, and modify the code bit by bit until you get achieve the plot you
want.

</div>

### R as a big calculator

Now, suppose we want to plot the total dimensions of each of the
diamonds. To compute this, we could use the fact that R is really just a
big calculator. We can type in mathematical expressions like

``` r
3.95 + 3.98 + 2.43
```

    ## [1] 10.36

to get the value for that first one. We could repeat this once for each
stone, but there is a faster way. If we add the vector for each, R will
compute all sums simultaneously.

``` r
sum_xyz <- diamonds$x + diamonds$y + diamonds$z
sum_xyz[1:10]
```

    ##  [1] 10.36 10.04 10.43 11.06 11.44 10.38 10.40 10.71 10.14 10.44

What you will see are 53940 numbers (in that packed display, because we
aren’t looking at a data frame here), each one representing the sum
we’re after. Take a look at a few of them and verify that they are
right.

### Adding a new variable to the data frame

We’ll be using this new vector to generate some plots, so we’ll want to
save it as a permanent column in our data frame.

``` r
diamonds <- diamonds %>%
  mutate(total = x + y + z)
```

What in the world is going on here? The `%>%` operator is called the
**piping** operator. Basically, it takes the output of the current line
and pipes it into the following line of code.

<div class="boxedtext">

**A note on piping: ** Note that we can read these three lines of code
as the following:

*“Take the `diamonds` dataset and **pipe** it into the `mutate`
function. Using this mutate a new variable called `total` that is the
sum of the dimensions called `x` and `y` and ‘z’ for each stone. Then
assign this new resulting dataset to the object called `diamonds`,
i.e. overwrite the old `diamonds` dataset with the new one containing
the new variable.”*

This is essentially equivalent to going through each row and adding up
the dimensions for each stone and recording that value in a new column
called total.

</div>

<div class="boxedtext">

**Where is the new variable? ** When you make changes to variables in
your dataset, click on the name of the dataset again to update it in the
data viewer.

</div>

You’ll see that there is now a new column called `total` that has been
tacked on to the data frame. The special symbol `<-` performs an
*assignment*, taking the output of one line of code and saving it into
an object in your workspace. In this case, you already have an object
called `diamondst`, so this command updates that data set with the new
mutated column.

We can make a plot comparing diamond table by total dimensions with the
following command.

``` r
ggplot(data = diamonds, aes(x = table, y = total)) +
  geom_line()
```

![](intro-r_files/figure-gfm/plot-total-vs-table-line-1.png)<!-- -->

Note that using `geom_line()` instead of `geom_point()` results in a
line plot instead of a scatter plot. You want both? Just layer them on:

``` r
ggplot(data = diamonds, aes(x = table, y = total)) +
  geom_line() +
  geom_point()
```

![](intro-r_files/figure-gfm/plot-total-vs-table-line-and-point-1.png)<!-- -->

<div class="exercise">

Eek…it looks like something that is going to crawl off the screen on its
six legs\! These are some really ugly plots. You can do better\!

Think about diamonds…some of them are fairly flat while others are quite
pointed. It all depends on the 4 C’s of the stone. There are many
resources on the internet to find out how diamonds are valued and what
is interesting about them.

Now, with your partner, play with mutate and piping and create a plot of
interest to you.

</div>

``` r
# type your code for the Exercise here, and Knit
```

Finally, in addition to simple mathematical operators like subtraction
and division, you can ask R to make logical comparisons like greater
than, `>`, less than, `<`, and equality, `==`. For example, we can ask
if the x dimension is greater than the y dimension for these stones with
the expression

``` r
diamonds <- diamonds %>%
  mutate(more_x = x > y)
```

This command add a new variable to the `diamonds` data frame containing
the values of either `TRUE` if that stone was longer than its width, or
`FALSE` if it was not (the answer may surprise you).

This variable contains different kind of data than we have considered so
far. All other columns in the `diamonds` data frame have values that are
numerical (carat, table and width) or text (color, cut). Here, we’ve
asked R to create *logical* data, data where the values are either
`TRUE` or `FALSE`. In general, data analysis will involve many different
kinds of data types, and one reason for using R is that it is able to
represent and compute with many of them.

We can use just part of the dataset by filtering. Here, we are going to
filter on a particular value of cut and color and plot price vs carat.

``` r
fair_diamonds <- diamonds %>%
  filter(cut == "Fair" & color =="G")
ggplot(data = fair_diamonds, aes(x = price, y = carat)) +
  geom_point()
```

![](intro-r_files/figure-gfm/try-filtering-diamonds-1.png)<!-- -->

\#\#Statistics?? What if you wanted some descriptive statistics? Let’s
get the means of the stone prices.

``` r
diamonds %>%
  summarise(mean = mean(price), sd = sd(price), median = median(price))
```

    ##     mean      sd median
    ## 1 3932.8 3989.44   2401

## Resources for learning R and working in RStudio

That was a short introduction to R and RStudio, but your instructors
will provide you with more functions and a more complete sense of the
language as your course progresses. You might find the following tips
and resources helpful.

  - Many courses use the Tidyverse while other courses will expect you
    to learn to work in base R, rather than in the RStudio IDE. In
    Tidyverse-flavored courses, you will use `dplyr` (for data
    wrangling) and `ggplot2` (for data visualization) extensively. If
    you are googling for R code, make sure to also include these package
    names in your search query. For example, instead of googling
    “scatterplot in R”, google “scatterplot in R with ggplot2”.

  - There is a terrific resource on Medium called Towards Data Science,
    and you can find good information there, although you may have a
    limited number of free articles to read.
    <https://towardsdatascience.com/data-science/home>

  - Do a quick search on “Free books on R” and you will find a huge
    array of choices.

  - Lots of R users post their own guides that you can find by
    searching. Here’s one from David Romney at Harvard:
    <https://scholar.harvard.edu/dromney/online-resources-learning-r>

  - The r-statistics blog is very helpful:
    <https://www.r-statistics.com/> In fact, you will find that the R
    community by its very nature is beginner friendly.

You can attend as much of the RStudio Conference that you want, by
joining our RStudio conference livestream watch party on January 29 and
30, right here at Duke. More info here:
<https://blogs.library.duke.edu/data/2020/01/13/2020-rstudio-conference-livestream-coming-to-duke-libraries/>

  - The following cheatsheets may come in handy throughout your courses.
    Note that some of the code on these cheatsheets may be too advanced
    for your needs now, however the majority of it will become useful as
    you progress through your statistical science courses.
      - [Data wrangling
        cheatsheet](http://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf)
      - [Data visualization
        cheatsheet](https://github.com/rstudio/cheatsheets/raw/master/data-visualization-2.1.pdf)
      - [R
        Markdown](https://github.com/rstudio/cheatsheets/raw/master/rmarkdown-2.0.pdf)

## Troubleshooting

If you run into problems with your RStudio work, start by inspecting the
console for error messages. See what it tells you. Then you can try to
look up that error message. Sites like Stack Overflow
<https://stackoverflow.com/questions/tagged/rstudio> provide lots of
resources and answers to questions people have already asked. You will
learn R more quickly if you try to solve problems yourself. We all need
help at times.

If you need help with a problem in your labs, please ask your TA or your
classmates. Don’t be the person who posts a question to a website like
Stack Overflow for which the answers can be readily found on the
internet via a simple search. Those kinds of questions will be ignored
or will result in heaps of abuse. Some sites are more beginner-friendly
than others. Your TAs will have some suggestions for you.

Whatever you do, please don’t post your assigned questions onto paid
answer-sharing services. That’s a violation of the Community Standard as
well as a very poor way to learn to use R.

Acknowledgements: This is derived from a Statistics with R lab derived
from an Open Intro Statistics lab. Thanks to Mine Cetinkaya-Rundel and
Maria Tackett for all their help.

<div id="license">

This is a derivative of an
[OpenIntro](https://www.openintro.org/stat/labs.php) lab, and is
released under a [Attribution-NonCommercial-ShareAlike 3.0 United
States](https://creativecommons.org/licenses/by-nc-sa/3.0/us/) license.

</div>
