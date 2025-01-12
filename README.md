# RetailSales
Retail Sales for Recreational Goods.<br/>
Here are some of the resources used in the project:<br/>
**Credits:** [Time-Series-Datasets](https://new.censusatschool.org.nz/resource/time-series-data-sets-2012/) from Census At School.<br/>
**Datasets:** http://www.stats.govt.nz/infoshare/Default.aspx on 6 December 2012, and formatted for importing into iNZight.<br/>
**Full Web Report:** [Web Report hosted in RPub](https://rpubs.com/roywong96/633767)


# Introduction

Analysis conducted through a Model-Building Strategy to find the best fitting model for the data of monthly retail sales in millions of dollars for recreational goods in New Zealand from 1995 to 2010. After this, the forecast for monthly retail sales for recreational goods in New Zealand for the next 10 units of time will be given at the end of the report.

![](https://github.com/roywong96/RetailSales/blob/main/TSA/TSA_main.png)


# Model Specification

- We started by checking for trend, seasonality and stationarity in the data through the ACF and PACF.
- By fitting for SARMA(1,1,1) component and see if we get rid of seasonal component.
- Before dealing with the behaviour of the series, at first we have to deal with the trend of the series followed by the changing variance.
- Using the BOX-COX transformation, the we can see that the series is then stationary as confirmed thought the ADF test.
- Finally, to de-trend the series, the differencing is performed.

![](https://github.com/roywong96/RetailSales/blob/main/TSA/PCA1.png)


# Overfitting

- SARIMA<sub>(2,1,2)X(1,1,1)<sub>12</sub></sub> and SARIMA<sub>(1,1,3)X(1,1,1)<sub>12</sub></sub> are consider and checked for overfitting SARIMA<sub>(1,1,2)X(1,1,1)<sub>12</sub></sub>.
- The coefficients in the specified model and in overfitted model are very different. We calculate AIC and BIC to compare the results.

![](https://github.com/roywong96/RetailSales/blob/main/TSA/AIC_overfit.png)
![](https://github.com/roywong96/RetailSales/blob/main/TSA/BIC_overfit.png)


- SARIMA<sub>(1,1,2)X(1,1,1)<sub>12</sub></sub> is considered to be the best fit with the lowest AIC and BIC score.

# Model Fitting

Using the EACF a the BIC table, we selected a few models as listed below:

- SARIMA<sub>(0,1,3)X(1,1,1)<sub>12</sub></sub>
- SARIMA<sub>(1,1,0)X(1,1,1)<sub>12</sub></sub>
- SARIMA<sub>(1,1,2)X(1,1,1)<sub>12</sub></sub>
- SARIMA<sub>(1,1,3)X(1,1,1)<sub>12</sub></sub>
- SARIMA<sub>(2,1,3)X(1,1,1)<sub>12</sub></sub>
- SARIMA<sub>(2,1,4)X(1,1,1)<sub>12</sub></sub>
- SARIMA<sub>(3,1,4)X(1,1,1)<sub>12</sub></sub>

![](https://github.com/roywong96/RetailSales/blob/main/TSA/BIC%20.png)

# Model Diagnostics

- We carry out the Residual Analysis to determine whether the model selected is suitable for forcasting
- SARIMA(1,1,2)X(1,1,1)<sub>12</sub> is proven to be normal so we can proceed with the forecasting.

![](https://github.com/roywong96/RetailSales/blob/main/TSA/Diagnostic_Check.png)




# Forecasting

The prediction of the next 10 units is shown. Clearly, it reflects on the seasonality. We notice that the forecast’s limits become bigger as long as the prediction is made for longer durations. That is because the uncertainty level in the forecast will increase due to the seasonality, the ordinal, and autocorrelation characteristics. In Figure 42, we can see that the next 10 units of sales of recreational goods will fluctuate in the blue region (80% confidence interval) and the grey region (95% confidence interval).

![](https://github.com/roywong96/RetailSales/blob/main/TSA/TSA_forecast.png)

# Conclusion

Firstly, the recreational goods sales series is not normal and nonstationary. As a result, we applied Box-Cox transformation to improve the stability of variance. Also, after the first seasonal and ordinary differencing, it turns out to be stationary.

From the set of selected models, model fitting is carried out to determine the most competative model which is SARIMA(1,1,2)X(1,1,1)<sub>12</sub> model. Through model diagnostics, it can be proved that SARIMA(1,1,2)X(1,1,1)<sub>12</sub> is a reliable and promising model to predict as shown above.

