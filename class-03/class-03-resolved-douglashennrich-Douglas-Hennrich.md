# MongoDB - Aula 03 - Exercício
autor: Douglas Hennrich

## Liste todos Pokemons com a altura **menor que** 5
```javascript
var query = { height: { $lt: 5 }}
MacBook-Pro-de-Douglas(mongod-3.0.6) be-mean-pokemons> db.pokedex.find(query)
{
  "_id": ObjectId("56427e4e8c701b87518b7cf4"),
  "name": "Mew",
  "description": "Because its battle abilities were raised to the ultimate level, it thinks only of de feating its foes.",
  "attack": 100,
  "defense": 100,
  "height": 4
}
Fetched 1 record(s) in 14ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 5
```javascript
var query = { height: { $gte: 5 }}
MacBook-Pro-de-Douglas(mongod-3.0.6) be-mean-pokemons> db.pokedex.find(query)
{
  "_id": ObjectId("56427e4e8c701b87518b7cf5"),
  "name": "Rhyhorn",
  "description": "Strong, but not too bright, this Pokmon can shatter even a skyscraper with its charging Tackles.",
  "attack": 85,
  "defense": 95,
  "height": 10
}
{
  "_id": ObjectId("56427e4e8c701b87518b7cf6"),
  "name": "Staryu",
  "description": "As long as the center section is unharmed, it can grow back fully even if it is chopped to bits.",
  "attack": 45,
  "defense": 55,
  "height": 8
}
{
  "_id": ObjectId("56427e4e8c701b87518b7cf7"),
  "name": "Gyarados",
  "description": "It has an extremely aggressive nature. The HYPER BEAM it shoots from its mouth totally incinerates all targets.",
  "attack": 125,
  "defense": 79,
  "height": 65
}
{
  "_id": ObjectId("56427e4e8c701b87518b7cf8"),
  "name": "Kabuto",
  "description": "It is thought to have inhabited beaches 300 million years ago. It is protected by a stiff shell.",
  "attack": 80,
  "defense": 90,
  "height": 5
}
Fetched 4 record(s) in 8ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 5 **E** attack **maior ou igual que** 80
```javascript
var query = { $and: [ { height: { $lte: 5 } }, { attack: { $gte: 80 } } ] }

db.pokedex.find(query)
{
  "_id": ObjectId("56427e4e8c701b87518b7cf4"),
  "name": "Mew",
  "description": "Because its battle abilities were raised to the ultimate level, it thinks only of de feating its foes.",
  "attack": 100,
  "defense": 100,
  "height": 4
}
{
  "_id": ObjectId("56427e4e8c701b87518b7cf8"),
  "name": "Kabuto",
  "description": "It is thought to have inhabited beaches 300 million years ago. It is protected by a stiff shell.",
  "attack": 80,
  "defense": 90,
  "height": 5
}
Fetched 2 record(s) in 12ms
```

## Liste todos Pokemons com o name `Mew` **OU** com attack **menor ou igual que** 80
```javascript
var query = { $or : [ { name: "Mew" }, { attack: { $lte: 80 } } ] }
MacBook-Pro-de-Douglas(mongod-3.0.6) be-mean-pokemons> db.pokedex.find(query)
{
  "_id": ObjectId("56427e4e8c701b87518b7cf4"),
  "name": "Mew",
  "description": "Because its battle abilities were raised to the ultimate level, it thinks only of de feating its foes.",
  "attack": 100,
  "defense": 100,
  "height": 4
}
{
  "_id": ObjectId("56427e4e8c701b87518b7cf6"),
  "name": "Staryu",
  "description": "As long as the center section is unharmed, it can grow back fully even if it is chopped to bits.",
  "attack": 45,
  "defense": 55,
  "height": 8
}
{
  "_id": ObjectId("56427e4e8c701b87518b7cf8"),
  "name": "Kabuto",
  "description": "It is thought to have inhabited beaches 300 million years ago. It is protected by a stiff shell.",
  "attack": 80,
  "defense": 90,
  "height": 5
}
Fetched 3 record(s) in 8ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 85 **E** com  height **menor ou igual que** 10
```javascript
var query = { $and: [ { attack: { $gte : 85 } }, { height: { $lte: 10 } } ] }
MacBook-Pro-de-Douglas(mongod-3.0.6) be-mean-pokemons> db.pokedex.find(query)
{
  "_id": ObjectId("56427e4e8c701b87518b7cf4"),
  "name": "Mew",
  "description": "Because its battle abilities were raised to the ultimate level, it thinks only of de feating its foes.",
  "attack": 100,
  "defense": 100,
  "height": 4
}
{
  "_id": ObjectId("56427e4e8c701b87518b7cf5"),
  "name": "Rhyhorn",
  "description": "Strong, but not too bright, this Pokmon can shatter even a skyscraper with its charging Tackles.",
  "attack": 85,
  "defense": 95,
  "height": 10
}
Fetched 2 record(s) in 2ms
```
