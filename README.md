# Crop Yield Estimator
Jordan Wheeler, Data Analytics Capstone Project 80/81FA23

## Project Goal
The goal of this project is to build a model that can determine the maximum crop yield that can be obtained given a set of parameters. This is a widely discussed topic within the Agriculture industry as improving crop yield reduces costs and helps provide sustanence for an ever growing population. This project focuses on trying to identify the best scenario to maximize crop yields while enabling a more sustainable form of Agriculture while reducing the environmental impacts. The full report can be read on [Overleaf](https://www.overleaf.com/read/kshnchhyhycm#1a66e0).


## Introduction
This project followed a standardized approach to a Data Science topic. It began by defining the scenario that the research would take place on. Once completed, data collection and preparation took place. After cleaning the data, it was then extracted, transformed, and loaded into a Jupyter Notebook file. From there, an exploratory analysis took place to tell what was happening with the data and get a better understanding of what we were working with. Once an understanding was had, model building and testing took place. The goal of this area was to find a model that would give accurate results and did not under or over fit the data. The models and their uses were explained and insights from the models were explored. Finally, the project looked at limitations with the models and future uses. For a more in depth review on these, please visit the [Overleaf](https://www.overleaf.com/read/kshnchhyhycm#1a66e0) report.

## Files Used
* [pesticides](Data/pesticides.csv): Contains the information about pesticide usage in tonnes for each country per year.
* [rainfall](Data/rainfall.csv): Provides the average amount of rainfall in each country in mm per year.
* [temp](Data/temp.csv): Provides the average tempearture for each country in degrees Celsius.
* [yield](Data/yield.csv): Provides the yield for each country by crop and year. Results are measured in hectagrams per hectare.
* [df_yield](Data/df_yield.csv): This file is the combined data from all the other datasets with only relevant fields.

* The data for pesticides and yield were collected from the [FAO](https://www.fao.org/home/en/) website.
* The data for rainfall and temperature were collected from the [World Bank](https://data.worldbank.org/) website.

## Getting Started

* Begin by creating a folder to house your information.
* This folder should contain all data that was found and will eventually be where you store the notebook.
* For organizational purposes, all data has been stored in the Data folder.
* After getting the data and performing cleaning operations, create a virtual environment within your repository.
* Type `python -m venv .venv` in your terminal to setup a virtual environment.
* To activate the virtual environment type `.venv\Scripts\activate` in the terminal.
* After creating the virtual environment use `pip install -r requirements.txt` in the terminal.
* Once there, type `jupyter lab` in the terminal. If a browser does not automatically pop up, use `CTRL + Click` on the link provided.

## Data Loading and Exploring
After initial setup, the data was loaded into the notebook using the pandas module for Python.
![Loading Data]((https://github.com/jordanwheeler7/capstone-crop-yield/blob/857b300777241d29ad437b0dfb0d84437102062a/Images/Loading%20Data.png)https://github.com/jordanwheeler7/capstone-crop-yield/blob/857b300777241d29ad437b0dfb0d84437102062a/Images/Loading%20Data.png)

