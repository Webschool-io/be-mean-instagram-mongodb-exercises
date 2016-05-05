# MongoDB - Aula 05 - Exercício
autor: Alex de Miranda

## 1. Importar as collections restaurantes e pokemons
C:\Users\Alex>mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file d:/be-mean-instagram-notas/restaurantes.json
2015-11-20T23:56:38.888-0200    connected to: 127.0.0.1
2015-11-20T23:56:38.891-0200    dropping: be-mean.restaurantes
2015-11-20T23:56:40.242-0200    imported 25359 documents

C:\Users\Alex>mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file d:/be-mean-instagram-notas/pokemons.json
2015-11-21T00:00:51.328-0200    connected to: 127.0.0.1
2015-11-21T00:00:51.330-0200    dropping: be-mean.pokemons

## 2. Distinct por cuisine na restaurantes
> db.restaurantes.distinct("cuisine")
[
        "Bakery",
        "Irish",
        "American ",
        "Jewish/Kosher",
        "Delicatessen",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Chinese",
        "Other",
        "Hamburgers",
        "Chicken",
        "Turkish",
        "Caribbean",
        "Donuts",
        "Sandwiches/Salads/Mixed Buffet",
        "Bagels/Pretzels",
        "Pizza",
        "Continental",
        "Italian",
        "Steak",
        "Polish",
        "Latin (Cuban, Dominican, Puerto Rican, South & Central Am
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
        "Greek",
        "Not Listed/Not Applicable",
        "African",
        "Hotdogs",
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

## 3. Distinct por types na pokemons
> db.pokemons.distinct("types")
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
        "fighting",
        "psychic",
        "ghost",
        "grass",
        "ground",
        "fairy",
        "rock",
        "dark",
        "dragon"
]

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5 * 0)
{ "name" : "Wartortle" }
{ "name" : "Charmeleon" }
{ "name" : "Charmander" }
{ "name" : "Rattata" }
{ "name" : "Blastoise" }
> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5 * 1)
{ "name" : "Caterpie" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }
> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5 * 2)
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Magneton" }
{ "name" : "Doduo" }
{ "name" : "Seel" }
> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5 * 3)
{ "name" : "Dewgong" }
{ "name" : "Dodrio" }
{ "name" : "Cloyster" }
{ "name" : "Muk" }
{ "name" : "Poliwhirl" }

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
> db.pokemons.group({
... initial:{total:0},
... reduce:function(curr, result){
... curr.types.forEach(function(type){
... if(result[type]){
... result[type]++;
... } else {
... result[type] = 1;
... }
... result.total++;
... });
... }
... });
[
	{
	  "total" : 915,
	  "water" : 105,
	  "fire" : 47,
	  "normal" : 78,
	  "bug" : 61,
	  "flying" : 77,
	  "poison" : 54,
	  "steel" : 37,
	  "electric" : 40,
	  "ice" : 24,
	  "fighting" : 38,
	  "psychic" : 62,
	  "ghost" : 34,
	  "grass" : 75,
	  "ground" : 51,
	  "fairy" : 28,
	  "rock" : 46,
	  "dark" : 38,
	  "dragon" : 20
	}
]
## 6. Realizar 3 counts na pokemons.
> db.pokemons.count({attack : {$gt:100}})
99
> db.pokemons.count({speed : {$lt:10}})
2
> db.pokemons.count({types:"fire"})
47