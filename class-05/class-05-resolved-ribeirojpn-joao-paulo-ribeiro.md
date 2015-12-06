# MongoDB - Aula 05 - Exercício
autor: João Paulo Ribeiro

## 1. Importar as collections restaurantes e pokemons

  ```
  // Pokemons
  joao@joao-Inspiron-5437:~$ mongoimport --db be-mean --collection pokemons --drop --file pokemons.json
  2015-12-05T03:05:44.418-0300	connected to: localhost
  2015-12-05T03:05:44.419-0300	dropping: be-mean.pokemons
  2015-12-05T03:05:44.672-0300	imported 620 documents

  // Restaurantes
  joao@joao-Inspiron-5437:~$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
  2015-12-05T03:06:40.176-0300	connected to: localhost
  2015-12-05T03:06:40.176-0300	dropping: be-mean.restaurantes
  2015-12-05T03:06:41.376-0300	imported 25359 documents

  ```

## 2. Distinct por 'cuisine' na restaurantes

  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
  [
    "Hamburgers",
    "Bakery",
    "American ",
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
    "Continental",
    "Bagels/Pretzels",
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
## 3. Distinct por 'types' na pokemons

  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
  [
    "flying",
    "normal",
    "poison",
    "electric",
    "water",
    "fighting",
    "psychic",
    "bug",
    "grass",
    "fairy",
    "fire",
    "rock",
    "ice",
    "ground",
    "steel",
    "ghost",
    "dark",
    "dragon"
  ]
  ```
## 4. As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)
  ```
  // Pagina 1
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*0)
  {
    "name": "Pidgey"
  }
  {
    "name": "Pidgeot"
  }
  {
    "name": "Raticate"
  }
  {
    "name": "Fearow"
  }
  {
    "name": "Ekans"
  }
  Fetched 5 record(s) in 1ms

  // Pagina 2
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*1)
  {
    "name": "Pikachu"
  }
  {
    "name": "Raichu"
  }
  {
    "name": "Arbok"
  }
  {
    "name": "Poliwag"
  }
  {
    "name": "Poliwhirl"
  }
  Fetched 5 record(s) in 1ms

  // Pagina 3
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*2)
  {
    "name": "Pidgeotto"
  }
  {
    "name": "Poliwrath"
  }
  {
    "name": "Abra"
  }
  {
    "name": "Machop"
  }
  {
    "name": "Kadabra"
  }
  Fetched 5 record(s) in 0ms
  ```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
  ```
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.group({
  ...     initial: {total:0},
  ...     reduce: function(curr,result){
  ...       curr.types.forEach(function(type){
  ...         if (result[type]){
  ...           result[type]++;
  ...         } else {
  ...           result[type] = 1;
  ...         }
  ...         result.total++;
  ...       });  
  ...     }
  ...   })
  [
    {
      "total": 934,
      "normal": 79,
      "flying": 81,
      "poison": 54,
      "electric": 47,
      "water": 101,
      "fighting": 42,
      "psychic": 61,
      "bug": 58,
      "grass": 70,
      "fairy": 31,
      "fire": 53,
      "rock": 42,
      "ice": 28,
      "ground": 53,
      "steel": 35,
      "ghost": 34,
      "dark": 35,
      "dragon": 30
    }
  ]
  ```
## 6. Realizar 3 counts na pokemons.
  ```
  // .count -- todos
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.count()
  620

  // .count -- só tipo fogo
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.count({types: 'fire'})
  53

  // .count -- só de quantos tem a defesa maior que 70
  joao-Inspiron-5437(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
  263
  ```
