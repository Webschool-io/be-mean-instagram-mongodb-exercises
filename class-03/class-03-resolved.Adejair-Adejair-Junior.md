# MongoDB - Aula 03 - Exercício
autor: Adejair Júnior

## Pokemon List
``` JavaScript
adejair(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({})
{
  "_id": ObjectId("5644f0f9ad609303b2baf806"),
  "name": "Charizard",
  "description": "Fire",
  "attack": 84,
  "defense": 78,
  "heigth": 1.7
}
{
  "_id": ObjectId("5644f0f9ad609303b2baf807"),
  "name": "Butterfree",
  "description": "Alterado",
  "attack": 45,
  "defense": 50,
  "heigth": 1.09
}
{
  "_id": ObjectId("5644f0f9ad609303b2baf808"),
  "name": "Pidgeot",
  "description": "Flying",
  "attack": 80,
  "defense": 75,
  "heigth": 1.5
}
{
  "_id": ObjectId("5644f0f9ad609303b2baf809"),
  "name": "Rattatá",
  "description": "Normal",
  "attack": 56,
  "defense": 35,
  "heigth": 0.3
}
{
  "_id": ObjectId("5644f0f9ad609303b2baf80a"),
  "name": "Raticate",
  "description": "Normal",
  "attack": 81,
  "defense": 60,
  "heigth": 0.71
}
Fetched 5 record(s) in 2ms
```



## 1. Liste todos Pokemons com a altura menor que 0.5;
``` JavaScript
var query = {heigth: {$lt: 0.5}}

db.pokemons.find(query)

// Resultado
adejair(mongod-2.4.9) be-mean-pokemons> var query = {heigth: {$lt: 0.5}}

adejair(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644f0f9ad609303b2baf809"),
  "name": "Rattatá",
  "description": "Normal",
  "attack": 56,
  "defense": 35,
  "heigth": 0.3
}
Fetched 1 record(s) in 21ms

```
## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```JavaScript

var query = {altura: {$gte: 0.5}}

db.pokemons.find(query)

// Resultado
Fetched 0 record(s) in 1ms
// Não tenho nenhum pokemon com altura >= 0.5

```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```JavaScript
var query = {$and:[{heigth: {$lte: 0.5}}, {description: "grama"}]}

db.pokemons.find(query)

// Resultado
Fetched 0 record(s) in 1ms

// Não tenho nenhum pokemon cadastrado do tipo "grama".
```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

``` JavaScript
var query = {$or:[{name: "Pikachu"}, {attack: {$lte: 0.5}}]}

db.pokemons.find(query)

// Resultado

Fetched 0 record(s) in 37ms
// Não tenho nenhum pokemon com o nome pikachu e o ataque menor que 0.5
```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

``` JavaScript
var query = {$and:[{attack:{$gte: 48}}, {height: {$lte: 0.5}}]}

db.pokemons.find(query)

// Resultado
Fetched 0 record(s) in 1ms

// Não há nenhum pokemon com esses dados

```
