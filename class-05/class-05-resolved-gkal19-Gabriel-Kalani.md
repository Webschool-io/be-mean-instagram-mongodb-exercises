#MongoDB - Aula 05 - Exercício
autor: Gabriel Kalani


1 - Importar as collections restaurantes e pokemons

```js
  mongoimport --host 127.0.0.1 --db db --collection restaurantes --drop --file restaurantes.json
  connected to: 127.0.0.1
  2016-01-28T12:42:02.150+0000 dropping: db.restaurantes
  2016-01-28T12:42:02.940+0000 check 9 25359
  2016-01-28T12:42:03.060+0000 imported 25359 objects
```

2 - Distinct por `cuisine` na restaurantes

```js
  db.restaurantes.distinct('cuisine')
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
```

3 - Distinct por `types` na pokemons

```js
  db.pokemons.distinct('types')
  [
    "fodao",
    "fogo",
    "fdp",
    "crackudo",
    "raio",
    "esperto",
    "electric"
  ]
```

4 - As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5)

```js
  db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*0)
  {
    "name": "Metagross"
  }
  {
    "name": "Pikachu"
  }
  {
    "name": "Mewtwo"
  }
  {
    "name": "Fracomon"
  }
  {
    "name": "Kakaroto"
  }
  Fetched 5 record(s) in 6ms
  
  db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*1)
  {
    "name": "Kakaroto"
  }
  {
    "name": "Muk"
  }
  {
    "name": "Suissa"
  }
  {
    "name": "Bulbasauro"
  }
  {
    "name": "Charmander"
  }
  Fetched 5 record(s) in 1ms

  db.pokemons.find({},{name:1,_id:0}).limit(5).skip(5*2)
  {
    "name": "Squirtle"
  }
  {
    "name": "AindaNaoExisteMom"
  }
  Fetched 2 record(s) in 2ms
```

5 - Group ou Aggregate contando a quantidade de pokemons de cada tipo

```js
  db.pokemons.aggregate([
   {
     $project: {types:1, _id:0}
     },
     {
         $unwind: '$types'
     },
     {
         $group:{
             _id:'$types',
             qnt: {$sum: 1}
         }
     }
 
     ]);
{
  "result": [ ],
  "ok": 1
}
}
```

6 - Realizar 3 counts na pokemons.

* Todos:
* 
```JS
  db.pokemons.count();
  12
  ```
  
  * Só do `types` `fire`:
  p.s: eu mudei de `fire` para `fogo
`
  ```JS
  db.pokemons.count({ types: "fogo"});
  1
  ```
  
  * Só com defesa maior que 70:
  * 
  ```JS
  db.pokemons.count({ defense: { $gt: 70 }});
  6
```
