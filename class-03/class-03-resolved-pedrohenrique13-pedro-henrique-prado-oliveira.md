# MongoDB - Aula 03 - Exercício
autor: Pedro Henrique Prado Oliveira

## 1. Liste todos Pokemons com a altura menor que 0.5;

```
db.pokemons.find({"height":{$lt:0.5}})
{
  "_id": ObjectId("56705cd06defc2ee15b8bce4"),
  "name": "Pikachu",
  "description": "Primeiro pokemon",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
db.pokemons.find({"height":{$gte:0.5}})
{
  "_id": ObjectId("56705cd06defc2ee15b8bce3"),
  "name": "Charizard",
  "description": "Dragão",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce5"),
  "name": "Mewtwo",
  "description": "Fodão",
  "type": "Psychic",
  "attack": 110,
  "defense": 90,
  "height": 2
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce6"),
  "name": "Gyarados",
  "description": "Quem nasceu para ser Magikarp, nunca vai ser Gyarados",
  "type": "Water",
  "attack": 125,
  "defense": 70,
  "height": 6.5
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce7"),
  "name": "Blastoise",
  "description": "Solta água pra krl",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 1.6
}
```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
var query = {$and: [{"height": {$lte: 0.5}}, {type: "Grass"}]}
db.pokemons.find(query)
Fetched 0 record(s) in 0ms

// Alterando o type para obter um resultado.
var query = {$and: [{"height": {$lte: 0.5}}, {type: "Eletric"}]}

db.pokemons.find(query)
{
  "_id": ObjectId("56705cd06defc2ee15b8bce4"),
  "name": "Pikachu",
  "description": "Primeiro pokemon",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```
## 4. Liste todos Pokemons com o nome 'Pikachu' OU com attack menor ou igual que 0.5;
```
var query = {$or: [{"attack": {$lte: 0.5}}, {name: "Pikachu"}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56705cd06defc2ee15b8bce4"),
  "name": "Pikachu",
  "description": "Primeiro pokemon",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```
## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5;
```
var query = {$and: [{"attack": {$gte: 48}}, {"height":{$lte: 0.5}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 0ms

// Alterando o type para obte resultados.
var query = {$and: [{"attack": {$gte: 48}}, {"height":{$lte: 10}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56705cd06defc2ee15b8bce3"),
  "name": "Charizard",
  "description": "Dragão",
  "type": "fire",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce5"),
  "name": "Mewtwo",
  "description": "Fodão",
  "type": "Psychic",
  "attack": 110,
  "defense": 90,
  "height": 2
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce6"),
  "name": "Gyarados",
  "description": "Quem nasceu para ser Magikarp, nunca vai ser Gyarados",
  "type": "Water",
  "attack": 125,
  "defense": 70,
  "height": 6.5
}
{
  "_id": ObjectId("56705cd06defc2ee15b8bce7"),
  "name": "Blastoise",
  "description": "Solta água pra krl",
  "type": "Water",
  "attack": 83,
  "defense": 100,
  "height": 1.6
}
Fetched 4 record(s) in 3ms
```
var query = {$and: [{"attack": {$gte: 48}}, {"height":{$lte: 10}}]}
