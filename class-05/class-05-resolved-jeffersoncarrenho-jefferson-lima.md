# MongoDB - Aula 05 - Exercício
autor: Jefferson Lima


## 1. Importar as collections restaurantes e pokemons

mongoimport --db be-mean-pokemons --collection pokemons --host=localhost --drop --file pokemons.json
2015-12-03T17:06:00.452-0200    connected to: localhost
2015-12-03T17:06:00.453-0200    dropping: be-mean-pokemons.pokemons
2015-12-03T17:06:00.492-0200    imported 610 documents

mongoimport --db be-mean-pokemons --collection restaurantes --host=localhost --drop --file restaurantes.json
2015-12-03T17:09:23.842-0200    connected to: localhost
2015-12-03T17:09:23.844-0200    dropping: be-mean-pokemons.restaurantes
2015-12-03T17:09:24.636-0200    imported 25359 documents


## 2. Distinct por `cuisine` na restaurantes

db.restaurantes.distinct('cuisine')

[
        "Hamburgers",
        "American ",
        "Irish",
        "Bakery",
        "Jewish/Kosher",
        "Delicatessen",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Chinese",
        "Other",
        "Chicken",
        "Turkish",
        "Caribbean",
        "Sandwiches/Salads/Mixed Buffet",
        "Bagels/Pretzels",
        "Continental",
        "Pizza",
        "Donuts",
        "Steak",
        "Italian",
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


## 3. Distinct por `types` na pokemons

db.pokemons.distinct('types')

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

var query = {name:1}
db.pokemons.find({}, query).limit(5).skip(5*0)

{ "_id" : ObjectId("564b1dad25337263280d0479"), "name" : "Rattata" }
{ "_id" : ObjectId("564b1dad25337263280d047b"), "name" : "Charmeleon" }
{ "_id" : ObjectId("564b1dad25337263280d047c"), "name" : "Wartortle" }
{ "_id" : ObjectId("564b1dad25337263280d047a"), "name" : "Charmander" }
{ "_id" : ObjectId("564b1dad25337263280d047e"), "name" : "Caterpie" }

db.pokemons.find({}, query).limit(5).skip(5*1)

{ "_id" : ObjectId("564b1dad25337263280d047d"), "name" : "Blastoise" }
{ "_id" : ObjectId("564b1dad25337263280d047f"), "name" : "Metapod" }
{ "_id" : ObjectId("564b1dad25337263280d0480"), "name" : "Butterfree" }
{ "_id" : ObjectId("564b1dad25337263280d0481"), "name" : "Spearow" }
{ "_id" : ObjectId("564b1dad25337263280d0482"), "name" : "Kakuna" }

db.pokemons.find({}, query).limit(5).skip(5*2)

{ "_id" : ObjectId("564b1dae25337263280d0483"), "name" : "Farfetchd" }
{ "_id" : ObjectId("564b1dae25337263280d0484"), "name" : "Magnemite" }
{ "_id" : ObjectId("564b1dae25337263280d0485"), "name" : "Magneton" }
{ "_id" : ObjectId("564b1dae25337263280d0487"), "name" : "Seel" }
{ "_id" : ObjectId("564b1dae25337263280d0486"), "name" : "Doduo" }



## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

db.pokemons.group({
    initial: {total: 0},
    reduce: function(current, result){
        current.types.forEach(function(type){
            if(result[type]){
                result[type]++;                
            }else{
                result[type] = 1;                
            }
            result.total++;            
        });
    }

});

[
        {
                "total" : 915,
                "normal" : 78,
                "fire" : 47,
                "water" : 105,
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

## 6. Realizar 3 counts na pokemons.

-> .count -- todos

db.pokemons.count()
610

-> .count -- só tipo fogo

db.pokemons.find({types:'fire'}).count()
47

-> .count -- só de quantos tem a defesa maior que 70

db.pokemons.find({defense:{$gt:70}}).count()
250
