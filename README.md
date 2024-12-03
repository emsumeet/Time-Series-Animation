# Population Data Visualization with Animated Chart

This project processes and visualizes global population data, focusing on key insights such as the top 10 most populous countries over time. The final result includes a bar chart animation that dynamically displays population rankings from 1950 onward.

Features
1.Data Cleaning:
Filters out countries with missing ISO3 codes.
Scales population data to millions for readability.
Extracts relevant columns and saves a cleaned dataset.

2.Static Visualization:
A horizontal bar chart visualizing the top 10 most populous countries in 1950.

3.Animated Visualization:
An animation showing population changes across decades.
Highlights dynamic trends in the population rankings of countries.


Data
Source: UN population data (assumed to be provided in CSV format: un-country-data.csv).
Fields used:
ISO3_code: Country code.
Location: Country name.
Time: Year of data observation.
TPopulation1Jan: Population on January 1 (scaled to millions).
TPopulation1July: Population on July 1 (scaled to millions).


Technologies Used
Python: Core programming language.
Pandas: For data processing and manipulation.
Matplotlib: For creating static and animated visualizations.
Matplotlib Animation: For generating time-based animations.

