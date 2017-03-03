# MongoDB - Aula 05 - Exercício
autor: Natália Nascimento de Ávila

#1. Importar as collections restaurantes e pokemons. 

```
./mongoimport.exe --db be-mean-pokemons --collection pokemons D:\projetos\Plugins\Estudos\MongoDB\Exercicios\Aula05\pokemons.json 
2016-05-09T16:06:52.335-0300    connected to: localhost
2016-05-09T16:06:54.643-0300    imported 620 documents

```

#2. Distinct por cuisine na restaurantes.

```
db.restaurantes.distinct("cuisine")
[
        "Bakery",
        "Hamburgers",
        "Irish",
        "American ",
        "Jewish/Kosher",
        "Delicatessen",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Chinese",
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
        "Latin (Cuban, Dominican, Puerto Rican, South & Central Am
        "German",
        "French",
        "Tex-Mex",
        "Juice, Smoothies, Fruit Salads",
        "Pizza/Italian",
        "Korean",
        "Café/Coffee/Tea",
        "Indian",
        "Japanese",
        "Thai",
        "Chinese/Cuban",
        "Spanish",
        "Mexican",
        "Brazilian",
        "Soups & Sandwiches",
        "Mediterranean",
        "Sandwiches",
        "Seafood",
        "Pancakes/Waffles",
        "Vegetarian",
        "Asian",
        "Afghan",
        "Bottled beverages, including water, sodas, juices, etc.",
        "Barbecue",
        "Soul Food",
        "Middle Eastern",
        "Greek",
        "Hotdogs",
        "Not Listed/Not Applicable",
        "African",
        "Ethiopian",
        "Russian",
        "Chinese/Japanese",
        "Tapas",
        "Other",
        "Bangladeshi",
        "Moroccan",
        "Czech",
        "Salads",
        "Indonesian",
        "English",
        "Armenian",
        "Eastern European",
        "Filipino",
        "Pakistani",
        "Peruvian",
        "Egyptian",
        "Vietnamese/Cambodian/Malaysia",
        "Portuguese",
        "CafÃ©/Coffee/Tea",
        "Creole",
        "Fruits/Vegetables",
        "Iranian",
        "Cajun",
        "Scandinavian",
        "Soups",
        "Australian",
        "Polynesian",
        "Southwestern",
        "Hotdogs/Pretzels",
        "Nuts/Confectionary",
        "Hawaiian",
        "Creole/Cajun",
        "Californian",
        "Chilean"
]

```

#3- Distinct por types na pokemons.

```
db.pokemons.distinct("types")
[
        "bug",
        "poison",
        "flying",
        "normal",
        "electric",
        "water",
        "fighting",
        "psychic",
        "grass",
        "fairy",
        "fire",
        "rock",
        "ice",
        "ground",
        "steel",
        "ghost",
        "dark",
        "dragon"
]

```

#4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```
db.pokemons.find({}, {name: 1, _id:0}).limit(5).skip(5 * 0)
{ "name" : "Beedrill" }
{ "name" : "Venusaur" }
{ "name" : "Jigglypuff" }
{ "name" : "Butterfree" }
{ "name" : "Beedrill" }

db.pokemons.find({}, {name: 1, _id:0}).limit(5).skip(5 * 1)
{ "name" : "Venusaur" }
{ "name" : "Jigglypuff" }
{ "name" : "Butterfree" }
{ "name" : "Wartortle" }
{ "name" : "Chespin" }

db.pokemons.find({}, {name: 1, _id:0}).limit(5).skip(5 * 2)
{ "name" : "Pidgeotto" }
{ "name" : "Pidgeot" }
{ "name" : "Raticate" }
{ "name" : "Fearow" }
{ "name" : "Pikachu" }

```

#5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
db.pokemons.aggregate([{$unwind: '$types'},{$group: {_id: '$types',count: {$sum: 1}}}]);
{ "_id" : "fairy", "count" : 31 }
{ "_id" : "grass", "count" : 70 }
{ "_id" : "electric", "count" : 47 }
{ "_id" : "flying", "count" : 81 }
{ "_id" : "poison", "count" : 54 }
{ "_id" : "bug", "count" : 58 }
{ "_id" : "dark", "count" : 35 }
{ "_id" : "water", "count" : 101 }
{ "_id" : "normal", "count" : 79 }
{ "_id" : "psychic", "count" : 61 }
{ "_id" : "fighting", "count" : 42 }
{ "_id" : "fire", "count" : 53 }
{ "_id" : "rock", "count" : 42 }
{ "_id" : "ice", "count" : 28 }
{ "_id" : "ground", "count" : 53 }
{ "_id" : "steel", "count" : 35 }
{ "_id" : "ghost", "count" : 34 }
{ "_id" : "dragon", "count" : 30 }


```

#6. Realizar 3 counts na pokemons.

```
db.pokemons.count({types: "rock"})
42

db.pokemons.count({attack: {$gt:50}})
488

db.pokemons.count({attack: {$gte:80}})
279

```