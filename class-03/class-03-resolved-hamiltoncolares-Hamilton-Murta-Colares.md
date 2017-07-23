# MongoDB - Aula 03 - Exerício
autor: Hamilton Murta Colares

## Exercício
1. Liste todos Pokemons com a altura menor que 0.5;
2. Liste todos Pokemons com a altura maior ou igual que 0.5;
3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;


## Liste todos Pokemons com a altura menor que 0.5

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var query = {height: {$lt: 0.5}}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("566efc41330b9efc28aedac4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("566efca9330b9efc28aedac5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("566efdf5330b9efc28aedac8"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}
Fetched 3 record(s) in 2ms
```
___
## Liste todos Pokemons com a altura maior ou igual que 0.5

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var query = {height: {$gte: 0.5}}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("566efcc2330b9efc28aedac6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("566efd99330b9efc28aedac7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("566f0a3a330b9efc28aedac9"),
  "name": "Charizard",
  "description": "Dinossauro voador gigante",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}
{
  "_id": ObjectId("566f0a48330b9efc28aedaca"),
  "name": "Wartortle",
  "description": "Tartaruga azul",
  "type": "água",
  "attack": 49,
  "height": 1
}
{
  "_id": ObjectId("566f0a57330b9efc28aedacb"),
  "name": "Blastoise",
  "description": "Tartaruga cascuda",
  "type": "água",
  "attack": 83,
  "height": 1.6
}
{
  "_id": ObjectId("566f0a60330b9efc28aedacc"),
  "name": "Pidgeotto",
  "description": "Pássaro topete",
  "type": "normal",
  "attack": 60,
  "height": 1.1
}
{
  "_id": ObjectId("566f0b3d330b9efc28aedace"),
  "name": "Nidorina",
  "description": "Coala olrelhudo",
  "type": "venenoso",
  "attack": 62,
  "height": 0.8
}
Fetched 7 record(s) in 4ms
```

____
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("566efca9330b9efc28aedac5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

___
## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("566efc41330b9efc28aedac4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

___
## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("566efc41330b9efc28aedac4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("566efca9330b9efc28aedac5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("566efd99330b9efc28aedac7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 2ms
```
