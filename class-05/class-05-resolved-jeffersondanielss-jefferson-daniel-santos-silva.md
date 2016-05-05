# MongoDB - Aula 05 - Exercício
autor: Jefferson Daniel (https://github.com/jeffersondanielss)

# 1. Importar as collections restaurantes e pokemons

```
  mongoimport --host localhost --db be-mean --collection pokemons --drop --file pokemons.json
  2015-11-21T12:15:21.371-0200    connected to: localhost
  2015-11-21T12:15:21.376-0200    dropping: be-mean.pokemons
  2015-11-21T12:15:21.450-0200    imported 610 documents

  mongoimport --host localhost --db be-mean --collection restaurantes --drop --file restaurantes.json
  2015-11-21T12:16:14.228-0200    connected to: localhost
  2015-11-21T12:16:14.233-0200    dropping: be-mean.restaurantes
  2015-11-21T12:16:17.145-0200    imported 25359 documents
```

# 2. distict por `cuisine` na restaurantes

```
  > db.restaurantes.distinct('cuisine').sort()
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

# 3. Distinct por `types` na pokemons

```
  > db.pokemons.distinct('types')
  [
    "fire",
    "normal",
    "water",
    "bug",
    "flying",
    "poison",
    "electric",
    "steel",
    "ice",
    "fighting",
    "psychic",
    "grass",
    "ground",
    "fairy",
    "ghost",
    "rock",
    "dark",
    "dragon"
  ]
```

# 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

```
  > db.pokemons.find( {}, { name: 1, _id: 0 } ).limit(5).skip(5 * 0)
  { "name" : "Charmeleon" }
  { "name" : "Rattata" }
  { "name" : "Charmander" }
  { "name" : "Wartortle" }
  { "name" : "Blastoise" }
  > db.pokemons.find( {}, { name: 1, _id: 0 } ).limit(5).skip(5 * 1)
  { "name" : "Metapod" }
  { "name" : "Caterpie" }
  { "name" : "Spearow" }
  { "name" : "Butterfree" }
  { "name" : "Kakuna" }
  > db.pokemons.find( {}, { name: 1, _id: 0 } ).limit(5).skip(5 * 2)
  { "name" : "Farfetchd" }
  { "name" : "Magnemite" }
  { "name" : "Doduo" }
  { "name" : "Seel" }
  { "name" : "Dodrio" }
```

# 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
db.pokemons.group({
  initial: { total: 0 },
  reduce: function( curr, result ) {
    curr.types.forEach(function( type ){
      if( result[type] ) {
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
    "total" : 915,
    "fire" : 47,
    "normal" : 78,
    "water" : 105,
    "bug" : 61,
    "flying" : 77,
    "steel" : 37,
    "electric" : 40,
    "poison" : 54,
    "ghost" : 34,
    "ice" : 24,
    "psychic" : 62,
    "fighting" : 38,
    "grass" : 75,
    "ground" : 51,
    "fairy" : 28,
    "rock" : 46,
    "dark" : 38,
    "dragon" : 20
  }
]
```

# 6. Realizar 3 counts na pokemons

### -> Todos

```
  > db.pokemons.count()
  610
```

### -> Só tipo fogo

```
  > db.pokemons.count( { types: 'fire' } )
  47
```

### -> Defesa maior que 70
```
  > db.pokemons.count({ defense: { $gt: 70 } })
  250
```