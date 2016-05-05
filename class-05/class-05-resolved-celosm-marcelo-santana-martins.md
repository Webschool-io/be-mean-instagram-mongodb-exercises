#MongoDB - Aula 05 - Exercícios
autor: Marcelo Santana Martins

##1. Importar as collections restaurantes e pokemons
```
marcelo@marcelo-VirtualBox:~$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file /home/marcelo/Downloads/restaurantes.json
2015-11-22T19:24:49.614-0200	connected to: 127.0.0.1
2015-11-22T19:24:49.614-0200	dropping: be-mean.restaurantes
2015-11-22T19:24:52.170-0200	imported 25359 documents

marcelo@marcelo-VirtualBox:~$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file /home/marcelo/Downloads/pokemons.json
2015-11-22T19:24:10.672-0200	connected to: 127.0.0.1
2015-11-22T19:24:10.672-0200	dropping: be-mean.pokemons
2015-11-22T19:24:10.695-0200	imported 610 documents
```

##2. Distinct por `cuisine` na restaurantes
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Hamburgers",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
  "Chicken",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Italian",
  "Steak",
  "Polish",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "German",
  "French",
  "Pizza/Italian",
  "Mexican",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Seafood",
  "Hotdogs",
  "Greek",
  "Not Listed/Not Applicable",
  "African",
  "Japanese",
  "Indian",
  "Armenian",
  "Thai",
  "Chinese/Cuban",
  "Mediterranean",
  "Korean",
  "Bottled beverages, including water, sodas, juices, etc.",
  "Russian",
  "Eastern European",
  "Middle Eastern",
  "Asian",
  "Ethiopian",
  "Vegetarian",
  "Barbecue",
  "Egyptian",
  "English",
  "Sandwiches",
  "Portuguese",
  "Indonesian",
  "Chinese/Japanese",
  "Filipino",
  "Juice, Smoothies, Fruit Salads",
  "Brazilian",
  "Afghan",
  "Vietnamese/Cambodian/Malaysia",
  "CafÃ©/Coffee/Tea",
  "Soups & Sandwiches",
  "Tapas",
  "Moroccan",
  "Pakistani",
  "Peruvian",
  "Bangladeshi",
  "Czech",
  "Salads",
  "Creole",
  "Fruits/Vegetables",
  "Iranian",
  "Cajun",
  "Scandinavian",
  "Polynesian",
  "Soups",
  "Australian",
  "Hotdogs/Pretzels",
  "Southwestern",
  "Nuts/Confectionary",
  "Hawaiian",
  "Creole/Cajun",
  "Californian",
  "Chilean"
]
```

##3. Distinct por `types` na pokemons
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
[
  "normal",
  "fire",
  "water",
  "bug",
  "flying",
  "poison",
  "electric",
  "steel",
  "ice",
  "ghost",
  "fighting",
  "psychic",
  "grass",
  "ground",
  "fairy",
  "rock",
  "dark",
  "dragon"
]
```

