### 1. Importar as collections de  pokemons.json e restaurantes.json

* Comando e resultado


```JS
// Import pokemons.json
leonardo@leonardo:~/Documentos/web-school/exercicios005-mongodb$ mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
connected to: 127.0.0.1
2015-11-22T20:00:32.170-0300 dropping: be-mean.pokemons
2015-11-22T20:00:32.247-0300 check 9 610
2015-11-22T20:00:32.247-0300 imported 610 object

// Import restaurantes.json
leonardo@leonardo:~/Documentos/web-school/exercicios005-mongodb$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
2015-11-22T20:01:39.486-0300 dropping: be-mean.restaurantes
2015-11-22T20:01:40.823-0300 check 9 25359
2015-11-22T20:01:40.951-0300 imported 25359 objects

```

### 2. Distinct por cuisine na collection restaurantes

```JS
leonardo(mongod-2.6.10) be-mean> db.restaurantes.distinct('cuisine').sort();
[
  "Afghan",
  "African",
  "American ",
  "Armenian",
  "Asian",
  "Australian",
  "Bagels/Pretzels",
  "Bakery",
  "Bangladeshi",
  "Barbecue",
  "Bottled beverages, including water, sodas, juices, etc.",
  "Brazilian",
  "CafÃ©/Coffee/Tea",
  "Café/Coffee/Tea",
  "Cajun",
  "Californian",
  "Caribbean",
  "Chicken",
  "Chilean",
  "Chinese",
  "Chinese/Cuban",
  "Chinese/Japanese",
  "Continental",
  "Creole",
  "Creole/Cajun",
  "Czech",
  "Delicatessen",
  "Donuts",
  "Eastern European",
  "Egyptian",
  "English",
  "Ethiopian",
  "Filipino",
  "French",
  "Fruits/Vegetables",
  "German",
  "Greek",
  "Hamburgers",
  "Hawaiian",
  "Hotdogs",
  "Hotdogs/Pretzels",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Indian",
  "Indonesian",
  "Iranian",
  "Irish",
  "Italian",
  "Japanese",
  "Jewish/Kosher",
  "Juice, Smoothies, Fruit Salads",
  "Korean",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
  "Mediterranean",
  "Mexican",
  "Middle Eastern",
  "Moroccan",
  "Not Listed/Not Applicable",
  "Nuts/Confectionary",
  "Other",
  "Pakistani",
  "Pancakes/Waffles",
  "Peruvian",
  "Pizza",
  "Pizza/Italian",
  "Polish",
  "Polynesian",
  "Portuguese",
  "Russian",
  "Salads",
  "Sandwiches",
  "Sandwiches/Salads/Mixed Buffet",
  "Scandinavian",
  "Seafood",
  "Soul Food",
  "Soups",
  "Soups & Sandwiches",
  "Southwestern",
  "Spanish",
  "Steak",
  "Tapas",
  "Tex-Mex",
  "Thai",
  "Turkish",
  "Vegetarian",
  "Vietnamese/Cambodian/Malaysia"
]

```

### 3. Distinct por types na collection pokemons

```JS
leonardo(mongod-2.6.10) be-mean> db.pokemons.distinct('types').sort();
[
  "bug",
  "dark",
  "dragon",
  "electric",
  "fairy",
  "fighting",
  "fire",
  "flying",
  "ghost",
  "grass",
  "ground",
  "ice",
  "normal",
  "poison",
  "psychic",
  "rock",
  "steel",
  "water"
]

```

### 4. As primeiras 3 páginas com .limit e .skip de pokemons. Pagine de (5 em 5)

```JS
var query = {};
var fields = { name: 1, _id :0 };

// Page 01
db.pokemons.find( query, fields ).limit(5).skip(5*0);
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

// Page 02
db.pokemons.find( query, fields ).limit(5).skip(5*1);

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

// Page 03
db.pokemons.find( query, fields ).limit(5).skip(5*2);
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

// Page 04
db.pokemons.find( query, fields ).limit(5).skip(5*3);

{
  "name": "Dodrio"
}
{
  "name": "Dewgong"
}
{
  "name": "Gastly"
}
{
  "name": "Cloyster"
}
{
  "name": "Muk"
}

// Page 05
db.pokemons.find( query, fields ).limit(5).skip(5*4);
{
  "name": "Poliwag"
}
{
  "name": "Poliwhirl"
}
{
  "name": "Poliwrath"
}
{
  "name": "Abra"
}
{
  "name": "Kadabra"
}
```

### 5. Faça um Group ou Aggregate contando a quantidade de pokemons de cada tipo, usamos com group ou aggregate.

```JS
// Using group
db.pokemons.group({
  initial : {},
  reduce  : function (current, result) {
    current.types.forEach( function( type ) {
      ( result[type] ) ? result[type]++ : result[type] = 1;
    });
  }
});
// Result
[
  {
    "normal": 78,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
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

// Using Aggregate
db.pokemons.aggregate([
  { $unwind : "$types" },
  {
    $group : { 
      _id   : "$types",
      total : { $sum : 1 },
    }
  }
]);

// result
{
  "result": [
    {
      "_id": "fairy",
      "total": 28
    },
    {
      "_id": "psychic",
      "total": 62
    },
    {
      "_id": "fighting",
      "total": 38
    },
    {
      "_id": "dark",
      "total": 38
    },
    {
      "_id": "ground",
      "total": 51
    },
    {
      "_id": "grass",
      "total": 75
    },
    {
      "_id": "electric",
      "total": 40
    },
    {
      "_id": "steel",
      "total": 37
    },
    {
      "_id": "rock",
      "total": 46
    },
    {
      "_id": "flying",
      "total": 77
    },
    {
      "_id": "fire",
      "total": 47
    },
    {
      "_id": "ice",
      "total": 24
    },
    {
      "_id": "bug",
      "total": 61
    },
    {
      "_id": "poison",
      "total": 54
    },
    {
      "_id": "ghost",
      "total": 34
    },
    {
      "_id": "dragon",
      "total": 20
    },
    {
      "_id": "water",
      "total": 105
    },
    {
      "_id": "normal",
      "total": 78
    }
  ],
  "ok": 1
}

```

### 6. Realizar 3 counts na collections pokemons

.count -- todos

```JS
leonardo(mongod-2.6.10) be-mean> db.pokemons.count();
610
```

.count -- apenas do tipo fogo
```JS
leonardo(mongod-2.6.10) be-mean> db.pokemons.count({types:"fire"});
47
```

.count -- só dos que tem a defesa maior que 70
```JS
leonardo(mongod-2.6.10) be-mean> db.pokemons.count({ defense : { $gt : 70 } });
250
```