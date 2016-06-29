# MongoDB - Aula 05 - Exercício
autor: Gabriel Panassol


## 1. Importar as collections restaurantes e pokemons
```
Gabriel@gabriel MINGW64 ~/Documents/BeMean/MongoDB
$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2015-11-24T23:56:00.914-0200    connected to: 127.0.0.1
2015-11-24T23:56:00.915-0200    dropping: be-mean.pokemons
2015-11-24T23:56:00.973-0200    imported 610 documents

Gabriel@gabriel MINGW64 ~/Documents/BeMean/MongoDB
$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-24T23:56:16.615-0200    connected to: 127.0.0.1
2015-11-24T23:56:16.616-0200    dropping: be-mean.restaurantes
2015-11-24T23:56:18.361-0200    imported 25359 documents
```

## 2. Distinct por 'cuisine' na restaurantes 

```
> db.restaurantes.distinct('cuisine')
[
        "Hamburgers",
        "Bakery",
        "American ",
        "Jewish/Kosher",
        "Delicatessen",
        "Irish",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Chinese",
        "Other",
        "Chicken",
        "Caribbean",
        "Donuts",
        "Turkish",
        "Continental",
        "Sandwiches/Salads/Mixed Buffet",
        "Pizza",
        "Bagels/Pretzels",
        "Italian",
        "Steak",
        "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
        "Polish",
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

## 3. Distinct por 'types' na pokemons 

```
> db.pokemons.distinct('types')
[
        "normal",
        "fire",
        "water",
        "bug",
        "flying",
        "poison",
        "electric",
        "steel",
        "ghost",
        "ice",
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons de (5 em 5)

```
> db.pokemons.find({},{name:1,_id:0}).limit()
{ "name" : "Rattata" }
{ "name" : "Charmeleon" }
{ "name" : "Charmander" }
{ "name" : "Wartortle" }
{ "name" : "Caterpie" }
{ "name" : "Blastoise" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Doduo" }
{ "name" : "Seel" }
{ "name" : "Dodrio" }
{ "name" : "Gastly" }
{ "name" : "Dewgong" }
{ "name" : "Magneton" }
{ "name" : "Cloyster" }
{ "name" : "Muk" }
> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5 * 0)
{ "name" : "Rattata" }
{ "name" : "Charmeleon" }
{ "name" : "Charmander" }
{ "name" : "Wartortle" }
{ "name" : "Caterpie" }
> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5 * 1)
{ "name" : "Blastoise" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }
> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5 * 2)
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Doduo" }
{ "name" : "Seel" }
{ "name" : "Dodrio" }
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
> db.pokemons.group({
...         initial:{total:0},
...         reduce: function(curr,result){
...                 curr.types.forEach(function(type){
...                         if(result[type]){
...                                 result[type]++;
...                         }else{
...                                 result[type] = 1;
...                         }
...                         result.total++;
...                 });
...         }
... });
[
        {
                "total" : 915,
                "bug" : 61,
                "normal" : 78,
                "water" : 105,
                "fire" : 47,
                "flying" : 77,
                "poison" : 54,
                "steel" : 37,
                "electric" : 40,
                "ice" : 24,
                "ghost" : 34,
                "psychic" : 62,
                "fighting" : 38,
                "grass" : 75,
                "ground" : 51,
                "fairy" : 28,
                "rock" : 46,
                "dragon" : 20,
                "dark" : 38
        }
```

## 6. Realizar 3 counts na pokemons

```
> db.pokemons.count( { types : 'fire' } )
47
> db.pokemons.count( { types : 'electric' } )
40
> db.pokemons.count( { types : 'ghost', defense : { $gt : 70 } } )
16
> db.pokemons.count( { types : 'ghost', defense : { $gt : 70 }, attack: { $gt : 90 } } )
7
```

e um mais dificil

```
> db.pokemons.count( { $or: [ {types : 'ghost'}, {types : 'water'} ], defense : { $gt : 70 }, attack: { $gt : 90 } } )
26
```