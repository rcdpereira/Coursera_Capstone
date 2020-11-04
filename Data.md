# 2. DATA ACQUISITION AND PRELIMINARY ANALYSIS

## 2.1 Getting data to support business decision

By webscraping [finder.com](https://www.finder.com/uk/uk-diet-trends), several tables are created with information about UK diet trends in 2020. The research conducted by finder points that the vegan market is growing, and therefore seems to be a good investment.

The first table shows the percent of the population and the type of diet they're in.

Table 1: The UK's current diet
| DIET                  | PERCENT |
|:----                  | -------:|
|Total vegetarian	      |  6.55%  |
|Total pescatarian      |	 4.10%  |
|Total vegan	           |  2.10%  |
|Total meat free	       | 12.75%  |
|Not following any diet | 87.25%  |

The second table presents the intentions of the UK citizen's to adopt some type of diet by the end of 2020. It's visible there is a tendency of more people starting to adopt a vegetarian or a vegan diet (those values are almost doubled!).

Table 2: The UK’s diet intentions by the end of 2020
| DIET                   | PERCENT |
| :----                  | -------:|
| Total vegetarian	      | 11.35%  |
| Total pescatarian      |	 7.35%  |
| Total vegan	           |  4.15%  |
| Total meat free	       | 22.85%  |
| Not following any diet | 77.15%  |

The changes to be seen in 2020 considering the percentage applied to the total population can be seen in table 3.

Table 3: Specific diet changes over 2020
| Type of diet	    | Current population |	People who intend to follow this diet |	Population by end of 2020	| % change |
| :---             |               ---: |                                  ---: |                      ---: |     ---: |
| No-specific diet	|           45721918 |                              -5292738	|                  40429180	|  -11.60% |
| Vegan	           |            1100470	|                               1074269	|                   2174739	|   97.60% |
| Vegetarian	      |            3432419	|                               2515361	|                   5947780	|   73.30% |
| Pescatarian	     |            2148537	|                               1703109	|                   3851646	|   79.30% |

Also, it is possible to see that new generations tend to be more adept to veganism and vegetarianism.

Table 4: Which generations are ditching the meat?
| Generation	       | Percent ditching meat |
|:---               |                  ---: |
| Postmillennial	   |                13.89% |
| Millennials	      |                14.74% |
|	Generation X	     |                13.79% |
|	Boomers	          |                10.57% |
|	Silent generation |	                8.86% |

And some gender differences can also be observed.

Table 5: Are there gender differences when it comes to diets?

| Intention	               | Female |	  Male |
|:---                      |   ---: |   ---: |
|	Planning to go meat free	|  8.84%	| 11.44% |
|	Already meat free	       | 14.57%	| 10.82% |

About the cost of becoming vegetarian or vegan, it's not uncommon to hear the phrase "I don't have money for that, it's very expensive". Well, for vegan foods this is slightly true, but the difference is not that much as one may think of. Take a look at table 6.

Table 6: Yearly cost of each diet per person

| Diet	                | Cost per year |
|:---                  |          ---: |
|	Vegan Diet           |	       £2,073 |
|	Normal Balanced Diet |	       £2,002 |
|	Pescatarian Diet     |	       £1,973 |
|	Vegetarian Diet      |	       £1,545 |

The above data show that an increasing number of the UK population is changing their diet to a more plant-based one, and that new generations tend to be more adherent to this lifestyle. Also, the last table breaks the concept that going vegan is more expensive, which can be used to induce more people to try it.

The important thing as a business owner is to offer plenty of options so the transition to a vegan or vegetarian diet is not difficult for the people wanting to pursue that.

## 2.2 Selecting and Cleaning Data

We'll use the Foursquare API to retrieve the locations of the vegan/vegetarian restaurants in London. With these locations, we can determine the best place to open a new restaurant. Several criteria can be considered, as distance to city centre, proximity to other types of restaurants, close to business centres, etc.

A geolocator service is used to retrieve the coordinates of London, and the search query in the Foursquare API looks for restaurants in a radius of 22 km, which will comprehend the total area of the Greater London (~1572 km2). Applying the acquired latitude and longitude, the API returns 50 venues, which is a limit imposed by [Foursquare API](https://developer.foursquare.com/docs/api-reference/venues/search/).

As the Foursquare search will return anything with the vegan / vegetarian words, a data evaluation shall be realised to gurantee that all the venues returned are indeed vegetarian / vegan restaurants. The evaluation of the results returns the following venues categories:

> Vegetarian / Vegan Restaurant: 36
> 
> Bakery: 2
>
> Food Truck: 2
> 
> School: 1
>
> Farmers Market: 1
>
> Organic Grocery: 1
> 
> Café: 1
>
> Tea Room: 1
> 
> Food Stand: 1
> 
> Fried Chicken Joint: 1 (Ouch! It's a crime for this to be listed here.)
> 
> Building: 1
> 
> Donut Shop: 1
> 
> Market: 1

It's clear that some venues shall be dropped from the acquired data, so some cleaning is performed and only the places with the category "Vegetarian / Vegan Restaurant", "Food Truck" and "Food Stand" are kept, since although having different categories, these types of places have the same business: serving prepared vegetarian / vegan food.
Now the total amount of places are 39, which are plotted in a map of London. And even if the idea of a vegan donut seems so good, it won't replace a nice meal. So, yeah, that goes out as well.

Figure 1: Vegetarian / Vegan Restaurants in London
![Vegan Restaurants in London](https://raw.githubusercontent.com/rcdpereira/Coursera_Capstone/main/Vegan_Restaurants_London_Map.png)

For the last part of the data acquisition, we want to know where are the gastronomic areas in London. These regions naturally attracts customers, being considered good spots for opening a new restaurant. But again, we encounter the limitations of the Foursquare API, returning only 50 venues. For the vegetarian / vegan restaurants, they covered a wide region, so let's check in the map where those normal restaurants are located.

Figure 2: Top 50 restaurants in London accordig to Foursquare
![Restaurants in London](https://raw.githubusercontent.com/rcdpereira/Coursera_Capstone/main/Restaurants_London_Map.png)

So, it's clear that these restaurants are concentrated in a small region, mostly at north of the River Thames, around Covent Garden district. For now, this will be enough for our basic study. A more detailed investigation can leverage evaluating several districts, and the restaurants in them, to achieve a more refined result.

With this data in hands, we'll move to the next section, where some analysis will be conducted to try and find the best place to open a new vegan restaurant.
