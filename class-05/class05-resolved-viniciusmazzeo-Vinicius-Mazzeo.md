# MongoDb - Aula 05 - Exercício
autor Vinicius Mazzeo

## 1. Importar as collections restaurantes e pokemons

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json 
mongoimport --db be-mean-instagram --collection pokemons --host=127.0.0.1 --drop --file pokemons.json 


```

## 2. Distinct por 'cuisine' na restaurantes

```
db.restaurantes.distinct('cuisine')

```
## 3. Distinct por 'Types' na pokemons

```
db.pokemons.distinct('types')

```

## 4. As 3 primeiras páginas com .limit() e .skip() de pokemons (5 em 5)

```
db.pokemons.find().limit(5).skip(5 * 0)
db.pokemons.find().limit(5).skip(5 * 1)
db.pokemons.find().limit(5).skip(5 * 2)

```

## 5. Group ou Aggregate contando a quantidade de pokemons de cada tipo

```
db.pokemons.group({
... initial: {total: 0},
... reduce: function(curr, result) {
... curr.types.forEach(function(type){
... if(result[type]){
... result[type]++;
... } else {
... result[type] = 1;
... }
... result.total++;
... });
... }
... })
[
  {
    "total": 915,
    "normal": 78,
    "fire": 47,
    "water": 105,
    "bug": 61,
    "flying": 77,
    "poison": 54,
    "steel": 37,
    "electric": 40,
    "ghost": 34,
    "ice": 24,
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

-> .count -- todos
-> .count -- só tipo fogo
-> .count -- só de quantos tem a defesa maior que 70

```
db.pokemons.count()
610

db.pokemons.count({types: 'fire'})
47

db.pokemons.count({defense: {$gt: 70}})
250

```