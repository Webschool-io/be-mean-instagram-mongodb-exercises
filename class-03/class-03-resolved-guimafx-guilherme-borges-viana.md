# MongoDB - Aula 03 - Exercício
autor: Guilherme Borges Viana (https://github.com/guimafx)

## Liste todos Pokemons com a altura menor que 0.5

```
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> var query = {height: {$lt:05}}
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56449ba08c78bf83fae9f35e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c038c78bf83fae9f35f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c438c78bf83fae9f360"),
  "name": "Bulbasaur",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c618c78bf83fae9f361"),
  "name": "Charmander",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c788c78bf83fae9f362"),
  "name": "Squirtle",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5642a69455b599c8d14a475d"),
  "name": "Metapod",
  "description": "Esperando evoluir mais demora em",
  "type": "grama",
  "attack": 0.5,
  "defense": 30,
  "height": 0.5
}
Fetched 6 record(s) in 2ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5

```
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> var query = { height: { $gte: 0.5 } }	
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642a69455b599c8d14a475d"),
  "name": "Metapod",
  "description": "Esperando evoluir mais demora em",
  "type": "grama",
  "attack": 0.5,
  "defense": 30,
  "height": 0.5
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons onde altura >=  0.5 & do type = ‘grama’


```		
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> var query = { $and : [ { height: { $lte: 0.5 } }, { type: 'grama' } ] }
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642a69455b599c8d14a475d"),
  "name": "Metapod",
  "description": "Esperando evoluir mais demora em",
  "type": "grama",
  "attack": 0.5,
  "defense": 30,
  "height": 0.5
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons nome name = 'Pikachu' OU com attack >= 0.5

```
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> var query = { $or: [ { name: 'Pikachu' }, { attack: { $lte: 0.5 } } ] }
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56449ba08c78bf83fae9f35e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c038c78bf83fae9f35f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5642a69455b599c8d14a475d"),
  "name": "Metapod",
  "description": "Esperando evoluir mais demora em",
  "type": "grama",
  "attack": 0.5,
  "defense": 30,
  "height": 0.5
}
Fetched 3 record(s) in 49ms
```

## Liste todos Pokemons com o attack >= 48 E com altura =< 0.5

```
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> var query = { $and: [ { attack: { $gte:48 } }, { height: { $lte: 0.5 } } ] }
Guilhermes-MacBook-Pro(mongod-2.6.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56449ba08c78bf83fae9f35e"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c038c78bf83fae9f35f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c438c78bf83fae9f360"),
  "name": "Bulbasaur",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c618c78bf83fae9f361"),
  "name": "Charmander",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56449c788c78bf83fae9f362"),
  "name": "Squirtle",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 5 record(s) in 3ms
```



