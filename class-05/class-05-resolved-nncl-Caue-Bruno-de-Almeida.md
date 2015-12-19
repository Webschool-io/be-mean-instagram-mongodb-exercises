#MongoDB - Aula 05 - Exercício
Autor: Cauê Bruno de Almeida

### 1. Importar as collections restaurantes.json e pokemons.json

Já tinha restaurantes importado.

```
cauebrunodealmeida$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2015-11-23T22:05:43.831-0200    connected to: 127.0.0.1
2015-11-23T22:05:43.831-0200    dropping: be-mean.pokemons
2015-11-23T22:05:43.945-0200    imported 610 documents
```

### 2. Distinct por `cuisine` na restaurantes

```
be-mean> db.restaurantes.distinct('cuisine')
[
  "Irish",
  "Hamburgers",
  "Bakery",
  "American ",
  "Jewish/Kosher",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Delicatessen",
  "Chinese",
  "Other",
  "Chicken",
  "Turkish",
  "Caribbean",
  "Donuts",
  "Sandwiches/Salads/Mixed Buffet",
  "Continental",
  "Pizza",
  "Bagels/Pretzels",
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

### 3. Distinct por `types` na pokemons

```
be-mean> db.pokemons.distinct('types')
[
  "water",
  "fire",
  "normal",
  "bug",
  "flying",
  "poison",
  "electric",
  "steel",
  "ice",
  "ghost",
  "psychic",
  "fighting",
  "grass",
  "ground",
  "fairy",
  "rock",
  "dark",
  "dragon"
]
```

### 4. As primeiras 3 páginas com `.limit()` e `.skip()` de pokemons (5 em 5)

```
be-mean> db.pokemons.find({}, {name : 1}).limit(5).skip(5 * 0)
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "name": "Wartortle"
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "name": "Charmeleon"
}
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "name": "Rattata"
}
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "name": "Charmander"
}
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "name": "Caterpie"
}
Fetched 5 record(s) in 2ms


be-mean> db.pokemons.find({}, {name : 1}).limit(5).skip(5 * 1)
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "name": "Blastoise"
}
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "name": "Metapod"
}
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "name": "Butterfree"
}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "name": "Spearow"
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "name": "Kakuna"
}
Fetched 5 record(s) in 1ms

db.pokemons.find({}, {name : 1}).limit(5).skip(5 * 2)
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "name": "Farfetchd"
}
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "name": "Magnemite"
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "name": "Magneton"
}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "name": "Doduo"
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "name": "Seel"
}
Fetched 5 record(s) in 2ms
```

### 5. Group ou Agregate contando a quantidade de pokemons de cada tipo

```
db.pokemons.group( {
  initial : { total: 0 },
  reduce : function(curr, result){
    curr.types.forEach(function(type){
      if(result[type]) {
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
    "total": 915,
    "water": 105,
    "fire": 47,
    "normal": 78,
    "bug": 61,
    "flying": 77,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ice": 24,
    "ghost": 34,
    "psychic": 62,
    "fighting": 38,
    "grass": 75,
    "ground": 51,
    "fairy": 28,
    "rock": 46,
    "dark": 38,
    "dragon": 20
  }
]
```

### 6. Realizar 3 counts na pokemons.

- De todo mundo

```
be-mean> db.pokemons.count()
610
```

- Só do tipo fogo

```
be-mean> db.pokemons.count({types : 'fire'})
47
```

- Só de quantos tem a defesa maior que 70

```
be-mean> db.pokemons.count({defense: {$gt: 70}})
250
```