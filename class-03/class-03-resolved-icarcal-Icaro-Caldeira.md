# MongoDB - Aula 03 - Exercício
autor: Icaro Caldeira (https://github.com/icarcal)

## Liste todos Pokemons com a altura menor que 0.5; (passo 1)
```js
> var query = {height: {$lt:0.5}}
> db.pokemons.find(query)
> {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce487"),
    "name" : "Pikachu",
    "description" : "It raises its tail to check its sur roundings. The tail is sometimes struck by lightning in this pose.",
    "type" :
    "eletric",
    "attack" : 42,
    "defense" : 40,
    "height" : 0.4
  }
```

## Liste todos Pokemons com a altura maior ou igual que 0.5; (passo 2)

```js
> var query = {height: {$gte:0.5}}
> db.pokemons.find(query)
> {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce484"),
    "name" : "Charmander",
    "description" : "The flame at the tip of its tail makes a sound as it burns. You can only hear it in quiet places.",
    "type" : "fire",
    "attack" : 40,
    "defense" : 43,
    "height" : 0.6
  }
  {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce485"),
    "name" : "Charmeleon",
    "description" : "When it swings its burning tail, it elevates the temperature to unbearably high levels.",
    "type" : "fire",
    "attack" : 64,
    "defense" : 58,
    "height" : 0.5
  }
  {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce486"),
    "name" : "Charizard",
    "description" : "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.",
    "type" : "fire",
    "attack" : 84,
    "defense" : 78,
    "height" : 0.5
  }
  {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce488"),
    "name" : "Raichu",
    "description" : "If the electric pouches in its cheeks become fully charged, both ears will stand straight up.",
    "type" : "eletric",
    "attack" : 90,
    "defense" : 55,
    "height" : 1
  }

```
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo fire; (passo 3)

```js
> var query1 = {height: {$lte:0.5}}
> var query2 = {type: "fire"}
> var query = {$and: [query1, query2]}
> db.pokemons.find(query)
> {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce485"),
    "name" : "Charmeleon", "description" : "When it swings its burning tail, it elevates the temperature to unbearably high levels.",
    "type" : "fire",
    "attack" : 64,
    "defense" : 58,
    "height" : 0.5
  }
  {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce486"),
    "name" : "Charizard",
    "description" : "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.",
    "type" : "fire",
    "attack" : 84,
    "defense" : 78,
    "height" : 0.5
  }
```

## Liste todos Pokemons com name 'Pikachu' OU com attack menor ou igual que 0.5 (passo 4)

```js
> var query1 = {name: "Pikachu"}
> var query2 = {attack: {$lte: 0.5}}
> var query = {$or: [query1, query2]}
> db.pokemons.find(query)
> {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce487"),
    "name" : "Pikachu",
    "description" : "It raises its tail to check its sur roundings. The tail is sometimes struck by lightning in this pose.",
    "type" : "eletric",
    "attack" : 42,
    "defense" : 40,
    "height" : 0.4
  }
```

## Liste todos Pokemons com attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 5)

```js
> var query1 = {attack: {$gte: 48}}
> var query2 = {height: {$lte: 0.5}}
> var query = {$and: [query1, query2]}
> db.pokemons.find(query)
> {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce485"),
    "name" : "Charmeleon",
    "description" : "When it swings its burning tail, it elevates the temperature to unbearably high levels.",
    "type" : "fire",
    "attack" : 64,
    "defense" : 58,
    "height" : 0.5
  }
  {
    "_id" : ObjectId("5647ea72ae7ee0ffc22ce486"),
    "name" : "Charizard",
    "description" : "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.",
    "type" : "fire",
    "attack" : 84,
    "defense" : 78,
    "height" : 0.5
  }
```

