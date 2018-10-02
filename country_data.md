

```python
import pandas as pd
df = pd.read_csv('countries_of_the_world.csv')
```

Data from https://www.kaggle.com/fernandol/countries-of-the-world

## Assess

#### Change columns names with spaces and capitalizations
#### Columns with commas instead of decimal place: 
- Pop. Density (per sq. mi.)
- Coastline (coast/area ratio)
- Net migration
- Infant mortality (per 1000 births)
- Literacy (%)
- Phones (per 1000)
- Arable (%)
- Crops (%)
- Other (%)
- Birthrate
- Deathrate
- Agriculture
- Industry
- Service

#### Change datatypes of columns with new values

### Change Column Names


```python
#changes column names
old_names = ('Country', 'Region', 'Population', 'Area (sq. mi.)', 'Pop. Density (per sq. mi.)', 'Coastline (coast/area ratio)', 'Net migration', 'Infant mortality (per 1000 births)', 'GDP ($ per capita)', 'Literacy (%)', 'Phones (per 1000)', 'Arable (%)', 'Crops (%)', 'Other (%)', 'Climate', 'Birthrate', 'Deathrate', 'Agriculture', 'Industry', 'Service')
new_names = ('country', 'region', 'population', 'area_sqm', 'pop_density_sqm', 'coastline_ratio', 'net_migration', 'infant_mortality_per_thousand', 'gdp', 'literacy', 'phones_per_thousand', 'arable', 'crops', 'other', 'climate', 'birthrate', 'deathrate', 'agriculture', 'industry', 'service')
df.rename(columns=dict(zip(old_names, new_names)), inplace=True)
```

### Change Commas and Datatypes


```python
#changes commas to periods and datatype to float
df['pop_density_sqm'] = df['pop_density_sqm'].str.replace(',','.').astype(float)
df['coastline_ratio'] = df['coastline_ratio'].str.replace(',','.').astype(float)
df['net_migration'] = df['net_migration'].str.replace(',','.').astype(float)
df['infant_mortality_per_thousand'] = df['infant_mortality_per_thousand'].str.replace(',','.').astype(float)
df['literacy'] = df['literacy'].str.replace(',','.').astype(float)
df['phones_per_thousand'] = df['phones_per_thousand'].str.replace(',','.').astype(float)
df['arable'] = df['arable'].str.replace(',','.').astype(float)
df['crops'] = df['crops'].str.replace(',','.').astype(float)
df['other'] = df['other'].str.replace(',','.').astype(float)
df['birthrate'] = df['birthrate'].str.replace(',','.').astype(float)
df['deathrate'] = df['deathrate'].str.replace(',','.').astype(float)
df['agriculture'] = df['agriculture'].str.replace(',','.').astype(float)
df['industry'] = df['industry'].str.replace(',','.').astype(float)
df['service'] = df['service'].str.replace(',','.').astype(float)
```

```python
#adds column of net population change
df['net_pop_change'] = df.birthrate - df.deathrate
```

### References
- https://www.kaggle.com/fernandol/countries-of-the-world
- https://en.wikipedia.org/wiki/Birth_rate
- https://stackoverflow.com/questions/38101009/changing-multiple-column-names-but-not-all-of-them-panda-python
- https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.groupby.html
- https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.sort_values.html
