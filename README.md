# Wildfire Analysis Project - Mesa, AZ

## Project Overview
This project investigates the health impacts of wildfire smoke exposure on the community of Mesa, Arizona. With the increasing frequency and intensity of wildfires, understanding their effect on public health has become an urgent priority. Using data from the US Geological Survey (USGS), EPA Air Quality System (AQS), CDC, and the Arizona Department of Health Services (ADHS), I analyze trends in respiratory disease mortality, healthcare utilization, and other health indicators.

The analysis combines historical smoke exposure data with health outcome trends to provide actionable insights for Mesa’s city council and residents. The goal is to inform strategies and policies that mitigate the long-term effects of wildfire smoke on community health and the healthcare system. This project aims to highlight the importance of proactive measures to address the challenges posed by wildfire smoke in urban environments.

### Information on my assigned city:
| City | State | 2023 Estimate | 2020 Census | 2020 Density (mi²) | Location         | FIPS |
|------|-------|---------------|-------------|--------------------|----------------- |------|
| Mesa | AZ    | 511,648       | 504,258     | 3,636              | 33.40°N 111.72°W |04013 |

## Motivation and Problem Statement
Wildfire smoke represents a growing public health concern in Mesa, Arizona, where wildfires have become increasingly common. Smoke exposure is associated with serious health risks, particularly for vulnerable populations such as children, the elderly, and individuals with pre-existing respiratory conditions. Despite these risks, there is limited localized analysis of how prolonged exposure affects community health outcomes. This project addresses the need for a comprehensive understanding of the relationship between wildfire smoke and health impacts in Mesa. Specifically, we examine trends in asthma-related hospitalizations, respiratory disease mortality, and other health indicators to identify patterns and correlations.

### Research Questions
1. How, if at all, have respiratory disease mortality rates in Mesa (based on Maricopa County) been influenced by wildfire smoke exposure, and what patterns might emerge through 2050?

2. What is the relationship between smoke exposure and healthcare utilization, specifically examining:
- Trends in asthma-related inpatient hospitalizations.
- Patterns in emergency department visits for respiratory issues.

3. How has the number of respiratory-related medical procedures changed over time with increased smoke exposure? Is there a relationship between the two?

By leveraging public health datasets and advanced analysis, this project provides evidence-based insights to support Mesa’s policymakers, healthcare providers, and residents in addressing the challenges posed by wildfire smoke. 

## Licenses

**Source Data**

1. The wildfire data used in this project comes from the ["Combined Wildland Fire Datasets for the United States and Certain Territories, 1800s-Present"](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81) dataset. It is publicly available and is not subkect to copyright restrictions, but must be cited as:
   
   `Welty, J.L., and Jeffries, M.I., 2021, Combined wildland fire datasets for the United States and certain territories, 1800s-Present: U.S. Geological Survey data release, https://doi.org/10.5066/P9ZXGFY3.`

   Note: This dataset offers a "combined" file that removes duplicate entries and contains details on various types of wildland fires. For our analysis, we use the JSON file `USGS_Wildland_Fire_Combined_Dataset.json`. However, the `USGS_Wildland_Fire_Combined_Dataset.json` file is over 2 GB in size and couldn't be uploaded on GIT. In order to get that, you need to go the site mentioned above and then download the zip folder, and extract the file.

