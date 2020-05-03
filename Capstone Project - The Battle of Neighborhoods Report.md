# Capstone Project - The Battle of Neighborhoods Report

## Introduction/Business Problem

All parents want to give their children the best possible upbringing; a balanced, healthy life full of fun and adventure. Settling in the appropriate family-friendly neighbourhood will arguably be one of the biggest decision’s parents make towards this goal. Some factors that contribute to a family-friendly neighbourhood include access to educational services such as schools, colleges, universities, museums and aquariums, and medical services such as hospitals, medical centres and pharmacies, as well as recreational and outdoor facilities such as parks and sports amenities. Proximity to these venues are also a factor, e.g. schools should be close enough for kids to get to and hospitals in reach in case of emergencies.

According to the 2016 Australian Census (Australian Bureau of Statistics), 452,422 out of 627,099 households in the City of Perth are family households, that is a staggering 72% of the Perth population. Furthermore, in the last 5 years 7084 migrants had arrived in Australia (Australian Bureau of Statistics), all these migrant families have little to no information on which suburb would be the best fit for their family's specific needs. Additionally, Perth has 355 suburbs, all unique in their own right, this makes finding the best neighbourhood particularly difficult for families that want to live there.

This report will give parents the means to make data-driven evidence-based decisions on where best to establish their family.

## Data

The list of Perth suburb names will be web scraped from a Wikipedia website using the BeautifulSoup library. The suburb data will be pulled into a pandas dataframe. Then the geospatial data (latitude and longitude values) will be retrieved using the geopy library and merged into the suburb datafame.

From here the report will leverage the Foursquare location data to explore specific venues in a calculated radius for every suburb; based on the distance to the closest neighbouring suburb. Only specific venue categories relating to the factors mentioned previously will be used as features in our dataset, these include:
* Arts & Entertainment
* College & University
* Outdoors & Recreation
* Shop & Service - Child Care Service, Pharmacy, Stationery Store
* Professional & Other Places - School, Medical Center

The number and variety of above mentioned venues categories reletive to each suburb will be used as the main features for the model.

Unfortunately, no additional external data sources such as house pricing, population and crime statistics will be used as the data is not openly available. If this data can be sourced in future projects then it will further support the accuracy of the model.

## Methodology

All the greater Perth region suburb names were web scraped from a Wikipedia page and placed in a pandas dataframe using the BeautifulSoup library. The next step was to find the geospatial data for every suburb. This data was obtained using the geopy service, and added to our suburb dataframe. Exploratory analysis showed that not all Suburbs location data could be obtained, this could be due to newly developed suburbs. These suburbs were removed from the dataset.

The resulted dataframe were then plotted on a map using folium. By looking at the data on the map it was easy to spot that several suburbs were outside of the Perth region, and thus did not apply to our report. To determine these outliers programmatically, the distance between neighbouring suburbs were calculated using the geopy distance service. This data was added to the dataframe. Next a violin chart was plotted using the distance data to further illustrate the distribution shape of the data. Suburbs with a neighbouring distance greater than 50km were removed from the dataset.

The calculated distance between neighbouring suburbs we genialised by adding the overall mean distance to the relevant suburb’s closest neighbour distance. This was to ensure the best geospatial coverage per suburb. Using the FOURSQUARE API, all venues within the pre-determined radius were used to get all relevant venues.

Next, the dataset was grouped by suburb by taking the mean of the frequency of occurrence of each venue category. Using the k-means clustering method, our dataset was clustered into 7 clusters.

## Results

Our analysis found that there are 353 suburbs in the greater Perth region. Of these only 313 suburbs had venues that were in our specific category list. These 313 suburb venues were clustered into 7 clusters. These clusters were merged with the top 5 most common and top 5 most uncommon venues within each suburb.

Each cluster has a distinct theme of venues both common and uncommon. By using this data, young families can determine what facilities and venues are important and less important to their needs. For example, families that like going to music events but do not mind living far away from a salsa club or museum might want to settle in cluster 1. Families that prefer to spend their time going to a circus or zoo, but don’t mind being a little further away from art galleries and theatres will want to live in cluster 6.

By looking at the folium map, you can easily see and distinguise where these clusters reside, and further narrow down which exact suburb might be the perfect fit.

## Discussion

There are a lot more venues for specific categories then the top 5 our report displayed. For example, there are a lot of music venues in most of the suburbs. A better way might be to add a weighting to a specific category, so that more important venues such as hospitals, medical centres’ etc carry greater value to the model.

Also, determining exact border lines for each suburb will more closely model that particular suburb. This report used an average distance as search radius, but this means some areas might not have been covered correctly especially in larger suburbs, and some areas overlapped especially in smaller suburbs giving them a higher score.

## Conclusion

In conclusion, this report illustrates that a Machine Learning model can be used to assist young families in making informed decisions on where they might want to settle their family. The city of Perth has 353 suburbs, now families can choose from 7 distinct clusters on where best to live, considering what venues are most important to them and most importantly within a short commute.

## References
Australian Bureau of Statistics, Census of Population and Housing 2016, viewed 4 April 2020, <https://www.abs.gov.au/census>

