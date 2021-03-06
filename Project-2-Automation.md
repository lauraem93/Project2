Automating Project 2
================
Laura Mathews
10/16/2020

# Purpose of this repository:

The purpose of this repository is to use two different tree models to
predict bike useage count for each day of the week. Data on bike sharing
was analyzed to create the models. The reports for each week were then
automated.


  - The analysis for [Monday is available here](https://lauraem93.github.io/Project2/MondayAnalysis).
  - The analysis for [Tuesday is available here](https://lauraem93.github.io/Project2/TuesdayAnalysis).
  - The analysis for [Wednesday is available
    here](https://lauraem93.github.io/Project2/WednesdayAnalysis).
  - The analysis for [Thursday is available here](https://lauraem93.github.io/Project2/ThursdayAnalysis).
  - The analysis for [Friday is available here](https://lauraem93.github.io/Project2/FridayAnalysis).
  - The analysis for [Saturday is available here](https://lauraem93.github.io/Project2/SaturdayAnalysis).
  - The analysis for [Sunday is available here](https://lauraem93.github.io/Project2/SundayAnalysis).

# Packages Needed

The packages needed for the analysis and automation of reports are  
\+ tidyverse + rmarkdown + knitr + tidyr + caret + ggplot2 + corrplot

``` r
#Packages needed for the automation and analysis

library(tidyverse)
library(rmarkdown)
library(knitr)
library(tidyr)
library(caret)
library(ggplot2)
library(corrplot)
```

# Automate creation of reports

Create output file names. Use the file names with the render function to
automate creation of reports for each day.

``` r
#Create output file names

daynames <- c("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday")
daynum <- 0:6

output_file <- paste0(daynames, "Analysis.md")

#Put parameters and day names in a list, create a data frame with the parameters, day names, and output file names

params1 <- lapply(daynames, FUN = function(x){list(day = x)})
params2 <- lapply(daynum, FUN = function(x){list(day = x)})

reports <- tibble(output_file, params1, params2)

#Use the render function to create reports

apply(reports, MARGIN = 1,
      FUN = function(x){
        render(input = "Project 2.Rmd", output_file = x[[1]], params = x[[3]])
      })
```
