# MongoDB - Aula 03 - Exercício

Autor: João Paulo Costa Marra

## Selecionando o banco be-mean-pokemons criado na aula 02 (passo 1)
``` shell
Jota-PC(mongod-3.2.1) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem de todos os Pokemons com a altura menor que 0.5 (passo 2)
``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {height: {$lt: 0.5}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c0"),
  "name": "Pikachu",
  "description": "Ratinho elétrico",
  "type": "elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c3"),
  "name": "Pidgey",
  "description": "Passarinho nervoso",
  "type": "normal",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}
Fetched 2 record(s) in 3ms
```

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5 (passo 3)
``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c1"),
  "name": "Charmander",
  "description": "Lagartixa isqueiro",
  "type": "fogo",
  "attack": 52,
  "defense": 43,
  "height": 0.61
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c2"),
  "name": "Squirtle",
  "description": "Tartaruga das bolhas",
  "type": "água",
  "attack": 48,
  "defense": 65,
  "height": 0.51
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c4"),
  "name": "Bulbasaur",
  "description": "Sapinho dos chicotes",
  "type": "grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
Fetched 3 record(s) in 4ms
```

## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 4)
``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c4"),
  "name": "Bulbasaur",
  "description": "Sapinho dos chicotes",
  "type": "grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

## Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5 (passo 5)
``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}}, {name: 'Pikachu'}]}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c0"),
  "name": "Pikachu",
  "description": "Ratinho elétrico",
  "type": "elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
Fetched 1 record(s) in 61ms
```

## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 6)
``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c0"),
  "name": "Pikachu",
  "description": "Ratinho elétrico",
  "type": "elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c4"),
  "name": "Bulbasaur",
  "description": "Sapinho dos chicotes",
  "type": "grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
Fetched 2 record(s) in 2ms
```