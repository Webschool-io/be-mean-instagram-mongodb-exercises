# MongoDB - Aula 05 - Exercício
Autor: Simone Amorim

##1. Importar as collections `restaurantes` e `pokemons`.

**Restaurantes**
```javascript
C:\Users\simone>mongoimport --db be-mean-pokemons --collection restaurantes --drop --file C:\Users\simone\Documents\GitHub\be-mean-instagran\mongodb-exercises\restaurantes.json
2016-02-04T01:51:08.444-0200    connected to: localhost
2016-02-04T01:51:08.448-0200    dropping: be-mean-pokemons.restaurantes
2016-02-04T01:51:10.181-0200    imported 25359 documents
```
<br/>
**Pokemons**
```javascript
C:\Users\simone>mongoimport --host 127.0.0.1 --db be-mean-pokemons --collection pokemons --drop --file C:\Users\simone\Documents\GitHub\be-mean-instagran\mongodb-exercises\pokemons.json
2016-02-04T01:50:53.982-0200    connected to: 127.0.0.1
2016-02-04T01:50:53.986-0200    dropping: be-mean-pokemons.pokemons
2016-02-04T01:50:54.036-0200    imported 610 documents
```
<br/>
##2. Distinct por `cuisine` na collection `restaurantes`, ordenando alfabeticamente os resultados.
```javascript
db.restaurantes.distinct("cuisine").sort()
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
<br/>
##3. Distinct por `types` na collection `pokemons`, ordenando alfabeticamente os resultados.
```javascript
db.pokemons.distinct("types").sort()
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
<br/>
##4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
```javascript
//Primeira Página
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{ "name" : "Charmander" }
{ "name" : "Rattata" }
{ "name" : "Wartortle" }
{ "name" : "Blastoise" }
{ "name" : "Caterpie" }

// Segunda Página
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{ "name" : "Charmeleon" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }

// Terceira Página
db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Doduo" }
{ "name" : "Magneton" }
{ "name" : "Seel" }
```
<br/>
##5. Group ou Aggregate contando a quantidade de `pokemons` de cada tipo
```javascript
db.pokemons.group({
  initial: { total: 0},
  reduce: function(curr, result) {
    curr.types.forEach(function(type){
      if (result[type]) {
        result[type]++;
      }else{
        result[type] = 1;
      }
      result.total++;
    });
  },
})
[
        {
                "total" : 915,
                "fire" : 47,
                "normal" : 78,
                "water" : 105,
                "bug" : 61,
                "flying" : 77,
                "poison" : 54,
                "steel" : 37,
                "electric" : 40,
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
<br/>
##6. Realizar 3 counts na collection `pokemons`.
```javascript
// Primeiro
db.pokemons.count({defense: {$gte: 75}, types: 'poison'})
14

// Segundo
db.pokemons.count({attack: {$lte: 75}, types: 'normal'})
43

// Terceiro
db.pokemons.count({height: {$gt: '5'}})
146

```
