# MongoDB - Aula 03 - Exercício
autor: LEONARDO FILIPE

## Liste todos Pokemons com a altura **menor que** 0.5;
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {height: {$lt: 0.5}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
"_id": ObjectId("5670bbb3dbd364f21b5949b0"),
"name": "Pikachu",
"description": "Rato Elétrico bem fofinho",
"type": "electric",
"attack": 55,
"height": 0.4
}
{
"_id": ObjectId("5670bde3dbd364f21b5949b5"),
"name": "Bulbassauro",
"description": "Chicote de trepadeira",
"type": "grama",
"attack": 49,
"height": 0.4
}
{
"_id": ObjectId("5670bec5dbd364f21b5949b8"),
"name": "Caterpie",
"description": "Larva lutadora",
"type": "inseto",
"attack": 30,
"height": 0.3,
"defense": 35
}
Fetched 3 record(s) in 13ms
```


## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {height: {$gte: 0.5}}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
"_id": ObjectId("5670bde8dbd364f21b5949b6"),
"name": "Charmander",
"description": "Esse é o cão chupando manga de fofinho",
"type": "fogo",
"attack": 52,
"height": 0.6
}
{
"_id": ObjectId("5670bdebdbd364f21b5949b7"),
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
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
"_id": ObjectId("5670bde3dbd364f21b5949b5"),
"name": "Bulbassauro",
"description": "Chicote de trepadeira",
"type": "grama",
"attack": 49,
"height": 0.4
}
Fetched 1 record(s) in 9ms
```


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {$or: [{attack: {$lte: 0.5}}, {name: "Pikachu"}]}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
"_id": ObjectId("5670bbb3dbd364f21b5949b0"),
"name": "Pikachu",
"description": "Rato Elétrico bem fofinho",
"type": "electric",
"attack": 55,
"height": 0.4
}
Fetched 1 record(s) in 11ms
```


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
Leonardos-MacBook-Pro(mongod-3.2.0) be-mean-instagram> db.pokemons.find(query)
{
"_id": ObjectId("5670bbb3dbd364f21b5949b0"),
"name": "Pikachu",
"description": "Rato Elétrico bem fofinho",
"type": "electric",
"attack": 55,
"height": 0.4
}
{
"_id": ObjectId("5670bde3dbd364f21b5949b5"),
"name": "Bulbassauro",
"description": "Chicote de trepadeira",
"type": "grama",
"attack": 49,
"height": 0.4
}
{
"_id": ObjectId("5670bdebdbd364f21b5949b7"),
"name": "Squirtle",
"description": "Ejeta água que passarinho não bebe",
"type": "água",
"attack": 48,
"height": 0.5
}
Fetched 3 record(s) in 12ms
```

