---
id: wazihub-smp-2019-zindi
title: WAZIHUB Soil Moisture Prediction Challenge
type: dataset
desc: Soil Moisture data from Gaston Berger University, Senegal, as collected by WaziHub Project in 2019 and made available for free.
color: "#f1f1f1"
tags:
    - Dataset
    - Soil Moisture Prediction
    - Waziup
    - WaziHub
    - Senegal
    - "2019"
---

# Introduction

On November 08, 2019 WAZIHUB launched a 3-month competition hosted by ZINDI to predict Soil Moisture and allow farmers to anticipate water needs and automate their irrigation schedule. The competition was possible with 3 months (February to April) of data collected from the agriculture pilot applications at the Gaston Berger University  in Senegal with WAZIUP soil moisture sensors. In numbers 677 data scientis enrolled and 6,443 total sessions across 96 countries.


## Challenge Context

As climate change impacts intensify, the agricultural sector in Africa must adapt its practices. Enabling farmers to accurately measure and predict soil humidity in their fields will allow them to optimally and efficiently plan irrigation schedules.

Sensor-based irrigation systems and machine learning algorithms offer a solution for more efficient water management. However, current machine learning models built on sensor data require extensive training data. Obtaining stable sensor data in rural Africa is challenging due to issues such as accessibility, limited battery power, lack of internet connectivity, and harsh environmental conditions.

The objective of this competition hosted by [Zindi](https://zindi.africa/) is to develop a machine learning model capable of predicting humidity levels for a specific plot in the upcoming days, using historical data. A key challenge is to design algorithms that are resilient and can be trained on incomplete data (e.g., missing data points) and unclean data (e.g., numerous outliers).

The resulting model will enable farmers to anticipate water needs and prepare their irrigation schedules accordingly.

https://www.waziup.io/research-innovation/projects/wazihub/

# About Dataset

Wazihub project conducted a 4-month experiment in Senegal, utilizing low-cost IoT sensors to collect data from 4 fields cultivating maize and peanuts.
An IoT sensor was deployed in each of the 4 adjacent plots, separated by a 1-meter perimeter, with consistent sowing amounts for each crop.

Three irrigation regimes were implemented:
1. Usual irrigation: Watering every two days
2. Deficit irrigation: Irregular watering intervals, providing less water than crop requirements
3. Water loss-based irrigation: Watering based on estimated water loss, calculated using evapotranspiration and soil moisture data from IoT sensors.

The field configurations were:

- Field 1: Maize, deficit irrigation
- Field 2: Peanuts, water loss-based irrigation
- Field 3: Peanuts, deficit irrigation
- Field 4: Peanuts, usual irrigation

![plot image](img/SM_plot_map.png#width=300)

# Goal

The objective of this challenge is to accurately predict the soil moisture level multiple days in advance for each of the fields individually. This solution will help farmers prepare their irrigation schedules more efficiently.

You are provided with data from four fields on which to train your model. You will need to predict, in 5-minute increments, the last four days for soil humidities in fields 1 and 3 and you will need to predict, in 5-minute increments, the last six days for soil humidities in fields 2 and 4.

# Data Files

Here are the data files:

- [SampleSubmission.csv](SampleSubmission.csv) - is an example of what your submission file should look like. Note that the variable ID in the submission file is Date and time "yyyy-mm-dd hh:mm:ss" + " x " + name of each field. The order of the rows does not matter, but the names of the IDs must be correct. The column "Values" is your prediction of the soil humidity for each field.
- [Train.csv](Train.csv) - contains the soil humidities for 4 fields and the other variables that are collected every five minutes by the IoT weather station. The last four days for soil humidities in fields 1 and 3 and the last six days for soil humidities in fields 2 and 4 have been removed as the test set. However, where the soil humidity peaks due to irrigation within the testset, you are provided with the peak soil humidity.
- [Context_data_maize.csv](Context_Data_Maize.csv) - Context data collected by hand in Excel.
- [Context_data_peanut.csv](Context_Data_Peanuts.csv) - Context data collected by hand in Excel.
- [Variable_Definitions.csv](VariableDefinitions.csv) - Definitions of variables

# Resourcce

One of the Waziup team member previously worked with this data for his Master Thesis and published his work in an international Conference on IEEE. The Publication can be found bellow link.
-   [A Comparative Study on Machine Learning Methods Through Evaluating the Impact of Contributing Factors on The Accuracy of Soil Moisture Prediction](https://ieeexplore.ieee.org/document/10310440)