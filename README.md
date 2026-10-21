## BA-780-A01-Project---Intermodal-Route-Optimization-for-Hurricane-Relief

# Summary
This repo summarizes the steps taken in a project looking to create an optimization function for U.S. rail and freight routing.

The Southern and Eastern states of the U.S. have long-since been of the highest risk stats for humanitarian crises, due to the volume of hurricanes which affect them. In this project, we look to build an optimal, intermodal, relief network for providing affected areas with necessary supplies after the natural disaster strikes. This study incorporates hurricane movement prediction based on historical storm data and optimization of U.S. freight and trucking routes. For the scope of the project, we will be looking at 9 states which have historically seen the highest volume of hurricanes, and limit relief planning to cities of a population over 100,000.

To predict how a hurricane will move after it hits land, we use historical hurricane data from NOAA, going back to 1851, which records the exact path of every major storm every six hours: where it was, how strong its winds were, and where it made landfall. We also add climate data (like ocean temperature and El Niño/La Niña patterns) to understand what kind of conditions were present when each storm formed. Using this information, we look for past hurricanes that formed in similar conditions and similar locations. By studying how those past storms moved and weakened after landfall, we can build simulations that show a range of likely paths for a new storm, instead of just one guess. This gives the humanitarian logistics team a realistic set of possible impact zones to plan around, even before the storm's final path is confirmed.

Once we have flagged a city and know the regionality of the storm, we can then determine the nearest possible city supplies can be shipped from that remains outside of the affected radius of the storm. To ship large amounts of goods, trains coming from large city hubs will be most effective. However, tracks must be inspected after a large storm, and often suffer significant maintenance delays. Thus, the train needs to bring the goods to the nearest intermodal facility that is just outside of the affected zone. At the facility, goods are moved from trains to trucks, and these trucks finish the final miles of the network.

In some cases, there might not be a need for a train. For example, if the nearest (safe to access by rail) hub to a flagged city is in Dallas, it can be assumed that since Dallas will have greater access to supplies, we can limit the network to trucks from Dallas to the city in need. However, if our example was a hurricane hitting Jackson, MS, with the Natchez hub being the nearest safely accessible hub by rail (for context, this is a hub outside of a city of 14,520 people), then we would need to get a train from a city that has enough supply to provide relief.
	
To clear up definitions, we say that a safe range for the rail component must be outside of the radius of the storm (where wind dies below 39mph should have tracks unaffected). As for the city providing relief, it must be at least half a million in population. Optimization will be defined by the minimum time it takes for supplies to reach the city in need of aid. Success will be measured by the % of optimal routes that achieve this solution within 3 days (the standard maximum time as per humanitarians).

# Motivation:
Hurricanes present a unique humanitarian logistics challenge, as communities in need of supplies can become the most difficult to reach. Transportation infrastructure can become damaged or inaccessible, requiring relief efforts to adapt quickly. This will explore how freight rail and trucking can be integrated to improve response and supply delivery.

# Data Sources:
Historical hurricane data from NOAA, which records the exact path of every major storm every six hours: where it was, how strong its winds were, and where it made landfall (https://www.nhc.noaa.gov/data/hurdat/hurdat2-1851-2025-02272026.txt).
(Size: 55,605 x 13 | 1 txt file | 5.1 MB)

Ocean temperature (https://climatedataguide.ucar.edu/sites/default/files/2022-03/amo_monthly.txt)  
(Size: 1,815 x 3 | 1 txt file | 42.7 KB)

El Niño/La Niña patterns (https://www.cpc.ncep.noaa.gov/data/indices/oni.ascii.txt),
(Size: 919 x 3 | 1 txt file | 21.7 KB)

Track Routes (https://geodata.bts.gov/datasets/197e48526e284a28bfddf9100553019f_0/explore?location=30.043250%2C-93.142549%2C7) (Size: 84,659 x 34 | Files: 1 | 22 MB)

Intermodal Facilities
(https://data-usdot.opendata.arcgis.com/datasets/usdot::intermodal-freight-facilities-rail-tofc-cofc/explore?location=34.889176%2C-85.157432%2C6) (Size: 242 x 15 | Files: 1 | 28.4 KB)

Census Data
(https://www.census.gov/data/tables/time-series/demo/popest/2020s-total-cities-and-towns.html) (Size: 1960 x 10 | Files: 1 | 153.2 KB)
Annual Estimates of the Resident Population for Incorporated Places of 20,000 or More, Ranked by July 1, 2025 Population: April 1, 2020 to July 1, 2025 (SUB-IP-EST2025-ANNRNK)

# Contributors
- Alexander Renaud (Manager)
- Julian LaLonde
- Alejandra Hurtado Burghardt
- Chao-Tsun (Sonic) Hsu
