# MongoDB - Aula 03 - Exercício
autor: Eduardo Pinheiro Quaresma Castro

## 01 - Listando pokemons com altura menor que 0.5
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {height: {$lt: 0.5}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac4978853bf472d952c28d"),
  "name": "Pikachu",
  "description": "An boring eletric mouse",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56ac4978853bf472d952c291"),
  "name": "Caterpie",
  "description": "Serve pra nada",
  "type": "bug",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}
Fetched 2 record(s) in 1ms
```

## 02 - Listando pokemons com altura maior ou igual que 0.5
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac4978853bf472d952c28e"),
  "name": "Bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7
}
{
  "_id": ObjectId("56ac4978853bf472d952c28f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de tão fofinho",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6
}
{
  "_id": ObjectId("56ac4978853bf472d952c290"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
Fetched 3 record(s) in 1ms
```

## 03 - Listando pokemons com altura menor ou igual que 0.5 e do tipo grama
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {$and: [{height: {$lte:0.5}}, {type: 'grass'}]}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9068"),
  "name": "Bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## 04 - Listando pokemons com name 'Pikachu' ou com attack menor ou igual que 0.5
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte:0.5}}]}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac4978853bf472d952c28d"),
  "name": "Pikachu",
  "description": "An boring eletric mouse",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

## 05 - Listando pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5
```js
Cybertron(mongod-3.0.9) be-mean-pokemons> var query = {$and: [{attack: {$gte:48}}, {height: {$lte: 0.5}}]}
Cybertron(mongod-3.0.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9067"),
  "name": "Pikachu",
  "description": "An boring eletric mouse",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd9068"),
  "name": "Bulbasaur",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56ac5ab2ff7ddea9ccdd906a"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
Fetched 3 record(s) in 1ms
```
