# MongoDB - Aula 03 - Exercício
autor: Deyves Carvalho

## Listando todos os pokemons com altura menor que 0.5

```
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {height: {$lt:0.5}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dac"),
  "name": "Rattata",
  "description": "Rato, que pode infectar facilmente seus oponentes.",
  "attack": 30,
  "defense": 20,
  "height": 0.3
}
Fetched 1 record(s) in 1ms
```

## Listando todos os pokemons com altura maior ou igual que 0.5

```
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {height: {$gte: 0.5}}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e2500c7a4c407e4ead4da9"),
  "name": "Alakazam",
  "description": "Esse mago, é um mago mui loco",
  "attack": 30,
  "defense": 20,
  "height": 1.5
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4daa"),
  "name": "Psyduck",
  "description": "Pato, que manja das magias mais fodas.",
  "attack": 30,
  "defense": 20,
  "height": 0.8
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dab"),
  "name": "Nidorino",
  "description": "Rinoceronte muito malandro",
  "attack": 40,
  "defense": 30,
  "height": 0.9
}
{
  "_id": ObjectId("56e2500c7a4c407e4ead4dad"),
  "name": "Butterfree",
  "description": "Borboleta com super ataque, através dos seus olhos de BLACK KAMEN RIDER.",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
Fetched 4 record(s) in 218ms
```

## Listando todos os pokemons com altura menor ou igual que 0.5 e do tipo grama

```
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{height: 0.5}, {type: 'grama'}]}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Listando todos os pokemons com nome 'Pikachu' ou com attack menor ou igual que 0.5

```
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {$or: [{name:'Pikachu'}, {$lte:{attack: 0.5}}]}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Listando todos os pokemons attack maior ou igual que 48 e com height menor ou igual que 0.5

```
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{$gte:{attack:48}}, {$lte:{height:0.5}}]}
deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```
