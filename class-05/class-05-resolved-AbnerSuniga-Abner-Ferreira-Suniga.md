# MongoDB - Aula 05 - Exercício
Autor: Anderson Machado Lemos

## Importar as collections restaurantes e pokemons

```
PS C:\Developer\be-mean-mongodb> mongoimport --host 127.0.0.1 --db be-mean2 --collection restaurantes  --drop --file res
taurantes.json
2016-09-16T15:33:12.356-0300    connected to: 127.0.0.1
2016-09-16T15:33:12.373-0300    dropping: be-mean2.restaurantes
2016-09-16T15:33:14.662-0300    imported 25359 documents

PS C:\Developer\be-mean-mongodb> mongoimport --host 127.0.0.1 --db be-mean2 --collection pokemons --drop --file pokemons
.json
2016-09-16T15:34:50.263-0300    connected to: 127.0.0.1
2016-09-16T15:34:50.279-0300    dropping: be-mean2.pokemons
2016-09-16T15:34:50.419-0300    imported 610 documents
```

## Distinct por cuisine na collection restaurante

```
> db.restaurantes.distinct("cuisine")
[
        "Hamburgers",
        "Irish",
        "Jewish/Kosher",
        "Delicatessen",
        "American ",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Bakery",
        "Chinese",
        "Chicken",
        "Turkish",
        "Caribbean",
        "Sandwiches/Salads/Mixed Buffet",
        "Bagels/Pretzels",
        "Continental",
        "Pizza",
        "Donuts",
        "Italian",
        "Polish",
        "Latin (Cuban, Dominican, Puerto Rican, South & Central American)"
        "Steak",
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
        "Other",
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

## Distinct por types na collection pokemons

```
> db.pokemons.distinct("types")
[
        "normal",
        "fire",
        "water",
        "bug",
        "flying",
        "poison",
        "electric",
        "steel",
        "fighting",
        "psychic",
        "ice",
        "ghost",
        "ground",
        "fairy",
        "grass",
        "rock",
        "dark",
        "dragon"
]
```

## As primeiras 3 páginas com .limit() e .skip() de pokemons (de 5 em 5)

```
> db.pokemons.find().limit(5).skip(0)
{ "_id" : ObjectId("564b1dad25337263280d0479"), "attack" : 56, "created" : "2013-11-03T15:05:41.305777", "defense" : 35, "height" : "3", "hp" : 30, "name" : "Rattata", "speed" : 72, "types" : [ "normal" ] }
{ "_id" : ObjectId("564b1dad25337263280d047a"), "attack" : 52, "created" : "2013-11-03T15:05:41.271082", "defense" : 43, "height" : "6", "hp" : 39, "name" : "Charmander", "speed" : 65, "types" : [ "fire" ] }
{ "_id" : ObjectId("564b1dad25337263280d047b"), "attack" : 64, "created" : "2013-11-03T15:05:41.273462", "defense" : 58, "height" : "11", "hp" : 58, "name" : "Charmeleon", "speed" : 80, "types" : [ "fire" ] }
{ "_id" : ObjectId("564b1dad25337263280d047c"), "attack" : 63, "created" : "2013-11-03T15:05:41.280718", "defense" : 80, "height" : "10", "hp" : 59, "name" : "Wartortle", "speed" : 58, "types" : [ "water" ] }
{ "_id" : ObjectId("564b1dad25337263280d047d"), "attack" : 83, "created" : "2013-11-03T15:05:41.282985", "defense" : 100
, "height" : "16", "hp" : 79, "name" : "Blastoise", "speed" : 78, "types" : [ "water" ] }
> db.pokemons.find().limit(5).skip(5)
{ "_id" : ObjectId("564b1dad25337263280d047e"), "attack" : 30, "created" : "2013-11-03T15:05:41.285736", "defense" : 35, "height" : "3", "hp" : 45, "name" : "Caterpie", "speed" : 45, "types" : [ "bug" ] }
{ "_id" : ObjectId("564b1dad25337263280d0480"), "attack" : 45, "created" : "2013-11-03T15:05:41.290411", "defense" : 50, "height" : "11", "hp" : 60, "name" : "Butterfree", "speed" : 70, "types" : [ "flying", "bug" ] }
{ "_id" : ObjectId("564b1dad25337263280d047f"), "attack" : 20, "created" : "2013-11-03T15:05:41.288107", "defense" : 55, "height" : "7", "hp" : 50, "name" : "Metapod", "speed" : 30, "types" : [ "bug" ] }
{ "_id" : ObjectId("564b1dad25337263280d0481"), "attack" : 60, "created" : "2013-11-03T15:05:41.310402", "defense" : 30, "height" : "3", "hp" : 40, "name" : "Spearow", "speed" : 70, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564b1dad25337263280d0482"), "attack" : 25, "created" : "2013-11-03T15:05:41.294947", "defense" : 50, "height" : "6", "hp" : 45, "name" : "Kakuna", "speed" : 35, "types" : [ "poison", "bug" ] }
> db.pokemons.find().limit(5).skip(10)
{ "_id" : ObjectId("564b1dae25337263280d0484"), "attack" : 35, "created" : "2013-11-03T15:05:41.435237", "defense" : 70, "height" : "3", "hp" : 25, "name" : "Magnemite", "speed" : 45, "types" : [ "steel", "electric" ] }
{ "_id" : ObjectId("564b1dae25337263280d0483"), "attack" : 65, "created" : "2013-11-03T15:05:41.439497", "defense" : 55, "height" : "8", "hp" : 52, "name" : "Farfetchd", "speed" : 60, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564b1dae25337263280d0485"), "attack" : 60, "created" : "2013-11-03T15:05:41.437483", "defense" : 95, "height" : "10", "hp" : 50, "name" : "Magneton", "speed" : 70, "types" : [ "steel", "electric" ] }
{ "_id" : ObjectId("564b1dae25337263280d0486"), "attack" : 85, "created" : 2013-11-03T15:05:41.441502", "defense" : 45, "height" : "14", "hp" : 35, "name" : "Doduo", "speed" : 75, "types" : [ "normal", "flying" ] }
{ "_id" : ObjectId("564b1dae25337263280d0487"), "attack" : 45, "created" : 11-03T15:05:41.445749", "defense" : 55, "height" : "11", "hp" : 65, "name" : "Seel", "speed" : 45, "types" : [ "water" ] }
>
```

## Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
> db.pokemons.group({
... initial: {},
... reduce: function (current,result) {
... current.types.forEach(function (type){
... if(result[type]){
... result[type]++;
... }else{
... result[type] = 1;
... }
... })
...
... }
... });
[
        {
                "normal" : 78,
                "fire" : 47,
                "water" : 105,
                "bug" : 61,
                "flying" : 77,
                "poison" : 54,
                "steel" : 37,
                "electric" : 40,
                "fighting" : 38,
                "psychic" : 62,
                "ice" : 24,
                "ghost" : 34,
                "ground" : 51,
                "fairy" : 28,
                "grass" : 75,
                "rock" : 46,
                "dark" : 38,
                "dragon" : 20
        }
]
> db.pokemons.count({types: "normal"})
78
>
```

## Realizar 3 counts na collection pokemons

### .count -> todos
```
> db.pokemons.count()
610
```
### .count -> só tipo fogo
```
> db.pokemons.count({types: "fire"})
47
```
### .count -> só de quantos tem a defesa maior que 70
```
> db.pokemons.count({defense: {$gt: 70}})
250
```