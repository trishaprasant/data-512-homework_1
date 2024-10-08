# Rare Disease Article Traffic Analysis

## Goal

This project analyzes Wikipedia traffic data for articles related to rare diseases. Using the Wikimedia Analytics API data, I acquired monthly pageview counts for these articles from July 2015 to September 2024. The analysis includes:
- Identifying articles with the highest and lowest average page views
- Finding articles with the peak page views
- Analyzing articles with the fewest months of data

## Data Source

The data is acquired from the Wikimedia Analytics API's Pageviews API, which provides access to traffic data for articles across the English Wikipedia. For more information on the API, please see the [Wikimedia Pageviews API documentation](https://www.mediawiki.org/wiki/Analytics#Pageviews).

The subset of rare diseases was selected using a database maintained by the [National Organization of Rare Diseases (NORD)](https://rarediseases.org). The `rare-disease_cleaned.AUG.2024.csv` contains a list of the selected rare diseases and their corresponding Wikipedia articles.

### License
This code example was developed by Trisha Prasant for use in DATA 512, a course in the UW MS Data Science degree program. The code is available under the MIT License. See the `LICENSE` file for more details.

The dataset used in this project is derived from the Wikimedia API, which is subject to the [Wikimedia Foundation Terms of Use](https://foundation.wikimedia.org/wiki/Terms_of_Use). The data retrieved through the API is available for reuse under the terms of use of this license, provided attribution is given.

## Data Files
The code to measure article traffic from the Wikimedia Analytics API can be found in `hw1_data_analysis.ipynb`. As mentioned in the code, parts of it were taken from and inspired by Dr. David McDonald's example of accessing page view data using the Wikimedia REST API. You can also find this code in `wp_article_views_example.ipynb`.

The code generates the following files:
- **`rare-disease_monthly_mobile_201501-202404.json`**: Contains monthly mobile page views for each article.
- **`rare-disease_monthly_desktop_201501-202404.json`**: Contains monthly desktop pageviews for each article.
- **`rare-disease_monthly_cumulative_201501-202404.json`**: Contains the sum of mobile and desktop views for each article.
- **`max_min_avg.png`**: A graph showing the maximum and minimum average pageviews for mobile and desktop.
- **`top_10_peak_page_views.png`**: A graph showing the top 10 articles by peak page views for mobile and desktop.
- **`fewest_months_data.png`**: A graph showing the ten articles with the fewest months of available data for mobile and desktop.

### Data Schema

The generated JSON files with mobile and desktop page views have the following schema:

| Column    | Type | Interpretation |
| -------- | ------- | ------- |
| **`article`**  | string | The rare disease article title.
| **`date`** | string | The date in YYYY-MM format. |
| **`views`**    | integer | The number of page views. |

## Known Issues and Considerations

- Some articles may have missing data for certain months, especially in the early years (2015-2017).
- The accuracy of the data depends on the consistency and availability of pageview data from the Wikimedia API.
- The `mobile` data includes both mobile web and mobile app traffic, combined in the analysis.
