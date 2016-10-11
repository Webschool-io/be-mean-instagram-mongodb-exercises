# MongoDB - Aula 03 - Exercício
autor: Luiz Fernando Cieslak

## 1. Liste pokemons com altura < 0.5

```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d637933407799dc5d18"),
  "name": "Pikachu",
  "description": "pokemon amarelo que solta raio pela bochecha",
  "type": "electric",
  "attack": 55,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("57db1d877933407799dc5d19"),
  "name": "Oddish",
  "description": "planta verde mt louca",
  "type": "grama",
  "attack": 60,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("57db1df04db19953af64a73d"),
  "name": "Metapod",
  "description": "casulo inquebravel",
  "type": "grama",
  "attack": 32,
  "defense": 60,
  "height": 0.4
}
{
  "_id": ObjectId("57db1e6d4db19953af64a73e"),
  "name": "Polygon",
  "description": "pato feito em origami",
  "type": "psychic",
  "attack": 90,
  "defense": 60,
  "height": 0.4
}
Fetched 4 record(s) in 1ms

```
## 2. Liste pokemons com altura >= 0.5

```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d927933407799dc5d1a"),
  "name": "Starmie",
  "description": "estrela de 8 pontas roxa que solta agua",
  "type": "agua",
  "attack": 80,
  "defense": 50,
  "height": 0.6
}
Fetched 1 record(s) in 0ms

```
## 3. Liste pokemons com altura <=0.5 E tipo grama

```
var query = {$and: [{type: "grama"}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d877933407799dc5d19"),
  "name": "Oddish",
  "description": "planta verde mt louca",
  "type": "grama",
  "attack": 60,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("57db1df04db19953af64a73d"),
  "name": "Metapod",
  "description": "casulo inquebravel",
  "type": "grama",
  "attack": 32,
  "defense": 60,
  "height": 0.4
}
Fetched 2 record(s) in 0ms

```
## 4. Liste pokemons com name 'Pikachu' OU attack <= 0.5

```
var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d637933407799dc5d18"),
  "name": "Pikachu",
  "description": "pokemon amarelo que solta raio pela bochecha",
  "type": "electric",
  "attack": 55,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 0ms

```

## 5. Liste pokemons com attack >= 48 E altura <=0.5

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)

{
  "_id": ObjectId("57db1d637933407799dc5d18"),
  "name": "Pikachu",
  "description": "pokemon amarelo que solta raio pela bochecha",
  "type": "electric",
  "attack": 55,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("57db1d877933407799dc5d19"),
  "name": "Oddish",
  "description": "planta verde mt louca",
  "type": "grama",
  "attack": 60,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("57db1e6d4db19953af64a73e"),
  "name": "Polygon",
  "description": "pato feito em origami",
  "type": "psychic",
  "attack": 90,
  "defense": 60,
  "height": 0.4
}
Fetched 3 record(s) in 1ms
```
