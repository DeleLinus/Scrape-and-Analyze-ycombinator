
# Author
Ayanwoye Gideon Ayandele – ayanwoyegideon@gmail.com

## Table of Contents
1. [ Project Description. ](#desc)
2. [ Web Scraping ](#scraper)
3. [ Data Wrangling and Exploration (`EDA_ycombinator.ipynb`) ](#eda)
4. [ Analysis Summary ](#ana_sum)
5. [ Details of Charts ](#charts)
8. [ References ](#ref)

<a name="desc"></a>
# March, 2022 - Scraping, Cleaning and Analyzing  Companies Information as listed on Ycombinator 

The motivation for this project is to achieve an end-to-end data engineering project by collecting, wrangling, cleaning and analysing/visualizing  companies' information listed on https://ycombinator.com/companies.

The project main objectives were:
1. Perform web scraping
2. Do data wrangling (gathering, assessing and cleaning) on the crawled data.
3. Store, analyze, and visualize the wrangled data.
4. Reporting on:
    * data wrangling efforts.
    * data analysis and visualizations

The project was divided into two parts:
1. [ Web Scraping ](#scraper)
2. [ Data Wrangling and Exploration (`EDA_ycombinator.ipynb`) ](#eda)

<a name="scraper"></a>
## Web Scraping (`ycombinator_scraper.ipynb`/`ycombinator_scraper.py`)
The dependencies and third party libraries for the scraper include:
* `Selenium`
* `BeautifulSoup`
* `requests`
* `numpy`       
* `pandas`

1. I scraped data pertaining to all 1000 companies listed on https://ycombinator.com/companies, which are:
- The listed company names
- The company's ycombinator page url 
- The company location
- The company short description (Description head)
 using the selenium library since the page is dynamic.
 ![Screenshot (218)](https://user-images.githubusercontent.com/58152694/162059499-b617988b-89d7-44fd-8429-6a1dae01b1e1.png)


 2. I then went through the scraped company's ycombinator page url using requests library since the pages are static, and grab many other informations (company's description, year founded, team size, company page url, social media urls, management details) as they appear for each company.
![Screenshot (217)](https://user-images.githubusercontent.com/58152694/162059535-208d9fe7-9baf-425a-9572-fd140ad4a201.png)


3. At the end, I will create a CSV file in the following format:

| Company_Name  | Company_Page_URL  | Company_Location |  Description_Head | Website  | Description| Founded| Team_Size| Linkedin_Profile| Twitter_Profile| Facebook_Profile| Crunchbase_Profile| Active_Founder1| Active_Founder2| Active_Founder3
| ------------- | ------------- | -------- |------------- | ------------- | -------- |------------- | -------- |------------- | ------------- | -------- |------------- | -------- |------------- | ------------- |
Airbnb|	https://www.ycombinator.com/companies/airbnb|	San Francisco, CA, US,|	Book accommodations around the world.|  http://airbnb.com | Founded in August of 2008 and based in San Fra... | 2008 | 5000 | https://www.linkedin.com/company/airbnb/ | https://twitter.com/Airbnb | https://www.facebook.com/airbnb/ | https://www.crunchbase.com/organization/airbnb | Nathan Blecharczyk\nNone\nhttps://twitter.com/... | Brian Chesky\nNone\nhttps://twitter.com/bchesky\n | Joe Gebbia\nNone\nhttps://twitter.com/jgebbia\n,

4. The scraper runs for approxiamtely 1.5 minute with multithreading and approximately 7 minutes when NOT multithreaded


<a name="eda"></a>
## Data Wrangling and Exploration (`EDA_ycombinator.ipynb`)
The dependencies and third party libraries for the scraper include:
* `numpy`       
* `pandas`
* `matplotlib`
* `seaborn`

The summary from the data assessment and cleaning were that:
* There were cases of duplicated company names (Nash, Atlas and Streak) which appeared twice but had their characteristics to be different from the duplicate, it was then concluded to neglect the issue.
2. Missing data were represented with NaN which would not be imputed or removed as they represented charateristics that were not for the particular company
3. New variable showing the `Country_Of_Origin` of the company was extracted from the `Company_Location` column and, another variable `Number_Of_Founders` was also extracted from `Active_Founder1` through to `Active_Founder6`


<a name="ana_sum"></a>
## Analysis Summary
Using both Univariate and Bivariate analysis:

* The most represented country of all is the USA which counts 654 of the total 1000 companies. It is followed by India, Canada, UK, Nigeria and Indonesia

* It could be seen that the more recent a company is founded, the likely it is to be funded/listed by ycombinator
* The Team size distribution is highly right-skewed with a really long tail that it was very difficult to view the plot. I had to resolve into binning of size 100 and also set the plot's x_axis limit to 3000. Most teamsize is between 2-4

* Most number of founders is 2 followed by 1 and 3
* No interesting relationship between country of origin and team size, number of founder and year founded. Also
* There is a weak, negative linear correlation between Number_Of_Founder and team size.

<a name="charts"></a>
## Details of Charts

* **Most represented country (Country_Of_Origin) on ycombinator**:  The most represented country of all is the USA which counts 654 of the total 1000 companies. It is followed by India, Canada, UK, Nigeria and Indonesia:
![Screenshot (209)](https://user-images.githubusercontent.com/58152694/162048750-00f8470d-b87c-4d59-8107-8726787e2f98.png)

* **The distribution of the Year founded of the companies**: It could be seen that the more recent a company is founded, the likely it is to be funded/listed by ycombinator:
![Screenshot (210)](https://user-images.githubusercontent.com/58152694/162048768-6e0af57e-685a-4470-9bc7-76eeb74b3594.png)


* **The distribution of the team size of the companies**: The Team size distribution is highly right-skewed with a really long tail that it was very difficult to view the plot. I had to resolve into binning of size 100 and also set the plot's x_axis limit to 3000. Most teamsize is between 2-4:
![Screenshot (211)](https://user-images.githubusercontent.com/58152694/162048776-5f40000b-8d1a-4d9f-aef4-c6660550a9e0.png)


* **The distribution of the Number_Of_Founder of the companies**: Most number of founders is 2 followed by 1 and 3:
![Screenshot (212)](https://user-images.githubusercontent.com/58152694/162048790-e0d539a7-105f-42a7-8783-d68db6f0230e.png)


There is no interesting relationship between country of origin and team size, number of founder and year founded. Also there is a weak, negative linear correlation between Number_Of_Founder and team size.

* **The relationship between Country_Of_Origin, and Year founded.**:
![Screenshot (213)](https://user-images.githubusercontent.com/58152694/162048795-56fa391a-59a9-45a5-aeb0-b58417b1069d.png)


* **The relationship between Country_Of_Origin, and team size**:
![Screenshot (214)](https://user-images.githubusercontent.com/58152694/162048817-2078862e-ea41-4b7f-b596-3c902892ff0f.png)

  
* **The relationship between Country_Of_Origin, and Number_Of_Founder**: 
![Screenshot (215)](https://user-images.githubusercontent.com/58152694/162048821-4445097f-71f1-4931-9b38-392bcb4a63f8.png)

* **The relationship between Number_Of_Founder, and team size**:
![Screenshot (216)](https://user-images.githubusercontent.com/58152694/162048824-d4c60575-6590-4018-a8cd-81daf584d855.png)


<a name="ref"></a>
## References
- [ycombinator](https://ycombinator.com/companies)
- [How to make infinite scrolling with selenium](https://www.youtube.com/watch?v=qhJ_gMB772U)
