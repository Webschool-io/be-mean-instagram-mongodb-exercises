# MongoDB - Aula 03 - Exercício
autor: Giuseppe Antonelli Santos

## Listagem dos Pokemons com height menor que 0.5
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 133ms
```

## Listagem dos Pokemons com height maior ou igual à 0.5
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5653cdacb5a20e0455611504"),
  "name": "Electrike",
  "description": "Electrike stores electricity in its long body hair",
  "type": "Eletric",
  "attack": 30,
  "height": 0.6
}
{
  "_id": ObjectId("5653cdf2b5a20e0455611505"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts th at protrude from its shell",
  "type": "Water",
  "attack": 40,
  "height": 1.6
}
{
  "_id": ObjectId("5653ce07b5a20e0455611506"),
  "name": "Charizard",
  "description": "Charizard flies around the sk y in search of powerful opponents.",
  "type": "Fire",
  "attack": 40,
  "height": 1.7
}
{
  "_id": ObjectId("5653ce0fb5a20e0455611507"),
  "name": "Marowak",
  "description": "The bone it holds is its key weapon. It throws the bone skillfully like a boomerang to KO targets.",
  "type": "ground",
  "attack": 80,
  "height": 10
}
{
  "_id": ObjectId("5653ce4fb5a20e0455611508"),
  "name": "Exeggcute",
  "description": "Often mistaken for eggs. When disturbed, they quickly gather and attack in swarms.",
  "type": "grass",
  "attack": 40,
  "height": 4
}
Fetched 5 record(s) in 2ms

```

## Listagem dos Pokemons com height menor ou igual à 0.5 e do type "grass"
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "grass"}]}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Listagem dos Pokemons com name "Pikachu" ou attack menor ou igual à 0.5
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listagem dos Pokemons com name "Electrike" ou height maior ou igual à 4
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Electrike"}, {height: {$gte: 4}}]}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5653cdacb5a20e0455611504"),
  "name": "Electrike",
  "description": "Electrike stores electricity in its long body hair",
  "type": "Eletric",
  "attack": 30,
  "height": 0.6
}
{
  "_id": ObjectId("5653ce0fb5a20e0455611507"),
  "name": "Marowak",
  "description": "The bone it holds is its key weapon. It throws the bone skillfully like a boomerang to KO targets.",
  "type": "ground",
  "attack": 80,
  "height": 10
}
{
  "_id": ObjectId("5653ce4fb5a20e0455611508"),
  "name": "Exeggcute",
  "description": "Often mistaken for eggs. When disturbed, they quickly gather and attack in swarms.",
  "type": "grass",
  "attack": 40,
  "height": 4
}
Fetched 3 record(s) in 1ms
```

## Listagem de todos os Pokemons com attack maior ou igual à 48 e height menor ou igual à 0.5
```
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
antonellisantos-GT60-0N-GT60-0NSR(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```