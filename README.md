# data-512-homework_1

## Introduction
The goal of this project is to construct, analyze, and publish a dataset of monthly article traffic for a subset of pages from Wikimedia, focusing on articles related to rare diseases. The dataset includes desktop and mobile traffic data sourced from the Wikimedia Analytics API. The project follows best practices for open scientific research, emphasizing reproducibility. It involves data acquisition, time series analysis, and visualizations to examine traffic trends on Wikipedia pages.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.   

The dataset created in this project is based on the data from Wikimedia, sourced through the Wikimedia Analytics API. All data provided by the Wikimedia Foundation is available under the Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0) and GNU Free Documentation License (GFDL) licenses. All the data sourced through the Wikimedia REST API is licensed under the CC-BY-SA 3.0 and GFDL licenses.

Some of the code in this project follows this code [template](https://drive.google.com/file/d/1fYTIX79t9jk-Jske8IwysV-rbRkD4_dc/view), which is licensed under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/). 

### Wikimedia Foundation Terms of Use 
The Wikimedia Foundation's terms of use can be found [here](https://foundation.wikimedia.org/wiki/Policy:Terms_of_Use).

### Source of Rare Disease List
The subset of Wikipedia articles used in this project is based on a list of rare diseases from the [National Organization for Rare Disorders (NORD)](https://rarediseases.org/).

## Output Data Files

**Datasets** <a name="output-data-files"></a>
These files contain monthly pageview counts for rare disease-related articles on Wikipedia, categorized by access type (mobile, desktop) and cumulative totals. These are saved as JSON files and stored in `data/jsons/` directory.

1. **Monthly Mobile Access:**
This file stores the total monthly pageviews for mobile access by summing pageviews from both mobile apps and mobile web traffic.    
File Name: rare-disease_monthly_mobile_201507-202409.json

2. **Monthly Desktop Access:**
This file stores the total monthly pageviews for desktop access, which is based on a single request from the API.    
File Name: rare-disease_monthly_dekstop_201507-202409.json

3. **Monthly Cumulative Data:**
This file stores the cumulative pageviews by summing both mobile and desktop pageviews for each article.    
File Name: rare-disease_monthly_cumulative_201507-202409.json

**Data Schema**    
All these JSON files follow the same schema. The only difference is the `views` field, depending on the access.
- `project` (string): The Wikipedia project from which the data was collected. In this project, all data is collected under the "en.wikipedia" for the English Wikipedia.
- `article` (string): The name of the article. Spaces in article titles are replaced with underscores.
- `granularity` (string): The time interval for the data. In this project, all data is collected at a "monthly" granularity.
- `timestamp` (string): A timestamp representing the month for which the pageviews were counted with this format YYYYMMDD00.
- `agent` (string): The type of user agent, which is "user" in this project, representing human.
- `views` (integer): The number of pageviews for the article in the given month. This value changes depending on the access type:
    - For mobile access files: Represents the sum of mobile app and mobile web views.
    - For desktop access files: Represents the desktop views.
    - For cumulative files: Represents the sum of mobile and desktop views for that article.

**Considerations**  
It is important to note that there may be specific months in which no data is available for certain articles.

**Analysis Output**    
These files are the analysis showing the graphs of each analysis. These are saved as PNG files and stored in the `data/pngs/` directory.

1. **Maximum Average and Minimum Average Page Requests:**
A time series showing the articles with the highest and lowest average page requests for both mobile and desktop access.    
File name: max_min_average.png

2. **Top 10 Peak Page Views:**
A time series of the top 10 article pages by peak page views (both desktop and mobile).    
File name: top_10_articles.png

3. **Fewest Months of Data:**
A time series displaying articles with the fewest months of available data, showing 10 articles for both desktop and mobile access.    
File name: fewest_months.png

## Steps
Steps to Run the Code   
1. **Data Acquisition:** `get_monthly_access.ipynb`    
This notebook is used for the first step of the project, which involves collecting monthly access data from the Wikipedia API.
Locate the cell that defines configurations (at the top of the notebook). Update the constants as needed for your data acquisition, such as the date range and any other relevant parameters.
Select "Run All".
The notebook will query the pageview data for the specified articles, generate the datasets, and store the output files as described in the [Output Data Files](#output-data-files) section.


2. **Data Analysis:** `visual_analysis.ipynb`   
This notebook is designed for the second step of the project, which involves visual analysis of the collected data.
Change the first cell to configure any necessary settings, such as file paths or parameters for the visualizations.
After configuring, run all cells in the notebook.
The notebook will generate various visualizations based on the data and save the figures to the specified output directory.