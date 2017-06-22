# MongoDB - Aula 03 - Exercício
autor: Higor Diego

## Liste todos Pokemons com a altura menor que 0.5; (passo 1)
```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}};
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms

```

## Liste todos Pokemons com a altura maior ou igual que 0.5; (passo 2)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}};
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a22"),
  "name": "Testandomon",
  "description": "teste",
  "type": "exercio",
  "attack": 7001,
  "defense": 600,
  "height": 0.69
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "Pokemon além do teste",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a24"),
  "name": "testando3",
  "description": "testando3",
  "type": "teste3",
  "attack": 3,
  "defense": 300,
  "height": 3.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a25"),
  "name": "testando4",
  "description": "testando4",
  "type": "teste4",
  "attack": 4,
  "defense": 400,
  "height": 4.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a26"),
  "name": "testando5",
  "description": "testando5",
  "type": "teste5",
  "attack": 5,
  "defense": 500,
  "height": 5.6
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a27"),
  "name": "testando6",
  "description": "testando6",
  "type": "teste6",
  "attack": 6,
  "defense": 600,
  "height": 6.6
}
Fetched 6 record(s) in 5ms

```
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama; (passo 3)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$gte: 0.5}}, {type: "grama"}]};
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms

```

## Liste todos Pokemons com name 'Pikachu' OU com attack menor ou igual que 0.5 (passo 4)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte:0.5}}]}
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms

```

## Liste todos Pokemons com attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 5)

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte:48}}, {height:{$lte:0.5}}]}
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms
  
```


