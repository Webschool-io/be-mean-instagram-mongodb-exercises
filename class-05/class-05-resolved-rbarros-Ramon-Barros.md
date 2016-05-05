# MongoDB - Aula 05 - Exercício
autor: Ramon Barros

## 1. Importar as collections restaurantes e pokemons
```
rbarros:~/workspace (master) $ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file db/restaurantes.json
connected to: 127.0.0.1
2015-11-23T15:02:48.260+0000 dropping: be-mean.restaurantes
2015-11-23T15:02:49.253+0000 check 9 25359
2015-11-23T15:02:49.262+0000 imported 25359 objects

rbarros:~/workspace (master) $ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file db/pokemons.json
connected to: 127.0.0.1
2015-11-23T15:03:13.194+0000 dropping: be-mean.pokemons
2015-11-23T15:03:13.211+0000 check 9 610
2015-11-23T15:03:13.211+0000 imported 610 objects
```


## 2. Distinct por `cuisine` na restaurantes
```
db.restaurantes.distinct('cuisine')
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

## 3. Distinct por `types` na pokemons
```
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
```

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```
var query = {};

db.pokemons.find(query).limit(5).skip(5 * 0)
{
        "_id" : ObjectId("564b1dad25337263280d0479"),
        "attack" : 56,
        "created" : "2013-11-03T15:05:41.305777",
        "defense" : 35,
        "height" : "3",
        "hp" : 30,
        "name" : "Rattata",
        "speed" : 72,
        "types" : [
                "normal"
        ]
}
{
        "_id" : ObjectId("564b1dad25337263280d047a"),
        "attack" : 52,
        "created" : "2013-11-03T15:05:41.271082",
        "defense" : 43,
        "height" : "6",
        "hp" : 39,
        "name" : "Charmander",
        "speed" : 65,
        "types" : [
                "fire"
        ]
}
{
        "_id" : ObjectId("564b1dad25337263280d047b"),
        "attack" : 64,
        "created" : "2013-11-03T15:05:41.273462",
        "defense" : 58,
        "height" : "11",
        "hp" : 58,
        "name" : "Charmeleon",
        "speed" : 80,
        "types" : [
                "fire"
        ]
}
{
        "_id" : ObjectId("564b1dad25337263280d047c"),
        "attack" : 63,
        "created" : "2013-11-03T15:05:41.280718",
        "defense" : 80,
        "height" : "10",
        "hp" : 59,
        "name" : "Wartortle",
        "speed" : 58,
        "types" : [
                "water"
        ]
}
{
        "_id" : ObjectId("564b1dad25337263280d047d"),
        "attack" : 83,
        "created" : "2013-11-03T15:05:41.282985",
        "defense" : 100,
        "height" : "16",
        "hp" : 79,
        "name" : "Blastoise",
        "speed" : 78,
        "types" : [
                "water"
        ]
}

db.pokemons.find(query).limit(5).skip(5 * 1)
{
        "_id" : ObjectId("564b1dad25337263280d047e"),
        "attack" : 30,
        "created" : "2013-11-03T15:05:41.285736",
        "defense" : 35,
        "height" : "3",
        "hp" : 45,
        "name" : "Caterpie",
        "speed" : 45,
        "types" : [
                "bug"
        ]
}
{
        "_id" : ObjectId("564b1dad25337263280d047f"),
        "attack" : 20,
        "created" : "2013-11-03T15:05:41.288107",
        "defense" : 55,
        "height" : "7",
        "hp" : 50,
        "name" : "Metapod",
        "speed" : 30,
        "types" : [
                "bug"
        ]
}
{
        "_id" : ObjectId("564b1dad25337263280d0480"),
        "attack" : 45,
        "created" : "2013-11-03T15:05:41.290411",
        "defense" : 50,
        "height" : "11",
        "hp" : 60,
        "name" : "Butterfree",
        "speed" : 70,
        "types" : [
                "flying",
                "bug"
        ]
}
{
        "_id" : ObjectId("564b1dad25337263280d0481"),
        "attack" : 60,
        "created" : "2013-11-03T15:05:41.310402",
        "defense" : 30,
        "height" : "3",
        "hp" : 40,
        "name" : "Spearow",
        "speed" : 70,
        "types" : [
                "normal",
                "flying"
        ]
}
{
        "_id" : ObjectId("564b1dad25337263280d0482"),
        "attack" : 25,
        "created" : "2013-11-03T15:05:41.294947",
        "defense" : 50,
        "height" : "6",
        "hp" : 45,
        "name" : "Kakuna",
        "speed" : 35,
        "types" : [
                "poison",
                "bug"
        ]
}

db.pokemons.find(query).limit(5).skip(5 * 2)
{
        "_id" : ObjectId("564b1dae25337263280d0483"),
        "attack" : 65,
        "created" : "2013-11-03T15:05:41.439497",
        "defense" : 55,
        "height" : "8",
        "hp" : 52,
        "name" : "Farfetchd",
        "speed" : 60,
        "types" : [
                "normal",
                "flying"
        ]
}
{
        "_id" : ObjectId("564b1dae25337263280d0484"),
        "attack" : 35,
        "created" : "2013-11-03T15:05:41.435237",
        "defense" : 70,
        "height" : "3",
        "hp" : 25,
        "name" : "Magnemite",
        "speed" : 45,
        "types" : [
                "steel",
                "electric"
        ]
}
{
        "_id" : ObjectId("564b1dae25337263280d0485"),
        "attack" : 60,
        "created" : "2013-11-03T15:05:41.437483",
        "defense" : 95,
        "height" : "10",
        "hp" : 50,
        "name" : "Magneton",
        "speed" : 70,
        "types" : [
                "steel",
                "electric"
        ]
}
{
        "_id" : ObjectId("564b1dae25337263280d0486"),
        "attack" : 85,
        "created" : "2013-11-03T15:05:41.441502",
        "defense" : 45,
        "height" : "14",
        "hp" : 35,
        "name" : "Doduo",
        "speed" : 75,
        "types" : [
                "normal",
                "flying"
        ]
}
{
        "_id" : ObjectId("564b1dae25337263280d0487"),
        "attack" : 45,
        "created" : "2013-11-03T15:05:41.445749",
        "defense" : 55,
        "height" : "11",
        "hp" : 65,
        "name" : "Seel",
        "speed" : 45,
        "types" : [
                "water"
        ]
}
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
db.pokemons.group({
    initial: { total: 0 },
    reduce:  function(cur, result) {
        cur.types.forEach(function(type) {
            if (result[type]) {
                result[type]++;
            } else {
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
```

## 6. Realizar 3 counts na pokemons.

-> .count -- todos
```
var query = {}
db.pokemons.count(query)
610
```
-> .count -- só tipo fogo
```
var query = {types:'fire'};
db.pokemons.count(query)
47
```
-> .count -- só de quantos tem a defesa maior que 70
```
var query = {defense: {$gt: 70}}
db.pokemons.count(query)
250
```