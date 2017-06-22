# MongoDB - Aula 03 - Exercício
autor: Ivomar

## Liste todos Pokemons com a altura **menor que** 0.5;

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.find({height: {$lt: 0.5}})
{
  "_id": ObjectId("56496536cbe279f611d7abe8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 63
}
{
  "_id": ObjectId("564965b5cbe279f611d7abeb"),
  "name": "Pikachu",
  "description": "Nunca evolui esse FDP",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40
}
Fetched 2 record(s) in 1ms}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.find({height: {$gte: 0.5}})
{
  "_id": ObjectId("564964d3cbe279f611d7abe6"),
  "name": "Venusaur",
  "description": "Bulba super evoluído",
  "type": "grama",
  "attack": 82,
  "height": 2,
  "defense": 83
}
{
  "_id": ObjectId("5649650ecbe279f611d7abe7"),
  "name": "Bulbassauro",
  "description": "Irmão mais velho do Bulba",
  "type": "grama",
  "attack": 62,
  "height": 1,
  "defense": 63
}
{
  "_id": ObjectId("56496569cbe279f611d7abe9"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43
}
{
  "_id": ObjectId("5649658ccbe279f611d7abea"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65
}
Fetched 4 record(s) in 2ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.find({$and: [{height: {$lte: 0.5}}, {type: "grama"}]})
{
  "_id": ObjectId("56496536cbe279f611d7abe8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 63
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.find({$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]})
{
  "_id": ObjectId("564965b5cbe279f611d7abeb"),
  "name": "Pikachu",
  "description": "Nunca evolui esse FDP",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.find({$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]})
{
  "_id": ObjectId("56496536cbe279f611d7abe8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 63
}
{
  "_id": ObjectId("5649658ccbe279f611d7abea"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65
}
{
  "_id": ObjectId("564965b5cbe279f611d7abeb"),
  "name": "Pikachu",
  "description": "Nunca evolui esse FDP",
  "type": "electric",
  "attack": 55,
  "
height": 0.4,
  "defense": 40
}
Fetched 3 record(s) in 1ms
```
