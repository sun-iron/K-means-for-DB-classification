# Automated Database classification and Analysis System Using K-Means Clustering
This article is for reaearch paper by sunpark (sunpark@soongsil.ac.kr) titled "A Design and Implementation of Automated Classification and Analysis System Using K-Means Clustering for Transition of Database to Micro-Services-Architecture"

The paper is http://dx.doi.org/10.7840/kics.2024.49.9.1306

## 1. What is K-Means DB Clustering Automation
This study propose a method to apply K-Means clustering to automate the classification of medium- to large-sized databases based on various attributes.
Legacy databases are large and complex. To transition to cloud native, they must be changed to domain-related small DBs. However, this process is expensive and has a high failure rate because it is analyzed and designed by DB experts rather than business logic.

I proposed a solution using a clustering algorithm and studied how to handle this problem.

## 2. What is K-Means Clustering
K-Means is a simple algorithm for performing cluster analysis. For more information, see Wikipedia.
> k-means clustering is a method of vector quantization, originally from signal processing, that aims to partition n observations into k clusters in which each observation belongs to the cluster with the nearest mean (cluster centers or cluster centroid), serving as a prototype of the cluster. This results in a partitioning of the data space into Voronoi cells. (`wikipedia.com` [https://en.wikipedia.org/wiki/K-means_clustering])

## 3. Converting Time-series data to coordinate data
Statistical data generated in IT systems are data that accumulate over time. It is difficult to perform clustering with such data.
I used the center of gravity of a triangle to change time series data into coordinate data.
The center of gravity of a triangle is the intersection of line segments that have a distance to three vertices, and has a center value that matches the characteristics of the time series graph.
This center of gravity was used to create one element with the x-axis as time and the y-axis as frequency.

## 4. Generating log-scale data from real data
There are three types of target DB tables.
These are service DB, statistics DB, and management DB.
The service DB shows a high data usage frequency throughout the day.
On the other hand, the statistics DB has the characteristic of operating in the early morning hours.
Lastly, the management DB has the characteristic of having a very low usage frequency during working hours.

![image](https://github.com/user-attachments/assets/31831ca0-0d3a-47cb-84a6-6ee7f48177c0)


From these characteristics, the frequency of use of the service DB and the frequency of use of the management DB are far apart. So, I applied log scale to transform the data so that it is expressed as adjacent data while maintaining the characteristics.

## 5. Comparison of results between human and automated analysis
![image](https://github.com/user-attachments/assets/7a2cf357-d0f5-4b9c-bdc5-f71c1ee54111)

