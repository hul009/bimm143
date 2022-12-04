class19
================

``` r
library("datapasta")
```

    Warning: package 'datapasta' was built under R version 4.2.2

``` r
library("ggplot2")
```

``` r
cdc <- tibble::tribble(
  ~Year, ~No..Reported.Pertussis.Cases,
  1922L,                        107473,
  1923L,                        164191,
  1924L,                        165418,
  1925L,                        152003,
  1926L,                        202210,
  1927L,                        181411,
  1928L,                        161799,
  1929L,                        197371,
  1930L,                        166914,
  1931L,                        172559,
  1932L,                        215343,
  1933L,                        179135,
  1934L,                        265269,
  1935L,                        180518,
  1936L,                        147237,
  1937L,                        214652,
  1938L,                        227319,
  1939L,                        103188,
  1940L,                        183866,
  1941L,                        222202,
  1942L,                        191383,
  1943L,                        191890,
  1944L,                        109873,
  1945L,                        133792,
  1946L,                        109860,
  1947L,                        156517,
  1948L,                         74715,
  1949L,                         69479,
  1950L,                        120718,
  1951L,                         68687,
  1952L,                         45030,
  1953L,                         37129,
  1954L,                         60886,
  1955L,                         62786,
  1956L,                         31732,
  1957L,                         28295,
  1958L,                         32148,
  1959L,                         40005,
  1960L,                         14809,
  1961L,                         11468,
  1962L,                         17749,
  1963L,                         17135,
  1964L,                         13005,
  1965L,                          6799,
  1966L,                          7717,
  1967L,                          9718,
  1968L,                          4810,
  1969L,                          3285,
  1970L,                          4249,
  1971L,                          3036,
  1972L,                          3287,
  1973L,                          1759,
  1974L,                          2402,
  1975L,                          1738,
  1976L,                          1010,
  1977L,                          2177,
  1978L,                          2063,
  1979L,                          1623,
  1980L,                          1730,
  1981L,                          1248,
  1982L,                          1895,
  1983L,                          2463,
  1984L,                          2276,
  1985L,                          3589,
  1986L,                          4195,
  1987L,                          2823,
  1988L,                          3450,
  1989L,                          4157,
  1990L,                          4570,
  1991L,                          2719,
  1992L,                          4083,
  1993L,                          6586,
  1994L,                          4617,
  1995L,                          5137,
  1996L,                          7796,
  1997L,                          6564,
  1998L,                          7405,
  1999L,                          7298,
  2000L,                          7867,
  2001L,                          7580,
  2002L,                          9771,
  2003L,                         11647,
  2004L,                         25827,
  2005L,                         25616,
  2006L,                         15632,
  2007L,                         10454,
  2008L,                         13278,
  2009L,                         16858,
  2010L,                         27550,
  2011L,                         18719,
  2012L,                         48277,
  2013L,                         28639,
  2014L,                         32971,
  2015L,                         20762,
  2016L,                         17972,
  2017L,                         18975,
  2018L,                         15609,
  2019L,                         18617
  )
```

> Q1. With the help of the R “addin” package datapasta assign the CDC
> pertussis case number data to a data frame called cdc and use ggplot
> to make a plot of cases numbers over time.

``` r
ggplot(cdc) +
  aes(x=Year, y=No..Reported.Pertussis.Cases) +
  geom_point() +
  geom_line() +
  labs("Pertussis Cases by year")
```

![](class19_files/figure-gfm/unnamed-chunk-3-1.png)

> Q2. Using the ggplot geom_vline() function add lines to your previous
> plot for the 1946 introduction of the wP vaccine and the 1996 switch
> to aP vaccine (see example in the hint below). What do you notice?

``` r
ggplot(cdc) +
  aes(x=Year, y=No..Reported.Pertussis.Cases) +
  geom_point() +
  geom_line() +
  geom_vline(xintercept = 1946)+
  geom_vline(xintercept = 1996)
```

![](class19_files/figure-gfm/unnamed-chunk-4-1.png)

``` r
  labs("Pertussis Cases by year")
```

    [[1]]
    [1] "Pertussis Cases by year"

    attr(,"class")
    [1] "labels"

> Q3. Describe what happened after the introduction of the aP vaccine?
> Do you have a possible explanation for the observed trend?

The pertussis cases are increasing again. Vaccine immunity might be a
possible explanation for the observed trend.

``` r
library(jsonlite)
```

    Warning: package 'jsonlite' was built under R version 4.2.2

``` r
subject <- read_json("https://www.cmi-pb.org/api/subject", simplifyVector = TRUE)
```

