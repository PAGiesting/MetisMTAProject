# PAG Metis NYC Spring 2020 Project 1

### Locating Hospital-Barren Areas in NYC

Team members: **Paul Giesting, Erik Janer, Rajkumar Katta, Natalie Paley, Nicole Semerano**

In this project, we used MTA station locations and ridership to explore the density of hospitals in NYC, looking for areas where hospitals are most distant from MTA stations, and using ridership as a proxy for population.

It turns out that Rockaway and southeast Brooklyn are far and away the least densely served areas with hospitals. One fairly high-ridership station in Brooklyn, Euclid Ave, has no hospital within 2 miles... a fairly long way in NYC traffic.

This project is in the form of a series of Jupyter Notebooks and depends on data from

* New York MTA weekly ridership data. Each of these is a 27 MB file. We pulled four months of data, November to February 2020. (March 2020 data is a wee bit skewed...)
* NYC Open Data on station locations.
* Homeland Infrastructure Foundation Level Data on hospital locations, which can be cut down by county to NYC hospitals.

The steps we took:

* Extracted the station and hospital locations and used the geopy distance function to find their straight-line map distances. (Pulling walking or driving distances from an API was beyond the scope of this project.) Code files:
  * Hospital_Data-PAG
  * LocatorCode
* Pulled and cleaned the hundreds of MB of turnstile data to clean up duplicate entries and match up stations with multiple names. Code file:
  * raj_project_turnstile_v3.1
* Created a lookup table to translate from the distance file station names to the turnstile file station names by outputting a side-by-side list in alphabetical order and cleaning it station by station in a spreadsheet app.
* Created a linked database of station names, average daily ridership, and distance to the nearest hospital. Code file:
  * PAG_turnstile_distance_linker-debug
* Plotted those data and saw a triangular distribution (StationHospitalPlot). Stations at the top edge of the triangle would be the ones of most concern, mixing high ridership / population with longer distances to the nearest hospital. Code file:
  * Project1_Visualization-PAG
* Examined stations at the "toe" of the triangle (LeastServedAreaPlot), the stations with the highest distance to a hospital regardless of ridership, and noticed they were all in Rockaway (the very furthest) and southeast Brooklyn (all those greater than 1.8 miles from a hospital) on the A, J, and C lines.

My role in the project:

* Wrote and debugged all the geographic code.
* Created the lookup table.
* Wrote and debugged the code that linked the averaged turnstile data and distance data using the lookup table.
* Did most of the final interpretation on the "toe" stations.