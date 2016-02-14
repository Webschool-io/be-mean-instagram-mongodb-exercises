# MongoDB - Aula 04 - Exercício
User: viniciusvsl
autor: Vinicius da Silva Lourenço

# Importar as collections `restaurantes` e `pokemons`.
```
mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
2016-02-12T22:16:14.554-0300	connected to: localhost
2016-02-12T22:16:14.555-0300	dropping: be-mean.pokemons
2016-02-12T22:16:14.725-0300	imported 610 documents

mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2016-02-13T21:09:42.742-0300	connected to: localhost
2016-02-13T21:09:42.744-0300	dropping: be-mean.restaurantes
2016-02-13T21:09:44.076-0300	imported 25359 documents
```

# Distinct por `cuisine` na restaurantes.
```
be-mean> db.restaurantes.distinct('cuisine')
[
 "Bakery",
 "Hamburgers",
 "Jewish/Kosher",
 "American ",
 "Delicatessen",
 "Irish",
 "Ice Cream, Gelato, Yogurt, Ices",
 "Chinese",
 "Chicken",
 "Caribbean",
 "Turkish",
 "Donuts",
 "Sandwiches/Salads/Mixed Buffet",
 "Bagels/Pretzels",
 "Continental",
 "Pizza",
 "Steak",
 "Polish",
 "Italian",
 "German",
 "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
 "French",
 "Pizza/Italian",
 "Mexican",
 "Spanish",
 "Café/Coffee/Tea",
 "Pancakes/Waffles",
 "Soul Food",
 "Tex-Mex",
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
 "Asian",
 "Middle Eastern",
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

# Distinct por `types` na pokemons.
```
db.pokemons.distinct('types')
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

# As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).
```
be-mean> db.pokemons.find({},{name:1}).limit(5).skip(5*0)
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "name": "Charmander"
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "name": "Charmeleon"
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "name": "Blastoise"
}
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "name": "Metapod"
}
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "name": "Caterpie"
}
Fetched 5 record(s) in 3ms

db.pokemons.find({},{name:1}).limit(5).skip(5*1)
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "name": "Spearow"
}
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "name": "Rattata"
}
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "name": "Farfetchd"
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "name": "Wartortle"
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "name": "Kakuna"
}
Fetched 5 record(s) in 3ms

db.pokemons.find({},{name:1}).limit(5).skip(5*2)
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
{
  "_id": ObjectId("564b1dae25337263280d0488"),
  "name": "Dodrio"
}
Fetched 5 record(s) in 3ms
```

# Group ou Aggregate contando a quantidade de pokemons de cada tipo.
```
db.pokemons.group({
  initial: {total: 0},
  reduce: function(curr, result){
    curr.types.forEach(function(type){
        if(result[type]>0){
            result[type]++;
        }else{
          result[type]=1;
        }
        result.total++;
      })
  }
  })
[
  {
    "total": 915,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "normal": 78,
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

# Realizar 3 counts na pokemons.
```
be-mean> db.pokemons.count({types:/fire/i, attack:{$gte:70}})
30

be-mean> db.pokemons.count({defense:{$gt:60}, attack:{$lt:80}})
139

be-mean> db.pokemons.count({types:{$all:[/fire/i, /flying/i]}})
5
```
