# MongoDB - Aula 05 - Exercício
# Autor: Fábio de Carvalho

### 1. Importar as collections restaurantes.json e pokemons.json
#### Restaurantes
```
Admin@Admin-PC MINGW64 ~/Desktop/Code/be-mean-instagram-mongodb/exercises (master)
$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
```

>```
2015-11-22T09:09:37.609-0200    connected to: 127.0.0.1
2015-11-22T09:09:37.611-0200    dropping: be-mean.restaurantes
2015-11-22T09:09:38.848-0200    imported 25359 documents
```

#### Pokemons
```
Admin@Admin-PC MINGW64 ~/Desktop/Code/be-mean-instagram-mongodb/exercises (master)
$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
```

>```
2015-11-22T09:10:23.351-0200    connected to: 127.0.0.1
2015-11-22T09:10:23.354-0200    dropping: be-mean.pokemons
2015-11-22T09:10:23.384-0200    imported 610 documents
```

### 2. Distinct por `cuisine` na restaurantes.json
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
```

>```
[
    "Irish",
    "Hamburgers",
    "American ",
    "Jewish/Kosher",
    "Delicatessen",
    "Ice Cream, Gelato, Yogurt, Ices",
    "Chinese",
    "Other",
    "Bakery",
    "Chicken",
    "Turkish",
    "Caribbean",
    "Donuts",
    "Sandwiches/Salads/Mixed Buffet",
    "Continental",
    "Bagels/Pretzels",
    "Pizza",
    "Steak",
    "Italian",
    "Polish",
    "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
    "French",
    "German",
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

### 3. Distinct por `types` na pokemons.json
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.distinct('types')
```

>```
[
    "fire",
    "water",
    "bug",
    "flying",
    "normal",
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

### 4. As primeiras 3 páginas com .limit() e skip() de pokemons de 5 em 5

**Página 1:**
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find({}, {_id: 1, name: 1}).limit(5).skip(5 * 0)
```

>```
{ "_id": ObjectId("564b1dad25337263280d047a"), "name": "Charmander" }
{ "_id": ObjectId("564b1dad25337263280d047b"), "name": "Charmeleon" }
{ "_id": ObjectId("564b1dad25337263280d047d"), "name": "Blastoise" }
{ "_id": ObjectId("564b1dad25337263280d047c"), "name": "Wartortle" }
{ "_id": ObjectId("564b1dad25337263280d047e"), "name": "Caterpie" }
Fetched 5 record(s) in 5ms
```

**Página 2:**
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find({}, {_id: 1, name: 1}).limit(5).skip(5 * 1)
```

>```
{ "_id": ObjectId("564b1dad25337263280d047f"), "name": "Metapod" }
{ "_id": ObjectId("564b1dad25337263280d0480"), "name": "Butterfree" }
{ "_id": ObjectId("564b1dad25337263280d0481"), "name": "Spearow" }
{ "_id": ObjectId("564b1dad25337263280d0482"), "name": "Kakuna" }
{ "_id": ObjectId("564b1dae25337263280d0483"), "name": "Farfetchd" }
Fetched 5 record(s) in 4ms
```

**Página 3:**
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find({}, {_id: 1, name: 1}).limit(5).skip(5 * 2)
```

>```
{ "_id": ObjectId("564b1dae25337263280d0484"), "name": "Magnemite" }
{ "_id": ObjectId("564b1dae25337263280d0486"), "name": "Doduo" }
{ "_id": ObjectId("564b1dae25337263280d0485"), "name": "Magneton" }
{ "_id": ObjectId("564b1dae25337263280d0487"), "name": "Seel" }
{ "_id": ObjectId("564b1dae25337263280d0488"), "name": "Dodrio" }
Fetched 5 record(s) in 4ms
```

### 5. Group ou Aggregate contando a quantidade de cada pokemon por tipo
```javascript
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.group({
...   initial: { total: 0 },
...   reduce: function(curr, result) {
...     curr.types.forEach(function(type) {
...       result[type] ? result[type]++ : result[type] = 1;
...       result.total++;
...     });
...   }
... });
```

>```
[
    {
        "total": 915,
        "fire": 47,
        "water": 105,
        "bug": 61,
        "flying": 77,
        "normal": 78,
        "poison": 54,
        "steel": 37,
        "electric": 40,
        "ice": 24,
        "ghost": 34,
        "fighting": 38,
        "psychic": 62,
        "grass": 75,
        "ground": 51,
        "fairy": 28,
        "rock": 46,
        "dark": 38,
        "dragon": 20
    }
]
```

### 6. Realizar 3 .count() na pokemons.
#### .count() -> Todos
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.count({})
```

>```
610
```

#### .count() -> Por tipo: Fogo
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.count({ types: /fire/i })
```

>```
47
```

#### .count() -> Defesa maior que 70
```
Admin-PC(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.count({ defense: { $gt: 70 } })
```

>```
250
```