##4. As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5)
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.restaurantes.find().limit(5).skip(5 * 0)
{
  "_id": ObjectId("565232a2ae40b9067be5f832"),
  "address": {
    "building": "1007",
    "coord": [
      -73.856077,
      40.848447
    ],
    "street": "Morris Park Ave",
    "zipcode": "10462"
  },
  "borough": "Bronx",
  "cuisine": "Bakery",
  "grades": [
    {
      "date": ISODate("2014-03-03T00:00:00Z"),
      "grade": "A",
      "score": 2
    },
    {
      "date": ISODate("2013-09-11T00:00:00Z"),
      "grade": "A",
      "score": 6
    },
    {
      "date": ISODate("2013-01-24T00:00:00Z"),
      "grade": "A",
      "score": 10
    },
    {
      "date": ISODate("2011-11-23T00:00:00Z"),
      "grade": "A",
      "score": 9
    },
    {
      "date": ISODate("2011-03-10T00:00:00Z"),
      "grade": "B",
      "score": 14
    }
  ],
  "name": "Morris Park Bake Shop",
  "restaurant_id": "30075445"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f833"),
  "address": {
    "building": "469",
    "coord": [
      -73.961704,
      40.662942
    ],
    "street": "Flatbush Avenue",
    "zipcode": "11225"
  },
  "borough": "Brooklyn",
  "cuisine": "Hamburgers",
  "grades": [
    {
      "date": ISODate("2014-12-30T00:00:00Z"),
      "grade": "A",
      "score": 8
    },
    {
      "date": ISODate("2014-07-01T00:00:00Z"),
      "grade": "B",
      "score": 23
    },
    {
      "date": ISODate("2013-04-30T00:00:00Z"),
      "grade": "A",
      "score": 12
    },
    {
      "date": ISODate("2012-05-08T00:00:00Z"),
      "grade": "A",
      "score": 12
    }
  ],
  "name": "Wendy'S",
  "restaurant_id": "30112340"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f834"),
  "address": {
    "building": "351",
    "coord": [
      -73.98513559999999,
      40.7676919
    ],
    "street": "West   57 Street",
    "zipcode": "10019"
  },
  "borough": "Manhattan",
  "cuisine": "Irish",
  "grades": [
    {
      "date": ISODate("2014-09-06T00:00:00Z"),
      "grade": "A",
      "score": 2
    },
    {
      "date": ISODate("2013-07-22T00:00:00Z"),
      "grade": "A",
      "score": 11
    },
    {
      "date": ISODate("2012-07-31T00:00:00Z"),
      "grade": "A",
      "score": 12
    },
    {
      "date": ISODate("2011-12-29T00:00:00Z"),
      "grade": "A",
      "score": 12
    }
  ],
  "name": "Dj Reynolds Pub And Restaurant",
  "restaurant_id": "30191841"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f835"),
  "address": {
    "building": "2780",
    "coord": [
      -73.98241999999999,
      40.579505
    ],
    "street": "Stillwell Avenue",
    "zipcode": "11224"
  },
  "borough": "Brooklyn",
  "cuisine": "American ",
  "grades": [
    {
      "date": ISODate("2014-06-10T00:00:00Z"),
      "grade": "A",
      "score": 5
    },
    {
      "date": ISODate("2013-06-05T00:00:00Z"),
      "grade": "A",
      "score": 7
    },
    {
      "date": ISODate("2012-04-13T00:00:00Z"),
      "grade": "A",
      "score": 12
    },
    {
      "date": ISODate("2011-10-12T00:00:00Z"),
      "grade": "A",
      "score": 12
    }
  ],
  "name": "Riviera Caterer",
  "restaurant_id": "40356018"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f836"),
  "address": {
    "building": "97-22",
    "coord": [
      -73.8601152,
      40.7311739
    ],
    "street": "63 Road",
    "zipcode": "11374"
  },
  "borough": "Queens",
  "cuisine": "Jewish/Kosher",
  "grades": [
    {
      "date": ISODate("2014-11-24T00:00:00Z"),
      "grade": "Z",
      "score": 20
    },
    {
      "date": ISODate("2013-01-17T00:00:00Z"),
      "grade": "A",
      "score": 13
    },
    {
      "date": ISODate("2012-08-02T00:00:00Z"),
      "grade": "A",
      "score": 13
    },
    {
      "date": ISODate("2011-12-15T00:00:00Z"),
      "grade": "B",
      "score": 25
    }
  ],
  "name": "Tov Kosher Kitchen",
  "restaurant_id": "40356068"
}
Fetched 5 record(s) in 4ms

