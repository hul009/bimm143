class17_miniProject
================

``` r
vax <- read.csv("29cd0b19-c7e6-4eb1-8be8-2b6e269f446e.csv")
head(vax)
```

      as_of_date zip_code_tabulation_area local_health_jurisdiction          county
    1 2021-01-05                    93562            San Bernardino  San Bernardino
    2 2021-01-05                    93437             Santa Barbara   Santa Barbara
    3 2021-01-05                    93445           San Luis Obispo San Luis Obispo
    4 2021-01-05                    93442           San Luis Obispo San Luis Obispo
    5 2021-01-05                    93444           San Luis Obispo San Luis Obispo
    6 2021-01-05                    93453           San Luis Obispo San Luis Obispo
      vaccine_equity_metric_quartile                 vem_source
    1                              1 Healthy Places Index Score
    2                             NA            No VEM Assigned
    3                              2 Healthy Places Index Score
    4                              3 Healthy Places Index Score
    5                              3 Healthy Places Index Score
    6                              3 Healthy Places Index Score
      age12_plus_population age5_plus_population tot_population
    1                1469.5                 1668           1771
    2                2494.5                 2871           3387
    3                6116.7                 6762           7106
    4               10005.2                10615          10917
    5               18951.8                20522          21331
    6                2373.6                 2499           2578
      persons_fully_vaccinated persons_partially_vaccinated
    1                       NA                           NA
    2                       NA                           NA
    3                       NA                           NA
    4                       NA                           NA
    5                       NA                           NA
    6                       NA                           NA
      percent_of_population_fully_vaccinated
    1                                     NA
    2                                     NA
    3                                     NA
    4                                     NA
    5                                     NA
    6                                     NA
      percent_of_population_partially_vaccinated
    1                                         NA
    2                                         NA
    3                                         NA
    4                                         NA
    5                                         NA
    6                                         NA
      percent_of_population_with_1_plus_dose booster_recip_count
    1                                     NA                  NA
    2                                     NA                  NA
    3                                     NA                  NA
    4                                     NA                  NA
    5                                     NA                  NA
    6                                     NA                  NA
      bivalent_dose_recip_count eligible_recipient_count
    1                        NA                        0
    2                        NA                        1
    3                        NA                        0
    4                        NA                        1
    5                        NA                        0
    6                        NA                        0
                                                                   redacted
    1 Information redacted in accordance with CA state privacy requirements
    2 Information redacted in accordance with CA state privacy requirements
    3 Information redacted in accordance with CA state privacy requirements
    4 Information redacted in accordance with CA state privacy requirements
    5 Information redacted in accordance with CA state privacy requirements
    6 Information redacted in accordance with CA state privacy requirements

``` r
head(vax$as_of_date)
```

    [1] "2021-01-05" "2021-01-05" "2021-01-05" "2021-01-05" "2021-01-05"
    [6] "2021-01-05"

``` r
tail(vax$as_of_date)
```

    [1] "2022-11-15" "2022-11-15" "2022-11-15" "2022-11-15" "2022-11-15"
    [6] "2022-11-15"

> Q1. What column details the total number of people fully vaccinated?
> persons_fully_vaccinated

> Q2. What column details the Zip code tabulation area?
> zip_code_tabulation_area

> Q3. What is the earliest date in this dataset? 2021-01-05

> Q4. What is the latest date in this dataset? 2022-11-15

``` r
skimr::skim(vax)
```

|                                                  |        |
|:-------------------------------------------------|:-------|
| Name                                             | vax    |
| Number of rows                                   | 172872 |
| Number of columns                                | 18     |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |        |
| Column type frequency:                           |        |
| character                                        | 5      |
| numeric                                          | 13     |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |        |
| Group variables                                  | None   |

Data summary

**Variable type: character**

| skim_variable             | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| as_of_date                |         0 |             1 |  10 |  10 |     0 |       98 |          0 |
| local_health_jurisdiction |         0 |             1 |   0 |  15 |   490 |       62 |          0 |
| county                    |         0 |             1 |   0 |  15 |   490 |       59 |          0 |
| vem_source                |         0 |             1 |  15 |  26 |     0 |        3 |          0 |
| redacted                  |         0 |             1 |   2 |  69 |     0 |        2 |          0 |

**Variable type: numeric**

