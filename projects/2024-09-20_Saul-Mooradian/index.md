---
format: html
execute:
  warning: false
editor: source
author: Saul Mooradian
eval: false
---



<img src="Sauls-image.png" alt="chcRne logo" style="width: 18%; float: left;"/>

<hr style="height:40px; visibility:hidden;" />

# Saul's 2024 DS Capstone


::: {.cell}

:::


<br/>

## My project

My capstone project centered around streamlining common data analysis processes for Chico State’s [Center for Healthy Communities](https://chcchicostate.org/) - a non-profit organization promoting food security, nutrition education, and much more. These processes included re-coding variables, creating tables, and generating dynamic inline code, allowing for faster data processing and report building.

To do this, I developed an R package [(chcRne)](https://smoorad99.github.io/chcRnePackage/index.html) designed for the Research and Evaluation team at CHC. R packages provide a mechanism to get all your functions in a single, easily accessible location accompanied by documentation and examples. 

## A couple of examples

Currently there are 10 functions with documentation in the [(chcRne)](https://smoorad99.github.io/chcRnePackage/index.html) package. Here are the installation instructions along with an introduction to a couple chcRne functions.

::: {.panel-tabset}

### Install chcRne


::: {.cell}

```{.r .cell-code}
# Run the following two lines of code to install chcRne
install.packages("devtools") 
devtools::install_github("Smoorad99/chcRnePackage", dependencies = TRUE)
```
:::


### to_binary
`to_binary()` converts all "String"/"NA" or "Yes/"No" responses in the selected columns to binary (1/0) where the strings are replaced by 1s and the NAs are replaced by 0s.


::: {.cell}

```{.r .cell-code}
df_converted <- to_binary(data = bns2_pkg_data, 
                          these.cols = c(q14_1, q14_4), 
                          prefix = FALSE, yesno = TRUE)

# View the converted dataframe side-by-side to check if the function worked
old <- bns2_pkg_data |> dplyr::select(q14_1, q14_4)
new <- df_converted |> dplyr::select(q14_1, q14_4)
cbind(old, new) |> head(10)
```
:::


### count_and_percent
`count_and_percent()` returns a string that includes the total count and percent of respondents that selected a category specified in the function. If you include one category, the function will return the count and percent of respondents that selected that category relative to all non-NA responses.


::: {.cell}

:::



:::

## Lessons learned

Here are a couple of lessons/things I wish I had put more thought into during the early stages of this project.

-   Function names are PAINFUL to change after a version of your package has been released and is being used by others. I would recommend spending some extra time when naming your functions and asking others for their opinion before a first release. If your second opinion grimaces when seeing the name of your function, you should probably change it. For example, `nperc_tbl_MATA` is not a good name for a function 😬

-   If you are including functions that already exist within your organization or that you use. Think about how you can improve these functions sooner rather than later. If you are like me, you many not have had the developer knowledge to do this immediately, but this may help you limit the breaking changes you make down the road.


## Resources for package creation

It is easy to be intimidated by scary phrases like "package development", but R makes building packages relatively simple, with the option to add complexity. You can [learn about and create a basic package](https://www.youtube.com/watch?v=EpTkT6Rkgbs&t=2224s) in less than two hours. Also, Hadley Wickham and Jennifer Bryan have a wonderful book called [R Packages](https://r-pkgs.org/) that offers a more detailed introduction to package building - a book I relied heavily on during this project.



***Thank you Robin Donatello, the Chico State Statistics Department, and the CHC team! This project would not have been possible without your guidance/mentoring over the last few years.***

