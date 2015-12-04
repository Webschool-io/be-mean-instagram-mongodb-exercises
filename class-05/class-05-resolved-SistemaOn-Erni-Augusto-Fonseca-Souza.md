MongoDB - Aula 05 - Exercício
autor: Erni Souza - SistemaOn

## 1. Importar as collections restaurantes e pokemons
sistemaon@sistemaon-VirtualBox:~$ mongoimport --host 127.0.0.1 --db be-mean-restaurante --collection restaurantes --drop --file Downloads/restaurantes.json
2015-11-19T00:08:37.966-0500	connected to: 127.0.0.1
2015-11-19T00:08:37.967-0500	dropping: be-mean-restaurante.restaurantes
2015-11-19T00:08:40.975-0500	[##################......] be-mean-restaurante.restaurantes	8.6 MB/11.4 MB (75.4%)
2015-11-19T00:08:43.767-0500	imported 25359 documents

sistemaon@sistemaon-VirtualBox:~$ mongoimport --host 127.0.0.1 --db be-mean-pokemon --collection pokemons --drop --file Downloads/pokemons.json 
2015-11-19T00:09:41.092-0500	connected to: 127.0.0.1
2015-11-19T00:09:41.093-0500	dropping: be-mean-pokemon.pokemons
2015-11-19T00:09:41.207-0500	imported 610 documents


## 2. Distinct por cuisine na restaurantes
sistemaon-VirtualBox(mongod-3.0.7) be-mean-restaurante> var query = "cuisine"
sistemaon-VirtualBox(mongod-3.0.7) be-mean-restaurante> db.restaurantes.distinct(query)
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


## 3. Distinct por types na pokemons
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> var query = "types"
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> db.pokemons.distinct(query)
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> var query = {}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> var field = {name: 1, _id: 0}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query, field).limit(5).skip(5 * 0)
{
  "name": "Rattata"
}
{
  "name": "Charmander"
}
{
  "name": "Charmeleon"
}
{
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}

sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query, field).limit(5).skip(5 * 1)
{
  "name": "Caterpie"
}
{
  "name": "Metapod"
}
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Kakuna"
}

sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query, field).limit(5).skip(5 * 2)
{
  "name": "Farfetchd"
}
{
  "name": "Magnemite"
}
{
  "name": "Magneton"
}
{
  "name": "Doduo"
}
{
  "name": "Seel"
}

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> var aggregate = [{$unwind: "$types"}, {$group: {_id: "$types", count: {$sum: 1}}}]
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> db.pokemons.aggregate(aggregate)
{
  "result": [
    {
      "_id": "fairy",
      "count": 28
    },
    {
      "_id": "psychic",
      "count": 62
    },
    {
      "_id": "fighting",
      "count": 38
    },
    {
      "_id": "dark",
      "count": 38
    },
    {
      "_id": "ground",
      "count": 51
    },
    {
      "_id": "grass",
      "count": 75
    },
    {
      "_id": "electric",
      "count": 40
    },
    {
      "_id": "steel",
      "count": 37
    },
    {
      "_id": "rock",
      "count": 46
    },
    {
      "_id": "flying",
      "count": 77
    },
    {
      "_id": "fire",
      "count": 47
    },
    {
      "_id": "ice",
      "count": 24
    },
    {
      "_id": "bug",
      "count": 61
    },
    {
      "_id": "poison",
      "count": 54
    },
    {
      "_id": "ghost",
      "count": 34
    },
    {
      "_id": "dragon",
      "count": 20
    },
    {
      "_id": "water",
      "count": 105
    },
    {
      "_id": "normal",
      "count": 78
    }
  ],
  "ok": 1
}

## 6. Realizar 3 counts na pokemons.

-> .count -- todos
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> var query = {}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> db.pokemons.count(query)
610
 
-> .count -- só tipo fogo
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> var query = {types: 'fire'}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> db.pokemons.count(query)
47

-> .count -- só de quantos tem a defesa maior que 70
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> var query = { defense: {$gt: 70}}
sistemaon-VirtualBox(mongod-3.0.7) be-mean-pokemon> db.pokemons.count(query)
250
