# MongoDB - Aula 03 - Exercício
autor: Thiago Milani

# Liste todos os Pokemons com altura menor que 0.5 (passo 1)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {height: {$lt: 0.5}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 9ms
```

# Liste todos os Pokemons com altura maior ou igual a 0.5 (passo 2)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query = {height: {$gte: 0.5}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a23e"),
  "name": "Raichu",
  "description": "Eletric modified",
  "attack": 50,
  "defense": 30,
  "height": 0.8
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a23f"),
  "name": "Sandshrew",
  "description": "Ground",
  "attack": 40,
  "defense": 40,
  "height": 0.6
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a240"),
  "name": "Emboar",
  "description": "Fire, Fighting",
  "attack": 60,
  "defense": 30,
  "height": 1.6
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a241"),
  "name": "Serperior",
  "description": "Grass",
  "attack": 40,
  "defense": 40,
  "height": 3.3
}
{
  "_id": ObjectId("5793ab9d8d7ebd1b1f72a242"),
  "name": "Arceus",
  "description": "Normal",
  "attack": 60,
  "defense": 50,
  "height": 3.2
}
Fetched 5 record(s) in 3ms
```

# Liste todos os Pokemons com altura menor ou igual a 0.5 e do tipo grama (passo 3)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query1 = {height: {$lte: 0.5}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query2 = {type: "grama"}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
Fetched 0 record(s) in 38ms
```

# Liste todos os Pokemons com nome Pikachu ou attack menor ou igual a 0.5 (passo 4)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query1 = {name: "Pikachu"}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query2 = {attack: {$lte: 0.5}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find({$or: [query1, query2]})
Fetched 0 record(s) in 22ms
```

# Liste todos os Pokemons com attack maior ou igual a 48 E altura menor ou igual a 0.5 (passo 5)

```
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query1 = {attack: {$gte: 48}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> var query2 = {height: {$lte: 0.5}}
zito-desktop(mongod-3.2.8) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
Fetched 0 record(s) in 82ms
```