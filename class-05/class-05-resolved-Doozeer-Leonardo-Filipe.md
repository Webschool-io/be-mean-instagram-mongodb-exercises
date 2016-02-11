# MongoDB - Aula 05 - Exercício
User: [Doozeer](https://github.com/Doozeer)
Autor: Leonardo Filipe

# Importar as collections `restaurantes` e `pokemons`.
```
Leonardos-MacBook-Pro:Mongo leonardofilipe$ mongoimport --host localhost -d be-mean -c restaurantes --drop --file restaurantes.json 
2016-02-10T09:25:54.025-0200    connected to: localhost
2016-02-10T09:25:54.025-0200    dropping: be-mean.restaurantes
2016-02-10T09:25:54.728-0200    imported 25359 documents
Leonardos-MacBook-Pro:Mongo leonardofilipe$ mongoimport --host localhost -d be-mean -c pokemons --drop --file pokemons.json 
2016-02-10T09:29:35.640-0200    connected to: localhost
2016-02-10T09:29:35.640-0200    dropping: be-mean.pokemons
2016-02-10T09:29:35.680-0200    imported 610 documents
```

# Distinct por `cuisine` na restaurantes.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.restaurantes.distinct('cuisine');
[
  "Bakery",
  "Hamburgers",
  "American ",
  "Jewish/Kosher",
  "Irish",
  "Delicatessen",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Chinese",
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
  "Pizza/Italian",
  "Mexican",
  "French",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Seafood",
  "Greek",
  "Not Listed/Not Applicable",
  "African",
  "Hotdogs",
  "Japanese",
  "Indian",
  "Armenian",
  "Chinese/Cuban",
  "Thai",
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
  "Czech",
  "Bangladeshi",
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
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.distinct('types');
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

# As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5).
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> pageSize = 5;
5
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.find().limit(pageSize).skip(pageSize*0);
{
  "_id": ObjectId("564b1dad25337263280d0479"),
  "attack": 56,
  "created": "2013-11-03T15:05:41.305777",
  "defense": 35,
  "height": "3",
  "hp": 30,
  "name": "Rattata",
  "speed": 72,
  "types": [
    "normal"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047a"),
  "attack": 52,
  "created": "2013-11-03T15:05:41.271082",
  "defense": 43,
  "height": "6",
  "hp": 39,
  "name": "Charmander",
  "speed": 65,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047b"),
  "attack": 64,
  "created": "2013-11-03T15:05:41.273462",
  "defense": 58,
  "height": "11",
  "hp": 58,
  "name": "Charmeleon",
  "speed": 80,
  "types": [
    "fire"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047c"),
  "attack": 63,
  "created": "2013-11-03T15:05:41.280718",
  "defense": 80,
  "height": "10",
  "hp": 59,
  "name": "Wartortle",
  "speed": 58,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047d"),
  "attack": 83,
  "created": "2013-11-03T15:05:41.282985",
  "defense": 100,
  "height": "16",
  "hp": 79,
  "name": "Blastoise",
  "speed": 78,
  "types": [
    "water"
  ]
}
Fetched 5 record(s) in 3ms
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.find().limit(pageSize).skip(pageSize*1);
{
  "_id": ObjectId("564b1dad25337263280d047e"),
  "attack": 30,
  "created": "2013-11-03T15:05:41.285736",
  "defense": 35,
  "height": "3",
  "hp": 45,
  "name": "Caterpie",
  "speed": 45,
  "types": [
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0480"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.290411",
  "defense": 50,
  "height": "11",
  "hp": 60,
  "name": "Butterfree",
  "speed": 70,
  "types": [
    "flying",
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0481"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.310402",
  "defense": 30,
  "height": "3",
  "hp": 40,
  "name": "Spearow",
  "speed": 70,
  "types": [
    "normal",
    "flying"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d0482"),
  "attack": 25,
  "created": "2013-11-03T15:05:41.294947",
  "defense": 50,
  "height": "6",
  "hp": 45,
  "name": "Kakuna",
  "speed": 35,
  "types": [
    "poison",
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0483"),
  "attack": 65,
  "created": "2013-11-03T15:05:41.439497",
  "defense": 55,
  "height": "8",
  "hp": 52,
  "name": "Farfetchd",
  "speed": 60,
  "types": [
    "normal",
    "flying"
  ]
}
Fetched 5 record(s) in 3ms
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.find().limit(pageSize).skip(pageSize*2);
{
  "_id": ObjectId("564b1dae25337263280d0484"),
  "attack": 35,
  "created": "2013-11-03T15:05:41.435237",
  "defense": 70,
  "height": "3",
  "hp": 25,
  "name": "Magnemite",
  "speed": 45,
  "types": [
    "steel",
    "electric"
  ]
}
{
  "_id": ObjectId("564b1dad25337263280d047f"),
  "attack": 20,
  "created": "2013-11-03T15:05:41.288107",
  "defense": 55,
  "height": "7",
  "hp": 50,
  "name": "Metapod",
  "speed": 30,
  "types": [
    "bug"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0485"),
  "attack": 60,
  "created": "2013-11-03T15:05:41.437483",
  "defense": 95,
  "height": "10",
  "hp": 50,
  "name": "Magneton",
  "speed": 70,
  "types": [
    "steel",
    "electric"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0487"),
  "attack": 45,
  "created": "2013-11-03T15:05:41.445749",
  "defense": 55,
  "height": "11",
  "hp": 65,
  "name": "Seel",
  "speed": 45,
  "types": [
    "water"
  ]
}
{
  "_id": ObjectId("564b1dae25337263280d0488"),
  "attack": 110,
  "created": "2013-11-03T15:05:41.443720",
  "defense": 70,
  "height": "18",
  "hp": 60,
  "name": "Dodrio",
  "speed": 100,
  "types": [
    "normal",
    "flying"
  ]
}
Fetched 5 record(s) in 2ms
```

# Group ou Aggregate contando a quantidade de pokemons de cada tipo.
```js
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.group({
    initial: {total: 0},
    reduce: function(curr, res){
        res.total++;
        curr.types.forEach(function(type) {
            if(res[type]) {
                res[type]++;
            } else {
                res[type] = 1;
            }
        });
    }
});
[
  {
    "total": 610,
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

# Realizar 3 counts na pokemons.
```js
// Contando todos os Pokemons
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.count({});
610
// Contando os Pokemons do tipo 'dragon'
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.count({types: 'dragon'});
20
// Contando os Pokemons com 2 ou mais tipos
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean> db.pokemons.count({'types.1': {$exists: true}});
305
```