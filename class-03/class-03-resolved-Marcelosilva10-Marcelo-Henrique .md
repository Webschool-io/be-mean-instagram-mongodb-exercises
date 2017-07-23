#MongoDB - Aula 03 - Exercício

autor: Marcelo Henrique

##Pokemons menor que 0.5

MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = {height: {$lt: 0.5}}
MarceloLocal(mongod-2.4.9) be-mean-instagram> query
{
  "height": {
    "$lt": 0.5
  }
}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e125ef80adb57fcfaffc8"),
  "name": "Rattata",
  "description": "Parente proximo do hantaro",
  "type": "normal",
  "attack": 33,
  "height": 0.3
}
{
  "_id": ObjectId("564e1334f80adb57fcfaffc9"),
  "name": "Caterpie",
  "description": "Lavra lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}
{
  "_id": ObjectId("564e1389f80adb57fcfaffca"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564e121cf80adb57fcfaffc5"),
  "name": "Caterpie",
  "description": "Lavra lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("56577949e1bc5add00ad15ea"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56577998e1bc5add00ad15eb"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 6 record(s) in 35ms

##Pokemons com a altura maior ou igual que 0.5

MarceloLocal(mongod-2.4.9) be-mean-instagram> var query = {height: {$gte: 0.5}}
MarceloLocal(mongod-2.4.9) be-mean-instagram> query
{
  "height": {
    "$gte": 0.5
  }
}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e1250f80adb57fcfaffc6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564e125af80adb57fcfaffc7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564e1395f80adb57fcfaffcb"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564e139ff80adb57fcfaffcc"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 4 record(s) in 24ms

##Pokemons com a altura menor ou igual que 0.5 E do tipo grama
var query = {$and: [{height: {$lte: 0.5}},{type: /grama/}]}
MarceloLocal(mongod-2.4.9) be-mean-instagram> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": /grama/
    }
  ]
}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e1389f80adb57fcfaffca"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56577949e1bc5add00ad15ea"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 1ms

##Liste os Pokemons com o nome de 'Pikachu' OU com ATTACK menor ou igual que 0.5
var query = {$or: [{attack: {$lte: 0.5}},{name: /Pikachu/i}]}
MarceloLocal(mongod-2.4.9) be-mean-instagram> query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": /Pikachu/i
    }
  ]
}
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56577998e1bc5add00ad15eb"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}

##Liste todos os Pokemons com attack maior igual a 48 e Height menor ou igual que 0.5

var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
MarceloLocal(mongod-2.4.9) be-mean-instagram> query
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
MarceloLocal(mongod-2.4.9) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e125af80adb57fcfaffc7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564e1389f80adb57fcfaffca"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564e139ff80adb57fcfaffcc"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56577949e1bc5add00ad15ea"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56577998e1bc5add00ad15eb"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 5 record(s) in 48ms
