# Introduction 

## Why R? {.unnumbered}

R is a complete programming language and software environment for statistical computing and graphical representation.
As part of the GNU Project (free software, mass collaboration project), the source code is free available.
Its functionalists can be expanded by importing packages.
For more details on R see <https://www.r-project.org/>.

Although R has a steep learning curve, the command-line approach advocated in this book can quickly pay off.
As you'll learn in subsequent chapters, R is an effective tool for tackling a wide range of geographic data challenges.
We expect that, with practice, R will become the program of choice in your geospatial toolbox for many applications.
Typing and executing commands at the command-line is, in many cases, faster than pointing-and-clicking around the graphical user interface (GUI) of a desktop GIS.
For some applications such as Spatial Statistics and modeling R may be the *only* realistic way to get the work done.

There are many reasons for using R for geocomputation: R is well-suited to the interactive use required in many geographic data analysis workflows compared with other languages.
R excels in the rapidly growing fields of Data Science (which includes data carpentry, statistical learning techniques and data visualization) and Big Data (via efficient interfaces to databases and distributed computing systems).
Furthermore R enables a reproducible workflow: sharing scripts underlying your analysis will allow others to build-on your work.

Other languages such as Python, Java and C++ can be used for geocomputation and there are excellent resources for learning geocomputation *without R*.
None of these provide the unique combination of package ecosystem, statistical capabilities, visualization options, powerful IDEs offered by the R community.
Furthermore, by teaching how to use one language (R) in depth, this book will equip you with the concepts and confidence needed to do geocomputation in other languages.

### R Packages

A package is a file generally composed of R scripts (e.g., functions).
On all operation systems the function "install.packages()" can be used to download and install a package automatically.
Once a package has been installed, it can be loaded in a session by using the command \textcolor{red}{library(package)}.
To check the list of the installed libraries, the function \textcolor{red}{library()} can be used.
When you open an **R Markdown** document (.Rmd) the program propose you automatically to install the libraries listed there.

### Some tips

-   R is case sensitive!
-   Previously used command can be recalled in the console by using the *up arrow* on the keyboard.
-   The working directory by default is "*C:/user/.../Documents*".
    -   It can be found using the command \textcolor{red}{getwd()}
    -   It can be changed using the command line \textcolor{red}{setwd("C:/Your/own/path")}
-   In **R Markdown**: the working directory when evaluating R code chunks is the directory of the input document by default.
    -   To access to a specific file in a sub-folder use ". /subfolder/file.ext"
    -   To access to a specific file in a up-folder use ". . /upfolder/file.ext"

### R Commands (online resources)

Many table resuming the main R commands can be found online.
Here some useful links:

