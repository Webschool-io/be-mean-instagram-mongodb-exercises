## MongoDb - Aula 03 Exercício
Autor: Leonardo Larocca

## 1 - Listando pokemons com altura menor que 0.5.
```
asus(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
asus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
asus(mongod-3.0.7) be-mean-pokemons> 
```

## 2 - Listando pokemons com altura maior ou igual a 0.5.
```
asus(mongod-3.0.7) be-mean-pokemons> var query = {height:{$gte: 0.5}}
asus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565a1a3275dfc16def1a8b62"),
  "name": "Pikachu",
  "description": "Rato eletrico fofinho",
  "attack": 55,
  "defense": 120,
  "height": 0.5,
  "lastModified": ISODate("2015-11-29T05:05:01.681Z")
}
{
  "_id": ObjectId("565a1a3275dfc16def1a8b63"),
  "name": "Charizard",
  "description": "Dragão teimoso",
  "attack": 120,
  "defense": 50,
  "height": 2
}
{
  "_id": ObjectId("565a1a3275dfc16def1a8b64"),
  "name": "Squirtle",
  "description": "Tartaruga a jato",
  "attack": 30,
  "defense": 45,
  "height": 0.6
}
{
  "_id": ObjectId("565a1a3275dfc16def1a8b65"),
  "name": "Entei",
  "description": "Starfish Head Horse",
  "attack": 85,
  "defense": 70,
  "height": 1.98
}
{
  "_id": ObjectId("565a1a3275dfc16def1a8b66"),
  "name": "Pidgeot",
  "description": "Calopsita eletrica",
  "attack": 150,
  "defense": 120,
  "height": 3.5
}
Fetched 5 record(s) in 4ms
asus(mongod-3.0.7) be-mean-pokemons> 

```

## 3 - Listando pokemons com altura menor ou igual a 0.5 e do tipo grama. 
```
asus(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{height:{lte: 0.5}},{description: 'grama'}]}
asus(mongod-3.0.7) be-mean-pokemons> db.foo.find(query)
Fetched 0 record(s) in 1ms
asus(mongod-3.0.7) be-mean-pokemons> 

```

## 4 - Listando pokemons com name "Pikachu" ou com attack menor ou igual a 0.5
```
asus(mongod-3.0.7) be-mean-pokemons> var query = {$or:[{name: 'Pikachu'},{attack:{lte: 0.5}}]}
asus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565a1a3275dfc16def1a8b62"),
  "name": "Pikachu",
  "description": "Rato eletrico fofinho",
  "attack": 55,
  "defense": 120,
  "height": 0.5,
  "lastModified": ISODate("2015-11-29T05:05:01.681Z")
}
Fetched 1 record(s) in 1ms
asus(mongod-3.0.7) be-mean-pokemons> 

```

## 5 - Listando pokemons com ataque maior ou igual que 48 e com height menor ou igual que 0.5
```
asus(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
asus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565a1a3275dfc16def1a8b62"),
  "name": "Pikachu",
  "description": "Rato eletrico fofinho",
  "attack": 55,
  "defense": 120,
  "height": 0.5,
  "lastModified": ISODate("2015-11-29T05:05:01.681Z")
}
Fetched 1 record(s) in 2ms

```

