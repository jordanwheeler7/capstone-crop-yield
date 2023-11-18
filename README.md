# Crop Yield Estimator
Jordan Wheeler, Data Analytics Capstone Project 80/81FA23

## Project Goal
The goal of this project is to build a model that can determine the maximum crop yield that can be obtained given a set of parameters. This is a widely discussed topic within the Agriculture industry as improving crop yield reduces costs and helps provide sustanence for an ever growing population. This project focuses on trying to identify the best scenario to maximize crop yields while enabling a more sustainable form of Agriculture while reducing the environmental impacts. The full report can be read on [Overleaf](https://www.overleaf.com/read/kshnchhyhycm#1a66e0).


## Introduction
This project followed a standardized approach to a Data Science topic as shown in the image below. It began by defining the scenario that the research would take place on. Once completed, data collection and preparation took place. After cleaning the data, it was then extracted, transformed, and loaded into a Jupyter Notebook file. From there, an exploratory analysis took place to tell what was happening with the data and get a better understanding of what we were working with. Once an understanding was had, model building and testing took place. The goal of this area was to find a model that would give accurate results and did not under or over fit the data. The models and their uses were explained and insights from the models were explored. Finally, the project looked at limitations with the models and future uses. For a more in depth review on these, please visit the [Overleaf](https://www.overleaf.com/read/kshnchhyhycm#1a66e0) report.

![Process](Images/Process_Flow.png)

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

## Data Loading
* After initial setup, the data was loaded into the notebook using the pandas module for Python.
![Loading Data](Images/Loading_Data.png)
* Each of the datasets were then explored to see what fields we would need to add from them. The first dataset was yield. We examined it and created the function, fields_needed.
![Data Yield](Images/Inspect_Yield.png)
* Temperature was then examined and the columns were renamed to match the yield dataset.
![Temperature](Images/Inspect_Temperature.png)
* Precipitation was looked at and all fields were applicable so there was no adjustments that had to be made.
![Precipitation](Images/Inspect_Precipitation.png)
* Pesticides was the last set to be looked at. Columns had to be dropped as all of the element, unit, and item were the same for all fields.
![Pesticides](Images/Inspect_Pesticides.png)
* With all columns matching, the data was ready to be merged into on dataframe for ease of use.
![Merged Data](Images/Merge_Data.png)
* The data was then written a new CSV file and inspected to ensure that it was appearing how it was intended to look.
![Data Inspection](Images/Create_DF_DF Info.png)

## Exploratory Data Analysis (EDA)
* The first step in the EDA was to examine the numerical and categorical features.
  ![Numerical](Images/Numerical_Statistics.png)
  ![Categorical](Images/Categorical_Statistics.png)
* The data was then looked at through the lens of histograms. The year feature was multimodal indicating that we have more records in some years than we do in others. Yield and pesticide usage were skewed left suggesting that higher yields and pesticide usage were a more rare occurrence. Both did have a slight tail to the right indicating that there is outlier data points. Finally, the temperature histogram showed that it was skewed right indicating that warmer temperatures occur more frequently in the data.
* After viewing the data, in order to prevent outlier data points, any country that contained less than 100 records was removed.
  ![Removal](
