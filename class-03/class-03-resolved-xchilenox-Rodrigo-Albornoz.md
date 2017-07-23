# MongoDB - Aula 03 - Exercício

Autor: Rodrigo Albornoz

## Liste todos Pokemons com a altura **menor que** 0.5
```
ubuntu-vm(mongod-3.0.9) be-mean-instagram> var query = {height: {$lt: 0.5}}
ubuntu-vm(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ac0055a73f788d7f353d72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56ac063b8c5a82193eb5c1c8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56ac0a988c5a82193eb5c1cb"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 1ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
ubuntu-vm(mongod-3.0.9) be-mean-instagram> var query = { height:  { $gte: 0.5 } }
ubuntu-vm(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ac06bb8c5a82193eb5c1c9"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56ac06d88c5a82193eb5c1ca"),
  "name": "Squirtle",
  "description": "Jorra água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 0ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
ubuntu-vm(mongod-3.0.9) be-mean-instagram> var query = { $and: [ {height:  { $lte: 0.5 }}, {type: 'grama'} ] }
ubuntu-vm(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ac063b8c5a82193eb5c1c8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
ubuntu-vm(mongod-3.0.9) be-mean-instagram> var query = { $or: [ {name: 'Pikachu'}, {attack:  { $lte: 0.5 } } ] }
ubuntu-vm(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ac0055a73f788d7f353d72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
ubuntu-vm(mongod-3.0.9) be-mean-instagram> var query = { $and: [ {attack:  { $gte: 48 }}, {height:  { $lte: 0.5 } } ] }
ubuntu-vm(mongod-3.0.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56ac0055a73f788d7f353d72"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56ac063b8c5a82193eb5c1c8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56ac06d88c5a82193eb5c1ca"),
  "name": "Squirtle",
  "description": "Jorra água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms
```
