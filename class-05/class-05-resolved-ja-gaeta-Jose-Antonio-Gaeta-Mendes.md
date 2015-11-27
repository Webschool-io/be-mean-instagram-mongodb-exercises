# MongoDB - Aula 05 - Exercício
autor: José Antonio Gaeta Mendes

## 1. Importar as collections restaurantes e pokemons
```
be-mean-instagram-mongodb @ MacBookPro $ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2015-11-21T11:46:58.597-0200    connected to: 127.0.0.1
2015-11-21T11:46:58.597-0200    dropping: be-mean.pokemons
2015-11-21T11:46:58.613-0200    imported 610 documents

MacBookPro(mongod-3.0.7) be-mean> show collections
pokemons       →  0.140MB /  0.164MB
restaurantes   → 14.012MB / 21.465MB
system.indexes →  0.000MB /  0.008MB
```


## 2. Distinct por `cuisine` na restaurantes
```
MacBookPro(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "American ",
  "Hamburgers",
  "Bakery",
  "Irish",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
  "Chicken",
  "Caribbean",
  "Turkish",
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
MacBookPro(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
[
  "water",
  "normal",
  "fire",
  "bug",
  "flying",
  "electric",
  "steel",
  "poison",
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
MacBookPro(mongod-3.0.7) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*0)
{
  "name": "Wartortle"
}
{
  "name": "Rattata"
}
{
  "name": "Charmander"
}
{
  "name": "Blastoise"
}
{
  "name": "Charmeleon"
}
Fetched 5 record(s) in 1ms

MacBookPro(mongod-3.0.7) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*1)
{
  "name": "Caterpie"
}
{
  "name": "Butterfree"
}
{
  "name": "Metapod"
}
{
  "name": "Spearow"
}
{
  "name": "Magnemite"
}
Fetched 5 record(s) in 1ms

MacBookPro(mongod-3.0.7) be-mean> db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*2)
{
  "name": "Farfetchd"
}
{
  "name": "Kakuna"
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
Fetched 5 record(s) in 2ms
```

## 5 . Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
db.pokemons.group({
 initial: { total: 0 },
 reduce: function(curr, result){
   curr.types.forEach(function(type){
    if(result[type]){
      result[type]++;
    } else {
        result[type] = 1;
      }
    result.total++;
   })
 }
})

[
  {
    "total": 915,
    "water": 105,
    "normal": 78,
    "fire": 47,
    "bug": 61,
    "flying": 77,
    "steel": 37,
    "electric": 40,
    "poison": 54,
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

## 6. Realizar 3 counts na pokemons.

-> .count -- todos
```
db.pokemons.count();
610
```

-> .count -- só tipo fogo
```
db.pokemons.count({ types: "fire"});
47
```

-> .count -- só de quantos tem a defesa maior que 70
```
db.pokemons.count({ defense: { $gt: 70 }});
250
```