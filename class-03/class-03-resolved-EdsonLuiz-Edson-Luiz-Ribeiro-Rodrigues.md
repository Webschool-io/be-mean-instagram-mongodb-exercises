# MongoDB - Aula 03 - Exercício
autor: Edson Luiz Ribeiro Rodrigues

## Listar todos os pokemons com a altura **menor que** 0.5

```
mac(mongod-3.2.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5777e96678dc84ee3b361f70"),
  "name": "Krabby",
  "description": "Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.",
  "attack": 105,
  "defense": 90,
  "height": 0.4
}
{
  "_id": ObjectId("5777e99878dc84ee3b361f73"),
  "name": "Floette",
  "description": "It flutters around fields of flowers and cares for flowers that are starting to wilt. It draws out the hidden power of flowers to battle.",
  "attack": 45,
  "defense": 47,
  "height": 0.2
}
Fetched 2 record(s) in 3ms
mac(mongod-3.2.7) be-mean-pokemons>
```

## Listar todos os pokemons com a altura **maior ou igual que** 0.5

```
mac(mongod-3.2.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5777e97f78dc84ee3b361f71"),
  "name": "Cresselia",
  "description": "Shiny particles are released from its wings like a veil. It is said to represent the crescent moon.",
  "attack": 70,
  "defense": 120,
  "height": 15
}
{
  "_id": ObjectId("5777e98b78dc84ee3b361f72"),
  "name": "Gothorita",
  "description": "Starlight is the source of their power. At night, they mark star positions by using psychic power to float stones.",
  "attack": 45,
  "defense": 70,
  "height": 0.7
}
{
  "_id": ObjectId("5777e9a278dc84ee3b361f74"),
  "name": "Gorebyss",
  "description": "Nova descrição",
  "attack": 84,
  "defense": 105,
  "height": 1.8
}
{
  "_id": ObjectId("5777e9ab78dc84ee3b361f75"),
  "name": "Milotic",
  "description": "Milotic is said to be the most beautiful of all the Pokémon. It has the power to becalm such emotions as anger and hostility to quell bitter feuding.",
  "attack": 60,
  "defense": 79,
  "height": 6.2
}
Fetched 4 record(s) in 2ms
mac(mongod-3.2.7) be-mean-pokemons>
```

## Listar todos os pokemons com a altura **MENOR OU IGUAL QUE** 0.5 **E** do tipo grama

```
mac(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
mac(mongod-3.2.7) be-mean-pokemons>
```

## Listar todos os pokemons com name 'Pikachu' **OU** com attack **MENOR OU IGUAL QUE** 0.5

```
mac(mongod-3.2.7) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.find()
```

## Listar todos os pokemons com attack **MAIOR OU IGUAL QUE** 48 **E** com height **MENOR OU IGUAL QUE** 0.5

```
mac(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
mac(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5777e96678dc84ee3b361f70"),
  "name": "Krabby",
  "description": "Krabby live on beaches, burrowed inside holes dug into the sand. On sandy beaches with little in the way of food, these Pokémon can be seen squabbling with each other over territory.",
  "attack": 105,
  "defense": 90,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
mac(mongod-3.2.7) be-mean-pokemons>
```
