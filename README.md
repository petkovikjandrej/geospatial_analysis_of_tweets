# Geospatial Analysis of #LongCovid Tweets

This document outlines the steps taken to analyze and visualize the geographical distribution of #LongCovid tweets, thereby understanding the global or regional prevalence of long COVID. The steps involved include data import, cleaning, location extraction, geocoding, geospatial analysis, and data visualization.

## Step 1: Data Import and Cleaning
The dataset was initially imported from a CSV file into a pandas DataFrame. Any rows with missing tweet data were subsequently removed to ensure the quality of the analysis.

## Step 2: Tweet Cleaning
A text cleaning function was applied to the 'Tweets' column to standardize and clean the tweet content. This involved converting all text to lowercase, removing URLs, eliminating usernames (represented by the '@' symbol), and removing non-alphanumeric characters. Additionally, the function discarded common English 'stop words', which are words that do not typically contain meaningful information, such as "the", "is", and "in".

## Step 3: Location Extraction
Named Entity Recognition (NER), a feature of the SpaCy library, was employed to extract geographical entities ('GPE') from the cleaned tweet text. This operation entailed tokenizing the tweet text and applying the SpaCy NER model to identify and extract location references. These identified locations were stored in a new column named 'Locations'.

## Step 4: Geocoding
The following step involved converting the extracted location references into corresponding geographical coordinates. For this purpose, the geopy library's Nominatim geocoder was utilized. It identified the longitude and latitude for each location mentioned in the 'Locations' column. The geographical coordinates obtained were stored as shapely Point objects in a new column labeled 'Geometry'.

## Step 5: Geospatial Analysis
The geographical coordinates of each tweet enabled the performance of a geospatial analysis. The data was converted into a GeoDataFrame, a special DataFrame format designed to handle geographical data.

## Step 6: Data Visualization
The geographical distribution of the tweets was visualized using the GeoDataFrame. The geopandas library was used to create a global map, and the tweet locations were plotted on this map as individual points.

## Step 7: Cluster Analysis
Finally, to identify 'hotspots' of tweet activity, a DBSCAN (Density-Based Spatial Clustering of Applications with Noise) clustering algorithm was applied to the geographical data. This algorithm groups points that are close to each other, according to a given distance measure and a minimum number of points. Points that do not belong to a cluster are marked as outliers. The resulting clusters were visualized on the map using different colors.

By following these steps, a comprehensive geographical analysis of #LongCovid tweets was achieved, providing a visual representation of the global or regional prevalence of long COVID.