2. The air quality index (AQI) data for this project was sourced using the US Environmental Protection Agency (EPA) Air Quality Service (AQS) API. The [API documentation](https://aqs.epa.gov/aqsweb/documents/data_api.html) provides detailed information on call parameters and includes sample requests. To retrieve AQI data from monitoring stations near Mesa, AZ, we utilized the [AQS API](https://aqs.epa.gov/aqsweb/documents/data_api.html) with [Federal Information Processing Standards (FIPS)](https://www.census.gov/library/reference/code-lists/ansi.html) codes specific to Mesa's city, county, and state, which we obtained from the above relevant resources. The AQI Data lies in the public domain and is not subject to domestic copyright protection under `17 U.S.C. § 105.`

3. CDC Wonder Mortality Data
The CDC Wonder Mortality Data provides detailed information on mortality from 1999–2022. The dataset is available in the public domain and is governed by the [Public Health Service Act (42 U.S.C. 242m(d))](https://wonder.cdc.gov/datause.html).

4. Arizona Department of Health Services (ADHS) Data
Multiple datasets from the Arizona Department of Health Services were used in this project, including:
   - [Asthma-Related Inpatient Discharges and Emergency Visits (2000-2021)](https://pub.azdhs.gov/health-stats/hip/index.php?pg=asthma)
   - [Medical Procedures Data (2000-2021)](https://pub.azdhs.gov/health-stats/hip/index.php?pg=procedure)

These datasets are publicly available for non-commercial use with proper attribution to the Arizona Department of Health Services.

Note: The ADHS data is not explicitly licensed under a specific framework, but usage is restricted to non-commercial purposes with proper citation.

**Data Acquisition Code for AQI and Wildfire Proximity Calculation**

- Parts of the code in were taken as-is or with minimal changes from the [example codes](./Resources/) that were developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the [Creative Commons](https://creativecommons.org) [CC-BY license](https://creativecommons.org/licenses/by/4.0/). Revision 1.3 - August 16, 2024

All other code is licensed under the [MIT licence](./LICENSE).

## Steps to run the code
In order to run the code and get the required output, you would have to run the following steps:

- **Pre-run Information:** In order to successfully run the code, you need to clone/ download the repository and upload it to a Jupyter Environment (a place where .ipynb files can run). After this, you will need to ensure that the required Python packages are installed. Instructions to do so can be found in the individual code files.

Now that you have the entire repository cloned and environment setup, you should run the following files in order:
(*Note: Each file has any required specific instructions to run successfully*)

1. [`wildfire_data_acquisition_and_proximity.ipynb`](./Code/wildfire_data_acquisition_and_proximity.ipynb): This file contains instructions to download the wildfire data and calculate the proximity of the wildfire data from Mesa, AZ.

2. [`aqi_data_acquisition_and_processing.ipynb`](./Code/aqi_data_acquisition_and_processing.ipynb): This file contains instructions to download the aqi data from the api for the city of Mesa, AZ based on the nearby stations.

3. [`smoke_estimate.ipynb`](./Code/smoke_estimate.ipynb): This file contains instructions to calculate the smoke estimate based on the wildfire data.

4. [`Prediction_Model.ipynb`](./Code/Prediction_Model.ipynb): This file contains code to create a prediction model in order to forecast the smoke estimate for the years (2021 - 2050). Again, it is from 2021 since we did not have data for 2021-2024 in the wildfire dataset.

5. [`Data_Visualizations.ipynb`](./Code/Data_Visualizations.ipynb): This file contains code to help visualize the data.

6. [`ExtensionPlan_DataPreprocessing.ipynb`](./Code/ExtensionPlan_DataPreprocessing.ipynb): This file contains code to read the raw health and mortality data from the [Raw Data folder](./Raw%20Data/), and preprocess it to make it more usable. It outputs multiple csv files and stores it in the [Processed Data folder](./Processed%20Data/).

7. [`ExtensionPlan_DataExploration.ipynb`](./Code/ExtensionPlan_DataExploration.ipynb): This file contains code to explore the preprocessed health and mortality data, and analyzes the correlation between the smoke from wildfires with these metrics. It produces a bunch of charts and graphs that are stored in the [Output Files folder](./Output%20Files/)

8. [`ExtensionPlan_Forecasting.ipynb`](./Code/ExtensionPlan_Forecasting.ipynb): This file contains code to forecast the impact of smoke from wildfires on the different health indicators from 2021-2050. It produces a bunch of charts and graphs that are stored in the [Output Files folder](./Output%20Files/)

Additionally, you would require API access to run some of the code. Instructions for the same are available inside the code file.

## Data Files

### Raw Data Files

1. [CDC Wonder Mortality Data](./Raw%20Data/1999-2020_Mortality%20Data.txt)
This dataset contains detailed information about respiratory mortality from 1999 - 2020. It contains the following details: Year, Age Group, Gender, Deaths, Population and Crude Rate. It was originally sourced from the [CDC Wonder Mortality Website](https://wonder.cdc.gov/mcd.html) using the query criteria:
 
States:	Maricopa County, AZ (04013)

UCD - ICD-10 Codes:	J00-J98 (Diseases of the respiratory system)

Group By:	Year; Ten-Year Age Groups; Gender

2. Arizona Department of Health Services (ADHS)
The ADHS is the state's public health agency responsible for overseeing a wide range of health-related programs and data collection efforts. For my analysis, I utilize several datasets provided by ADHS to explore the healthcare impacts of wildfire smoke on respiratory illnesses in Mesa.

   - [ADHS Asthma-Related Inpatient Discharges and Emergency Visits Data](./Raw%20Data/Inpatient%20VS%20Emergency/): This dataset includes information on asthma-related inpatient discharges (2000-2021) and emergency visits (2003-2021) across Maricopa County. It contains the following fields: County, Year, Gender, Age Group, Number of Discharges, Number of Emergency Visits. The original data was sourced from the [ADHS website](https://pub.azdhs.gov/health-stats/hip/index.php?pg=asthma)
   Note: This data also contains information about whether Asthma was the first-listed diagnosis or was one of All Diagnosis.

   - [ADHS Medical Procedures Data](./Raw%20Data/By%20Procedures/): This dataset includes county-level information about the number of inpatient discharges by different medical procedures performed annually from 2000 to 2021 by procedure category. It includes procedure categories such as respiratory therapy, which can be used to understand whether wildfires are leading to an increase in respiratory procedures. The original data was sourced from the [ADHS website](https://pub.azdhs.gov/health-stats/hip/index.php?pg=procedure)

### Processed Data Files

During the execution of the project, several data files are created. Below is a list of these files and their descriptions:
(*Note: Some of these files are in a zipped folder given their massive size and github size restrictions*)

1. [`AQI_data.csv`](./Processed%20Data/AQI_data.zip): This file contains the filterd AQI Data. It is filtered for the years 1964-2024, and for the fire season May 1 - Oct 31.

2. [`complete_wildfires_with_distances.csv`](./Processed%20Data/complete_wildfires_with_distances.zip): This file contains complete record of wildfires from 1964-2020.

3. [`filtered_wildfires_with_distances.csv`](./Processed%20Data/filtered_wildfires_with_distances.csv): This file contains the distance filtered (less than or equal to 650 miles) record of wildfires from 1964-2020.

4. [`gaseous_pollutants.csv`](./Processed%20Data/gaseous_pollutants.zip): This file contains the gaseous pollutants data from the AQI API. It contains information for years 1964-2024, excluding 1964 and 1970.

5. [`particulate_pollutants.zip`](./Processed%20Data/particulate_pollutants.zip): This file contains the particulate pollutants data from the AQI API. It contains information for years 1988-2024.

6. [`smoke_estimate_with_year_aqi.csv`](./Processed%20Data/smoke_estimate_with_year_aqi.csv): This file contains the final smoke estimates based on the wildfire data for the years 1964-2020. It also contains information about the annual average aqi.

7. [`1999_2020_Mortality_Data.csv`](./Processed%20Data/1999_2020_Mortality_Data.csv): This file contains the information about the respiratory related mortality data for Maricopa county from 1999 - 2020.

8. [`2000_2015_respiratory_therapy.csv`](./Processed%20Data/2000_2015_respiratory_therapy.csv): This file contains the information about the number of respiratory therapies from 2000 - 2015 in Maricopa county.

9. [`2000_2020_respiratory_system_operations.csv`](./Processed%20Data/2000_2020_respiratory_system_operations.csv): This file contains the information about the number of operations of the respiratory system from 2000 - 2020 in Maricopa county.

10. [`2003_2021_emergency_visits_data.csv`](./Processed%20Data/2003_2021_emergency_visits_data.csv): This file contains the information about the number of emergency visits where one of the potential causes was Asthma from 2003 - 2021 in Maricopa county.

11. [`2003_2021_inpatient_discharge_data.csv`](./Processed%20Data/2003_2021_inpatient_discharge_data.csv): This file contains the information about the number of inpatient discharges where one of the potential causes was Asthma from 2003 - 2021 in Maricopa county.

### Final Output Files
The final output for this project includes a bunch of data visualizations and some reports and plans, including:

1. [**Histogram of Wildfires by Distance from Mesa, AZ (Up to 1800 Miles)**](./Output%20Files/Visualization%201.jpg): This plot shows the number of wildfires occurring at every 50-mile interval from Mesa, AZ, up to 1800 miles. It also highlights the 650-mile cut-off used for modeling wildfire impacts on the city.
   
2. [**Time Series of Total Acres Burned Per Year Within 650 Miles of Mesa, AZ**](./Output%20Files/Visualization%201.jpg): This graph displays the total acres burned per year for wildfires occurring within 650 miles of Mesa, AZ.

3. [**Time Series of Wildfire Smoke Estimates and AQI for Mesa, AZ (1964-2024)**](./Output%20Files/Visualization%203.jpg): This time series graph compares the annual wildfire smoke estimates calculated for Mesa, AZ, with the calculated yearly average EPA's Air Quality Index (AQI) data from 1964 to 2024.

4. [**Reflection**](./Data%20512_%20Part%201_%20Project%20Reflection.pdf): This file contains the reflection answering questions about the visualazations, learnings and collaborations.


## Potential Limitations and Considerations: 
The following considerations are important to consider when using this code:

- **API Rate Limits**: Although the code accounts for API rate limits, there might be a possibility that it may affect data acquistion, especially in case the API changes. 

- **Missing Data**: There is a possibility that you might not get data for a particular year. This is possible if the dataset where we are pulling from has not been updated or incase the data for that year does not exist. This causes problems since the lack of data will lead to lower accuracy of results. Specifically, we have missing data in the following:
   - Wildfire Data: I could not get data for wildfire from 2021-2024.
   - AQI Data: I could not get data for 1964 and 1970.
   - CDC Mortality Data: The suppression of death counts of 9 or fewer limits the granularity of the analysis, especially for smaller subpopulations. Additionally, county-level data does not capture city-specific trends, which could obscure localized impacts. Lastly, this data exists only from 1999 - 2020.
   - ADHS Data: Not all data is available for all years, most is available only from 2000 - 2015.

- **Smoke Estimate Calculations**: I utilized a combination of proximity, size (based on acres burned), and the type of fire in order to make an estimate of the smoke. However, in doing this, I did not consider other factors like wind, shape, and cause. It is also critical to know that my correlation with the AQI was only about 32%, indicating room for improvement in the estimation approach. This is important because every person might have a different way to calculate the estimate. 

- **Causality vs. Correlation**: The project identifies potential correlations but does not establish causality due to confounding factors like healthcare access, socioeconomic disparities, and environmental influences not accounted for in the analysis.  

- **Sparse Historical Data**: While smoke data spans several decades, healthcare datasets are available only from 2000 onward. This limits the ability to study the long-term health impacts of wildfire smoke exposure.  

- **External Factors**: I am looking at smoke data only near my county, however, there is evidence that wildfires from far away, like in California also affect the AQI of Mesa, AZ.

- **Predictive Model Limitations**: While the model explains a significant portion of the variation in the data, it is not perfect. For example, predictions for certain years or health indicators may deviate due to limited features or sparse training data. Moreover,confounding variables like pre-existing health conditions, dietary habits, or exposure to other pollutants are not considered, reducing the model's comprehensiveness.

## Conclusion

In this project, I analyzed the impact of wildfire smoke on respiratory health in Mesa, AZ, using historical data and predictive models. To calculate the smoke estimates, I considered factors such as proximity to wildfires, fire size (acres burned), and fire type to estimate the level of smoke exposure in the region. The analysis revealed a strong correlation between increased smoke exposure and higher respiratory mortality, as well as an uptick in respiratory therapy procedures and number of operations of the respiratory system and inpatient discharges for asthma. While the correlation with asthma-related emergency visits was weaker, I found that respiratory procedures showed a strong positive relationship with smoke levels.

Using the VARMAX model, I forecasted future trends in respiratory health outcomes from 2021 to 2050, predicting a significant increase in asthma-related issues, respiratory operations, and therapy procedures. This upward trend in both smoke exposure and health complications emphasizes the growing threat of wildfires to public health. The findings underscore the need for proactive public health measures, including enhanced air quality monitoring, improved healthcare infrastructure, and stronger wildfire prevention policies. By understanding these trends, we can better prepare for the long-term health impacts of wildfire smoke in Mesa and similar regions.