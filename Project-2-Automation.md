Automating Project 2
================
Laura Mathews
10/14/2020

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

<!-- end list -->

``` r
#Packages Needed

library(tidyverse)
```

    ## Warning: package 'tidyverse' was built under R version 3.6.3

    ## -- Attaching packages ------------------------------------------- tidyverse 1.3.0 --

    ## v ggplot2 3.3.2     v purrr   0.3.3
    ## v tibble  3.0.0     v dplyr   0.8.5
    ## v tidyr   1.0.2     v stringr 1.4.0
    ## v readr   1.3.1     v forcats 0.5.0

    ## Warning: package 'ggplot2' was built under R version 3.6.3

    ## Warning: package 'tibble' was built under R version 3.6.3

    ## Warning: package 'tidyr' was built under R version 3.6.3

    ## Warning: package 'readr' was built under R version 3.6.3

    ## Warning: package 'purrr' was built under R version 3.6.3

    ## Warning: package 'dplyr' was built under R version 3.6.3

    ## Warning: package 'forcats' was built under R version 3.6.3

    ## -- Conflicts ---------------------------------------------- tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(rmarkdown)
library(knitr)
```

    ## Warning: package 'knitr' was built under R version 3.6.3

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

    ## 
    ## 
    ## processing file: Project-2.Rmd

    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 1
    ##  $ include: logi FALSE
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

    ## Warning: package 'caret' was built under R version 3.6.3

    ## Warning: package 'corrplot' was built under R version 3.6.3

    ## Parsed with column specification:
    ## cols(
    ##   instant = col_double(),
    ##   dteday = col_date(format = ""),
    ##   season = col_double(),
    ##   yr = col_double(),
    ##   mnth = col_double(),
    ##   hr = col_double(),
    ##   holiday = col_double(),
    ##   weekday = col_double(),
    ##   workingday = col_double(),
    ##   weathersit = col_double(),
    ##   temp = col_double(),
    ##   atemp = col_double(),
    ##   hum = col_double(),
    ##   windspeed = col_double(),
    ##   casual = col_double(),
    ##   registered = col_double(),
    ##   cnt = col_double()
    ## )

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
    ## label: unnamed-chunk-8 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 2
    ##  $ verbose: logi FALSE
    ##  $ eval   : logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE

    ## output file: Project-2.knit.md

    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output SundayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS SundayAnalysis.md --to html4 --from gfm --output SundayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW

    ## 
    ## Preview created: C:\Users\laura\AppData\Local\Temp\RtmpKAhwNZ\preview-4fe426c22dad.html

    ## 
    ## Output created: SundayAnalysis.md

    ## 
    ## 
    ## processing file: Project-2.Rmd

    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 1
    ##  $ include: logi FALSE
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

    ## Parsed with column specification:
    ## cols(
    ##   instant = col_double(),
    ##   dteday = col_date(format = ""),
    ##   season = col_double(),
    ##   yr = col_double(),
    ##   mnth = col_double(),
    ##   hr = col_double(),
    ##   holiday = col_double(),
    ##   weekday = col_double(),
    ##   workingday = col_double(),
    ##   weathersit = col_double(),
    ##   temp = col_double(),
    ##   atemp = col_double(),
    ##   hum = col_double(),
    ##   windspeed = col_double(),
    ##   casual = col_double(),
    ##   registered = col_double(),
    ##   cnt = col_double()
    ## )

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
    ## label: unnamed-chunk-8 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 2
    ##  $ verbose: logi FALSE
    ##  $ eval   : logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE

    ## output file: Project-2.knit.md

    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output MondayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS MondayAnalysis.md --to html4 --from gfm --output MondayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW

    ## 
    ## Preview created: C:\Users\laura\AppData\Local\Temp\RtmpKAhwNZ\preview-4fe45b1a444b.html

    ## 
    ## Output created: MondayAnalysis.md

    ## 
    ## 
    ## processing file: Project-2.Rmd

    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 1
    ##  $ include: logi FALSE
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

    ## Parsed with column specification:
    ## cols(
    ##   instant = col_double(),
    ##   dteday = col_date(format = ""),
    ##   season = col_double(),
    ##   yr = col_double(),
    ##   mnth = col_double(),
    ##   hr = col_double(),
    ##   holiday = col_double(),
    ##   weekday = col_double(),
    ##   workingday = col_double(),
    ##   weathersit = col_double(),
    ##   temp = col_double(),
    ##   atemp = col_double(),
    ##   hum = col_double(),
    ##   windspeed = col_double(),
    ##   casual = col_double(),
    ##   registered = col_double(),
    ##   cnt = col_double()
    ## )

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
    ## label: unnamed-chunk-8 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 2
    ##  $ verbose: logi FALSE
    ##  $ eval   : logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE

    ## output file: Project-2.knit.md

    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output TuesdayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS TuesdayAnalysis.md --to html4 --from gfm --output TuesdayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW

    ## 
    ## Preview created: C:\Users\laura\AppData\Local\Temp\RtmpKAhwNZ\preview-4fe46eb42c9.html

    ## 
    ## Output created: TuesdayAnalysis.md

    ## 
    ## 
    ## processing file: Project-2.Rmd

    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 1
    ##  $ include: logi FALSE
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

    ## Parsed with column specification:
    ## cols(
    ##   instant = col_double(),
    ##   dteday = col_date(format = ""),
    ##   season = col_double(),
    ##   yr = col_double(),
    ##   mnth = col_double(),
    ##   hr = col_double(),
    ##   holiday = col_double(),
    ##   weekday = col_double(),
    ##   workingday = col_double(),
    ##   weathersit = col_double(),
    ##   temp = col_double(),
    ##   atemp = col_double(),
    ##   hum = col_double(),
    ##   windspeed = col_double(),
    ##   casual = col_double(),
    ##   registered = col_double(),
    ##   cnt = col_double()
    ## )

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
    ## label: unnamed-chunk-8 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 2
    ##  $ verbose: logi FALSE
    ##  $ eval   : logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE

    ## output file: Project-2.knit.md

    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output WednesdayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS WednesdayAnalysis.md --to html4 --from gfm --output WednesdayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW

    ## 
    ## Preview created: C:\Users\laura\AppData\Local\Temp\RtmpKAhwNZ\preview-4fe45ef561db.html

    ## 
    ## Output created: WednesdayAnalysis.md

    ## 
    ## 
    ## processing file: Project-2.Rmd

    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 1
    ##  $ include: logi FALSE
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

    ## Parsed with column specification:
    ## cols(
    ##   instant = col_double(),
    ##   dteday = col_date(format = ""),
    ##   season = col_double(),
    ##   yr = col_double(),
    ##   mnth = col_double(),
    ##   hr = col_double(),
    ##   holiday = col_double(),
    ##   weekday = col_double(),
    ##   workingday = col_double(),
    ##   weathersit = col_double(),
    ##   temp = col_double(),
    ##   atemp = col_double(),
    ##   hum = col_double(),
    ##   windspeed = col_double(),
    ##   casual = col_double(),
    ##   registered = col_double(),
    ##   cnt = col_double()
    ## )

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
    ## label: unnamed-chunk-8 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 2
    ##  $ verbose: logi FALSE
    ##  $ eval   : logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE

    ## output file: Project-2.knit.md

    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output ThursdayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS ThursdayAnalysis.md --to html4 --from gfm --output ThursdayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW

    ## 
    ## Preview created: C:\Users\laura\AppData\Local\Temp\RtmpKAhwNZ\preview-4fe43a15499.html

    ## 
    ## Output created: ThursdayAnalysis.md

    ## 
    ## 
    ## processing file: Project-2.Rmd

    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 1
    ##  $ include: logi FALSE
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

    ## Parsed with column specification:
    ## cols(
    ##   instant = col_double(),
    ##   dteday = col_date(format = ""),
    ##   season = col_double(),
    ##   yr = col_double(),
    ##   mnth = col_double(),
    ##   hr = col_double(),
    ##   holiday = col_double(),
    ##   weekday = col_double(),
    ##   workingday = col_double(),
    ##   weathersit = col_double(),
    ##   temp = col_double(),
    ##   atemp = col_double(),
    ##   hum = col_double(),
    ##   windspeed = col_double(),
    ##   casual = col_double(),
    ##   registered = col_double(),
    ##   cnt = col_double()
    ## )

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
    ## label: unnamed-chunk-8 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 2
    ##  $ verbose: logi FALSE
    ##  $ eval   : logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE

    ## output file: Project-2.knit.md

    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output FridayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS FridayAnalysis.md --to html4 --from gfm --output FridayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW

    ## 
    ## Preview created: C:\Users\laura\AppData\Local\Temp\RtmpKAhwNZ\preview-4fe438a23000.html

    ## 
    ## Output created: FridayAnalysis.md

    ## 
    ## 
    ## processing file: Project-2.Rmd

    ##   |                                                                              |                                                                      |   0%  |                                                                              |...                                                                   |   5%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......                                                                |   9%
    ## label: unnamed-chunk-1 (with options) 
    ## List of 1
    ##  $ include: logi FALSE
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

    ## Parsed with column specification:
    ## cols(
    ##   instant = col_double(),
    ##   dteday = col_date(format = ""),
    ##   season = col_double(),
    ##   yr = col_double(),
    ##   mnth = col_double(),
    ##   hr = col_double(),
    ##   holiday = col_double(),
    ##   weekday = col_double(),
    ##   workingday = col_double(),
    ##   weathersit = col_double(),
    ##   temp = col_double(),
    ##   atemp = col_double(),
    ##   hum = col_double(),
    ##   windspeed = col_double(),
    ##   casual = col_double(),
    ##   registered = col_double(),
    ##   cnt = col_double()
    ## )

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
    ## label: unnamed-chunk-8 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |......................................................                |  77%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |.........................................................             |  82%
    ## label: unnamed-chunk-9 (with options) 
    ## List of 2
    ##  $ verbose: logi FALSE
    ##  $ eval   : logi FALSE
    ## 
    ##   |                                                                              |............................................................          |  86%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |................................................................      |  91%
    ## label: unnamed-chunk-10 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE
    ## 
    ##   |                                                                              |...................................................................   |  95%
    ##   ordinary text without R code
    ## 
    ##   |                                                                              |......................................................................| 100%
    ## label: unnamed-chunk-11 (with options) 
    ## List of 1
    ##  $ eval: logi FALSE

    ## output file: Project-2.knit.md

    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS Project-2.utf8.md --to gfm --from markdown+autolink_bare_uris+tex_math_single_backslash --output SaturdayAnalysis.md --standalone --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\default.md" 
    ## "C:/Program Files/RStudio/bin/pandoc/pandoc" +RTS -K512m -RTS SaturdayAnalysis.md --to html4 --from gfm --output SaturdayAnalysis.html --standalone --self-contained --highlight-style pygments --template "C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\preview.html" --variable "github-markdown-css:C:\Users\laura\OneDrive\Documents\R\win-library\3.6\rmarkdown\rmarkdown\templates\github_document\resources\github.css" --email-obfuscation none --metadata pagetitle=PREVIEW

    ## 
    ## Preview created: C:\Users\laura\AppData\Local\Temp\RtmpKAhwNZ\preview-4fe426fb526e.html

    ## 
    ## Output created: SaturdayAnalysis.md

    ## [1] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/SundayAnalysis.md"   
    ## [2] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/MondayAnalysis.md"   
    ## [3] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/TuesdayAnalysis.md"  
    ## [4] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/WednesdayAnalysis.md"
    ## [5] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/ThursdayAnalysis.md" 
    ## [6] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/FridayAnalysis.md"   
    ## [7] "C:/Users/laura/OneDrive/Desktop/Github Repositories/Project2/SaturdayAnalysis.md"
