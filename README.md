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
  ![Removal](Images/Drop_Countries.png)
* After preforming this step, the data was dropped from 28248 down to 26297 records.
* The next step was to begin using visualizations to understand the data better. A copy of the data was created so that a correlation matrix could be used. From the matrix, a few weak negative correlations were discovered. There was nothing discovered in the data though that would suggest a linear relationship.
  ![Correlation](Images/SNS_Heatmap.png)
* After seeing the correlation matrix, another set of histograms was created to see if the skews had changed since removing countries with less than 100 records.
  ![Distribution](Images/Distribution.png)
* At the same time, scatter plots were created to see how each crop faired against temperature, pesticides, and precipitation.
  ![Scatter Plots](Images/Scatter_Yield_Item.png)
* From the images we have obtained, we can see that for our average yield, we have a right tail indicating that high yields are less common than average yields. The average precipitation seems to have a fairly normal skew while pesticides values tend to be on the lower end. Looking at the scatter plots, we see variability between all of our crops and yields. Average temperature shows that some crops have a wider variability such as wheat and rice whereas cassava and sweet potatoes are more clustered. This indicates that temperature ranges are variable depending on the crop but no significant linear relationship exists. Pesticide usuage shows that most of our yield comes from lower pesticide usage. Finally, with precipitation we still do not have a distinct linear relationship. It is noted that on precipitation, we have a larger cluster towarsd the bottom. This can indicate that crops have a threshold of precipitation when it comes to determining the yield.
* Pairplots were created to try and help get a better sense of where the data was at. The first group of charts shows the year, yield, and average temperature with crop distribution overlaid. We can see that the values are bimodal indicating different peaks in the various crops. When observing, Year vs Yield, we can see a more concentrated level of data in the late 2000's meaning that we crop yields are either getting better or we have more data. Due to there being a non discernible upward or downward trend, the inference is that we have more data. Average temperature seems to be remaining near the same across the years whereas pesticide usage has increased. When comparing yield to environmental factors, we again do not see a strong correlation between temperatures and crop yield. As shown in the correlation matrix, high pesticide usage does not show a clear indication of higher yield. One interesting point is when looking at the variance in soybeans and sweet potatoes suggesting they are more susceptible to environmental factors
  ![Pairplots](Images/Pair_Plot.png)
* It was at this point, that it was needed to see what the yield distribution looked like by crops. A boxplot was created that offered some interesting insights. It waas seen that potatoes, cassava, and sweet potatoes had the most variance whereas sorghum, wheat, and soybeans had the least variability. Yams and cassava were the only two crops that did not have outlier data.
  ![Boxplot](Images/Box_Whisker.png)
* To provide a more clear image, the different countries were split up into 5 groups. Each of these groups were then plotted to show the yield by average precipitation and yield by pesticide useage. The logic for this step was to see if there was a theme with precipitation and to see if pesticide use really increased the crop yield. There was not a clear relationship between a higher yield and either lower or higher precipitation. It is inferred that this has to do with countries producing the crops that fit best for that region. Again, a clear connection to higher pesticide use and higher yields was not present.
  ![Yield and Precipitation](Images/Group_0_1.png)
  ![Yield and Precipitation2](Images/Group_2_3.png)
  ![Yield and Precipitation3](Images/Group_4_5.png)
  ![Pesticide](Images/Pest_0_1.png)
  ![Pesticide2](Images/Pest_2_3.png)
  ![Pesticide3](Images/Pest_4_5.png)
* While the breakdown by groups suggested that pesticide use did not always provide higher yields, two plots were created. The first was each crops yield and pesticide use. Logarithmic scaling was completed on this to get a clear image. The second plot, showed the total yield for each crop and the total pesticides used on an interactive scatter plot. Overall, most of the data is shown to be on the lower end of the pesticide use. There are some outlier features however, the highest yielding crops sit on the lower end of the scale for pesticide use.
  ![Log Scale](Images/Log_Scale.png)
  ![Interactive](Images/Yield_Pesticide_Crop.png)
* The final EDA visualization created was the range of temperatures each crop yield was collected in. This range of temperatures showed those that are less susceptible to environmental factors and those that might be more sensitive.
  ![Temperature Range](Images/Temp_Yield_Crop.png)
* The key insights gained in this part of the project suggests that there is not a linear relationship between the features in the data. The data all falls within a normal distribution indicating that no further transformation was needed. The outliers in the data were left in as they all fall within a normal range. The importance of the EDA helped decide the direction that was taken in the model building process.

## Model Building
