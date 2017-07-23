###MongoDB - Aula 03 - Exercício
Autor: Willian Dutras

##Liste todos Pokemons com a altura menor que 0.5
```
canalsushi(mongod-3.0.7) pokemons> var query = {height: {$lt: 0.5}}
canalsushi(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564921350910df3d8696d70e"),
  "name": "Weedle",
  "description": "Minhoca arregaça cú",
  "type": "bug",
  "attack": 30,
  "defense": 10,
  "height": 0.3
}
Fetched 1 record(s) in 2ms
```

##Liste todos Pokemons com a altura maior ou igual que 0.5
```
canalsushi(mongod-3.0.7) pokemons> var query = {height: {$gte: 0.5}}
canalsushi(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564921350910df3d8696d709"),
  "name": "Beedrill",
  "description": "Mel deus do céu!",
  "type": "bug",
  "attack": 70,
  "defense": 30,
  "height": 1
}
{
  "_id": ObjectId("564921350910df3d8696d70a"),
  "name": "Raichu",
  "description": "Tipo o pikachu, só que sem a pika",
  "type": "bug",
  "attack": 90,
  "defense": 30,
  "height": 0.8
}
{
  "_id": ObjectId("564921350910df3d8696d70b"),
  "name": "Vulpix",
  "description": "Lindos cachos",
  "type": "fire",
  "attack": 40,
  "defense": 30,
  "height": 0.6
}
{
  "_id": ObjectId("564921350910df3d8696d70c"),
  "name": "Machamp",
  "description": "Veem monstro!",
  "type": "fighting",
  "attack": 100,
  "defense": 40,
  "height": 1.6
}
{
  "_id": ObjectId("564921350910df3d8696d70d"),
  "name": "Rapidash",
  "description": "Éssa fera aí mêu!",
  "type": "fire",
  "attack": 80,
  "defense": 30,
  "height": 1.7
}
Fetched 5 record(s) in 4ms
```

##Liste todos Pokemons com a altura menor ou igual que 0.5 e do tipo grama
```
canalsushi(mongod-3.0.7) pokemons> var query = {$and: [{height: {$lte: 0.5}},{type: 'Grama'}]}
canalsushi(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564d232e8592ada165362bd6"),
  "name": "Maconha",
  "description": "Suave na nave",
  "type": "Grama",
  "attack": 420,
  "defense": 40,
  "height": 0.5
}
Fetched 1 record(s) in 1ms
```

##Liste todos Pokemons com o name 'Pikachu' ou com attack menor ou igual que 0.5
```
canalsushi(mongod-3.0.7) pokemons> var query = {$or: [{name: 'Maconha'},{attack: {$lte: 0.5}}]}
canalsushi(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564d232e8592ada165362bd6"),
  "name": "Maconha",
  "description": "Suave na nave",
  "type": "Grama",
  "attack": 420,
  "defense": 40,
  "height": 0.5
}
Fetched 1 record(s) in 20ms
```

##Liste todos Pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5
```
canalsushi(mongod-3.0.7) pokemons> var query = {$and: [{attack: {$gte:48}},{height: {$lte: 0.5}}]}
canalsushi(mongod-3.0.7) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564d232e8592ada165362bd6"),
  "name": "Maconha",
  "description": "Suave na nave",
  "type": "Grama",
  "attack": 420,
  "defense": 40,
  "height": 0.5
}
Fetched 1 record(s) in 3ms
```
