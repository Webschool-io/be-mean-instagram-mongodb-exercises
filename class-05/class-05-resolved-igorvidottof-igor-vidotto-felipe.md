# MongoDB - Aula 05 - Exercício
autor: **Igor Vidotto Felipe**

**1 -** Importar as collections restaurantes e pokemons.

#### Restaurantes
```
mongoimport -h 127.0.0.1 -d be-mean -c restaurantes --drop --file restaurantes.json
```

##### Saída

>```
2015-11-21T18:02:40.681-0200  connected to: 127.0.0.1
2015-11-21T18:02:40.681-0200  dropping: be-mean.restaurantes
2015-11-21T18:02:42.061-0200  imported 25359 documents
```

#### Pokemons

```
mongoimport -h 127.0.0.1 -d be-mean -c pokemons --drop --file pokemons.json
```

##### Saída

>```
2015-11-21T18:04:48.654-0200  connected to: 127.0.0.1
2015-11-21T18:04:48.654-0200  dropping: be-mean.pokemons
2015-11-21T18:04:48.673-0200  imported 610 documents
```


**2 -** Distinct por `cuisine` na restaurantes.

```
db.restaurantes.distinct("cuisine");
```

##### Saída

>```
[
  "Bakery",
  "Irish",
  "American ",
  "Jewish/Kosher",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
  "Other",
  "Chicken",
  "Hamburgers",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Bagels/Pretzels",
  "Continental",
  "Pizza",
  "Sandwiches/Salads/Mixed Buffet",
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

**3 -** Distinct por `types` na pokemons.

```
db.pokemons.distinct("types");
```

##### Saída

>```
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

**4 -** As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5).

#### Primeira página:
```
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0);
```

##### Saída

>```
{
  "name": "Rattata"
}
{
  "name": "Charmander"
}
{
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}
{
  "name": "Metapod"
}
```

#### Segunda página:
```
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1);
```

##### Saída

>```
{
  "name": "Caterpie"
}
{
  "name": "Butterfree"
}
{
  "name": "Spearow"
}
{
  "name": "Charmeleon"
}
{
  "name": "Kakuna"
}
```

#### Terceira página:
```
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2);
```

##### Saída

>```
{
  "name": "Farfetchd"
}
{
  "name": "Magnemite"
}
{
  "name": "Doduo"
}
{
  "name": "Magneton"
}
{
  "name": "Seel"
}
```


**5 -** Group ou Aggregate contando a quantidade de pokemons de cada tipo.

> Tendo em vista a resposta correta é necessário aplicar a condição de que somente serão incluídos pokémons com defesa maior que 40. - Igor Vidotto


```javascript
db.pokemons.group({
  initial: {total: 0},
  cond: {defense: {$gt: 40}},
  reduce: function(cur, result){
    cur.types.forEach(function(type){
      result.total++;
      if(result[type]){
        result[type]++;
      } else{
        result[type] = 1;
      }
    });
  }
});
```

##### Saída

>```
[
  {
    "total": 796,
    "fire": 41,
    "water": 92,
    "bug": 54,
    "flying": 67,
    "poison": 45,
    "normal": 59,
    "steel": 37,
    "electric": 31,
    "ice": 21,
    "fighting": 33,
    "grass": 67,
    "ground": 47,
    "fairy": 21,
    "psychic": 55,
    "rock": 45,
    "dark": 30,
    "dragon": 20,
    "ghost": 31
  }
]
```

**6 -** Realizar 3 counts na pokemons: 

#### -> .count -- todos 

```
db.pokemons.count();
```

##### Saída

>```
610
```

#### -> .count -- só tipo fogo 

```
db.pokemons.count({types: "fire"});
```

##### Saída

>```
47
```

#### -> .count -- só de quantos tem a defesa maior que 70

```
db.pokemons.count({defense: {$gt: 70}});
```

##### Saída

>```
250
```




