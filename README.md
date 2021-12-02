## NYC Park Maintenance

### What is the project about?

We want to test how often NYC parks receives maintenance depending on where they are built, what borough they are in, and that show when the park was built, what borough it is in, and when the last time they received maintenance.

### What is this significant?

Parks are so valuable and enrich the lives of so many New Yorkers. There’s nothing like being in a beautiful park that is very well taken care of. It is important to solve this problem because there are parks in New York that are not properly taken care of and they are so important to our mental health to be in a nice, peaceful, and clean environment. From kids to adults, everyone needs nice quality parks accessible to them, no matter where in New York City they live.

### Links:
- [Open NYC Data](https://data.cityofnewyork.us/City-Government/ARCHIVED-Parks-Properties/k2ya-ucmv)
- [Open NYC Data](https://data.cityofnewyork.us/Recreation/Open-Space-Parks-/g84h-jbjm)
- [NYC Council Data](https://council.nyc.gov/data/parks-in-nyc/)

### Import Libraries:
```markdown
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import seaborn as sns
import geoplotlib as geoplot
```
### User Inputs:
```markdown
#Get input and output file names:
inFile = input('Enter input file name: ')
inFile2 = input('Enter input file name: ')
inFile3 = input('Enter input file name: ')
outFile = input('Enter output file name: ')
```
### Reading in files to the DataFrame:
```markdown
#Reading selected file to df:
df = pd.csv_read(inFile)
```
