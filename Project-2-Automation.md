Automating Project 2
================
Laura Mathews
10/16/2020

# Purpose of this repository:

The purpose of this repository is to use two different tree models to
predict bike useage count for each day of the week. Data on bike sharing
was analyzed to create the models. The reports for each week were then
automated.

  - The analysis for [Monday is available here](MondayAnalysis.md).
  - The analysis for [Tuesday is available here](TuesdayAnalysis.md).
  - The analysis for [Wednesday is available
    here](WednesdayAnalysis.md).
  - The analysis for [Thursday is available here](ThursdayAnalysis.md).
  - The analysis for [Friday is available here](FridayAnalysis.md).
  - The analysis for [Saturday is available here](SaturdayAnalysis.md).
  - The analysis for [Sunday is available here](SundayAnalysis.md).

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

    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 3
    ##  $ include: logi FALSE
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |..........                                                            |  14%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............                                                         |  18%
    ## label: unnamed-chunk-2 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |................                                                      |  23%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................                                                   |  27%
    ## label: unnamed-chunk-3 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |......................                                                |  32%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................                                             |  36%
    ## label: unnamed-chunk-4
    ##   |                                                                              |.............................                                         |  41%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................                                      |  45%
    ## label: unnamed-chunk-5

    ##   |                                                                              |...................................                                   |  50%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................                                |  55%
    ## label: unnamed-chunk-6

    ##   |                                                                              |.........................................                             |  59%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............................................                         |  64%
    ## label: unnamed-chunk-7
    ##   |                                                                              |................................................                      |  68%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................................................                   |  73%
    ## label: unnamed-chunk-8

    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 1
    ##  $ warning: logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11
    ## 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output SundayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS SundayAnalysis.md --to html4 --from gfm --output SundayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW 
    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 3
    ##  $ include: logi FALSE
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |..........                                                            |  14%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............                                                         |  18%
    ## label: unnamed-chunk-2 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |................                                                      |  23%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................                                                   |  27%
    ## label: unnamed-chunk-3 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |......................                                                |  32%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................                                             |  36%
    ## label: unnamed-chunk-4
    ##   |                                                                              |.............................                                         |  41%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................                                      |  45%
    ## label: unnamed-chunk-5

    ##   |                                                                              |...................................                                   |  50%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................                                |  55%
    ## label: unnamed-chunk-6

    ##   |                                                                              |.........................................                             |  59%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............................................                         |  64%
    ## label: unnamed-chunk-7
    ##   |                                                                              |................................................                      |  68%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................................................                   |  73%
    ## label: unnamed-chunk-8

    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 1
    ##  $ warning: logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11
    ## 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output MondayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS MondayAnalysis.md --to html4 --from gfm --output MondayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW 
    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 3
    ##  $ include: logi FALSE
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |..........                                                            |  14%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............                                                         |  18%
    ## label: unnamed-chunk-2 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |................                                                      |  23%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................                                                   |  27%
    ## label: unnamed-chunk-3 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |......................                                                |  32%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................                                             |  36%
    ## label: unnamed-chunk-4
    ##   |                                                                              |.............................                                         |  41%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................                                      |  45%
    ## label: unnamed-chunk-5

    ##   |                                                                              |...................................                                   |  50%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................                                |  55%
    ## label: unnamed-chunk-6

    ##   |                                                                              |.........................................                             |  59%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............................................                         |  64%
    ## label: unnamed-chunk-7
    ##   |                                                                              |................................................                      |  68%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................................................                   |  73%
    ## label: unnamed-chunk-8

    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 1
    ##  $ warning: logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11
    ## 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output TuesdayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS TuesdayAnalysis.md --to html4 --from gfm --output TuesdayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW 
    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 3
    ##  $ include: logi FALSE
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |..........                                                            |  14%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............                                                         |  18%
    ## label: unnamed-chunk-2 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |................                                                      |  23%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................                                                   |  27%
    ## label: unnamed-chunk-3 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |......................                                                |  32%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................                                             |  36%
    ## label: unnamed-chunk-4
    ##   |                                                                              |.............................                                         |  41%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................                                      |  45%
    ## label: unnamed-chunk-5

    ##   |                                                                              |...................................                                   |  50%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................                                |  55%
    ## label: unnamed-chunk-6

    ##   |                                                                              |.........................................                             |  59%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............................................                         |  64%
    ## label: unnamed-chunk-7
    ##   |                                                                              |................................................                      |  68%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................................................                   |  73%
    ## label: unnamed-chunk-8

    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 1
    ##  $ warning: logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11
    ## 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output WednesdayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS WednesdayAnalysis.md --to html4 --from gfm --output WednesdayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW 
    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 3
    ##  $ include: logi FALSE
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |..........                                                            |  14%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............                                                         |  18%
    ## label: unnamed-chunk-2 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |................                                                      |  23%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................                                                   |  27%
    ## label: unnamed-chunk-3 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |......................                                                |  32%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................                                             |  36%
    ## label: unnamed-chunk-4
    ##   |                                                                              |.............................                                         |  41%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................                                      |  45%
    ## label: unnamed-chunk-5

    ##   |                                                                              |...................................                                   |  50%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................                                |  55%
    ## label: unnamed-chunk-6

    ##   |                                                                              |.........................................                             |  59%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............................................                         |  64%
    ## label: unnamed-chunk-7
    ##   |                                                                              |................................................                      |  68%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................................................                   |  73%
    ## label: unnamed-chunk-8

    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 1
    ##  $ warning: logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11
    ## 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output ThursdayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS ThursdayAnalysis.md --to html4 --from gfm --output ThursdayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW 
    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 3
    ##  $ include: logi FALSE
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |..........                                                            |  14%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............                                                         |  18%
    ## label: unnamed-chunk-2 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |................                                                      |  23%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................                                                   |  27%
    ## label: unnamed-chunk-3 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |......................                                                |  32%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................                                             |  36%
    ## label: unnamed-chunk-4
    ##   |                                                                              |.............................                                         |  41%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................                                      |  45%
    ## label: unnamed-chunk-5

    ##   |                                                                              |...................................                                   |  50%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................                                |  55%
    ## label: unnamed-chunk-6

    ##   |                                                                              |.........................................                             |  59%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............................................                         |  64%
    ## label: unnamed-chunk-7
    ##   |                                                                              |................................................                      |  68%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................................................                   |  73%
    ## label: unnamed-chunk-8

    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 1
    ##  $ warning: logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11
    ## 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output FridayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS FridayAnalysis.md --to html4 --from gfm --output FridayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW 
    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 3
    ##  $ include: logi FALSE
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |..........                                                            |  14%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............                                                         |  18%
    ## label: unnamed-chunk-2 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |................                                                      |  23%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................                                                   |  27%
    ## label: unnamed-chunk-3 (with options) 
    ## List of 2
    ##  $ warning: logi FALSE
    ##  $ message: logi FALSE
    ## 
    ##   |                                                                              |......................                                                |  32%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................                                             |  36%
    ## label: unnamed-chunk-4
    ##   |                                                                              |.............................                                         |  41%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................                                      |  45%
    ## label: unnamed-chunk-5

    ##   |                                                                              |...................................                                   |  50%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................                                |  55%
    ## label: unnamed-chunk-6

    ##   |                                                                              |.........................................                             |  59%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.............................................                         |  64%
    ## label: unnamed-chunk-7
    ##   |                                                                              |................................................                      |  68%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |...................................................                   |  73%
    ## label: unnamed-chunk-8

    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 1
    ##  $ warning: logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11
    ## 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output SaturdayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS SaturdayAnalysis.md --to html4 --from gfm --output SaturdayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW

    ## [1] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/SundayAnalysis.md"   
    ## [2] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/MondayAnalysis.md"   
    ## [3] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/TuesdayAnalysis.md"  
    ## [4] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/WednesdayAnalysis.md"
    ## [5] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/ThursdayAnalysis.md" 
    ## [6] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/FridayAnalysis.md"   
    ## [7] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/SaturdayAnalysis.md"
