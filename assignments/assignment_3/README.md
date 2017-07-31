# Assignment 3: Data (Pre)processing

## Task

  1. Read the entire dataset of Danish housing sales data (DHSD), see Assignment 2, into a Pandas `DataFrame`. Use the `read_csv` function from the `pandas` module.

  ```python
  import pandas as pd

  housing df = pd.read_csv(path_to_csv)
  ```
  2. Convert all sales dates in the DHSD into proper `datetime` objects.
  3. Compute the average price per square meter for the years 1992 and 2016 respectively for the city centers of Copenhagen (zip code 1050-1049), Odense (zip code 5000), Aarhus (zip code 8000), and Aalborg (zip code 9000). Create two new `DataFrame`s, one for the year 1992 and one for the year 2016, which contain the respective zip codes and the average price per square meter corresponding to the aforementioned cities. Let the `DataFrame`s be sorted by ascending prices.
  4. Create, with the help of the `pandas` module, four new CSV files containing the sales data for the year 1992 for the city centers of Copenhagen (zip code 1050-1049), Odense (zip code 5000), Aarhus (zip code 8000), and Aalborg (zip code 9000).
  5. Add two new columns to each of the new CSV files from the previous step. The columns will store the latitude and longitude of each address. Make use of a geocoding service of your liking to receive the corresponding values for the addresses of interest.


## Hints

  1. In case your data is distributed over multiple CSV files, read each CSV file into a `DataFrame` and concatenate those `DataFrame`s into a single one, see http://pandas.pydata.org/pandas-docs/stable/merging.html.
  2. For geocoding you might want to have a look on the `geopy` module http://geopy.readthedocs.io/en/latest/, which wraps many services, such as Openstreetmaps, Google, Bing, etc.

