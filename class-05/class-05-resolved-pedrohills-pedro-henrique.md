# MongoDB - Aula 05 - Exercício
autor: Pedro Henrique

## 1. Importar as collections restaurantes e pokemons
```js
E:\>mongoimport --db be-mean -c pokemons --drop --file E:/mongodb/pokemons.json.txt
2015-11-18T23:53:28.774-0200    connected to: localhost
2015-11-18T23:53:28.778-0200    dropping: be-mean.pokemons
2015-11-18T23:53:28.895-0200    imported 610 documents

E:\>mongoimport --db be-mean -c restaurantes --drop --file E:/mongodb/restaurantes.json
2015-11-18T23:55:43.213-0200    connected to: localhost
2015-11-18T23:55:43.214-0200    dropping: be-mean.restaurantes
2015-11-18T23:55:44.405-0200    imported 25359 documents
```


## 2. Distinct por `cuisine` na restaurantes
```js
> db.restaurantes.distinct('cuisine')
[
        "Hamburgers",
        "Irish",
        "Bakery",
        "American ",
        "Jewish/Kosher",
        "Delicatessen",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Other",
        "Chinese",
        "Chicken",
        "Turkish",
        "Caribbean",
        "Donuts",
        "Sandwiches/Salads/Mixed Buffet",
        "Bagels/Pretzels",
        "Pizza",
        "Continental",
        "Steak",
        "Italian",
        "Polish",
        "German",
        "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
        "French",
        "Pizza/Italian",
        "Mexican",
        "Spanish",
        "Café/Coffee/Tea",
        "Tex-Mex",
        "Pancakes/Waffles",
        "Soul Food",
        "Seafood",
        "Not Listed/Not Applicable",
        "Greek",
        "Hotdogs",
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
```js
> db.pokemons.distinct('types')
[
        "fire",
        "water",
        "normal",
        "flying",
        "bug",
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
```js
// Página 1
> db.pokemons.find().limit(5).skip(5 * 0).pretty()
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

// Página 2
> db.pokemons.find().limit(5).skip(5 * 1).pretty()
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

// Página 3
> db.pokemons.find().limit(5).skip(5 * 2).pretty()
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
{
        "_id" : ObjectId("564b1dae25337263280d0489"),
        "attack" : 70,
        "created" : "2013-11-03T15:05:41.447897",
        "defense" : 80,
        "height" : "17",
        "hp" : 90,
        "name" : "Dewgong",
        "speed" : 70,
        "types" : [
                "water",
                "ice"
        ]
}
{
        "_id" : ObjectId("564b1dae25337263280d0488"),
        "attack" : 110,
        "created" : "2013-11-03T15:05:41.443720",
        "defense" : 70,
        "height" : "18",
        "hp" : 60,
        "name" : "Dodrio",
        "speed" : 100,
        "types" : [
                "normal",
                "flying"
        ]
}

// Página 4 - BONUS
> db.pokemons.find().limit(5).skip(5 * 3).pretty()
{
        "_id" : ObjectId("564b1dae25337263280d048a"),
        "attack" : 35,
        "created" : "2013-11-03T15:05:41.457865",
        "defense" : 30,
        "height" : "13",
        "hp" : 30,
        "name" : "Gastly",
        "speed" : 80,
        "types" : [
                "poison",
                "ghost"
        ]
}
{
        "_id" : ObjectId("564b1daf25337263280d048d"),
        "attack" : 50,
        "created" : "2013-11-03T15:05:41.388462",
        "defense" : 40,
        "height" : "6",
        "hp" : 40,
        "name" : "Poliwag",
        "speed" : 90,
        "types" : [
                "water"
        ]
}
{
        "_id" : ObjectId("564b1dae25337263280d048c"),
        "attack" : 105,
        "created" : "2013-11-03T15:05:41.452237",
        "defense" : 75,
        "height" : "12",
        "hp" : 105,
        "name" : "Muk",
        "speed" : 50,
        "types" : [
                "poison"
        ]
}
{
        "_id" : ObjectId("564b1daf25337263280d048e"),
        "attack" : 65,
        "created" : "2013-11-03T15:05:41.390744",
        "defense" : 65,
        "height" : "10",
        "hp" : 65,
        "name" : "Poliwhirl",
        "speed" : 90,
        "types" : [
                "water"
        ]
}
{
        "_id" : ObjectId("564b1dae25337263280d048b"),
        "attack" : 95,
        "created" : "2013-11-03T15:05:41.456387",
        "defense" : 180,
        "height" : "15",
        "hp" : 50,
        "name" : "Cloyster",
        "speed" : 70,
        "types" : [
                "water",
                "ice"
        ]
}
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo
```js
> db.pokemons.group({
...         initial: {total: 0},
...         reduce: function(current, result){
...                 result.total++;
...                 current.types.forEach(function(type){
...                         if(result[type]){
...                                 result[type]++;
...                         } else {
...                                 result[type] = 1;
...                         }
...                 });
...         }
... });
[
        {
                "total" : 610,
                "fire" : 47,
                "water" : 105,
                "normal" : 78,
                "flying" : 77,
                "bug" : 61,
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
-> .count -- só tipo fogo
-> .count -- só de quantos tem a defesa maior que 70

```js
// .count -- todos
> db.pokemons.count()
610


// .count -- só tipo fogo
> db.pokemons.count({types: "fire"})
47

// .count -- só de quantos tem a defesa maior que 70
> db.pokemons.count({defense: {$gt: 70}})
250

```