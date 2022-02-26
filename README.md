# ts-plots.R
ts-plots.R

Packages: fpp3, readr

* tsibble objects
* Data: PBS (tsibble object) containing monthly data on Australia medicare prescription data
* Filtering (Month, Concession, Type, Cost)
* Summarise (all costs in a given month)
* Mutate to create a new cost column

New Data: prison
* Date conversion
* Tsibble object Date conversion 


## Time series plots
* Airport Data
* Autoplot of Cost (Antidiabetic drug sales)
* Checking for seasonality
* Seasonal subseries plot
* Demand per day, week, year etc. 

![image](https://user-images.githubusercontent.com/65502025/155845275-5b63dcc4-3a7e-4fac-9e72-d49f171bdb97.png)
  
![image](https://user-images.githubusercontent.com/65502025/155845284-a4b498fa-e7db-4e99-98d0-eebabf4c0f95.png)

![image](https://user-images.githubusercontent.com/65502025/155845506-6e3c8a48-5f50-4c36-a312-bf10a8b76b97.png)

![image](https://user-images.githubusercontent.com/65502025/155845552-18080323-bf7b-4f71-bad4-f61a3e7b2b9f.png)

![image](https://user-images.githubusercontent.com/65502025/155845586-d62f19e4-734a-4805-ada5-ac787a3af9e9.png)

![image](https://user-images.githubusercontent.com/65502025/155845594-bcfeb0d0-3337-4cbd-9cf4-0cac3964fcd8.png)

![image](https://user-images.githubusercontent.com/65502025/155845603-3b24b497-696e-48da-be72-3e3d8676d1fc.png)

Holiday Tourism Data
* "Australian domestic holiday nights" Time series plots
  * autoplot, gg_season, gg_subseries
* Cross Correlation: "Half-hourly electricity demand: Victoria, Australia"
  * Demand, temperature
* GGally

![image](https://user-images.githubusercontent.com/65502025/155845625-f84e0746-f1f3-4662-8b9d-d6393ebe1757.png)

![image](https://user-images.githubusercontent.com/65502025/155845835-7d54db60-a14e-452f-8d6f-4837cffce395.png)


# Cross-correlation
vic_elec %>%
  filter(year(Time) == 2014) %>%
  autoplot(Demand) +
  xlab("Year: 2014") + ylab(NULL) +
  ggtitle("Half-hourly electricity demand: Victoria, Australia")

vic_elec %>%
  filter(year(Time) == 2014) %>%
  autoplot(Temperature) +
  xlab("Year: 2014") + ylab(NULL) +
  ggtitle("Half-hourly temperatures: Melbourne, Australia")

vic_elec %>%
  filter(year(Time) == 2014) %>%
  ggplot(aes(x = Temperature, y = Demand)) +
  geom_point() +
  ylab("Demand (GW)") + xlab("Temperature (Celsius)")

visitors <- tourism %>%
  group_by(State) %>%
  summarise(Trips = sum(Trips))

visitors %>%
  ggplot(aes(x = Quarter, y = Trips)) +
  geom_line() +
  facet_grid(vars(State), scales = "free_y") +
  ylab("Number of visitor nights each quarter (millions)")

visitors %>%
  spread(State, Trips) %>%
  GGally::ggpairs(columns = 2:9)

# Auto-correlation (self correlation)
recent_production <- aus_production %>%
  filter(year(Quarter) >= 1992)

recent_production %>% gg_lag(Beer, geom="point") 
#current(y axis) vs previous quarter(x-axis) a year ago
#explains if time series related to it's self one time period ago

recent_production %>% ACF(Beer, lag_max = 9)
#(ACF) auto correlation function

recent_production %>% ACF(Beer) %>% autoplot()

# Trends and seasonality affect ACF
a10 %>% ACF(Cost, lag_max = 48) %>% autoplot()

# When there is no auto-correlation
set.seed(30)
y <- tsibble(sample = 1:50, wn = rnorm(50), index = sample)
y %>% autoplot(wn) + ggtitle("White noise")

y %>% ACF(wn) %>% autoplot()

# Code to play with a time series
help(us_employment)

#before you start modeling, filter
us_retail_employment <- us_employment %>%
  filter(year(Month) >= 1990, Title == "Retail Trade") %>%
  select(-Series_ID)

us_retail_employment

#do an autoplot to view
us_retail_employment %>%
  autoplot(Employed) +
  xlab("Year") + ylab("Persons (thousands)") +
  ggtitle("Total employment in US retail")

frequency(us_retail_employment)

us_retail_employment %>% gg_season(Employed, labels = "both") +
  ylab("Persons (thousands)") +
  ggtitle("Seasonal plot")

us_retail_employment %>%
  gg_subseries(Employed) +
  ylab("Persons (thousands)") +
  ggtitle("Seasonal subseries plot")

us_retail_employment %>% ACF(Employed) %>% autoplot() +
  xlab("Lag")

us_retail_employment %>% gg_lag(Employed, geom="point")

