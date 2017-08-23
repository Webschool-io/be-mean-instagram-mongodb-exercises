# MongoDB - Aula 03 - Exercício
Autor: Rafael Barros

## 1. Liste todos Pokemons com a altura menor que 0.5;

```
DEV(mongod-3.4.6) be-mean-pokemons> var query = {height: {$lt: 0.5}}
DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa74"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa75"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa78"),
  "name": "Caterpie",
  "description": "Inseto bem fofinho",
  "type": "Bug",
  "attack": 30,
  "height": 0.3
}
Fetched 3 record(s) in 9ms

```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
DEV(mongod-3.4.6) be-mean-pokemons> var query = {height: {$gte: 0.5}}
DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa76"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa77"),
  "name": "Squirtle",
  "description": "Ejeta água mais que uma Baleia",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 8ms

```
## 3. Liste todos os Pokemons com a altura menor ou igual que 0.5 AND do tipo grama;

```
DEV(mongod-3.4.6) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa75"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 10ms

```

## 4. Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5;

```

DEV(mongod-3.4.6) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa74"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 8ms

```
## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5;

```
DEV(mongod-3.4.6) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
DEV(mongod-3.4.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa74"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa75"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5977f7b9a11aa5d85502aa77"),
  "name": "Squirtle",
  "description": "Ejeta água mais que uma Baleia",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 9ms
```
