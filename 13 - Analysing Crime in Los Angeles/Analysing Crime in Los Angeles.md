## Project Description

Los Angeles, California, attracts people from all over the world, offering lots of opportunities, not always of the good kind!

In this project, you'll serve as a data detective, supporting the Los Angeles Police Department (LAPD) in analysing crime data to guide how they should allocate resources to protect the people of their city!
![[Pasted image 20250305165144.png]]
Los Angeles, California 😎. The City of Angels. Tinseltown. The Entertainment Capital of the World!

Known for its warm weather, palm trees, sprawling coastline, and Hollywood, along with producing some of the most iconic films and songs. However, as with any highly populated city, it isn't always glamorous and there can be a large volume of crime. That's where you can help!

You have been asked to support the Los Angeles Police Department (LAPD) by analysing crime data to identify patterns in criminal behaviour. They plan to use your insights to allocate resources effectively to tackle various crimes in different areas.

### The Data
They have provided you with a single dataset to use. A summary and preview are provided below.

It is a modified version of the original data, which is publicly available from Los Angeles Open Data.
## crimes.csv

|Column|Description|
|---|---|
|`'DR_NO'`|Division of Records Number: Official file number made up of a 2-digit year, area ID, and 5 digits.|
|`'Date Rptd'`|Date reported - MM/DD/YYYY.|
|`'DATE OCC'`|Date of occurrence - MM/DD/YYYY.|
|`'TIME OCC'`|In 24-hour military time.|
|`'AREA NAME'`|The 21 Geographic Areas or Patrol Divisions are also given a name designation that references a landmark or the surrounding community that it is responsible for. For example, the 77th Street Division is located at the intersection of South Broadway and 77th Street, serving neighborhoods in South Los Angeles.|
|`'Crm Cd Desc'`|Indicates the crime committed.|
|`'Vict Age'`|Victim's age in years.|
|`'Vict Sex'`|Victim's sex: `F`: Female, `M`: Male, `X`: Unknown.|
|`'Vict Descent'`|Victim's descent:<br><br>- `A` - Other Asian<br>- `B` - Black<br>- `C` - Chinese<br>- `D` - Cambodian<br>- `F` - Filipino<br>- `G` - Guamanian<br>- `H` - Hispanic/Latin/Mexican<br>- `I` - American Indian/Alaskan Native<br>- `J` - Japanese<br>- `K` - Korean<br>- `L` - Laotian<br>- `O` - Other<br>- `P` - Pacific Islander<br>- `S` - Samoan<br>- `U` - Hawaiian<br>- `V` - Vietnamese<br>- `W` - White<br>- `X` - Unknown<br>- `Z` - Asian Indian|
|`'Weapon Desc'`|Description of the weapon used (if applicable).|
|`'Status Desc'`|Crime status.|
|`'LOCATION'`|Street address of the crime.|
```Python
# Re-run this cell
# Import required libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
crimes = pd.read_csv("crimes.csv", parse_dates=["Date Rptd", "DATE OCC"], dtype={"TIME OCC": str})
crimes.head()
```
Explore the `crimes.csv` dataset and use your findings to answer the following questions:

- Which hour has the highest frequency of crimes? Store as an integer variable called `peak_crime_hour`.
```Python
# Start coding here
# Use as many cells as you need
crimes["TIME OCC"] = crimes["TIME OCC"].astype(int)
print(crimes.dtypes)

crimes["HOUR OCC"] = crimes["TIME OCC"] // 100
crimes["HOUR OCC"].head()

peak_crime_hour = crimes["HOUR OCC"].mode().iloc[0]
```
- Which area has the largest frequency of night crimes (crimes committed between 10pm and 3:59am)? Save as a string variable called `peak_night_crime_location`
```Python
night_crimes = crimes[(crimes["TIME OCC"] <= 359) | (crimes["TIME OCC"] >= 2200)]

peak_night_crime_location = night_crimes["AREA NAME"].mode().iloc[0]
```
- Identify the number of crimes committed against victims of different age groups. Save as a pandas Series called `victim_ages`, with age group labels `"0-17"`, `"18-25"`, `"26-34"`, `"35-44"`, `"45-54"`, `"55-64"`, and `"65+"` as the index and the frequency of crimes as the values.
```Python
labels = ["0-17", "18-25", "26-34", "35-44", "45-54", "55-64", "65+"]

bins = [0, 17, 25, 34, 44, 54, 64, np.inf]

crimes["age_groups"] = pd.cut(crimes["Vict Age"],
                              bins=bins,
                              labels=labels)

victim_ages = crimes["age_groups"].value_counts()

print(victim_ages)
```