``` r
head(subject, 3)
```

      subject_id infancy_vac biological_sex              ethnicity  race
    1          1          wP         Female Not Hispanic or Latino White
    2          2          wP         Female Not Hispanic or Latino White
    3          3          wP         Female                Unknown White
      year_of_birth date_of_boost      dataset
    1    1986-01-01    2016-09-12 2020_dataset
    2    1968-01-01    2019-01-28 2020_dataset
    3    1983-01-01    2016-10-10 2020_dataset

> Q4. How may aP and wP infancy vaccinated subjects are in the dataset?

``` r
table(subject$infancy_vac)
```


    aP wP 
    47 49 

47 and 49

> Q5. How many Male and Female subjects/patients are in the dataset?

``` r
table(subject$biological_sex)
```


    Female   Male 
        66     30 

There are 66 female and 30 male.

> Q6. What is the breakdown of race and biological sex (e.g. number of
> Asian females, White males etc…)?

``` r
table(subject$biological_sex, subject$ethnicity) 
```

            
             Hispanic or Latino Not Hispanic or Latino Unknown
      Female                 18                     47       1
      Male                    5                     22       3

``` r
library(lubridate)
```

    Warning: package 'lubridate' was built under R version 4.2.2

    Loading required package: timechange

    Warning: package 'timechange' was built under R version 4.2.2


    Attaching package: 'lubridate'

    The following objects are masked from 'package:base':

        date, intersect, setdiff, union

> Q7. Using this approach determine (i) the average age of wP
> individuals, (ii) the average age of aP individuals; and (iii) are
> they significantly different?

``` r
subject$age <- today() - ymd(subject$year_of_birth)
```

``` r
library(dplyr)
```


    Attaching package: 'dplyr'

    The following objects are masked from 'package:stats':

        filter, lag

    The following objects are masked from 'package:base':

        intersect, setdiff, setequal, union

``` r
ap <- subject %>% filter(infancy_vac == "aP")

round( summary( time_length( ap$age, "years" ) ) )
```

       Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
         23      25      26      25      26      27 

``` r
wp <- subject %>% filter(infancy_vac == "wP")
round( summary( time_length( wp$age, "years" ) ) )
```

       Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
         28      32      35      36      40      55 

25 ; 36; They are significant;y different

> Q8. Determine the age of all individuals at time of boost?

``` r
int <- ymd(subject$date_of_boost) - ymd(subject$year_of_birth)
age_at_boost <- time_length(int, "year")
head(age_at_boost)
```

    [1] 30.69678 51.07461 33.77413 28.65982 25.65914 28.77481

> Q9. With the help of a faceted boxplot (see below), do you think these
> two groups are significantly different?

