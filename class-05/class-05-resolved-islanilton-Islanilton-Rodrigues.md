# MongoDB - Aula 05 - Exercício  
Autor: Islanilton Rodrigues


## 1 - Importar as collections restaurantes e pokemons

```  
islanilton@ubuntu-dev:~/Documentos/Video aulas/Webscholl/be-mean/mongo-db/JSON$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
connected to: 127.0.0.1
2015-11-21T23:30:21.243-0300 dropping: be-mean.pokemons
2015-11-21T23:30:21.279-0300 check 9 610
2015-11-21T23:30:21.281-0300 imported 610 objects

ubuntu-dev(mongod-2.6.3) be-mean> show collections
pokemons       →  0.140MB /  0.164MB
restaurantes   → 14.040MB / 21.465MB
system.indexes →  0.000MB /  0.008MB
```


## 2 - Distinct por cuisine na collection restaurante

```  
ubuntu-dev(mongod-2.6.3) be-mean> db.restaurantes.distinct('cuisine');
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

ubuntu-dev(mongod-2.6.3) be-mean> db.restaurantes.distinct('cuisine').length;
85
```


## 3 - Distinct por types na collection pokemons

```  
ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.distinct('types').sort();
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

ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.distinct('types').length;
18
 ```

## 4 - As primeiras 3 páginas com .limit() e .skip() de pokemons (de 5 em 5)

```  
ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip();
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
Fetched 5 record(s) in 26ms

ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1);
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
Fetched 5 record(s) in 2ms

ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 3);
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

```


## 5 - Group ou Aggregate contando a quantidade de pokemons de cada tipo
```  
ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.group({
...   initial: {total: 0},
...   reduce: function(current, result){
...     current.types.forEach(function(type){
...       if(result[type]){
...         result[type]++;
...       }else{
...         result[type] = 1;
...       }
...       result.total++;
...     });
...   }
... });
[
  {
    "total": 915,
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
```


## 6 - Realizar 3 counts na collection pokemons

### .count -> todos  

```  
ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.count();
610
```

### .count -> só tipo ghost

```  
ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.count({types: 'ghost'});
34
```


### .count -> só que tem attack maior ou igual a 106 e do tipo fire

```  
ubuntu-dev(mongod-2.6.3) be-mean> db.pokemons.count({attack:{$gte: 106}, types:"fire"});
7

```
