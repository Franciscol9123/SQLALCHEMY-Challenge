# SurfsUp

The `SurfsUp` directory contains `climate.ipynb` Jupyter Notebook, the `app.py` Python script, and a `Resources` folder which contains the `hawaii.sqlite` database, `hawaii_measurements.csv` and `hawaii_stations.csv`.

## Analyze and Explore the Climate Data
Climate analysis and data exploration was done on the `hawaii.sqlite` database. The `climate.ipynb` Jupyter Notebook was created to perform precipitation analysis and station analysis. The `app.py` Python script was created to design a climate app with a Flask API with 5 routes with JSON lists of climate information. 

**Precipitation Analysis**
* ORM queries were done to get the date and prcp data for the previous 12 months.

* Pandas DataFrame was created using the queried data.
  |           | precipitation |
  | ----------|:-------------:|
  |2016-08-23	| 0.00          |
  |2016-08-23	| NaN           |
  |2016-08-23	| 1.79          |
  |2016-08-23	| 0.05          |
  |2016-08-23	| 0.15          |
  |...	      | ...           |

* The results were plotted by using the Pandas plot method.

	![image](https://user-images.githubusercontent.com/120543690/221071429-98f38337-cdee-4bfc-908a-b159c9794587.png)

* A summary statistics table was printed for the precipitation data for the previous 12 months.

	|               | precipitation |
  | ------------- |:-------------:|
  |count	        | 2021.000000   |
  |mean 	        | 0.177279      |
  |std  	        | 0.461190      |
  |min  	        | 0.000000      |
  |25%            |	0.000000      |
  |50%	          | 0.020000      |
  |75%	          | 0.130000      |
  |max	          | 6.700000      |

**Station Analysis**
* All stations and its number of counts were listed in descending order.
```
[('USC00519281', 2772),
 ('USC00519397', 2724),
 ('USC00513117', 2709),
 ('USC00519523', 2669),
 ('USC00516128', 2612),
 ('USC00514830', 2202),
 ('USC00511918', 1979),
 ('USC00517948', 1372),
 ('USC00518838', 511)]
 ```
* The minimum, average and maximum temperature data were queried for the most active station (by id)

* The last 12 months of temperature observation data for the most active station were queried
  |      | tobs |
  | ---- |:----:|
  |0     | 77.0 |
  |1	 | 77.0 |
  |2	 | 80.0 |
  |3     | 80.0 |
  |4	 | 75.0 | 
  |...   | ...  |

* The results were binned and plotted in histogram using Pandas plot histogram method. 
	![image](https://user-images.githubusercontent.com/120543690/221074591-79dc85f6-102a-40aa-8bd2-75f80ab42ce6.png)

## Design Climate API
A Climate API was created using Flask. The following 5 routes are available routes created using Flask:
1. `/`(Homepage)
- Start at the homepage.
- List all the available routes.

2. `/api/v1.0/precipitation` (Precipitation)
- Convert the query results from your precipitation analysis (i.e. retrieve only the last 12 months of data) to a dictionary using date as the key and prcp as the value.
- Return the JSON representation of your dictionary.

3. `/api/v1.0/stations` (Stations)
- Return a JSON list of stations from the dataset.
