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

## References
Australian Bureau of Statistics, Census of Population and Housing 2016, viewed 4 April 2020, <https://www.abs.gov.au/census>