| skim_variable                              | n_missing | complete_rate |     mean |       sd |    p0 |      p25 |      p50 |      p75 |     p100 | hist  |
|:-------------------------------------------|----------:|--------------:|---------:|---------:|------:|---------:|---------:|---------:|---------:|:------|
| zip_code_tabulation_area                   |         0 |          1.00 | 93665.11 |  1817.39 | 90001 | 92257.75 | 93658.50 | 95380.50 |  97635.0 | ▃▅▅▇▁ |
| vaccine_equity_metric_quartile             |      8526 |          0.95 |     2.44 |     1.11 |     1 |     1.00 |     2.00 |     3.00 |      4.0 | ▇▇▁▇▇ |
| age12_plus_population                      |         0 |          1.00 | 18895.04 | 18993.88 |     0 |  1346.95 | 13685.10 | 31756.12 |  88556.7 | ▇▃▂▁▁ |
| age5_plus_population                       |         0 |          1.00 | 20875.24 | 21105.98 |     0 |  1460.50 | 15364.00 | 34877.00 | 101902.0 | ▇▃▂▁▁ |
| tot_population                             |      8428 |          0.95 | 23372.77 | 22628.51 |    12 |  2126.00 | 18714.00 | 38168.00 | 111165.0 | ▇▅▂▁▁ |
| persons_fully_vaccinated                   |     15440 |          0.91 | 13309.15 | 14740.07 |    11 |   859.00 |  7687.00 | 22253.00 |  87305.0 | ▇▃▁▁▁ |
| persons_partially_vaccinated               |     15440 |          0.91 |  1679.13 |  1993.86 |    11 |   157.00 |  1158.00 |  2483.00 |  39201.0 | ▇▁▁▁▁ |
| percent_of_population_fully_vaccinated     |     18986 |          0.89 |     0.54 |     0.26 |     0 |     0.36 |     0.58 |     0.73 |      1.0 | ▃▃▆▇▃ |
| percent_of_population_partially_vaccinated |     18986 |          0.89 |     0.08 |     0.09 |     0 |     0.05 |     0.06 |     0.08 |      1.0 | ▇▁▁▁▁ |
| percent_of_population_with_1\_plus_dose    |     19822 |          0.89 |     0.60 |     0.26 |     0 |     0.42 |     0.64 |     0.79 |      1.0 | ▂▃▆▇▆ |
| booster_recip_count                        |     70642 |          0.59 |  5701.06 |  6972.68 |    11 |   276.00 |  2546.00 |  9513.00 |  58301.0 | ▇▂▁▁▁ |
| bivalent_dose_recip_count                  |    156937 |          0.09 |  1512.94 |  1994.71 |    11 |   101.00 |   662.00 |  2236.00 |  16790.0 | ▇▁▁▁▁ |
| eligible_recipient_count                   |         0 |          1.00 | 12114.80 | 14551.97 |     0 |   438.00 |  5520.00 | 20714.00 |  86817.0 | ▇▂▁▁▁ |

``` r
sum( is.na(vax$persons_fully_vaccinated) )
```

    [1] 15440

``` r
nrow(vax$persons_fully_vaccinated)
```

    NULL

> Q5. How many numeric columns are in this dataset? 13

> Q6. Note that there are “missing values” in the dataset. How many NA
> values there in the persons_fully_vaccinated column? 15440

> Q7. What percent of persons_fully_vaccinated values are missing (to 2
> significant figures)? 9percent

``` r
library(lubridate)
```

    Warning: package 'lubridate' was built under R version 4.2.2

    Loading required package: timechange

    Warning: package 'timechange' was built under R version 4.2.2


    Attaching package: 'lubridate'

    The following objects are masked from 'package:base':

        date, intersect, setdiff, union

``` r
today()
```

    [1] "2022-12-03"

``` r
vax$as_of_date <- ymd(vax$as_of_date)
```

> Q9. How many days have passed since the last update of the dataset? 6

> Q10. How many unique dates are in the dataset (i.e. how many different
> dates are detailed)? 98

``` r
library(zipcodeR)
```

    Warning: package 'zipcodeR' was built under R version 4.2.2

``` r
geocode_zip('92037')
```

    # A tibble: 1 × 3
      zipcode   lat   lng
      <chr>   <dbl> <dbl>
    1 92037    32.8 -117.

``` r
zip_distance('92037','92109')
```

      zipcode_a zipcode_b distance
    1     92037     92109     2.33

``` r
reverse_zipcode(c('92037', "92109") )
```

    # A tibble: 2 × 24
      zipcode zipcode_…¹ major…² post_…³ common_c…⁴ county state   lat   lng timez…⁵
      <chr>   <chr>      <chr>   <chr>       <blob> <chr>  <chr> <dbl> <dbl> <chr>  
    1 92037   Standard   La Jol… La Jol… <raw 20 B> San D… CA     32.8 -117. Pacific
    2 92109   Standard   San Di… San Di… <raw 21 B> San D… CA     32.8 -117. Pacific
    # … with 14 more variables: radius_in_miles <dbl>, area_code_list <blob>,
    #   population <int>, population_density <dbl>, land_area_in_sqmi <dbl>,
    #   water_area_in_sqmi <dbl>, housing_units <int>,
    #   occupied_housing_units <int>, median_home_value <int>,
    #   median_household_income <int>, bounds_west <dbl>, bounds_east <dbl>,
    #   bounds_north <dbl>, bounds_south <dbl>, and abbreviated variable names
    #   ¹​zipcode_type, ²​major_city, ³​post_office_city, ⁴​common_city_list, …

``` r
library(dplyr)
```


    Attaching package: 'dplyr'

    The following objects are masked from 'package:stats':

        filter, lag

    The following objects are masked from 'package:base':

        intersect, setdiff, setequal, union

``` r
sd <- filter(vax, county == "San Diego")

nrow(sd)
```

    [1] 10486

