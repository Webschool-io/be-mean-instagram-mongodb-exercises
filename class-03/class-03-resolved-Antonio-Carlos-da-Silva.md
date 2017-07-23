# MongoDB - Aula 03 - Exercício
autor: Antonio Carlos da silva 

## Lista dos Pokemons com altura menor que 0.5;

```
var query = { height: {$lt:0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f43273847848e"),
  "name": "Caterpie",
  "description": "Apetite voraz e odor forte.",
  "type": "bug",
  "attack": 20,
  "defense": 20,
  "height": 0.3
}
{
  "_id": ObjectId("57faee89839f432738478490"),
  "name": "Pikachu",
  "description": "Sempre que se depara com algo novo, ele dispara  um choque de elétrico",
  "type": "electric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 2 record(s) in 1ms
```

## Lista dos Pokemons com altura maior ou menor que 0.5;

```
var query = { height: {$gte:0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f432738478489"),
  "name": "bulbasaur",
  "description": "Ṕode ser visto dormindo na luz solar. Por absorver os raios do sol.",
  "type": "grass",
  "attack": 30,
  "defense": 20,
  "height": 0.7
}
{
  "_id": ObjectId("57faee89839f43273847848a"),
  "name": "Ivysaur",
  "description": "Se ele começa a passar mais tempo deitado ao sol, é um sinal de que  vai florescer uma grande flor em breve.",
  "type": "grass",
  "attack": 30,
  "defense": 30,
  "height": 1
}
{
  "_id": ObjectId("57faee89839f43273847848b"),
  "name": "Venusaur",
  "description": "Há uma grande flor na parte traseira. A flor é dito para ter  cores vivas. O aroma da flor acalma as emoções das pessoas.",
  "type": "grass",
  "attack": 40,
  "defense": 40,
  "height": 2
}
{
  "_id": ObjectId("57faee89839f43273847848c"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da cauda é uma indicação das suas emoções. Se o Pokémon fica furioso, a chama queima ferozmente.",
  "type": "fire",
  "attack": 30,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("57faee89839f43273847848d"),
  "name": "Charizard",
  "description": "voa em torno do céu em busca de adversários poderosos.",
  "type": "fire",
  "attack": 40,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("57faee89839f43273847848f"),
  "name": "Beedrill",
  "description": "Extremamente territorial. Ninguém deve aproximar seu ninho para sua própria segurança.",
  "type": "bug",
  "attack": 50,
  "defense": 20,
  "height": 1
}
Fetched 6 record(s) in 2ms
```

## Lista dos Pokemons com altura maior ou menor que 0.5 E do tipo grama;

```
var query = {$and: [{height: {$gte:0.5}}, {type: /grass/}]}
query
{
  "$and": [
    {
      "height": {
        "$gte": 0.5
      }
    },
    {
      "type": /grass/
    }
  ]
}
db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f432738478489"),
  "name": "bulbasaur",
  "description": "Ṕode ser visto dormindo na luz solar. Por absorver os raios do sol.",
  "type": "grass",
  "attack": 30,
  "defense": 20,
  "height": 0.7
}
{
  "_id": ObjectId("57faee89839f43273847848a"),
  "name": "Ivysaur",
  "description": "Se ele começa a passar mais tempo deitado ao sol, é um sinal de que  vai florescer uma grande flor em breve.",
  "type": "grass",
  "attack": 30,
  "defense": 30,
  "height": 1
}
{
  "_id": ObjectId("57faee89839f43273847848b"),
  "name": "Venusaur",
  "description": "Há uma grande flor na parte traseira. A flor é dito para ter  cores vivas. O aroma da flor acalma as emoções das pessoas.",
  "type": "grass",
  "attack": 40,
  "defense": 40,
  "height": 2
}
Fetched 3 record(s) in 2ms
```

## Lista dos Pokemons com o nome 'Pikachu' OU com attack menor ou igual que 0.5;

```
var query = {$or: [{attack: {$lte:0.5}}, {name: /PiKachu/i}]}
query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": /Pikachu/i
    }
  ]
}

db.pokemons.find(query)
{
  "_id": ObjectId("57faee89839f432738478490"),
  "name": "Pikachu",
  "description": "Sempre que se depara com algo novo, ele dispara  um choque de elétrico",
  "type": "electric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 3m
```

## Lista dos Pokemons com attck maior ou menor que 48 E com height menor ou igual que 0.5;

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte:0.5}}]}
query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}
db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```

