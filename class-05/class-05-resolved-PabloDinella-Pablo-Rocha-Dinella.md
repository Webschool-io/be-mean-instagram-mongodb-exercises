# MongoDb - Aula 05 - Exercício
autor: Pablo R. Dinella

# 1. Importar as collections restaurantes e pokemons

```
╭─owner@Pablos-MacBook-Air  ~/Projetos/be-mean ‹›
╰─$ mongoimport --db be-mean-instagram --collection pokemons --drop --file ~/Downloads/pokemons.json
╭─owner@Pablos-MacBook-Air  ~/Projetos/be-mean ‹›
╰─$ mongoimport --db be-mean-instagram --collection pokemons --drop --file ~/Downloads/restaurantes.json

```

# 2. Distinct por `cuisine` na collection restaurantes

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "American ",
  "Hamburgers",
  "Jewish/Kosher",
  "Irish",
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
  "German",
  "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
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

# 3. Distinct por `types` na collection pokemons

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.distinct('types')
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

# 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.find({},{name:1}).limit(5).skip(5*0)
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "name": "Rattata"
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
  "_id": ObjectId("564b1dad25337263280d047a"),
  "name": "Charmander"
}
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "name": "Caterpie"
}
Fetched 5 record(s) in 5ms
Pablos-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.find({},{name:1}).limit(5).skip(5*1)
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
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "name": "Farfetchd"
}
Fetched 5 record(s) in 6ms
Pablos-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.find({},{name:1}).limit(5).skip(5*2)
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "name": "Magneton"
}
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "name": "Magnemite"
}
{
  "_id": ObjectId("564b1dae25337263280d0486"),
  "name": "Doduo"
}
{
  "_id": ObjectId("564b1dae25337263280d0488"),
  "name": "Dodrio"
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "name": "Seel"
}
Fetched 5 record(s) in 9ms
```

# 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```javascript
db.pokemons.group({
  initial: { total: 0 },
  reduce: function(curr, result) {
    curr.types.forEach(function(type){
      if (result[type]) {
        result[type]++;
      } else {
        result[type] = 1;
      }
      result.total++;
    })
  }
});
```

# 6. Realizar 3 counts na collection pokemons (de todos, só do tipo fogo e só de quantos têm a defesa maior que 70)

```
Pablos-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.count()
610
Pablos-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.count({types: "fire"})
47
Pablos-MacBook-Air(mongod-3.0.7) be-mean-instagram> db.pokemons.count({defense: {$gt: 70}})
250
```
