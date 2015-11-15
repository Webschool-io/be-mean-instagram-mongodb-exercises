# MongoDB - Aula 03 - Exercício
autor: Victor Pereira

## Liste todos Pokemons com a altura **menor que** 0.5;
```
victorbzk(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt:0.5}}
victorbzk(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
victorbzk(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte:0.5}}
victorbzk(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647b5319dd42619b4f09b74"),
  "name": "Pikachu",
  "description": "Rato elétrico fofinho demais da conta",
  "attack": 50,
  "defense": 30,
  "height": 0.5
}
{
  "_id": ObjectId("5647b5669dd42619b4f09b75"),
  "name": "Charmander",
  "description": "Mini-Charizard",
  "attack": 40,
  "defense": 20,
  "height": 0.6
}
{
  "_id": ObjectId("5647b5899dd42619b4f09b76"),
  "name": "Squirtle",
  "description": "Pokémon astro do pornô",
  "attack": 60,
  "defense": 30,
  "height": 0.5
}
{
  "_id": ObjectId("5647b5b59dd42619b4f09b77"),
  "name": "Bulbassauro",
  "description": "Pokémon da floresta",
  "attack": 45,
  "defense": 40,
  "height": 0.7
}
{
  "_id": ObjectId("5647b63a9dd42619b4f09b78"),
  "name": "Caterpie",
  "description": "Pokémon ET",
  "attack": 55,
  "defense": 30,
  "height": 0.5
}
Fetched 5 record(s) in 14ms

```
## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** attack igual a 55
```
victorbzk(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{ height: {$lte: 0.5} } , {attack: 55 }] }
victorbzk(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647b63a9dd42619b4f09b78"),
  "name": "Caterpie",
  "description": "Pokémon ET",
  "attack": 55,
  "defense": 30,
  "height": 0.5
}
Fetched 1 record(s) in 3ms

```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
victorbzk(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte:0.5}}]}
victorbzk(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647b5319dd42619b4f09b74"),
  "name": "Pikachu",
  "description": "Rato elétrico fofinho demais da conta",
  "attack": 50,
  "defense": 30,
  "height": 0.5
}
Fetched 1 record(s) in 8ms

```
## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
victorbzk(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{ attack: {$gte:48}} , {height: {$lte:0.5}} ]}
victorbzk(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647b5319dd42619b4f09b74"),
  "name": "Pikachu",
  "description": "Rato elétrico fofinho demais da conta",
  "attack": 50,
  "defense": 30,
  "height": 0.5
}
{
  "_id": ObjectId("5647b5899dd42619b4f09b76"),
  "name": "Squirtle",
  "description": "Pokémon astro do pornô",
  "attack": 60,
  "defense": 30,
  "height": 0.5
}
{
  "_id": ObjectId("5647b63a9dd42619b4f09b78"),
  "name": "Caterpie",
  "description": "Pokémon ET",
  "attack": 55,
  "defense": 30,
  "height": 0.5
}
Fetched 3 record(s) in 5ms

```