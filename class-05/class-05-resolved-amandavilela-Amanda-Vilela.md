# MongoDB - Aula 05 - Exercício

autor: Amanda Vilela

## 1. Importar as collections restaurantes e pokemons.

```
$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
connected to: 127.0.0.1
Sun Jan 24 13:26:59.234 dropping: be-mean.restaurantes
Sun Jan 24 13:27:00.118 check 9 25359
Sun Jan 24 13:27:00.165 imported 25359 objects


$ mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
connected to: 127.0.0.1
Sun Jan 24 13:28:13.820 dropping: be-mean.restaurantes
Sun Jan 24 13:28:13.843 check 9 620
Sun Jan 24 13:28:13.844 imported 620 objects


```

## 2. Distinct por cuisine na restaurantes.

```

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.restaurantes.distinct("cuisine")
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
  "Other",
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

## 3. Distinct por types na pokemons.

```

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.distinct("types")
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

## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```
amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5*0)
{
  "name": "Beedrill"
}
{
  "name": "Pidgey"
}
{
  "name": "Pidgeotto"
}
{
  "name": "Pidgeot"
}
{
  "name": "Raticate"
}
Fetched 5 record(s) in 1ms
amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5*1)
{
  "name": "Fearow"
}
{
  "name": "Pikachu"
}
{
  "name": "Ekans"
}
{
  "name": "Raichu"
}
{
  "name": "Arbok"
}
Fetched 5 record(s) in 23ms
amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.find({}, {name:1, _id:0}).limit(5).skip(5*2)
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
Fetched 5 record(s) in 1ms


```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.group({
...   initial: {total: 0},
...   reduce: function(curr, result){
...     curr.types.forEach(function(type){
...       if (result[type]){
...         result[type]++;
...       }else{
...           result[type] =1;
...       }
...       result.total++;
...     });
...   }
... });
[
  {
    "total": 934,
    "poison": 54,
    "bug": 58,
    "normal": 79,
    "flying": 81,
    "electric": 47,
    "water": 101,
    "fighting": 42,
    "psychic": 61,
    "grass": 70,
    "fairy": 31,
    "fire": 53,
    "rock": 42,
    "ice": 28,
    "ground": 53,
    "steel": 35,
    "ghost": 34,
    "dark": 35,
    "dragon": 30
  }
]



```

## 6. Realizar 3 counts na pokemons.

```

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.count()
620

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.count({"types" : "fire"})
53

amanda-Inspiron-7520(mongod-2.4.9) be-mean> db.pokemons.count({"defense" : {$gt:70}})
263


```
