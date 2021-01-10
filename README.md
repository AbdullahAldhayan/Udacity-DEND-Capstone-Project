# Udacity-DEND-Capstone-Project
This is the capstone project of Data Engineering Nanodegree.

#### Project Summary
--describe your project at a high level--<br>
**I94 Immigration data and city temperature data will be used to create a database that is optimized to query and analyze immigration events. An ETL pipeline is to be build with these to data sources to create the database. Finally, the database will be used to access immigration behaviour to location temperatures.**

The project follows the follow steps:
* Step 1: Scope the Project and Gather Data
* Step 2: Explore and Assess the Data
* Step 3: Define the Data Model
* Step 4: Run ETL to Model the Data
* Step 5: Complete Project Write Up

#### Describe and Gather Data 
Describe the data sets you're using. Where did it come from? What type of information is included?<br> 
I used 3 different engine:<br>
* Koalas
* Pandas
* Pyspark
<br>The reason behind these engins is to show the optimization on reading and gathering Data.<br>
But almost the whole project has been done by **Koalas**.

#### Define the Data Model

Fact Table `fact_table`
Columns:

i94yr = 4 digit year.<br>
i94mon = numeric month.<br>
i94cit = 3 digit code of origin city.<br>
i94port = 3 character code of destination USA city.<br>
i94mode = 1 digit travel code.<br>
i94visa = reason for immigration.<br>
AverageTemperature = average temperature of destination city.<br>



Dimension Table `i94_table` - I94 immigration data columns:

i94yr = 4 digit year<br>
i94mon = numeric month<br>
i94cit = 3 digit code of origin city<br>
i94port = 3 character code of destination USA city<br>
arrdate = arrival date in the USA<br>
i94mode = 1 digit travel code<br>
depdate = departure date from the USA<br>
i94visa = reason for immigration<br>


Dimension Table `temp_table` - temperature data columns:

AverageTemperature = average temperature<br>
City = city name<br>
Country = country name<br>
Latitude= latitude<br>
Longitude = longitude<br>

Dimension Table `time_table` -  any columns related to time.
<br>columns:

i94yr = 4 digit year<br>
i94mon = numeric month<br>
i94port = 3 character code of destination USA city<br>
arrdate = arrival date in the USA<br>
depdate = departure date from the USA<br>

#### Notice:
Some cells throw **WARNING**, it is from the engine itself so that is not an error. If the execution of all cells doesn't work well.. I could provide something to prove that all cells have been executed well without any error.<br>
This is the warning when I run `kdf.info()`:
<br>/opt/conda/lib/python3.6/site-packages/databricks/koalas/generic.py:406: FutureWarning: `get_dtype_counts` has been deprecated and will be removed in a future version. For DataFrames use `.dtypes.value_counts()`
  FutureWarning,
<br> If `kdf.info()` is not executed well, kindly make the cell `markdown` or do not run it.
<br> I use this `kdf.info()` to show how many nulls in the data, names of the columns and the datatype of each column.

#### Answering on the scenarios.
* The data was increased by 100x.<br>
I used Apache Spark to do all the processing data and create the model. The reason for this is because Spark can scale a lot of data and the library spark.sql has many tools to transform data. So, it is not problem if the data is increased while using Spark.<br>
* The data populates a dashboard that must be updated on a daily basis by 7am every day.<br>
Use Airflow which is atuomated, has a dashboard feature and supports alerts (sending emails if a falure happens).<br>
* The database needed to be accessed by 100+ people.<br>
The more people accessing the database the more CPU resources you need to get a fast experience. By using a distributed database you can improve your replications and partitioning to get faster query results for each user.<br>

#### Tools of the projects:
As I talked in the first part of the capstone that I used 3 tools:
* Koalas
* Pandas
* Pyspark
these are my favourite tools that I'm familiar to deal Data with.
Otherwise, after many execution and data wrangling in this project I dicovered to cancel **pandas** due to execution time.
<br>For example, let's see time execution of gathering SAS Data (has `3096313` records) .
* `Koalas` : CPU times: user 464 ms, sys: 632 ms, total: 1.1 s, Wall time: 3min 3s.
* `Pandas` : CPU times: user 2min 21s, sys: 40.7 s, total: 3min 2s, Wall time: 21min 11s.
* `Spark` : CPU times: user 58.2 ms, sys: 3.19 ms, total: 61.4 ms, Wall time: 16.5 s.

Additionally, In Exploratory and Wrangling.
<br> I did these steps by `Koalas` because I prefer using Pandas and I'm used to deal with Data by Pandas.
<br> So, almost the whole project has been done by **Koalas** because has optimization in gathering and simplicity.
