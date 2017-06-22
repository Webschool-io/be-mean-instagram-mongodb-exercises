# MongoDB - Aula 03 - Exercício
autor: Jefferson da Silva

## Liste todos Pokemons com a altura **menor que** 0.5;
```js
var query = { height: {$lt: 0.5}}
db.pokemons.find(query)
Fetched 0 record(s) in 18ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```js
var query = { height: {$gte: 0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("56bb0e84681eaca5d83a6912"),
  "name": "Fearow",
  "description": "Fearow is recognized by its long neck and elongated beak.",
  "attack": 5,
  "defense": 3,
  "height": 1.2
}
{
  "_id": ObjectId("56bb0e84681eaca5d83a6913"),
  "name": "Sandshrew",
  "description": "Tatu do deserto",
  "attack": 4,
  "defense": 4,
  "height": 0.6
}
{
  "_id": ObjectId("56bb0e84681eaca5d83a6914"),
  "name": "Nidoqueen",
  "description": "Nidoqueen's body is encased in extremely hard scales.",
  "attack": 5,
  "defense": 4,
  "height": 1.3
}
{
  "_id": ObjectId("56bb0e84681eaca5d83a6915"),
  "name": "Oddish",
  "description": "During the daytime, Oddish buries itself in soil to absorb nutrients from the ground using its entire body.",
  "attack": 3,
  "defense": 3,
  "height": 0.5
}
{
  "_id": ObjectId("56bb0e84681eaca5d83a6916"),
  "name": "Parasect",
  "description": "Parasect is known to infest large trees en masse and drain nutrients from the lower trunk and roots.",
  "attack": 5,
  "defense": 4,
  "height": 1
}
Fetched 5 record(s) in 3ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```js
var query = { $and: [{ height: {$lte: 0.5}}, {type: 'grass'}]}
db.pokemons.find(query)
Fetched 0 record(s) in 35ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```js
var query = { $or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 23ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```js
var query = { $and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```
