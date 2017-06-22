# MongoDB - Aula 03 - Exercício
autor: C0D3R4

##Liste todos Pokemons com a altura menor que 0.5
```
john1(mongod-3.0.7) be-mean-pokemons> var query = {height:{$lte:0.5}}
john1(mongod-3.0.7) be-mean-pokemons> query
{
  "height": {
    "$lte": 0.5
  }
}
john1(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645142fe649ecb17651a01b"),
  "name": "Blastoise",
  "description": "Tartaruga Ninja cabulozaaa",
  "type": "Turtle",
  "weaknesses": "Grass",
  "attack": 5,
  "defense": 10,
  "height": 0.5,
  "weight": 188.5
}
{
  "_id": ObjectId("5645142fe649ecb17651a01d"),
  "name": "Bulbasaur",
  "description": "Dragão Comodo cabulozooo",
  "type": "Dragao Comodo",
  "weaknesses": "Ice",
  "attack": 10,
  "defense": 20,
  "height": 0.2,
  "weight": 199.5
}
{
  "_id": ObjectId("5645142fe649ecb17651a01e"),
  "name": "Pikachu",
  "description": "Ratinho com rabo de raio cabulozooo",
  "type": "Rato",
  "weaknesses": "Water",
  "attack": 15,
  "defense": 15,
  "height": 0.4,
  "weight": 13.2
}
Fetched 3 record(s) in 1ms
john1(mongod-3.0.7) be-mean-pokemons>

```

## Liste todos Pokemons com a altura maior ou igual que 0.5
```
john1(mongod-3.0.7) be-mean-pokemons> var query = {height:{$gte:0.5}}
john1(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645142fe649ecb17651a01b"),
  "name": "Blastoise",
  "description": "Tartaruga Ninja cabulozaaa",
  "type": "Turtle",
  "weaknesses": "Grass",
  "attack": 5,
  "defense": 10,
  "height": 0.5,
  "weight": 188.5
}
{
  "_id": ObjectId("5645142fe649ecb17651a01c"),
  "name": "Charizard",
  "description": "Dragao cabulozooo",
  "type": "Dragao",
  "weaknesses": "Water",
  "attack": 5,
  "defense": 10,
  "height": 1.05,
  "weight": 199.5
}
Fetched 2 record(s) in 2ms

```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
john1(mongod-3.0.7) be-mean-pokemons> var query = ( { $or: [ { height: { $lt: 0.5 } }, { type: 'grass' } ] } )
john1(mongod-3.0.7) be-mean-pokemons> query
{
  "$or": [
    {
      "height": {
        "$lt": 0.5
      }
    },
    {
      "type": "grass"
    }
  ]
}
john1(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5645142fe649ecb17651a01d"),
  "name": "Bulbasaur",
  "description": "Dragão Comodo cabulozooo",
  "type": "Dragao Comodo",
  "weaknesses": "Ice",
  "attack": 10,
  "defense": 20,
  "height": 0.2,
  "weight": 199.5
}
{
  "_id": ObjectId("5645142fe649ecb17651a01e"),
  "name": "Pikachu",
  "description": "Ratinho com rabo de raio cabulozooo",
  "type": "Rato",
  "weaknesses": "Water",
  "attack": 15,
  "defense": 15,
  "height": 0.4,
  "weight": 13.2
}
Fetched 2 record(s) in 35ms
john1(mongod-3.0.7) be-mean-pokemons>

```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
john1(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(exe)
{
  "_id": ObjectId("5645142fe649ecb17651a01e"),
  "name": "Pikachu",
  "description": "Ratinho com rabo de raio cabulozooo",
  "type": "Rato",
  "weaknesses": "Water",
  "attack": 15,
  "defense": 15,
  "height": 0.4,
  "weight": 13.2
}
Fetched 1 record(s) in 67ms
john1(mongod-3.0.7) be-mean-pokemons>

```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
john1(mongod-3.0.7) be-mean-pokemons> var exercicio = {$or: [{attack:{$gte:48}},{height:{$lte:0.5}}]}
john1(mongod-3.0.7) be-mean-pokemons> exercicio
{
  "$or": [
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
john1(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(exercicio)
{
  "_id": ObjectId("5645142fe649ecb17651a01b"),
  "name": "Blastoise",
  "description": "Tartaruga Ninja cabulozaaa",
  "type": "Turtle",
  "weaknesses": "Grass",
  "attack": 5,
  "defense": 10,
  "height": 0.5,
  "weight": 188.5
}
{
  "_id": ObjectId("5645142fe649ecb17651a01d"),
  "name": "Bulbasaur",
  "description": "Dragão Comodo cabulozooo",
  "type": "Dragao Comodo",
  "weaknesses": "Ice",
  "attack": 10,
  "defense": 20,
  "height": 0.2,
  "weight": 199.5
}
{
  "_id": ObjectId("5645142fe649ecb17651a01e"),
  "name": "Pikachu",
  "description": "Ratinho com rabo de raio cabulozooo",
  "type": "Rato",
  "weaknesses": "Water",
  "attack": 15,
  "defense": 15,
  "height": 0.4,
  "weight": 13.2
}
Fetched 3 record(s) in 2ms
john1(mongod-3.0.7) be-mean-pokemons>

```  
