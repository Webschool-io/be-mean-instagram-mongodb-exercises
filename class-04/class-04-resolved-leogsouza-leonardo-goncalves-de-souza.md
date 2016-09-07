# MongoDB - Aula 04 - Exercício
autor: Leonardo Gonçalves de Souza

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> query
{
  "name": {
    "$in": [
      "Pikachu",
      "Squirtle",
      "Bulbassauro",
      "Charmander"
    ]
  }
}

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> mod
{
  "$pushAll": {
    "moves": [
      "hadouken",
      "sonic boom"
    ]
  }
}

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> options
{
  "multi": true
}

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 26ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c230927eb136c4319ae3e3"),
  "name": "Pikachu",
  "description": "Pokemon elétrico",
  "attack": 55,
  "defense": 40,
  "height": "4",
  "type": "eletrico",
  "moves": [
    "hadouken",
    "sonic boom"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e4"),
  "name": "Squirtle",
  "description": "Vive na água",
  "attack": 48,
  "defense": 65,
  "height": "5",
  "type": "agua",
  "moves": [
    "hadouken",
    "sonic boom"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e5"),
  "name": "Bulbassauro",
  "description": "Quem é esse pokemon",
  "attack": 49,
  "defense": 49,
  "height": "7",
  "type": "venenoso",
  "moves": [
    "hadouken",
    "sonic boom"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e2"),
  "name": "Charmander",
  "description": "Pokemon fofinho",
  "attack": 52,
  "defense": 43,
  "height": "6",
  "type": "fogo",
  "moves": [
    "hadouken",
    "sonic boom"
  ]
}
```

## Adicionar 1 movimento em todos os pokemons: desvio.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var query = {}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 15 existing record(s) in 26ms
WriteResult({
  "nMatched": 15,
  "nUpserted": 0,
  "nModified": 15
})
```

## Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> mod
{
  "$setOnInsert": {
    "name": "AIndaNaoExisteMon",
    "attack": null,
    "defense": null,
    "height": null,
    "type": null,
    "moves": [ ]
  }
}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var options = {upsert: true}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 16ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("57c242be238dfe8efd3c40a9")
})

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find({"_id": ObjectId("57c242be238dfe8efd3c40a9")})
{
  "_id": ObjectId("57c242be238dfe8efd3c40a9"),
  "name": "AIndaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null,
  "moves": [ ]
}
Fetched 1 record(s) in 7ms
```

## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var query = {moves: {$all: ['investida','hadouken']}}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c230927eb136c4319ae3e4"),
  "name": "Squirtle",
  "description": "Vive na água",
  "attack": 48,
  "defense": 65,
  "height": "5",
  "type": "agua",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e5"),
  "name": "Bulbassauro",
  "description": "Quem é esse pokemon",
  "attack": 49,
  "defense": 49,
  "height": "7",
  "type": "venenoso",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e2"),
  "name": "Charmander",
  "description": "Pokemon fofinho",
  "attack": 52,
  "defense": 43,
  "height": "6",
  "type": "fogo",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida"
  ]
}
Fetched 3 record(s) in 115ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> query
{
  "moves": {
    "$all": [
      "hadouken",
      "sonic boom",
      "desvio",
      "investida",
      "ave fenix"
    ]
  }
}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c230927eb136c4319ae3e2"),
  "name": "Charmander",
  "description": "Pokemon fofinho",
  "attack": 52,
  "defense": 43,
  "height": "6",
  "type": "fogo",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida",
    "ave fenix"
  ]
}
Fetched 1 record(s) in 16ms
```

## Pesquisar todos os pokemons que não são do tipo elétrico
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> query
{
  "type": {
    "$ne": "elétrico"
  }
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3db"),
  "name": "Pidgeot",
  "description": "Passarinho legalzinho",
  "attack": 56,
  "defense": 35,
  "height": 3,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3dc"),
  "name": "Clefairy",
  "description": "Que fofura",
  "attack": 45,
  "defense": 48,
  "height": 6,
  "type": "mágico",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3dd"),
  "name": "Zubat",
  "description": "O mais odiado em Pokemon Go",
  "attack": 45,
  "defense": 35,
  "height": 8,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3de"),
  "name": "Psyduck",
  "description": "Pato Maluco",
  "attack": 52,
  "defense": 48,
  "height": 8,
  "type": "agua",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c1fca57eb136c4319ae3df"),
  "name": "Miguelmon",
  "description": "Pokemon estranho",
  "attack": 27,
  "defense": 25,
  "height": 0.2,
  "type": "grama",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c1fcc57eb136c4319ae3e0"),
  "name": "Fabianamon",
  "description": "Pokemon femea",
  "attack": 48,
  "defense": 32,
  "height": 0.4,
  "type": "grama",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c20f457eb136c4319ae3e1"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("57c22000238dfe8efd3c40a8"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e4"),
  "name": "Squirtle",
  "description": "Vive na água",
  "attack": 48,
  "defense": 65,
  "height": "5",
  "type": "agua",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e5"),
  "name": "Bulbassauro",
  "description": "Quem é esse pokemon",
  "attack": 49,
  "defense": 49,
  "height": "7",
  "type": "venenoso",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e2"),
  "name": "Charmander",
  "description": "Pokemon fofinho",
  "attack": 52,
  "defense": 43,
  "height": "6",
  "type": "fogo",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida",
    "ave fenix"
  ]
}
{
  "_id": ObjectId("57c242be238dfe8efd3c40a9"),
  "name": "AIndaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "type": null,
  "moves": [ ]
}
```

## Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> query
{
  "moves": "investida",
  "defense": {
    "$not": {
      "$lte": 49
    }
  }
}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3d8"),
  "name": "Sandshrew",
  "description": "Parece um tatu",
  "attack": 75,
  "defense": 85,
  "height": 6,
  "type": "terra",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3d9"),
  "name": "Nidorino",
  "description": "Tá com cara de bravo",
  "attack": 72,
  "defense": 57,
  "height": 9,
  "type": "venenoso",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3da"),
  "name": "Charizard",
  "description": "Meu dragão favorito",
  "attack": 84,
  "defense": 78,
  "height": 17,
  "type": "fogo",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c20f457eb136c4319ae3e1"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("57c22000238dfe8efd3c40a8"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("57c230927eb136c4319ae3e4"),
  "name": "Squirtle",
  "description": "Vive na água",
  "attack": 48,
  "defense": 65,
  "height": "5",
  "type": "agua",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida"
  ]
}
Fetched 6 record(s) in 136ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> query
{
  "$and": [
    {
      "type": "agua",
      "attack": {
        "$lte": 50
      }
    }
  ]
}
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c230927eb136c4319ae3e4"),
  "name": "Squirtle",
  "description": "Vive na água",
  "attack": 48,
  "defense": 65,
  "height": "5",
  "type": "agua",
  "moves": [
    "hadouken",
    "sonic boom",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 16ms
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 6ms
WriteResult({
  "nRemoved": 1
})
```
