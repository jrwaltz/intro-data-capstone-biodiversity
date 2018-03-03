Completed Code in the Learning Environment

1/15

import codecademylib
import pandas as pd
import matplotlib as plt

species = pd.read_csv("species_info.csv")

print species.head()

species_count = species["scientific_name"].nunique()

print(species_count)

species_type = species["category"].unique()

conservation_statuses = species["conservation_status"].unique()

species.fillna('No Intervention', inplace = True)

conservation_counts_fixed = conservation_counts = species.groupby("conservation_status").scientific_name .nunique().reset_index()

print(conservation_counts)

2/15

import codecademylib
import pandas as pd
import matplotlib as plt

species = pd.read_csv("species_info.csv")

print species.head()

species_count = species["scientific_name"].nunique()

print(species_count)

species_type = species["category"].unique()

conservation_statuses = species["conservation_status"].unique()

species.fillna('No Intervention', inplace = True)

conservation_counts_fixed = conservation_counts = species.groupby("conservation_status").scientific_name .nunique().reset_index()

print(conservation_counts)

3/15

import codecademylib
import pandas as pd
import matplotlib as plt

species = pd.read_csv("species_info.csv")

print species.head()

species_count = species["scientific_name"].nunique()

print(species_count)

species_type = species["category"].unique()

conservation_statuses = species["conservation_status"].unique()

species.fillna('No Intervention', inplace = True)

conservation_counts_fixed = conservation_counts = species.groupby("conservation_status").scientific_name .nunique().reset_index()

print(conservation_counts)

4/15

import codecademylib
import pandas as pd
import matplotlib as plt

species = pd.read_csv("species_info.csv")

print species.head()

species_count = species["scientific_name"].nunique()

print(species_count)

species_type = species["category"].unique()

conservation_statuses = species["conservation_status"].unique()

species.fillna('No Intervention', inplace = True)

conservation_counts_fixed = conservation_counts = species.groupby("conservation_status").scientific_name .nunique().reset_index()

print(conservation_counts)

5/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt

species = pd.read_csv('species_info.csv')

species.fillna('No Intervention', inplace = True)

protection_counts = species.groupby('conservation_status')\
    .scientific_name.nunique().reset_index()\
    .sort_values(by='scientific_name')

plt.figure(figsize=(10,4))
ax = plt.subplot()
plt.bar(range(len(protection_counts)),protection_counts.scientific_name.values)
ax.set_xticks(range(len(protection_counts)))
ax.set_xticklabels(protection_counts.conservation_status.values)
plt.ylabel('Number of Species')
plt.title('Conservation Status by Species')
labels = [e.get_text() for e in ax.get_xticklabels()]
plt.show()

6/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt

species = pd.read_csv('species_info.csv')

species.fillna('No Intervention', inplace = True)

species['is_protected'] = species.conservation_status != 'No Intervention'

category_counts = species.groupby(['category', 'is_protected']).scientific_name.nunique().reset_index()

category_pivot = category_counts.pivot(columns='is_protected',
                      index='category',
                      values='scientific_name')\
                      .reset_index()
  
category_pivot.columns = ['category', 'not_protected', 'protected']

category_pivot['percent_protected'] = category_pivot.protected / (category_pivot.protected + category_pivot.not_protected)

print category_pivot

7/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt

species = pd.read_csv('species_info.csv')

species.fillna('No Intervention', inplace = True)

species['is_protected'] = species.conservation_status != 'No Intervention'

category_counts = species.groupby(['category', 'is_protected']).scientific_name.nunique().reset_index()

category_pivot = category_counts.pivot(columns='is_protected',
                      index='category',
                      values='scientific_name')\
                      .reset_index()
  
category_pivot.columns = ['category', 'not_protected', 'protected']

category_pivot['percent_protected'] = category_pivot.protected / (category_pivot.protected + category_pivot.not_protected)

print category_pivot

8/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt
from scipy.stats import chi2_contingency

contingency = [[73,5],
              [4216,46]]

pval = chi2_contingency(contingency)[1]
print(pval)
contingency_reptile_mammal = [[30, 146],
                              [5, 73]]

pval_reptile_mammal = chi2_contingency(contingency_reptile_mammal)[1]
#print(pval_reptile_mammal)

9/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt
from scipy.stats import chi2_contingency

contingency = [[73,5],
              [4216,46]]

pval = chi2_contingency(contingency)[1]
print(pval)
contingency_reptile_mammal = [[30, 146],
                              [5, 73]]

pval_reptile_mammal = chi2_contingency(contingency_reptile_mammal)[1]
#print(pval_reptile_mammal)

10/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt

species = pd.read_csv('species_info.csv')
species.fillna('No Intervention', inplace = True)
species['is_protected'] = species.conservation_status != 'No Intervention'

observations = pd.read_csv('observations.csv')

species['is_sheep'] = species.common_names.apply(lambda x: 'Sheep' in x)

species_is_sheep = species[species.is_sheep]

sheep_species = species[(species.is_sheep) & (species.category == 'Mammal')]

sheep_observations = observations.merge(sheep_species)

print sheep_observations.head()

obs_by_park = sheep_observations.groupby('park_name').observations.sum().reset_index()

print obs_by_park

11/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt

species = pd.read_csv('species_info.csv')
species.fillna('No Intervention', inplace = True)
species['is_protected'] = species.conservation_status != 'No Intervention'

observations = pd.read_csv('observations.csv')

species['is_sheep'] = species.common_names.apply(lambda x: 'Sheep' in x)

species_is_sheep = species[species.is_sheep]

sheep_species = species[(species.is_sheep) & (species.category == 'Mammal')]

sheep_observations = observations.merge(sheep_species)

print sheep_observations.head()

obs_by_park = sheep_observations.groupby('park_name').observations.sum().reset_index()

print obs_by_park

12/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt

species = pd.read_csv('species_info.csv')
species.fillna('No Intervention', inplace = True)
species['is_protected'] = species.conservation_status != 'No Intervention'

observations = pd.read_csv('observations.csv')

species['is_sheep'] = species.common_names.apply(lambda x: 'Sheep' in x)

species_is_sheep = species[species.is_sheep]

sheep_species = species[(species.is_sheep) & (species.category == 'Mammal')]

sheep_observations = observations.merge(sheep_species)

print sheep_observations.head()

obs_by_park = sheep_observations.groupby('park_name').observations.sum().reset_index()

print obs_by_park

13/15

import codecademylib
import pandas as pd
from matplotlib import pyplot as plt

species = pd.read_csv('species_info.csv')
species['is_sheep'] = species.common_names.apply(lambda x: 'Sheep' in x)
sheep_species = species[(species.is_sheep) & (species.category == 'Mammal')]

observations = pd.read_csv('observations.csv')

sheep_observations = observations.merge(sheep_species)

obs_by_park = sheep_observations.groupby('park_name').observations.sum().reset_index()

plt.figure(figsize=(16, 4))
ax = plt.subplot()
plt.bar(range(len(obs_by_park)),
        obs_by_park.observations.values)
ax.set_xticks(range(len(obs_by_park)))
ax.set_xticklabels(obs_by_park.park_name.values)
plt.ylabel('Number of Observations')
plt.title('Observations of Sheep per Week')
plt.show()

14/15

baseline = 15

minimum_detectable_effect = 100*5/15

sample_size_per_variant = 510

yellowstone_weeks_observing = 1

bryce_weeks_observing = 2

15/15

baseline = 15

minimum_detectable_effect = 100*5/15

sample_size_per_variant = 510

yellowstone_weeks_observing = 1

bryce_weeks_observing = 2
