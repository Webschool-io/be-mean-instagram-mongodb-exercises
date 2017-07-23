# MongoDB - Aula 03 - Exercício
autor: **Fernando de Albuquerque Ponte Filho**

## Liste todos Pokemons com a altura **menor que** 0.5
```
var query = {height: {$lt: 0.5}}

db.pokemons.find(query)
{
  "_id": ObjectId("564b93c4ce0395086dc46c79"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("564b93c4ce0395086dc46c7a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564b93c4ce0395086dc46c7b"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 2ms

```
## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
macsobra(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
macsobra(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b89c7ce0395086dc46c74"),
  "name": "Fernandomon",
  "description": "Pokemon Estudante Eterno",
  "type": "bombril",
  "attack": 443,
  "defense": 2222,
  "height": 1.75
}
{
  "_id": ObjectId("564b89c7ce0395086dc46c75"),
  "name": "Brahmomon",
  "description": "Pokemon de Pilsen fake",
  "type": "cerveja",
  "attack": 5000,
  "defense": 3000,
  "height": 3.55
}
{
  "_id": ObjectId("564b89c7ce0395086dc46c76"),
  "name": "Skolomon",
  "description": "Pokemon de Pilsen fake tambem",
  "type": "cerveja",
  "attack": 6000,
  "defense": 4000,
  "height": 3.55
}
{
  "_id": ObjectId("564b89c7ce0395086dc46c77"),
  "name": "Heinekenmon",
  "description": "Pokemon Premium/Verdinho",
  "type": "cerveja",
  "attack": 8000,
  "defense": 5000,
  "height": 3.55
}
{
  "_id": ObjectId("564b89c7ce0395086dc46c78"),
  "name": "BadenWeissmon",
  "description": "Pokemon de melhor custo beneficio",
  "type": "cerveja",
  "attack": 9000,
  "defense": 8000,
  "height": 6
}
{
  "_id": ObjectId("564b9447ce0395086dc46c7c"),
  "name": "Charmander",
  "description": "Esse e o cao chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564b9447ce0395086dc46c7d"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5
}
Fetched 7 record(s) in 4ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
macsobra(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
macsobra(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b93c4ce0395086dc46c7a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
macsobra(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
macsobra(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b93c4ce0395086dc46c79"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
macsobra(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
macsobra(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b93c4ce0395086dc46c79"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("564b93c4ce0395086dc46c7a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564b9447ce0395086dc46c7d"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 2ms
```
