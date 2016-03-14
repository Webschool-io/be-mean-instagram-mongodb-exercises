# MongoDB - Aula 03 - Exercício
autor: HERMANN PESSOA

## Listagem pokemons com altura menor que 5

```
environment(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
environment(mongod-3.0.7) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
environment(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ca20e21aa449a200e3339a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339e"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}

```

## Listagem pokemons com altura maior ou igual que 5

```

environment(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
environment(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ca20e21aa449a200e3339c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defense": 43
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339d"),
  "name": "Squirtle",
  "description": "Pokemon Dazágua",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65
}
Fetched 2 record(s) in 6ms

```

## Listagem pokemons com altura menor ou igual que 5 e tipo grama

```
environment(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}},{type:'grama'}]}
environment(mongod-3.0.7) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grama"
    }
  ]
}
environment(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ca20e21aa449a200e3339b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49
}
Fetched 1 record(s) in 28ms

```

## Listagem pokemons com name "Pikachu" OU com attack menor ou igual que 5

```

environment(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}},{name:'Pikachu'}]}
environment(mongod-3.0.7) be-mean-pokemons> query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": "Pikachu"
    }
  ]
}
environment(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ca20e21aa449a200e3339a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40
}
Fetched 3 record(s) in 31ms
environment(mongod-3.0.7) be-mean-pokemons> 
```

## Listagem pokemons com attack maior ou igual que 48 e com height menor ou igual que 0.5

```
environment(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
environment(mongod-3.0.7) be-mean-pokemons> query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}
environment(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ca20e21aa449a200e3339a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "defense": 40
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defense": 49
}
{
  "_id": ObjectId("56ca20e21aa449a200e3339d"),
  "name": "Squirtle",
  "description": "Pokemon Dazágua",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "defense": 65
}
Fetched 5 record(s) in 8ms