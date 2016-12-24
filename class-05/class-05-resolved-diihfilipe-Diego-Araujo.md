
######1. Importar as collections restaurantes e pokemons

mestre@Zeus:~$ mongoimport --host 127.0.0.1 --db be-mean-restaurante --collection restaurantes --drop --file Downloads/restaurantes.json 2015-11-26T00:00:33.975-0500 conn

ected to: 127.0.0.1 2015-11-26T00:00:34.975-0500 dropping: be-mean-restaurante.restaurantes 2015-11-26T00:00:40.975-0500 [##################......] be-mean-restaurante.restaurantes 8.6 MB/11.4 MB (75.4%) 2015-11-26T00:00:38.975-0500 imported 25359 documents

mestre@Zeus:~$ mongoimport --host 127.0.0.1 --db be-mean-pokemon --collection pokemons --drop --file Downloads/pokemons.json 2015-11-26T00:00:41.975-0500 connected to: 127.0.0.1 2015-11-26T00:00:41.975-0500 dropping: be-mean-pokemon.pokemons 2015-11-26T00:00:41.975-0500 imported 610 documents
2. Distinct por cuisine na restaurantes

Zeus(mongod-3.0.7) be-mean-restaurante> var query = "cuisine" Zeus(mongod-3.0.7) be-mean-restaurante> db.restaurantes.distinct(query) [ "Bakery", "Hamburgers", "Irish", "American ", "Jewish/Kosher", "Delicatessen", "Ice Cream, Gelato, Yogurt, Ices", "Chinese", "Other", "Chicken", "Turkish", "Caribbean", "Donuts", "Sandwiches/Salads/Mixed Buffet", "Bagels/Pretzels", "Continental", "Pizza", "Italian", "Steak", "Polish", "Latin (Cuban, Dominican, Puerto Rican, South & Central American)", "German", "French", "Pizza/Italian", "Mexican", "Spanish", "Café/Coffee/Tea", "Tex-Mex", "Pancakes/Waffles", "Soul Food", "Seafood", "Hotdogs", "Greek", "Not Listed/Not Applicable", "African", "Japanese", "Indian", "Armenian", "Thai", "Chinese/Cuban", "Mediterranean", "Korean", "Bottled beverages, including water, sodas, juices, etc.", "Russian", "Eastern European", "Middle Eastern", "Asian", "Ethiopian", "Vegetarian", "Barbecue", "Egyptian", "English", "Sandwiches", "Portuguese", "Indonesian", "Chinese/Japanese", "Filipino", "Juice, Smoothies, Fruit Salads", "Brazilian", "Afghan", "Vietnamese/Cambodian/Malaysia", "CafÃ©/Coffee/Tea", "Soups & Sandwiches", "Tapas", "Moroccan", "Pakistani", "Peruvian", "Bangladeshi", "Czech", "Salads", "Creole", "Fruits/Vegetables", "Iranian", "Cajun", "Scandinavian", "Polynesian", "Soups", "Australian", "Hotdogs/Pretzels", "Southwestern", "Nuts/Confectionary", "Hawaiian", "Creole/Cajun", "Californian", "Chilean" ]
3. Distinct por types na pokemons

Zeus(mongod-3.0.7) be-mean-pokemon> var query = "types" Zeus(mongod-3.0.7) be-mean-pokemon> db.pokemons.distinct(query) [ "normal", "fire", "water", "bug", "flying", "poison", "electric", "steel", "ice", "ghost", "fighting", "psychic", "grass", "ground", "fairy", "rock", "dark", "dragon" ]
4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

Zeus(mongod-3.0.7) be-mean-pokemon> var query = {} Zeus(mongod-3.0.7) be-mean-pokemon> var field = {name: 1, _id: 0} Zeus(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query, field).limit(5).skip(5 * 0) { "name": "Rattata" } { "name": "Charmander" } { "name": "Charmeleon" } { "name": "Wartortle" } { "name": "Blastoise" }

Zeus(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query, field).limit(5).skip(5 * 1) { "name": "Caterpie" } { "name": "Metapod" } { "name": "Butterfree" } { "name": "Spearow" } { "name": "Kakuna" }

Zeus(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query, field).limit(5).skip(5 * 2) { "name": "Farfetchd" } { "name": "Magnemite" } { "name": "Magneton" } { "name": "Doduo" } { "name": "Seel" }
5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

Zeus(mongod-3.0.7) be-mean-pokemon> var aggregate = [{$unwind: "$types"}, {$group: {_id: "$types", count: {$sum: 1}}}] Zeus(mongod-3.0.7) be-mean-pokemon> db.pokemons.aggregate(aggregate) { "result": [ { "_id": "fairy", "count": 28 }, { "_id": "psychic", "count": 62 }, { "_id": "fighting", "count": 38 }, { "_id": "dark", "count": 38 }, { "_id": "ground", "count": 51 }, { "_id": "grass", "count": 75 }, { "_id": "electric", "count": 40 }, { "_id": "steel", "count": 37 }, { "_id": "rock", "count": 46 }, { "_id": "flying", "count": 77 }, { "_id": "fire", "count": 47 }, { "_id": "ice", "count": 24 }, { "_id": "bug", "count": 61 }, { "_id": "poison", "count": 54 }, { "_id": "ghost", "count": 34 }, { "_id": "dragon", "count": 20 }, { "_id": "water", "count": 105 }, { "_id": "normal", "count": 78 } ], "ok": 1 }
6. Realizar 3 counts na collection pokemons.

-> .count -- todos 
eus(mongod-3.0.7) be-mean-pokemon> var query = {} Zeus(mongod-3.0.7) be-mean-pokemon> db.pokemons.count(query) 610

-> .count -- só tipo fogo
Zeus(mongod-3.0.7) be-mean-pokemon> var query = {types: 'fire'} Zeus(mongod-3.0.7) be-mean-pokemon> db.pokemons.count(query) 47

-> .count -- todos com defesa > 70
 Zeus(mongod-3.0.7) be-mean-pokemon> var query = { defense: {$gt: 70}} Zeus(mongod-3.0.7) be-mean-pokemon> db.pokemons.count(query) 250