``` r
ggplot(subject) +
  aes(time_length(age, "year"),
      fill=as.factor(infancy_vac)) +
  geom_histogram(show.legend=FALSE) +
  facet_wrap(vars(infancy_vac), nrow=2) 
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](class19_files/figure-gfm/unnamed-chunk-16-1.png)

I think these two groups are significantly different.

``` r
specimen <- read_json("https://www.cmi-pb.org/api/specimen", simplifyVector = TRUE) 
titer <- read_json("https://www.cmi-pb.org/api/ab_titer", simplifyVector = TRUE) 
```

> Q9. Complete the code to join specimen and subject tables to make a
> new merged data frame containing all specimen records along with their
> associated subject details:

``` r
meta <- inner_join(specimen, subject)
```

    Joining, by = "subject_id"

``` r
dim(meta)
```

    [1] 729  14

``` r
head(meta)
```

      specimen_id subject_id actual_day_relative_to_boost
    1           1          1                           -3
    2           2          1                          736
    3           3          1                            1
    4           4          1                            3
    5           5          1                            7
    6           6          1                           11
      planned_day_relative_to_boost specimen_type visit infancy_vac biological_sex
    1                             0         Blood     1          wP         Female
    2                           736         Blood    10          wP         Female
    3                             1         Blood     2          wP         Female
    4                             3         Blood     3          wP         Female
    5                             7         Blood     4          wP         Female
    6                            14         Blood     5          wP         Female
                   ethnicity  race year_of_birth date_of_boost      dataset
    1 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    2 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    3 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    4 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    5 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    6 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
             age
    1 13485 days
    2 13485 days
    3 13485 days
    4 13485 days
    5 13485 days
    6 13485 days

> Q10. Now using the same procedure join meta with titer data so we can
> further analyze this data in terms of time of visit aP/wP, male/female
> etc.

``` r
abdata <- inner_join(titer, meta)
```

    Joining, by = "specimen_id"

``` r
dim(abdata)
```

    [1] 32675    21

> Q11. How many specimens (i.e. entries in abdata) do we have for each
> isotype?

``` r
table(abdata$isotype)
```


     IgE  IgG IgG1 IgG2 IgG3 IgG4 
    6698 1413 6141 6141 6141 6141 

> Q12. What do you notice about the number of visit 8 specimens compared
> to other visits?

``` r
table(abdata$visit)
```


       1    2    3    4    5    6    7    8 
    5795 4640 4640 4640 4640 4320 3920   80 

It is significantly lower.

``` r
ig1 <- abdata %>% filter(isotype == "IgG1", visit!=8)
head(ig1)
```

      specimen_id isotype is_antigen_specific antigen        MFI MFI_normalised
    1           1    IgG1                TRUE     ACT 274.355068      0.6928058
    2           1    IgG1                TRUE     LOS  10.974026      2.1645083
    3           1    IgG1                TRUE   FELD1   1.448796      0.8080941
    4           1    IgG1                TRUE   BETV1   0.100000      1.0000000
    5           1    IgG1                TRUE   LOLP1   0.100000      1.0000000
    6           1    IgG1                TRUE Measles  36.277417      1.6638332
       unit lower_limit_of_detection subject_id actual_day_relative_to_boost
    1 IU/ML                 3.848750          1                           -3
    2 IU/ML                 4.357917          1                           -3
    3 IU/ML                 2.699944          1                           -3
    4 IU/ML                 1.734784          1                           -3
    5 IU/ML                 2.550606          1                           -3
    6 IU/ML                 4.438966          1                           -3
      planned_day_relative_to_boost specimen_type visit infancy_vac biological_sex
    1                             0         Blood     1          wP         Female
    2                             0         Blood     1          wP         Female
    3                             0         Blood     1          wP         Female
    4                             0         Blood     1          wP         Female
    5                             0         Blood     1          wP         Female
    6                             0         Blood     1          wP         Female
                   ethnicity  race year_of_birth date_of_boost      dataset
    1 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    2 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    3 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    4 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    5 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
    6 Not Hispanic or Latino White    1986-01-01    2016-09-12 2020_dataset
             age
    1 13485 days
    2 13485 days
    3 13485 days
    4 13485 days
    5 13485 days
    6 13485 days

> Q13. Complete the following code to make a summary boxplot of Ab titer
> levels for all antigens:

``` r
ggplot(ig1) +
  aes(MFI, antigen) +
  geom_boxplot() + 
  facet_wrap(vars(visit), nrow=2)
```

![](class19_files/figure-gfm/unnamed-chunk-23-1.png)

> Q14. What antigens show differences in the level of IgG1 antibody
> titers recognizing them over time? Why these and not others?

TT,FHA, FIM2/3 and more

> Q15. Filter to pull out only two specific antigens for analysis and
> create a boxplot for each.

``` r
filter(ig1, antigen=="Measles") %>%
  ggplot() +
  aes(MFI, col=infancy_vac) +
  geom_boxplot(show.legend = TRUE) +
  facet_wrap(vars(visit)) +
  theme_bw()
```

![](class19_files/figure-gfm/unnamed-chunk-24-1.png)

``` r
filter(ig1, antigen=="FIM2/3") %>%
  ggplot() +
  aes(MFI, col=infancy_vac) +
  geom_boxplot(show.legend = TRUE) +
  facet_wrap(vars(visit)) +
  theme_bw()
```

![](class19_files/figure-gfm/unnamed-chunk-25-1.png)

> Q16. What do you notice about these two antigens time course and the
> FIM2/3 data in particular?

They have risen over time and exceed those of Measles.

> Q17. Do you see any clear difference in aP vs. wP responses?

In Measles not so much but in FIM2/3 the difference is more obvious.

``` r
url <- "https://www.cmi-pb.org/api/v2/rnaseq?versioned_ensembl_gene_id=eq.ENSG00000211896.7"

rna <- read_json(url, simplifyVector = TRUE) 
```

``` r
ssrna <- inner_join(rna, meta)
```

    Joining, by = "specimen_id"

``` r
ggplot(ssrna) +
  aes(visit, tpm, group=subject_id) +
  geom_point() +
  geom_line(alpha=0.2)
```

![](class19_files/figure-gfm/unnamed-chunk-28-1.png)

> Q19.: What do you notice about the expression of this gene (i.e. when
> is it at it’s maximum level)?

It is mostly in its fourth visit.

> Q20. Does this pattern in time match the trend of antibody titer data?
> If not, why not?

It doesn’t seems to match because it seems to increase after the fourth
visit in the titer data but not in the pattern.
