# MongoDB - Aula 04 - Exercício
autor: Luciano Silva de Lima

# 1. Importação das collections restaurantes e pokemons

$ mongoimport --host localhost --db be-mean --collection pokemons --drop --file pokemons.json
```
2015-12-04T07:07:39.543-0200    connected to: localhost
2015-12-04T07:07:39.546-0200    dropping: be-mean.pokemons
2015-12-04T07:07:39.823-0200    imported 610 documents
```

$ mongoimport --host localhost --db be-mean --collection restaurantes --drop --f                ile restaurantes.json
```
2015-12-04T07:09:12.365-0200    connected to: localhost
2015-12-04T07:09:12.368-0200    dropping: be-mean.restaurantes
2015-12-04T07:09:15.360-0200    [##########..............] be-mean.restaurantes5                .2 MB/11.4 MB (45.5%)
2015-12-04T07:09:18.360-0200    [####################....] be-mean.restaurantes9                .8 MB/11.4 MB (86.2%)
2015-12-04T07:09:21.249-0200    imported 25359 documents
```

# 2. Realizar um distinct por 'cuisine' na collection de restaurantes

> db.restaurantes.distinct("cuisine")
```
[
        "Hamburgers",
        "Bakery",
        "Jewish/Kosher",
        "American ",
        "Irish",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Delicatessen",
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
        "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
        "German",
        "French",
        "Polish",
        "Pizza/Italian",
        "Mexican",
        "Spanish",
        "Café/Coffee/Tea",
        "Tex-Mex",
        "Pancakes/Waffles",
        "Soul Food",
        "Seafood",
        "Greek",
        "Hotdogs",
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

# 3. Realizar um distinct por types na collection de pokemons
> db.pokemons.distinct("types")
```
[
        "water",
        "fire",
        "normal",
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
# 4. Exibir as 3 primeiras páginas, com 5 itens, de pokemons

> var currPage = 0
> var pageLen = 5
> db.pokemons.find({},{name:1}).limit(pageLen).skip(currPage)
```
{ "_id" : ObjectId("564b1dad25337263280d047c"), "name" : "Wartortle" }
{ "_id" : ObjectId("564b1dad25337263280d047b"), "name" : "Charmeleon" }
{ "_id" : ObjectId("564b1dad25337263280d0479"), "name" : "Rattata" }
{ "_id" : ObjectId("564b1dad25337263280d047a"), "name" : "Charmander" }
{ "_id" : ObjectId("564b1dad25337263280d047d"), "name" : "Blastoise" }
```
> ++currPage
```
1
```
> db.pokemons.find({},{name:1}).limit(pageLen).skip(currPage)
```
{ "_id" : ObjectId("564b1dad25337263280d047b"), "name" : "Charmeleon" }
{ "_id" : ObjectId("564b1dad25337263280d0479"), "name" : "Rattata" }
{ "_id" : ObjectId("564b1dad25337263280d047a"), "name" : "Charmander" }
{ "_id" : ObjectId("564b1dad25337263280d047d"), "name" : "Blastoise" }
{ "_id" : ObjectId("564b1dad25337263280d047e"), "name" : "Caterpie" }
```
> ++currPage
```
2
```
> db.pokemons.find({},{name:1}).limit(pageLen).skip(currPage)
```
{ "_id" : ObjectId("564b1dad25337263280d0479"), "name" : "Rattata" }
{ "_id" : ObjectId("564b1dad25337263280d047a"), "name" : "Charmander" }
{ "_id" : ObjectId("564b1dad25337263280d047d"), "name" : "Blastoise" }
{ "_id" : ObjectId("564b1dad25337263280d047e"), "name" : "Caterpie" }
{ "_id" : ObjectId("564b1dad25337263280d047f"), "name" : "Metapod" }
```
# 5. Realizar um aggregation ou group, na collections de pokemons, agrupando por tipos de pokemons.

> db.pokemons.group({
... initial:{},
... reduce: function(curr, result) {
... curr["types"].forEach(function(type){
	... if (result[type]) {
	...   result[type]++;
	... }else{
	...   result[type]= 1;
	... }
... });
... }
})
```
[
        {
                "water" : 105,
                "fire" : 47,
                "normal" : 78,
                "bug" : 61,
                "flying" : 77,
                "poison" : 54,
                "steel" : 37,
                "electric" : 40,
                "ice" : 24,
                "ghost" : 34,
                "fighting" : 38,
                "psychic" : 62,
                "grass" : 75,
                "ground" : 51,
                "fairy" : 28,
                "rock" : 46,
                "dark" : 38,
                "dragon" : 20
        }
]
```

# 6. Realizar 3 counts na collection de pokemons.

   6.1 Count geral
		> db.pokemons.count({})
		```
		610
		```
   6.2 Count pelo tipo 'fire'
		> db.pokemons.count({types:"fire"})
		```
		47
		```
   6.3 Count de quantos tem a defesa maior que 70.
		> db.pokemons.count({defense:{$gt:70}})
		```
		250
		```