-   [A short list of the most useful R commands](https://www.maths.usyd.edu.au/u/jchan/Rcommands.pdf)

-   [Table of Useful R commands](https://sites.calvin.edu/scofield/courses/m143/materials/RcmdsFromClass.pdf)

-   [Basic Commands to Get Started with R](https://rpubs.com/ssammut/ResearchStats)

## R Markdown

This is an R Markdown document :-)

Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents.
It is a simple and easy to use **plain text language** used to combine R code, results from your data analysis (including plots and tables), and written commentary into a single nicely formatted and reproducible document (like a report, publication, thesis chapter or a web pages).

Code lines are organized as code block, seeking to solve e specified task, and referred to as **"code chunk"**.
For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

All what you have to do during the computing labs is to read each explanatory paragraph before running each individual R code chunk, one by one, and to interpret the results.
Finally, to create a personal document (usually PDF) from rmarkdown, you need to **Knit** the document.
Knitting a document simply means taking all the text and code and creating a nicely formatted document.

## Data type in computational analysis

### Variables

Variables are used to store values in a computer program.
Values can be numbers (real and complex), words (string), matrices, and even tables.

The fundamental or atomic data in R Programming can be:

-   **integer**: number without decimals
-   **numeric**: number with decimals (float or double depending on the precision)
-   **character**: string, label
-   **factors**: a label with a limited number of categories
-   **logical**: true/false

<div class="figure" style="text-align: center">
<img src="images/Rvariablesdata.jpg" alt="Data Types in R \label{data_Type}" width="100%" height="80%" />
<p class="caption">(\#fig:img1)Data Types in R \label{data_Type}</p>
</div>

\newpage

### Data structure in R

R's base data structures can be organised by their dimensionality (1d, 2d, or nd) and whether they are homogeneous (all contents must be of the same type) or heterogeneous (the contents can be of different types).

This gives rise to the four data structures most often used in data analysis:

<div class="figure" style="text-align: center">
<img src="images/data_type.jpg" alt="Data structures in R \label{data_str}" width="50%" height="60%" />
<p class="caption">(\#fig:img2)Data structures in R \label{data_str}</p>
</div>

A **Vector** is a one-dimensional structure winch can contain object of one type only: numerical (integer and double), character, and logical.


```r
# Investigate vector's types:

v1 <- c(0.5, 0.7); v1; typeof(v1)
#> [1] 0.5 0.7
#> [1] "double"

v2 <-c(1:10); v2; typeof(v2)
#>  [1]  1  2  3  4  5  6  7  8  9 10
#> [1] "integer"

v3 <- c(TRUE, FALSE); v3; typeof(v3)
#> [1]  TRUE FALSE
#> [1] "logical"

v4 <- c("Swiss", "Itay", "France", "Germany"); v4; typeof(v4)
#> [1] "Swiss"   "Itay"    "France"  "Germany"
#> [1] "character"
```


```r
#Create a sequence from 0 to 5 with a step of 0.5:

v5 <- seq(1, 5, by=0.5); v5; typeof(v5)
#> [1] 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0
#> [1] "double"

length(v5)
#> [1] 9

summary(v5)
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
#>       1       2       3       3       4       5
```


```r
#Extract the third element of the vector
v5[3]
#> [1] 2

#Exclude the third element from the vector and save as new vector
v5[-3]
#> [1] 1.0 1.5 2.5 3.0 3.5 4.0 4.5 5.0
w5<-v5[-3]; w5
#> [1] 1.0 1.5 2.5 3.0 3.5 4.0 4.5 5.0
```

A **Matrix** is a two-dimensional structure winch can contain object of one type only.
The function \textcolor{red}{matrix()} can be used to construct matrices with specific dimensions.


```r

# Matrix of elements equal to "zero" and dimension 2x5 
m1<-matrix(0,2,5); m1  #(two rows by five columns)
#>      [,1] [,2] [,3] [,4] [,5]
#> [1,]    0    0    0    0    0
#> [2,]    0    0    0    0    0

# Matrix of integer elements (1 to 12, 3x4) 
m2<-matrix(1:12, 3,4); m2 
#>      [,1] [,2] [,3] [,4]
#> [1,]    1    4    7   10
#> [2,]    2    5    8   11
#> [3,]    3    6    9   12

# Extract the second row
m2[2, ]
#> [1]  2  5  8 11
# Extract the third column
m2[,3]
#> [1] 7 8 9
# Extract the the second element of the third column
m2[2,3]
#> [1] 8
```

### Data Frame

A **data frame** allows to collect data of different type.
All elements must have the same length.

A **list** is a more flexible structure since it can contain variables of different types and lengths.
Nevertheless, the preferred structure for statistical analyses and computation is the data frame.

It is a good practice to explore the data frame before performing further computation on the data.
This can be simply accomplished by using the commands \textcolor{red}{str} to explore the structure of the data and \textcolor{red}{summary} to display the summary statistics and quickly summarize the data.
For numerical vectors the command \textcolor{red}{hist()} can be used to plot the basic histogram of the given values.


```r
# Create the vectors with the variables

cities <- c("Berlin", "New York", "Paris", "Tokyo")
area <- c(892, 1214, 105, 2188)
population <- c(3.4, 8.1, 2.1, 12.9)
continent <- c("Europe", "Norh America", "Europe", "Asia")
```


```r
# Concatenate the vectors into a new data frame
df1 <- data.frame(cities, area, population, continent)
df1
#>     cities area population    continent
#> 1   Berlin  892        3.4       Europe
#> 2 New York 1214        8.1 Norh America
#> 3    Paris  105        2.1       Europe
#> 4    Tokyo 2188       12.9         Asia

#Add a column (e.g., language spoken) using the command "cbind"
df2 <- cbind (df1, "Language" = c ("German", "English", "Freanch", "Japanese"))
df2
#>     cities area population    continent Language
#> 1   Berlin  892        3.4       Europe   German
#> 2 New York 1214        8.1 Norh America  English
#> 3    Paris  105        2.1       Europe  Freanch
#> 4    Tokyo 2188       12.9         Asia Japanese
```


```r
#Explore the data frame
str(df2) # see the structure
#> 'data.frame':	4 obs. of  5 variables:
#>  $ cities    : chr  "Berlin" "New York" "Paris" "Tokyo"
#>  $ area      : num  892 1214 105 2188
#>  $ population: num  3.4 8.1 2.1 12.9
#>  $ continent : chr  "Europe" "Norh America" "Europe" "Asia"
#>  $ Language  : chr  "German" "English" "Freanch" "Japanese"
summary(df2) # compute basic statistics
#>     cities               area          population    
#>  Length:4           Min.   : 105.0   Min.   : 2.100  
#>  Class :character   1st Qu.: 695.2   1st Qu.: 3.075  
#>  Mode  :character   Median :1053.0   Median : 5.750  
#>                     Mean   :1099.8   Mean   : 6.625  
#>                     3rd Qu.:1457.5   3rd Qu.: 9.300  
#>                     Max.   :2188.0   Max.   :12.900  
#>   continent           Language        
#>  Length:4           Length:4          
#>  Class :character   Class :character  
#>  Mode  :character   Mode  :character  
#>                                       
#>                                       
#> 

# Use the symbol "$" to address a particular column
pop<-(df2$population)
pop
#> [1]  3.4  8.1  2.1 12.9
hist(pop) # plot the histogram
```

<img src="01-IntrotoR_files/figure-html/data-frame3-1.png" width="672" />
