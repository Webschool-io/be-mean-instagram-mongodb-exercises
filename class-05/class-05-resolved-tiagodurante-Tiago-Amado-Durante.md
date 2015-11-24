# Importar as collections restaurantes e pokemons

c:\MongoDB\Server\3.0\bin>mongoimport --db test --collection restaurantes --drop --file c:/restaurantes.json
2015-11-19T15:07:26.133-0200    connected to: localhost
2015-11-19T15:07:26.135-0200    dropping: test.restaurantes
2015-11-19T15:07:28.703-0200    imported 25359 documents

c:\MongoDB\Server\3.0\bin>mongoimport --db test --collection pokemons --drop --file c:/pokemons.json
2015-11-19T15:07:49.582-0200    connected to: localhost
2015-11-19T15:07:49.584-0200    dropping: test.pokemons
2015-11-19T15:07:49.700-0200    imported 610 documents

# Distinct por 'cuisine' na restaurantes

> db.restaurantes.distinct('cuisine')
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
        "Not Listed/Not Applicable",
        "African",
        "Greek",
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

# Distinct por 'types' na pokemons

> db.pokemons.distinct('types')
[
        "normal",
        "fire",
        "bug",
        "water",
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

# As primeiras 3 paginas com .limit() e .skip() de pokemons (5 em 5)

> db.pokemons.find({}, {name:1}).limit(10).skip(10*0)
{ "_id" : ObjectId("564b1dad25337263280d0479"), "name" : "Rattata" }
{ "_id" : ObjectId("564b1dad25337263280d047a"), "name" : "Charmander" }
{ "_id" : ObjectId("564b1dad25337263280d047b"), "name" : "Charmeleon" }
{ "_id" : ObjectId("564b1dad25337263280d047e"), "name" : "Caterpie" }
{ "_id" : ObjectId("564b1dad25337263280d047f"), "name" : "Metapod" }
{ "_id" : ObjectId("564b1dad25337263280d047c"), "name" : "Wartortle" }
{ "_id" : ObjectId("564b1dad25337263280d047d"), "name" : "Blastoise" }
{ "_id" : ObjectId("564b1dad25337263280d0480"), "name" : "Butterfree" }
{ "_id" : ObjectId("564b1dad25337263280d0481"), "name" : "Spearow" }
{ "_id" : ObjectId("564b1dad25337263280d0482"), "name" : "Kakuna" }
> db.pokemons.find({}, {name:1}).limit(10).skip(10*1)
{ "_id" : ObjectId("564b1dae25337263280d0484"), "name" : "Magnemite" }
{ "_id" : ObjectId("564b1dae25337263280d0483"), "name" : "Farfetchd" }
{ "_id" : ObjectId("564b1dae25337263280d0485"), "name" : "Magneton" }
{ "_id" : ObjectId("564b1dae25337263280d0486"), "name" : "Doduo" }
{ "_id" : ObjectId("564b1dae25337263280d0487"), "name" : "Seel" }
{ "_id" : ObjectId("564b1dae25337263280d0488"), "name" : "Dodrio" }
{ "_id" : ObjectId("564b1dae25337263280d0489"), "name" : "Dewgong" }
{ "_id" : ObjectId("564b1dae25337263280d048a"), "name" : "Gastly" }
{ "_id" : ObjectId("564b1dae25337263280d048b"), "name" : "Cloyster" }
{ "_id" : ObjectId("564b1dae25337263280d048c"), "name" : "Muk" }
> db.pokemons.find({}, {name:1}).limit(10).skip(10*2)
{ "_id" : ObjectId("564b1daf25337263280d048d"), "name" : "Poliwag" }
{ "_id" : ObjectId("564b1daf25337263280d048e"), "name" : "Poliwhirl" }
{ "_id" : ObjectId("564b1daf25337263280d048f"), "name" : "Poliwrath" }
{ "_id" : ObjectId("564b1daf25337263280d0490"), "name" : "Abra" }
{ "_id" : ObjectId("564b1daf25337263280d0491"), "name" : "Kadabra" }
{ "_id" : ObjectId("564b1daf25337263280d0492"), "name" : "Machop" }
{ "_id" : ObjectId("564b1daf25337263280d0493"), "name" : "Machoke" }
{ "_id" : ObjectId("564b1daf25337263280d0495"), "name" : "Bellsprout" }
{ "_id" : ObjectId("564b1daf25337263280d0494"), "name" : "Machamp" }
{ "_id" : ObjectId("564b1daf25337263280d0496"), "name" : "Ivysaur" }

# Group ou Aggregate contando a quantidade de pokemons de cada tipo
Professor, tentei fazer por aggregate para ficar diferente com o exemplo que o senhor passou na aula. Apesar de ter feito, não consegui colocar a variavel total, exibindo o total de pokemons que foram exibidos.
> db.pokemons.aggregate([
...         {"$unwind": "$types" } ,
...         { "$group": { _id: "$types", total : {$sum : 1} } },
...         { "$sort" : { _id : 1 } }
...     ])
{ "_id" : "bug", "total" : 61 }
{ "_id" : "dark", "total" : 38 }
{ "_id" : "dragon", "total" : 20 }
{ "_id" : "electric", "total" : 40 }
{ "_id" : "fairy", "total" : 28 }
{ "_id" : "fighting", "total" : 38 }
{ "_id" : "fire", "total" : 47 }
{ "_id" : "flying", "total" : 77 }
{ "_id" : "ghost", "total" : 34 }
{ "_id" : "grass", "total" : 75 }
{ "_id" : "ground", "total" : 51 }
{ "_id" : "ice", "total" : 24 }
{ "_id" : "normal", "total" : 78 }
{ "_id" : "poison", "total" : 54 }
{ "_id" : "psychic", "total" : 62 }
{ "_id" : "rock", "total" : 46 }
{ "_id" : "steel", "total" : 37 }
{ "_id" : "water", "total" : 105 }

# Realizar 3 counts na pokemons

1. todos
> db.pokemons.count()
610

2. tipo fogo
> db.pokemons.count({types: 'fire'})
47

3. defesa > 70
> db.pokemons.count({defense: {$gt: 70}})
250
