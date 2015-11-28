# MongoDB - Aula 05 - Exercício  
Autor: Ednilson Amaral


## Importar as collections restaurantes e pokemons

```  
ednilson@EDNILSON-NB:/var/www/be-mean-instagram-mongodb$ mongoimport --db be-mean --collection pokemons --drop --file pokemons.json  
2015-11-19T19:37:34.451-0200	connected to: localhost  
2015-11-19T19:37:34.451-0200	dropping: be-mean.pokemons  
2015-11-19T19:37:34.686-0200	imported 610 documents  

be-mean> show collections  
pokemons     →  0.100MB / 0.004MB  
restaurantes → 10.138MB / 3.961MB  
```


## Distinct por cuisine na collection restaurante

```  
be-mean> db.restaurantes.distinct('cuisine').sort()  
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


## Distinct por types na collection pokemons

```  
be-mean> db.pokemons.distinct('types').sort()  
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


## As primeiras 3 páginas com .limit() e .skip() de pokemons (de 5 em 5)

```  
be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(0)  
{  
  "name": "Rattata"  
}  
{  
  "name": "Charmeleon"  
}  
{  
  "name": "Charmander"  
}  
{  
  "name": "Wartortle"  
}  
{  
  "name": "Caterpie"  
}  
Fetched 5 record(s) in 5ms  

be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5)  
{  
  "name": "Blastoise"  
}  
{  
  "name": "Metapod"  
}  
{  
  "name": "Spearow"  
}  
{  
  "name": "Butterfree"  
}  
{  
  "name": "Kakuna"  
}  
Fetched 5 record(s) in 6ms  

be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(10)  
{  
  "name": "Magnemite"  
}  
{  
  "name": "Farfetchd"  
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
Fetched 5 record(s) in 4ms  
```


## Group ou Aggregate contando a quantidade de pokemons de cada tipo

```  
be-mean> db.pokemons.group({  
initial: {total: 0},  
reduce: function(curr, result){  
curr.types.forEach(function(type){  
if(result[type]){  
result[type]++;  
} else {  
result[type] = 1;  
}  
result.total++;  
});  
}  
})  
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

## Realizar 3 counts na collection pokemons

### .count -> todos  

```  
be-mean> db.pokemons.count()  
610  
```


### .count -> só tipo fogo

```  
be-mean> db.pokemons.count({types: 'fire'})  
47  
```


### .count -> só de quantos tem a defesa maior que 70

```  
be-mean> db.pokemons.count({defense: {$gt: 70}})  
250  
```