marcelo-VirtualBox(mongod-3.0.7) be-mean> db.restaurantes.find().limit(5).skip(5 * 1)
{
  "_id": ObjectId("565232a2ae40b9067be5f837"),
  "address": {
    "building": "8825",
    "coord": [
      -73.8803827,
      40.7643124
    ],
    "street": "Astoria Boulevard",
    "zipcode": "11369"
  },
  "borough": "Queens",
  "cuisine": "American ",
  "grades": [
    {
      "date": ISODate("2014-11-15T00:00:00Z"),
      "grade": "Z",
      "score": 38
    },
    {
      "date": ISODate("2014-05-02T00:00:00Z"),
      "grade": "A",
      "score": 10
    },
    {
      "date": ISODate("2013-03-02T00:00:00Z"),
      "grade": "A",
      "score": 7
    },
    {
      "date": ISODate("2012-02-10T00:00:00Z"),
      "grade": "A",
      "score": 13
    }
  ],
  "name": "Brunos On The Boulevard",
  "restaurant_id": "40356151"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f838"),
  "address": {
    "building": "2206",
    "coord": [
      -74.1377286,
      40.6119572
    ],
    "street": "Victory Boulevard",
    "zipcode": "10314"
  },
  "borough": "Staten Island",
  "cuisine": "Jewish/Kosher",
  "grades": [
    {
      "date": ISODate("2014-10-06T00:00:00Z"),
      "grade": "A",
      "score": 9
    },
    {
      "date": ISODate("2014-05-20T00:00:00Z"),
      "grade": "A",
      "score": 12
    },
    {
      "date": ISODate("2013-04-04T00:00:00Z"),
      "grade": "A",
      "score": 12
    },
    {
      "date": ISODate("2012-01-24T00:00:00Z"),
      "grade": "A",
      "score": 9
    }
  ],
  "name": "Kosher Island",
  "restaurant_id": "40356442"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f839"),
  "address": {
    "building": "7114",
    "coord": [
      -73.9068506,
      40.6199034
    ],
    "street": "Avenue U",
    "zipcode": "11234"
  },
  "borough": "Brooklyn",
  "cuisine": "Delicatessen",
  "grades": [
    {
      "date": ISODate("2014-05-29T00:00:00Z"),
      "grade": "A",
      "score": 10
    },
    {
      "date": ISODate("2014-01-14T00:00:00Z"),
      "grade": "A",
      "score": 10
    },
    {
      "date": ISODate("2013-08-03T00:00:00Z"),
      "grade": "A",
      "score": 8
    },
    {
      "date": ISODate("2012-07-18T00:00:00Z"),
      "grade": "A",
      "score": 10
    },
    {
      "date": ISODate("2012-03-09T00:00:00Z"),
      "grade": "A",
      "score": 13
    },
    {
      "date": ISODate("2011-10-14T00:00:00Z"),
      "grade": "A",
      "score": 9
    }
  ],
  "name": "Wilken'S Fine Food",
  "restaurant_id": "40356483"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f83a"),
  "address": {
    "building": "6409",
    "coord": [
      -74.00528899999999,
      40.628886
    ],
    "street": "11 Avenue",
    "zipcode": "11219"
  },
  "borough": "Brooklyn",
  "cuisine": "American ",
  "grades": [
    {
      "date": ISODate("2014-07-18T00:00:00Z"),
      "grade": "A",
      "score": 12
    },
    {
      "date": ISODate("2013-07-30T00:00:00Z"),
      "grade": "A",
      "score": 12
    },
    {
      "date": ISODate("2013-02-13T00:00:00Z"),
      "grade": "A",
      "score": 11
    },
    {
      "date": ISODate("2012-08-16T00:00:00Z"),
      "grade": "A",
      "score": 2
    },
    {
      "date": ISODate("2011-08-17T00:00:00Z"),
      "grade": "A",
      "score": 11
    }
  ],
  "name": "Regina Caterers",
  "restaurant_id": "40356649"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f83b"),
  "address": {
    "building": "1839",
    "coord": [
      -73.9482609,
      40.6408271
    ],
    "street": "Nostrand Avenue",
    "zipcode": "11226"
  },
  "borough": "Brooklyn",
  "cuisine": "Ice Cream, Gelato, Yogurt, Ices",
  "grades": [
    {
      "date": ISODate("2014-07-14T00:00:00Z"),
      "grade": "A",
      "score": 12
    },
    {
      "date": ISODate("2013-07-10T00:00:00Z"),
      "grade": "A",
      "score": 8
    },
    {
      "date": ISODate("2012-07-11T00:00:00Z"),
      "grade": "A",
      "score": 5
    },
    {
      "date": ISODate("2012-02-23T00:00:00Z"),
      "grade": "A",
      "score": 8
    }
  ],
  "name": "Taste The Tropics Ice Cream",
  "restaurant_id": "40356731"
}
Fetched 5 record(s) in 5ms

