# Assignment 3: Data (Pre)processing

## Task

  1. Read the entire dataset of Danish housing sales data, see Assignment 2, into a Pandas `DataFrame`. Use the `read_csv` function from the `pandas` module.

  ```python
  import pandas as pd

  housing df = pd.read_csv(path_to_csv)
  ```
  * Geocode the the entire dataset of Danish housing sales data, see Assignment 2. Add two new columns to the `DataFrame`, one for latitude (`lat`) and one for longitude (`lon`) coordinates per address. Do the geocoding with help of the OSM dataset stored in a file as discussed in class. Save that `DataFrame` to a CSV file with the help of pandas' 
  * Convert all sales dates in the dataset into proper `datetime` objects, see http://pandas.pydata.org/pandas-docs/stable/generated/pandas.to_datetime.html.
  * Compute the average price per square meter for the years 1992 and 2016 respectively for the city centers of Copenhagen (zip code 1050-1049), Odense (zip code 5000), Aarhus (zip code 8000), and Aalborg (zip code 9000). Create two new `DataFrame`s, one for the year 1992 and one for the year 2016, which contain the respective zip codes and the average price per square meter corresponding to the aforementioned cities. Let the `DataFrame`s be sorted by ascending prices.
  * Create, with the help of the `pandas` module, four new CSV files containing the sales data for the year 1992 for the city centers of Copenhagen (zip code 1050-1049), Odense (zip code 5000), Aarhus (zip code 8000), and Aalborg (zip code 9000).
  * Create a 2-dimensional scatter plot, which contains a dot for each location in the dataset of Danish housing sales data. Plot the longitude values on the x- axis and plot the latitude values on the y-axis.
  * Use the following function, which computes the Haversine Distance (https://en.wikipedia.org/wiki/Haversine_formula) to compute an array of distances (`distances`) for each for each location in the dataset of Danish housing sales data to the city center of Roskilde (lat=55.65, lon=12.083333).

  ```python
  def haversine_distance(origin, destination):

      lat_orig, lon_orig = origin
      lat_dest, lon_dest = destination
      radius = 6371

      dlat = math.radians(lat_dest-lat_orig)
      dlon = math.radians(lon_dest-lon_orig)
      a = (math.sin(dlat / 2) * math.sin(dlat / 2) + math.cos(math.radians(lat_orig)) 
          * math.cos(math.radians(lat_dest)) * math.sin(dlon / 2) * math.sin(dlon / 2))
      c = 2 * math.atan2(math.sqrt(a), math.sqrt(1 - a))
      d = radius * c

      return d
  ```

  Create another satter plot as in the task above, but use the computed dsitances as color values, see keyword arguments `c=` and `cmap=` in the documentation of the scatter function `plt.scatter?`.


## Hand-in Procedure

  * Provide all code, documentation, and solution text for this assignment in a repository on Github.
  * Create a release of your project on Github, see https://help.github.com/articles/creating-releases/
  * Create a Markdown (.md) file called `README.md` in the root of your project.
    - That `README.md` contains a first section with your solutions to all tasks.
  * Hand-in a link to the **release** on Moodle, see https://help.github.com/articles/linking-to-releases/
  * Hand-in at latest on Sunday 24th Sept. 2017 at 23:59. You will upload a link to the **release** on Moodle (one link per group).

