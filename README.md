# Time Series Plots .R
Time Series analysis concepts using examples in r. Multiple data sets were used to demonstrate reading in data, filtering, date conversion, plotting (autoplot, gg_season, gg_subseries, GGalley), seasonality, cross correlation, autocorrelation, ACF, lag, white noise etc. 

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

## Holiday Tourism Data
* "Australian domestic holiday nights" Time series plots
  * autoplot, gg_season, gg_subseries
* Cross Correlation: "Half-hourly electricity demand: Victoria, Australia"
  * Demand, temperature
* GGally
* Auto-correlation - checking for lag one time period ago
* (ACF) auto correlation function
* White Noise
* 

![image](https://user-images.githubusercontent.com/65502025/155845625-f84e0746-f1f3-4662-8b9d-d6393ebe1757.png)

![image](https://user-images.githubusercontent.com/65502025/155845835-7d54db60-a14e-452f-8d6f-4837cffce395.png)

![image](https://user-images.githubusercontent.com/65502025/155846107-f9bab63d-0276-45c7-8bda-c790dcb95ab7.png)



## Code to play with a time series
US Employment

![image](https://user-images.githubusercontent.com/65502025/155846163-4be97621-d9df-4ca6-a32d-b656575a1bb5.png)

![image](https://user-images.githubusercontent.com/65502025/155846175-b96f872f-e087-4810-a920-2fa7714c6678.png)

![image](https://user-images.githubusercontent.com/65502025/155846196-4a6f6b63-0eae-4e48-9921-734c1f4efa68.png)

![image](https://user-images.githubusercontent.com/65502025/155846206-1ef67f3d-ca81-47b1-949e-f5685e68b71e.png)

