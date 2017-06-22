# MongoDB - Aula 03 - Exercício
autor: Michel Mattos

## Liste todos Pokemons com a altura **menor que** 0.5;

```
be-mean-instagram> var query = { height: {$lt: 0.5} }
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56480a2d29b9c62e120d5166"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56480b3a29b9c62e120d5167"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56480c9129b9c62e120d516a"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 6ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
be-mean-instagram> var query = { height: {$gte: 0.5} }
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56480b6829b9c62e120d5168"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56480b9429b9c62e120d5169"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 6ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
be-mean-instagram> var query = { height: {$lte: 0.5}, type: 'grama' }
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56480b3a29b9c62e120d5167"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 4ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
be-mean-instagram> var query = { $or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}] }
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56480a2d29b9c62e120d5166"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
be-mean-instagram> var query = { $and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}] }
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56480a2d29b9c62e120d5166"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56480b3a29b9c62e120d5167"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56480b9429b9c62e120d5169"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 5ms
```