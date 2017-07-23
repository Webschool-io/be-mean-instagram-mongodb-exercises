# MongoDB - Aula 03 - Exercício
autor: Raphael Lima

## Liste todos Pokemons com a altura **menor que** 0.5;
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {'height':{$lt:0.5}}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {'height':{$gte:0.5}}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5647fad53b616ac39c6286dc"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "water",
  "attack": 85,
  "height": 16
}
{
  "_id": ObjectId("5647fb2f3b616ac39c6286dd"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents",
  "type": "fire",
  "attack": 109,
  "height": 17
}
{
  "_id": ObjectId("5647fb363b616ac39c6286de"),
  "name": "Beedrill",
  "description": "Beedrill is extremely territorial",
  "type": "flying",
  "attack": 45,
  "height": 10
}
{
  "_id": ObjectId("5647fb3c3b616ac39c6286df"),
  "name": "Scizor",
  "description": "Scizor is a bipedal, insectoid Pokémon with a red, metallic exoskeleton. It has gray, retractable forewings and hind wings with simple, curved venation",
  "attack": 999,
  "defense": 999,
  "height": 33.33
}
{
  "_id": ObjectId("5647fb413b616ac39c6286e0"),
  "name": "Raticate",
  "description": "Mudança da descrição para atender o exercício",
  "type": "normal",
  "attack": 50,
  "height": 7
}
Fetched 5 record(s) in 1ms

```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{'height':{$lte:0.5}}, {'type':'grama'}]}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{'name':'Pikachu'}, {'attack':{$lte:0.5}}]}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
debian(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{'attack':{$gte:48}}, {'height':{$lte:0.5}}]}
debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```
