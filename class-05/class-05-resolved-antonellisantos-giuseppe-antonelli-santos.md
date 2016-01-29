# MongoDB - Aula 05 - Exercício
autor: GIUSEPPE ANTONELLI

## 1. Importar as collections restaurantes e pokemons
```
# antonellisantos at antonellisantos-GT60-0N-GT60-0NSR in ~/Área de Trabalho/be-mean-instagram/Modulos/MongoDB on git:master x [2:51:20]
$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2015-11-24T02:52:38.546-0200  connected to: 127.0.0.1
2015-11-24T02:52:38.547-0200  dropping: be-mean.pokemons
2015-11-24T02:52:38.872-0200  imported 610 documents
# antonellisantos at antonellisantos-GT60-0N-GT60-0NSR in ~/Área de Trabalho/be-mean-instagram/Modulos/MongoDB on git:master x [2:52:38]
$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-24T02:52:55.468-0200  connected to: 127.0.0.1
2015-11-24T02:52:55.468-0200  dropping: be-mean.restaurantes
2015-11-24T02:52:56.417-0200  imported 25359 documents
```

## 2. Distinct por cuisine na restaurantes
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.restaurantes.distinct('cuisine')
[
  "Bakery",
  "Irish",
  "Jewish/Kosher",
  "Hamburgers",
  "Delicatessen",
  "American ",
  "Ice Cream, Gelato, Yogurt, Ices",
  "Other",
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
  "French",
  "Pizza/Italian",
  "Mexican",
  "Spanish",
  "Café/Coffee/Tea",
  "Tex-Mex",
  "Pancakes/Waffles",
  "Soul Food",
  "Seafood",
  "Greek",
  "Hotdogs",
  "African",
  "Not Listed/Not Applicable",
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

## 3. Distinct por types na pokemons
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.distinct('types')
[
  "fire",
  "water",
  "bug",
  "electric",
  "steel",
  "flying",
  "normal",
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

## 4. As primeiras 3 pág. com .limit() e .skip() de pokemons (5 em 5)
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> var i = 0
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*i++)
{
  "name": "Charmeleon"
}
{
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}
{
  "name": "Caterpie"
}
{
  "name": "Metapod"
}
Fetched 5 record(s) in 1ms
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*i++)
{
  "name": "Charmander"
}
{
  "name": "Magnemite"
}
{
  "name": "Doduo"
}
{
  "name": "Butterfree"
}
{
  "name": "Kakuna"
}
Fetched 5 record(s) in 0ms
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5*i++)
{
  "name": "Spearow"
}
{
  "name": "Seel"
}
{
  "name": "Farfetchd"
}
{
  "name": "Dewgong"
}
{
  "name": "Dodrio"
}
Fetched 5 record(s) in 0ms
```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.aggregate([
... {$unwind: '$types'},
... {$group: {
... _id: '$types',
... total: {$sum: 1}
... }}])
{
  "result": [
    {
      "_id": "fairy",
      "total": 28
    },
    {
      "_id": "psychic",
      "total": 62
    },
    {
      "_id": "fighting",
      "total": 38
    },
    {
      "_id": "rock",
      "total": 46
    },
    {
      "_id": "flying",
      "total": 77
    },
    {
      "_id": "fire",
      "total": 47
    },
    {
      "_id": "ice",
      "total": 24
    },
    {
      "_id": "bug",
      "total": 61
    },
    {
      "_id": "poison",
      "total": 54
    },
    {
      "_id": "normal",
      "total": 78
    },
    {
      "_id": "dark",
      "total": 38
    },
    {
      "_id": "ground",
      "total": 51
    },
    {
      "_id": "grass",
      "total": 75
    },
    {
      "_id": "electric",
      "total": 40
    },
    {
      "_id": "steel",
      "total": 37
    },
    {
      "_id": "ghost",
      "total": 34
    },
    {
      "_id": "dragon",
      "total": 20
    },
    {
      "_id": "water",
      "total": 105
    }
  ],
  "ok": 1
}
```
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.group({
... initial: {total: 0},
... reduce: function(cur, res){
... cur.types.forEach(function(type){
... if(res[type]){
... res[type]++;
... } else {
... res[type] = 1;
... }
... res.total++;
... })}})
[
  {
    "total": 915,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "steel": 37,
    "electric": 40,
    "normal": 78,
    "flying": 77,
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
* Todos
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.count()
610
```

* Só do types fire
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.count({types: 'fire'})
47
```

* Só os com defesa maior que 70
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean> db.pokemons.count({defense: {$gt: 70}})
250
```