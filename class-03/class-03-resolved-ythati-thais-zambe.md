# MongoDB - Aula 03 - Exercício
Autor: Thais Zambe

## Liste todos Pokemons com a altura **menor que** 0.5;
```json
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {height:{$lt: 0.5}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564894bf8c1c831aa98033f8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564898108c1c831aa98033fe"),
  "name": "Aron",
  "description": "Coisa estranha furadinha e fofinha",
  "type": "steel",
  "attack": 70,
  "height": 0.4
}
Fetched 3 record(s) in 2ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```json
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {height:{$gte: 0.5}}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f9"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564894bf8c1c831aa98033fa"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564898108c1c831aa98033fb"),
  "name": "Zorua",
  "description": "Raposa metida",
  "type": "dark",
  "attack": 65,
  "height": 0.7
}
{
  "_id": ObjectId("564898108c1c831aa98033fc"),
  "name": "Charmeleon",
  "description": "Charmander revolts",
  "type": "fire",
  "attack": 64,
  "height": 1.09
}
{
  "_id": ObjectId("564898108c1c831aa98033fd"),
  "name": "Gourgeist",
  "description": "Abóbora Nicky Minaj",
  "type": "ghost",
  "attack": 90,
  "height": 1.7
}
{
  "_id": ObjectId("564898108c1c831aa98033ff"),
  "name": "Mawile",
  "description": "Aquele Ukyo do Samurai Shodown",
  "type": "steel",
  "attack": 85,
  "height": 0.6
}
Fetched 6 record(s) in 2ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```json
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {$and: [{height:{$lte: 0.5}}, {type:'grama'}]}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```json
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {$or: [{name:'Pikachu'}, {attack:{$lte: 0.5}}]}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com height **menor ou igual que** 0.5
```json
wolkenritter(mongod-3.0.6) be-mean-pokemons> var query = {$and: [{attack:{$gte: 48}}, {height:{$lte: 0.5}}]}
wolkenritter(mongod-3.0.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564894bf8c1c831aa98033f7"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564894bf8c1c831aa98033f8"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564894bf8c1c831aa98033fa"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564898108c1c831aa98033fe"),
  "name": "Aron",
  "description": "Coisa estranha furadinha e fofinha",
  "type": "steel",
  "attack": 70,
  "height": 0.4
}
Fetched 4 record(s) in 1ms
```

