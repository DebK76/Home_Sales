# Home_Sales

**1. Overview:**

In this challenge, we harnessed the power of Apache Spark to glean essential insights from home sales data. Our Spark journey encompassed various tasks, including creating temporary views, partitioning data, caching and uncaching temporary tables, and validating the uncaching process.

One pivotal aspect of our mission involved leveraging the temporary view multiple times for querying and structuring data through SparkSQL. However, a critical facet of the assignment revolved around a fundamental comparison: runtime performance between cached data and Parquet data. This comparison assumes paramount importance, especially when dealing with colossal datasets, as the manner in which data is stored and retrieved can significantly impact efficiency.

Caching, in its essence, involves the storage of a dataframe, residing primarily in memory. On the other hand, Parquet entails the creation of "parqueted" files, a process carried out on disk. Notably, columnar storage, as exemplified by Parquet, organizes data by columns rather than rows (in contrast to formats like .csv). This design enables the system to swiftly access the values of a specific column without the need to scan through unrelated data, which proves invaluable when executing tailored queries. (This prompts the question: why isn't columnar data the universal norm, given its efficiency? The answer lies in the fact that it's less visually intuitive than traditional relational, row-based tables, and its resource-saving benefits become truly pronounced only with exceptionally large datasets.)

It's worth highlighting that when data is initially read (prior to caching, when it's not yet in memory), the reading process from a Parquet file can outpace less efficient file formats. This initial advantage arises from the inherent advantages of columnar storage, including enhanced data compression capabilities. However, once data is cached in memory, subsequent reads generally outperform reading from any disk-based storage, including Parquet.

