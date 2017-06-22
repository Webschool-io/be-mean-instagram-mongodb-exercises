# MongoDB - Aula 03 - Exercício
autor: DIEGO FERREIRA

## Listagem de todos os pokemons com altura menor que 0.5

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {height : {$lt : 0.5}}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc001ab2c09858ea975d"),
  "name": "Pikachu",
  "description": "Pikachu usa eletricidade como forca. Amigo fiel do Ash",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Listagem de todos os pokemons com altura maior ou igual que 0.5

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {height : {$gte : 0.5}}

Air-de-Diego(mongod-3.0.7) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643b9421ab2c09858ea975c"),
  "name": "Charmeleon",
  "description": "Charmeleon mercilessly destroys its foes using its sharp claws. If it encounters a strong foe, it turns agressive.",
  "attack": 64,
  "defense": 58,
  "height": 11
}
{
  "_id": ObjectId("5643bc5e1ab2c09858ea975e"),
  "name": "Gurdurr",
  "description": "With strengthened bodies, they skillfully wield steel beams to take down buildings. ",
  "attack": 105,
  "defense": 85,
  "height": 12
}
{
  "_id": ObjectId("5643bce81ab2c09858ea975f"),
  "name": "Charizard",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("5643bd581ab2c09858ea9760"),
  "name": "Sawk",
  "description": "Desiring the strongest karate chop, they seclude themselves in mountains and train without sleeping.",
  "attack": 125,
  "defense": 75,
  "height": 14
}
Fetched 4 record(s) in 6ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = { $and : [ { height : { $lte : 0.5 } }, { type : 'grama' } ] }
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> query
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
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 26ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {$or : [{name : 'Pikachu'},{attack : {$lte : 0.5}}]}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc001ab2c09858ea975d"),
  "name": "Pikachu",
  "description": "Pikachu usa eletricidade como forca. Amigo fiel do Ash",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 30ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> var query = {$and : [{attack : {$gte : 48}}, {height : {$lte : 0.5}}]}
Air-de-Diego(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643bc001ab2c09858ea975d"),
  "name": "Pikachu",
  "description": "Pikachu usa eletricidade como forca. Amigo fiel do Ash",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 4ms
```