marcelo-VirtualBox(mongod-3.0.7) be-mean> db.restaurantes.find().limit(5).skip(5 * 2)
{
  "_id": ObjectId("565232a2ae40b9067be5f83c"),
  "address": {
    "building": "2300",
    "coord": [
      -73.8786113,
      40.8502883
    ],
    "street": "Southern Boulevard",
    "zipcode": "10460"
  },
  "borough": "Bronx",
  "cuisine": "American ",
  "grades": [
    {
      "date": ISODate("2014-05-28T00:00:00Z"),
      "grade": "A",
      "score": 11
    },
    {
      "date": ISODate("2013-06-19T00:00:00Z"),
      "grade": "A",
      "score": 4
    },
    {
      "date": ISODate("2012-06-15T00:00:00Z"),
      "grade": "A",
      "score": 3
    }
  ],
  "name": "Wild Asia",
  "restaurant_id": "40357217"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f83d"),
  "address": {
    "building": "7715",
    "coord": [
      -73.9973325,
      40.61174889999999
    ],
    "street": "18 Avenue",
    "zipcode": "11214"
  },
  "borough": "Brooklyn",
  "cuisine": "American ",
  "grades": [
    {
      "date": ISODate("2014-04-16T00:00:00Z"),
      "grade": "A",
      "score": 5
    },
    {
      "date": ISODate("2013-04-23T00:00:00Z"),
      "grade": "A",
      "score": 2
    },
    {
      "date": ISODate("2012-04-24T00:00:00Z"),
      "grade": "A",
      "score": 5
    },
    {
      "date": ISODate("2011-12-16T00:00:00Z"),
      "grade": "A",
      "score": 2
    }
  ],
  "name": "C & C Catering Service",
  "restaurant_id": "40357437"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f83e"),
  "address": {
    "building": "1269",
    "coord": [
      -73.871194,
      40.6730975
    ],
    "street": "Sutter Avenue",
    "zipcode": "11208"
  },
  "borough": "Brooklyn",
  "cuisine": "Chinese",
  "grades": [
    {
      "date": ISODate("2014-09-16T00:00:00Z"),
      "grade": "B",
      "score": 21
    },
    {
      "date": ISODate("2013-08-28T00:00:00Z"),
      "grade": "A",
      "score": 7
    },
    {
      "date": ISODate("2013-04-02T00:00:00Z"),
      "grade": "C",
      "score": 56
    },
    {
      "date": ISODate("2012-08-15T00:00:00Z"),
      "grade": "B",
      "score": 27
    },
    {
      "date": ISODate("2012-03-28T00:00:00Z"),
      "grade": "B",
      "score": 27
    }
  ],
  "name": "May May Kitchen",
  "restaurant_id": "40358429"
}
{
  "_id": ObjectId("565232a2ae40b9067be5f83f"),
  "address": {
    "building": "1",
    "coord": [
      -73.96926909999999,
      40.7685235
    ],
    "street": "East   66 Street",
    "zipcode": "10065"
  },
  "borough": "Manhattan",
  "cuisine": "American ",
  "grades": [
    {
      "date": ISODate("2014-05-07T00:00:00Z"),
      "grade": "A",
      "score": 3
    },
    {
      "date": ISODate("2013-05-03T00:00:00Z"),
      "grade": "A",
      "score": 4
    },
    {
      "date": ISODate("2012-04-30T00:00:00Z"),
      "grade": "A",
      "score": 6
    },
    {
      "date": ISODate("2011-12-27T00:00:00Z"),
      "grade": "A",
      "score": 0
    }
  ],
  "name": "1 East 66Th Street Kitchen",
  "restaurant_id": "40359480"
}
{
  "_id": ObjectId("565232a4ae40b9067be647fc"),
  "address": {
    "building": "42",
    "coord": [
      -73.82948700000001,
      40.657432
    ],
    "street": "Broadway",
    "zipcode": "11414"
  },
  "borough": "Queens",
  "cuisine": "Other",
  "grades": [ ],
  "name": "Laquana King",
  "restaurant_id": "50003441"
}
Fetched 5 record(s) in 2ms
```

##5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.group({
...   initial: { total: 0 },
...   reduce: function(curr, result) {
...     curr.types.forEach(function(type) {
...       if(result[type])
...         result[type]++;
...       else
...         result[type] = 1;
...       result.total++;
...     });
...   }
... })
[
  {
    "total": 915,
    "normal": 78,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ice": 24,
    "ghost": 34,
    "fighting": 38,
    "psychic": 62,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
]
```

##6. Realizar 3 counts na pokemons.
```
marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.count({ defense: { $gt: 90} })
129

marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.count({ defense: { $lt: 30}, attack: { $gte: 50 } })
3

marcelo-VirtualBox(mongod-3.0.7) be-mean> db.pokemons.count({ types: 'fire', name: /P/ })
3
```
