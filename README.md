The BFDB Extended is a collection geometries and interaction energies from several Sherrill Group publications.

Please cite the following publication if you use this dataset: "The BioFragment Database (BFDb): An open-data platform for computational chemistry analysis of noncovalent interactions" J. Chem. Phys. 147, 161727 (2017) 10.1063/1.5001028

How to Use
The pickle file can be used through the following python example:

```py
import requests
import numpy as np
import pandas as pd
from pprint import pprint as pp

# After downloading the file, you can load it as follows:
df = pd.read_pickle("./bfdb_ext.pkl")
pp(df.columns.tolist())
print(df[['system_id', 'db', 'B3LYP/aug-cc-pVTZ/unCP']])
df['Geometry'] = df['Geometry'].apply(lambda x: np.array(x))
df['monAs'] = df['monAs'].apply(lambda x: np.array(x))
df['monBs'] = df['monBs'].apply(lambda x: np.array(x))
df['geom_A'] = df.apply(lambda x: x['Geometry'][x['monAs']], axis=1)
df['geom_B'] = df.apply(lambda x: x['Geometry'][x['monBs']], axis=1)
print(df['geom_A'].iloc[0])
print(df['geom_B'].iloc[0])
```
