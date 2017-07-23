# MongoDB - Aula 03 - Exercício
autor: Victor Carli

## Listando todos os pokemons com altura menor que 0.5

```
carli(mongod-2.6.10) be-mean-pokemons> var query = {height: {$lt: 0.5}}
carli(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58a1077522450349d35f9e57"),
  "name": "Raiuchu",
  "description": "Evolução do Pikachu",
  "type": "eletric",
  "attack": 50,
  "defense": 45,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
carli(mongod-2.6.10) be-mean-pokemons>

```

## Listando todos os pokemons com altura maior ou igual que 0.5

```
carli(mongod-2.6.10) be-mean-pokemons> var query = {height: {$gte: 0.5}}
carli(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58a1073b22450349d35f9e53"),
  "name": "Zubat",
  "description": "morcego sem olho da cor roxa",
  "type": "Poison",
  "attack": 20,
  "defense": 30,
  "height": 0.8
}
{
  "_id": ObjectId("58a1075122450349d35f9e54"),
  "name": "Blastoise",
  "description": "Tartaruga tipo bombeira",
  "type": "Água",
  "attack": 40,
  "defense": 35,
  "height": 1.6
}
{
  "_id": ObjectId("58a1075d22450349d35f9e55"),
  "name": "Raticate",
  "description": "Rato de esgoto",
  "type": "Normal",
  "attack": 40,
  "defense": 40,
  "height": 0.7
}
{
  "_id": ObjectId("58a1076a22450349d35f9e56"),
  "name": "Kadabra",
  "description": "Raposa grande de colher",
  "type": "Psychic",
  "attack": 60,
  "defense": 50,
  "height": 1.3
}
Fetched 4 record(s) in 2ms

```

## Listando todos os pokemons com altura menor ou igual que 0.5

```
carli(mongod-2.6.10) be-mean-pokemons> var query = {height: {$lte: 0.5}}
carli(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58a1077522450349d35f9e57"),
  "name": "Raiuchu",
  "description": "Evolução do Pikachu",
  "type": "eletric",
  "attack": 50,
  "defense": 45,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Listando todos os pokemons com nome 'Pikachu' ou com attack menor ou igual que 0.5

```
carli(mongod-2.6.10) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
carli(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```

## Listando todos os pokemons attack maior ou igual que 48 e com height menor ou igual que 0.5

```
carli(mongod-2.6.10) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
carli(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58a1077522450349d35f9e57"),
  "name": "Raiuchu",
  "description": "Evolução do Pikachu",
  "type": "eletric",
  "attack": 50,
  "defense": 45,
  "height": 0.4
}
Fetched 1 record(s) in 4ms

```