``` r
length(unique(sd$zip_code_tabulation_area))
```

    [1] 107

``` r
which.max(sd$age12_plus_population)
```

    [1] 90

``` r
sd[90,]
```

       as_of_date zip_code_tabulation_area local_health_jurisdiction    county
    90 2021-01-05                    92154                 San Diego San Diego
       vaccine_equity_metric_quartile                 vem_source
    90                              2 Healthy Places Index Score
       age12_plus_population age5_plus_population tot_population
    90               76365.2                82971          88979
       persons_fully_vaccinated persons_partially_vaccinated
    90                       17                         1376
       percent_of_population_fully_vaccinated
    90                               0.000191
       percent_of_population_partially_vaccinated
    90                                   0.015464
       percent_of_population_with_1_plus_dose booster_recip_count
    90                               0.015655                  NA
       bivalent_dose_recip_count eligible_recipient_count
    90                        NA                       17
                                                                    redacted
    90 Information redacted in accordance with CA state privacy requirements

> Q11. How many distinct zip codes are listed for San Diego County? 107

> Q12. What San Diego County Zip code area has the largest 12 +
> Population in this dataset? 92154

``` r
sd.1 <- filter( vax, county == "San Diego" &
                as_of_date =="2022-11-15")
```

``` r
mean(sd.1$percent_of_population_fully_vaccinated,na.rm=TRUE)
```

    [1] 0.7381765

> Q13. What is the overall average “Percent of Population Fully
> Vaccinated” value for all San Diego “County” as of “2022-11-15”?
> 0.7381765

> Q14. Using either ggplot or base R graphics make a summary figure that
> shows the distribution of Percent of Population Fully Vaccinated
> values as of “2022-11-15”?

``` r
hist(sd.1$percent_of_population_fully_vaccinated)
```

![](class17_files/figure-gfm/unnamed-chunk-20-1.png)

``` r
ucsd <- filter(sd, zip_code_tabulation_area=="92037")
ucsd[1,]$age5_plus_population
```

    [1] 36144

> Q15. Using ggplot make a graph of the vaccination rate time course for
> the 92037 ZIP code area:

``` r
library(ggplot2)
```

``` r
ggplot(ucsd) +
  aes(x=as_of_date,
      y=percent_of_population_fully_vaccinated) +
  geom_point() +
  geom_line(group=1) +
  ylim(c(0,1)) +
  labs(x="Date", y="Percent Vaccinated")+
  geom_hline(yintercept = 0.7088141)
```

![](class17_files/figure-gfm/unnamed-chunk-23-1.png)

``` r
vax.36 <- filter(vax, age5_plus_population > 36144 &
                as_of_date == "2022-11-15")
```

> Q16. Calculate the mean “Percent of Population Fully Vaccinated” for
> ZIP code areas with a population as large as 92037 (La Jolla)
> as_of_date “2022-11-15”. Add this as a straight horizontal line to
> your plot from above with the geom_hline() function?

``` r
mean(vax.36$percent_of_population_fully_vaccinated,na.rm=TRUE)
```

    [1] 0.7088141

> Q17. What is the 6 number summary (Min, 1st Qu., Median, Mean, 3rd
> Qu., and Max) of the “Percent of Population Fully Vaccinated” values
> for ZIP code areas with a population as large as 92037 (La Jolla)
> as_of_date “2022-11-15”?

``` r
summary(vax.36$percent_of_population_fully_vaccinated)
```

       Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
     0.1986  0.6338  0.7162  0.7088  0.7893  1.0000 

> Q18. Using ggplot generate a histogram of this data.

``` r
ggplot(vax.36, aes(x=percent_of_population_fully_vaccinated)) + geom_histogram()
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](class17_files/figure-gfm/unnamed-chunk-27-1.png)

> Q19. Is the 92109 and 92040 ZIP code areas above or below the average
> value you calculated for all these above?

``` r
vax %>% filter(as_of_date == "2022-11-15") %>%  
  filter(zip_code_tabulation_area=="92040") %>%
  select(percent_of_population_fully_vaccinated)
```

      percent_of_population_fully_vaccinated
    1                               0.547251

It is below.

> Q20. Finally make a time course plot of vaccination progress for all
> areas in the full dataset with a age5_plus_population \> 36144

``` r
vax.36.all <- filter(vax, age5_plus_population > 36144)


ggplot(vax.36.all) +
  aes(x=as_of_date,
      y=percent_of_population_fully_vaccinated, 
      group=zip_code_tabulation_area) +
  geom_line(alpha=0.2, color="blue") +
  ylim(c(0,1)) +
  labs(x="Date", y="Percent vaccinated",
       title="Vaccination rate across California",
       subtitle="Only areas with a population above 36k are shown") +
  geom_hline(yintercept = 0.54 , linetype="solid")
```

    Warning: Removed 183 row(s) containing missing values (geom_path).

![](class17_files/figure-gfm/unnamed-chunk-29-1.png)

> Q21. How do you feel about traveling for Thanksgiving Break and
> meeting for in-person class afterwards?

I am ok with it.
