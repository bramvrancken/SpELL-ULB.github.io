# Introduction to R

R is among the world’s most popular programming languages. The [TIOBE Programming Community index](https://www.tiobe.com/tiobe-index/) places it 18th overall at the time of writing (January 2025) and it is amongst the most popular languages, if not the most popular language, designed specifically for statistical analysis.

Should you want to install R and perhaps the RStudio integrated development environment (IDE) on your computer: the installation instructions for R can be found at <https://www.r-project.org/>, and those for RStudio at <https://posit.co/>. 

There are lots of high quality tutorials available online. Here, we only list a few features that are needed for a quick start. Inspiration for this introduction was taken from <https://www.geeksforgeeks.org/>. 

## Variables

In R, values of any type (integer, character, list, data frame, ...) can be assigned to variables. Variables are not declared with a data type. Rather they take the data type of the R-object assigned to them. This feature is shared with languages like Python. An example to clarify this: a variable that is assigned the value '1' will automatically be set to be of type double. Likewise, if a variable is assigned the value 'a', it will be set to type 'character'. You can check this by typing the following command in the R console (text preceded by a # is output of the previous command):

```R
> a = 1 
> typeof(a)
[1] "double"
> a = "a" 
> typeof(a)
[1] "character"
```

A major reason for assigning types to variables is to allow or not allow particular operations to be performed on variables. Think about summing characters  "a" and "b", which will not be possible, while summing is an allowed operation on e.g. integers. 

There are some syntax rules for the names of variables. A valid variable name consists of a combination of letters, numbers, dot ('.'), and underscore ('_') characters. Apart from the dot and underscore, no other special character is allowed. Variables can start with a letter or a dot. Example: '.var' or 'var' is valid. The variable should not start with a number or an underscore. Example: '2var' or '_var' is  not valid. When a variable starts with a dot the next thing after the dot cannot be a number. Example: '.3var' is invalid.

Content can be assigned to variables in three ways:
```R
### 1.	simple assignment ###
> var1 = 1 #simple assignment
> print(var1)
[1] 1

### 2.	leftward assignment ###
> var2 <- 2 #leftward assignment
> print(var2)
[1] 2

### 3.	rightward assignment ###
> 3 -> var3 #rightward assignment
> print(var3)
[1] 3
```

In the above example, the print() function was used to print the content of a variable to screen. An alternative way to check the content of a variable is to execute it, for example by typing the variable name in the console and pressing enter:

```R
> print(var1)
[1] 1
> var1
[1] 1
```

## Comments in R

Comments are a way to improve your code’s readability. It is only meant for the user so the interpreter ignores them. Comments can be written by using '#' at the beginning of the statement. 

```R
# this line is a comment and is not interpreted as code
> print("this is fun")
[1] "this is fun"
```

## Commands

R is case sensitive, so 'A' and 'a' are different symbols and would refer to different variables. Commands are separated either by a semi-colon (';'), or by a newline. If a command is not complete at the end of a line, R will give a different prompt, by default the plus-symbol, on second and subsequent lines and continue to read input until the command is syntactically complete:

```R
> print("this is fun"
+ 
+ 
+ 
+ )
[1] "this is fun"
```

## Examples of manipulations 

R operates on named data structures. The simplest such structure is the numeric vector, which is a single entity consisting of an ordered collection of numbers. To set up a vector named x, say, consisting of five numbers, namely 1 to 5, use the command

```R
> x <- c(1, 2, 3, 4, 5)
```

This is an assignment statement using the function c(). Note: 'c' is shorthand for 'concatenate'. Elements of a vector can be selected using the [] operator and passing the index of the value. Mind that indexing in R starts with 1 rather than 0. Several variations with the indexing are possible:

```R
> x[4]
[1] 4

# pass a sequence of indices to retrieve multiple values
> x[c(1,4)]
[1] 1 4

# use the '-' sign to ignore items
> x[-1] # ignores the first item
[1] 2 3 4 5

> x[-(1:3)] #ignores the first three items. '1:3' stands for '1 to 3'
[1] 4 5
```

If the vector has named elements, items can be selected based on the names. Elements can be named with the names() command.
 
```R 
> names(x) = c("one", "two", "three", "four", "five")
> x
 one   two three  four  five 
  1     2     3     4     5 

> x[c("one", "five")]
one five 
 1    5
```

Strings are a set of characters. In R, strings are declared by enclosing characters by single or double quotes. An empty string is initiated by not including anything in between the quotes: '' or "". Strings are always stored as double-quoted values in R.    
Syntax rules: a double quoted string can contain single quotes within it but a single quoted strings can’t contain single quotes. Similarly, double quotes can't be surrounded by double quotes.

```R
> s <- 'string'
> s
[1] "string"
> s <- "string"
> s
[1] "string"
```

Strings can represent the path to the directory where e.g. the files needed for an exercise are stored, and can be passed to the setwd() command, which is equivalent to the `cd` command in `bash`.

```R
> my.dir <- "astringthatmostlikelyhasatleastonetypo"
> setwd(dir = my.dir)
```

**TIP**: to avoid making mistakes when typing names of files, paths or commands, make use of the autocomplete functionality in RStudio or whatever IDE you use. When you start typing a name and press tab, a list of options between which you can choose is shown.

The [] operator can also be used to select elements of lists. A list is an object consisting of an ordered collection of objects known as its components. To illustrate what a list is, let's look at the strsplit() command, which splits a string based on matches to another string, and returns these elements as a list. For example, to split a string on each occurence of a space: 

```R
> x <- "a vector I want to split"
> strsplit(x = x, split = " ")
[[1]]
 [1] "a"     "vector"  "I"     "want"  "to"    "split"
```
	
Components of a list can be selected by their index within [[]]. In this example, the component is a vector, meaning that its elements can be selected by their indexes within []. 

```R
> a.list <- strsplit(x = x, split = " ")
> a.list
[[1]]
 [1] "a"      "vector" "I"      "want"   "to"     "split" 
> a.list[[1]] #select first component of list
[1] "a"      "vector" "I"      "want"   "to"     "split" 
> a.list[[1]][3] #select 3rd element of first component of the list
[1] "I"
```

Strings can also be glued together, e.g. with the paste0() command. 

```R
> paste0(x[[1]][2], ".part.2")
[1] "vector.part.2"
```

Throughout scripts, string manipulation with strsplit() and paste0() can be used to adhere to a consistent file naming protocol when using R. For example, an alignment file name  (e.g. a file with sequence data in FASTA format) can be passed to a variable, which can easily be used to create a meaningful names for the file in which to store the result after performing some operations on the sequences such as aligning the sequences:

```R
> fasta.in <- "a-set-of-virus-sequences.fasta"
> fileStem <- strsplit(x = fasta.in, split = ".fasta")[[1]][1]
> fasta.aln <- paste0(fileStem, ".aln.fasta")
> fasta.aln #check:
[1] "a-set-of-virus-sequences.aln.fasta"
```

As variables can be re-used in subsequent commands, this strategy has the advantage that only the input file name needs to be adapted to re-use the code for another analysis/exercise.

## Packages

Packages are a set of R functions, compiled code, and sample data. By default, R installs a core set of packages during installation and on startup only those are available. Other packages with useful functions that are not part of the core set need to be installed separately. They also need to be activated or loaded to be used.

Packages can be downloaded from repositories. The most popular repositories for R packages include: 

- [The Comprehensive R Archive Network](https://cran.r-project.org/) (CRAN). This is a repository that's maintained by the global R community. For a package to be published in CRAN, the Package needs to pass several tests to ensure that the package is following CRAN policies.

- [Bioconductor](https://www.bioconductor.org/) is a topic-specific repository, intended for open source software for bioinformatics. Similar to [CRAN](https://cran.r-project.org/), it has its own submission and review processes in order to maintain its quality standards. A key feature of Bioconductor is the well-organized package management system. More details about the advantages of using Bioconductor can be found at their [website](https://www.bioconductor.org/).

As Bioconductor is easy-to-use and handles package-version issues well, it is advised to read the documentation on their website. As this may convince you of its advantages over the default way R handles packages, we provide some more info on how to use it below. 

Bioconductor can be installed using standard R installation procedures, which is required only once per R installation:

```R
# install BiocManager if not already done so:
> if (!require("BiocManager", quietly = TRUE)){
+  install.packages("BiocManager")    
+ }
```

To take advantage of the latest package-features and to access packages that have been added to Bioconductor since the previous release, users of older R and Bioconductor versions must update their installation. Alternatively, if you have good reasons not to update to the latest version of R and Bioconductor, one can try to install a specific version of BiocManager. For this, first find out which R version is installed:

```R
> version

platform       x86_64-apple-darwin17.0     
arch           x86_64                      
os             darwin17.0                  
system         x86_64, darwin17.0          
status                                     
major          4                           
minor          2.0                         
year           2022                        
month          04                          
day            22                          
svn rev        82229                       
language       R                           
version.string R version 4.2.0 (2022-04-22)
nickname       Vigorous Calisthenics      
```

In this example, R version 4.2.0 is installed. To find out which version of Bioconductor is compatible, browse to <https://bioconductor.org/about/release-announcements/> and look up the version of Bioconductor that correspons to the installed R version. A Bioconductor version that corresponds to e.g. R version 4.2 can be installed with the following command:

```R
> BiocManager::install(version = "3.16")
```

The installed version of Bioconductor can be checked with

```R
> BiocManager::version()
[1] ‘3.16’
```

Bioconductor packages work best when they are all from the same release. Use valid() to identify packages that are out-of-date or from unexpected versions. This command returns an object with lots of info, including a list of packages that are out of date as can be seen in the example below: 

```R
> v <- BiocManager::valid()
'getOption("repos")' replaces Bioconductor standard repositories, see '?repositories' for details

replacement repositories:
   CRAN: https://cran.rstudio.com/

Warning message:
8 packages out-of-date; 0 packages too new 
...

v$out_of_date
         Package     LibPath                                                          Installed Built   ReposVer
aplot     "aplot"     "/Library/Frameworks/R.framework/Versions/4.2/Resources/library" "0.1.8"   "4.2.0" "0.1.9" 
...
```

As it in general is a good idea to be able to make use of the latest functionalities, the default behavior of `BiocManager::install()` it to ask to update out-of-date packages. You are of course free to not do so as sometimes these version differences are not relevant. It's up to you to make an informed decision on this. Note that this behaviour can be changed by setting the update argument to `FALSE`, in which case no attempt will be made to update old packages.

The above already gave it away: the command to install and manage packages from the Bioconductor project is `BiocManager::install()`. For example, the following command installs the ape package: 

```R
> BiocManager::install(pkgs = "ape")
```

As soon as a package is installed, be it from Bioconductor or not, its functionalities can be accessed with the following syntax: `packagename::functionname()`. Alternatively, a package can be activated for the current R session after which its functions can be directly accessed:

```R
# Without activating the package to the current R session:
> ape::rtree(arguments)

# activate package: library(name of package):
> library(ape)
# now these package's functions can be directly used
> rtree(arguments)
```

Mind that when packages have functions with the same name, the function that is used by default is that of the last loaded package. This information is printed to screen the first time such a conflict arises. This is, for example, the case when activating the Rsamtools package:

```R
> library(Rsamtools)
Loading required package: GenomeInfoDb
Loading required package: BiocGenerics

Attaching package: ‘BiocGenerics’

The following objects are masked from ‘package:stats’:

    IQR, mad, sd, var, xtabs 
...
```

## The help system

R has an inbuilt help facility similar to the `man` facility of UNIX. To get more information on any specific named function, for example rtree() of the ape-package, the command is

```R
> help(rtree)
# or equivalently:
> ?rtree
```
 
If one does not know the name of the function that is needed, a search with keywords is possible with the function help.search(). This looks for a specified topic, given as a character string, in the help pages of all installed packages. For instance:

```R
> help.search("tree")
```

will display a list of the functions where help pages mention "tree". 
