# MongoDB - Aula 03 - Exercício
autor: Gustavo Gomes da Fé

##Liste todos Pokemons com a altura menor que 0.5
```
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> var query = { height: { $lt: 0.5 } }
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("568444ac69b7e3b263872a83"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5684452669b7e3b263872a84"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 17ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5
```
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> var query = { height: {$gte: 0.5} }
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56844b6769b7e3b263872a8a"),
  "name": "Butterfree",
  "description": "Description modificada",
  "type": "bug/flying",
  "attack": 45,
  "height": 11,
  "defense": 50
}
{
  "_id": ObjectId("56844bae69b7e3b263872a8b"),
  "name": "Spearow",
  "description": "Spearow has a very loud cry that can be heard over half a mile away. If its high, keening cry is heard echoing all around, it is a sign that they are warning each other of danger.",
  "type": "voador",
  "attack": 60,
  "height": 3,
  "defense": 30
}
Fetched 2 record(s) in 2ms
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> var query = { $and: [ {height: {$lte: 0.5}}, {type: 'grama'} ] }
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fae0adb6ef20dd5aaa43"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> var query = { $or: [ {name: 'Pikachu'}, { attack: {$lte: 0.5} } ] }
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fad0adb6ef20dd5aaa42"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> var query = { $and: [ {attack: {$gte: 48}}, {height: {$lte: 0.5}} ] }
Gustavos-MacBook-Air(mongod-3.2.0) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fad0adb6ef20dd5aaa42"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5643fae0adb6ef20dd5aaa43"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5643faffadb6ef20dd5aaa45"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms
```
