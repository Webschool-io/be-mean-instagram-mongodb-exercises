# MongoDB - Aula 03 - Exercício
autor: Eric Cristhiano Marcelino da Silva

## Liste todos Pokemons com a altura **menor que** 0.5;
```
var query = { height: { $lt: 0.5 } }
db.pokemons.find(query)
Fetched 0 record(s) in 15ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
var query = { height: { $gte: 0.5 } }
db.pokemons.find(query)
{
  "_id": ObjectId("564296f061b7097f40e4bb13"),
  "name": "Beedrill",
  "description": "Abelha matadora",
  "type": "poison",
  "attack": 90,
  "defense": 40,
  "height": 1
}
{
  "_id": ObjectId("564296f561b7097f40e4bb14"),
  "name": "Blastoise",
  "description": "Pokemon da água",
  "type": "water",
  "attack": 83,
  "defense": 100,
  "height": 1.6
}
{
  "_id": ObjectId("564296f961b7097f40e4bb15"),
  "name": "Mr. Mime",
  "description": "Pokemon engraçado",
  "type": "psychic",
  "attack": 45,
  "defense": 65,
  "height": 1.3
}
{
  "_id": ObjectId("564296fc61b7097f40e4bb16"),
  "name": "Magmar",
  "description": "Pokemon de fogo",
  "type": "fire",
  "attack": 95,
  "defense": 57,
  "height": 1.3
}
{
  "_id": ObjectId("564296ff61b7097f40e4bb17"),
  "name": "Scizor",
  "description": "Pokemon malvado",
  "type": "bug",
  "attack": 130,
  "defense": 100,
  "height": 1.8
}
Fetched 5 record(s) in 3ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
var query = { $and: [{ height: { $lte: 0.5 } }, { type: "grama" }] }
db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
var query = { $or: [{ name: "Pikachu" }, { attack: { $lte: 0.5 } }] }
db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
var query = { $and: [{ attack: { $gte: 48 } }, { height: { $lte : 0.5 } }] }
db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```