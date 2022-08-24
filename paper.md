---
title: 'VMDML: R package for Variational Mode Decomposition based Machine Learning Models'
tags:
  - R
  - Variational Mode Decomposition
  - VMD based Autoregressive Moving Average Model
  - VMD based Random Forest model
  - VMD based Timedelay Neural Network model
  - VMD based Support Vector Regression model
  
authors:
  - name: Pankaj Das
    orcid: 0000-0003-1672-2502
    affiliation: "1"
  - name: Girish Kumar Jha
    affiliation: "2"
  - name: Tauqueer Ahmad
    affiliation: "1"
  - name: Achal Lama
    affiliation: "1"
  - name: Lampros Mouselimis.
    affiliation: "3"
affiliations:
 - name: ICAR-Indian Agricultural Statistics Research Institute, New Delhi, India.
   index: 1
 - name: ICAR-Indian Agricultural Research Institute, New Delhi, India.
   index: 2
 - name: Monopteryx, Paramithiá, Epirus, Greece.
   index: 3
   
date: August 23, 2022 
bibliography: paper.bib

---

# Summary

In times series analysis,forecasting a timesseries data like commodity price is very difficult due to its inherent nonstationarity and nonlinear behaviour [@Das:2020]. Nonstationarity properties of a data may be solved by decomposing the data in small components through different time series decompostion techniques like wavelet decomposition [@Zhang:2017], empirical mode decomposition [@Das:2020], variational mode decomposition [@Hu:2020] etc. Now a days machine learning (ML) models like timedelay neural network (TDNN) model, support vector regression (SVR) model, random forest (RF) etc. gain popularity to deal nonlinear timeseries data. But no such models or approaches have been developed that deal with both nonstationarity and nonlinear behaviour in timeseries data. With the contest, an ensemble approach i.e. VMDML has been developed by combining the VMD and ML techniques. This ensemble approach is capable of dealing with both nonstationarity and nonlinear behaviour in time series data. 
The R package VMDML provides forecasts of nonstationarity and nonlinear timeseries data. Users can choose different ML models based on their interests. It will also provide you with accuracy measures along with an option to select the proportion of training and testing data sets. Users can choose among the available choices of parameters of variational mode decomposition for fitting the ML models. In this package we have modelled the dependency of the study variable by assuming first-order autocorrelation.

# Statement of need

Timeseries analysis is one of the important areas where many researchers work in the world. Timely and reliable forecasts are useful for governments, policy planners, and industries. It is almost universally agreed in the forecasting literature that no single method is best in every situation. This is largely because a real-world problem is often complex in nature and any single model may not be able to capture different patterns equally well [@Das:2020]. Therefore, there is a need for an ensemble model, i.e., a combination of a decomposition model and a machine learning technique that deals with both nonstationary and nonlinear patterns. The R packages VMDML were created using the VMD ([@Dragomiretskiy:2014] and ML models. It first decomposes nonstationary and nonlinear timeseries data into different stationary components called intrinsic mode functions (IMFs). Further, different ML models like RF, TDNN and SVR (based on interest) are used to forecast these decomposed components, i.e., IMFs. Finally, the algorithm aggregates all forecast values of IMFs to produce a final forecast of the timeseries data. This package will help researchers working in the area of hybrid machine learning models.

# Information for Users

`VMDML` is a collection of four VMD based machine learning models. Details of four models are given below.

## Apps included in the package

|Sl. No.| App Title | Function to call |Utility|
|:-----:| :----------- | :-----------:|:----------------|
|1|Variational Mode Decomposition Based Autoregressive Moving Average Model   | VMDARIMA()      |VMDARIMA model,Total no of IMFs, Prediction Accuracy, Final Prediction value |
|2|Variational Mode Decomposition Based Random Forest Model   | VMDRF()      |VMDRF model,Total no of IMFs, Prediction Accuracy, Final Prediction value |
|3|Variational Mode Decomposition based Support Vector Regression Model   | VMDSVR()      |VMDSVR model,Total no of IMFs, Prediction Accuracy, Final Prediction value |
|6|Variational Mode Decomposition based Timedelay Neural Network Model | VMDTDNN()      |VMDTDNN model,Total no of IMFs, Prediction Accuracy, Final Prediction value|

The package can be installed from CRAN as follows:

``` r
# Install from CRAN
install.packages('VMDML', dependencies=TRUE)
```

The development version can be installed from GitHub as follows:

``` r
# Install VMDML development version from Github using the code below:
if (!require('devtools')) install.packages('devtools')
devtools::install_github("Pankajdas7/VMDML")
```

## Package dependencies and details of functions used 

VMDARIMA() function uses `vmd` function of `VMDecomp` package [@VMDecomp_2022] for VMD decomposition. `forecast` [@forecast_2022] package was used to fit ARIMA model and produce forecast values of IMFs. 

VMDRF() function uses `vmd` function of `VMDecomp` package [@VMDecomp_2022] for VMD decomposition. `randomForest` [@randomForest_2022] and `stats` [@stats_2022] packages were used to fit random forest model and produce forecast values of IMFs.

VMDSVR()function uses `vmd` function of `VMDecomp` package [@VMDecomp_2022] for VMD decomposition. `svm` function of`e1071` [@e1071_2022] packages were used to fit SVR model.`predict` function from `stats` [@stats_2022] package was used to  produce forecast values of IMFs.

VMDSVR()function uses `vmd` function of `VMDecomp` package [@VMDecomp_2022] for VMD decomposition. `nnetar` and `forecast` functions of `forecast`[@forecast_2022] package were used to fit TDNN model and produce forecast values of IMFs.


# Usage

``` r
VMDML::VMDARIMA() # Fitting of VMD based ARIMA model
VMDML::VMDRF() # Fitting of VMD based RF model
VMDML::VMDSVR() # Fitting of VMD based SVR model
VMDML::VMDTDNN() # Fitting of VMD based TDNN model
```
# Acknowledgements

We wish to thank ICAR-Indian Agricultural Statistics Reaserch Institute, New Delhi, India for providing facilities for carrying out the present research.

# References