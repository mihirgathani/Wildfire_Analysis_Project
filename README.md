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

Additionally, you would require API access to run some of the code. Instructions for the same are available inside the code file.

## Data Files
During the execution of the project, several data files are created. Below is a list of these files and their descriptions:
(*Note: Some of these files are in a zipped folder given their massive size and github size restrictions*)

1. [`AQI_data.csv`](./Processed%20Data/AQI_data.zip): This file contains the filterd AQI Data. It is filtered for the years 1964-2024, and for the fire season May 1 - Oct 31.

2. [`complete_wildfires_with_distances.csv`](./Processed%20Data/complete_wildfires_with_distances.zip): This file contains complete record of wildfires from 1964-2020.

3. [`filtered_wildfires_with_distances.csv`](./Processed%20Data/filtered_wildfires_with_distances.csv): This file contains the distance filtered (less than or equal to 650 miles) record of wildfires from 1964-2020.

4. [`gaseous_pollutants.csv`](./Processed%20Data/gaseous_pollutants.zip): This file contains the gaseous pollutants data from the AQI API. It contains information for years 1964-2024, excluding 1964 and 1970.

5. [`particulate_pollutants.zip`](./Processed%20Data/particulate_pollutants.zip): This file contains the particulate pollutants data from the AQI API. It contains information for years 1988-2024.

6. [`smoke_estimate_with_year_aqi.csv`](./Processed%20Data/smoke_estimate_with_year_aqi.csv): This file contains the final smoke estimates based on the wildfire data for the years 1964-2020. It also contains information about the annual average aqi.


## Final Output
The final output for this part of the project is 3 Data Visualizations and a PDF with the reflection as follows:

1. [**Histogram of Wildfires by Distance from Mesa, AZ (Up to 1800 Miles)**](./Output%20Files/Visualization%201.jpg): This plot shows the number of wildfires occurring at every 50-mile interval from Mesa, AZ, up to 1800 miles. It also highlights the 650-mile cut-off used for modeling wildfire impacts on the city.
   
2. [**Time Series of Total Acres Burned Per Year Within 650 Miles of Mesa, AZ**](./Output%20Files/Visualization%201.jpg): This graph displays the total acres burned per year for wildfires occurring within 650 miles of Mesa, AZ.

3. [**Time Series of Wildfire Smoke Estimates and AQI for Mesa, AZ (1964-2024)**](./Output%20Files/Visualization%203.jpg): This time series graph compares the annual wildfire smoke estimates calculated for Mesa, AZ, with the calculated yearly average EPA's Air Quality Index (AQI) data from 1964 to 2024. 

4. [**Reflection**](./Data%20512_%20Part%201_%20Project%20Reflection.pdf): This file contains the reflection answering questions about the visualazations, learnings and collaborations.


## Potential Considerations: 
The following considerations are important to consider when using this code:

- **API Rate Limits**: Although the code accounts for API rate limits, there might be a possibility that it may affect data acquistion, especially in case the API changes. 

- **Missing Data**: There is a possibility that you might not get data for a particular year. This is possible if the dataset where we are pulling from has not been updated or incase the data for that year does not exist. I faced this situation for the AQI data, as I could not get data for 1964 and 1970. Also, I could not get data for wildfire from 2021-2024

- **Smoke Estimate Calculations**: I utilized a combination of proximity, size (based on acres burned), and the type of fire in order to make an estimate of the smoke. However, in doing this, I did not consider other factors like wind, shape, and cause. It is also critical to know that my correlation with the AQI was only about 32%. This is important because every person might have a different way to calculate the estimate. 
