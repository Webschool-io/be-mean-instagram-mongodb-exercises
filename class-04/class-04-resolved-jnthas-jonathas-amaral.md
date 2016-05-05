# MongoDB - Aula 04 - Exercicio
autor: Jonathas Amaral

## 1 - Adicionar 2 ataques ao mesmo tempo para 3 pokemons

### Criando query para retornar 3 pokemons
```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> query = {$or: [{name: /rattata/i}, {name: /oddish/i}, {name: /blastoise/i}]}
{
  "$or": [
    {
      "name": /rattata/i
    },
    {
      "name": /oddish/i
    },
    {
      "name": /blastoise/i
    }
  ]
}
```

###Adicionando os ataques nos pokemons
```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, {$pushAll: {attacks: ['soco alto', 'soco baixo']}}, {multi: true});
Updated 3 existing record(s) in 1ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5642a5844f9f678b0b9d94ae"),
  "name": "Blastoise",
  "description": "Pokemon com bazooka",
  "type": "shellfish",
  "attack": 40,
  "height": 0.5,
  "attacks": [
    "soco alto",
    "soco baixo"
  ]
}
{
  "_id": ObjectId("5642a5d24f9f678b0b9d94af"),
  "name": "Oddish",
  "description": "Cara de cebola",
  "type": "weed",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ]
}
{
  "_id": ObjectId("5642a6c64f9f678b0b9d94b1"),
  "name": "Rattata",
  "description": "Ratata é bicho solto, ficar ligeiro ja faz parte do jogo",
  "type": "mouse",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ]
}
Fetched 3 record(s) in 1ms
```


## 2 - Adicionar 1 movimento em todos os pokemons

```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.update({}, {$push: {moves: 'desvio'}}, {multi: true});
Updated 5 existing record(s) in 1ms
WriteResult({
  "nMatched": 5,
  "nUpserted": 0,
  "nModified": 5
})

jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5642a5354f9f678b0b9d94ad"),
  "name": "Snorlax",
  "description": "Pokemon preguiçoso",
  "type": "sleeping",
  "attack": 60,
  "height": 0.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a5844f9f678b0b9d94ae"),
  "name": "Blastoise",
  "description": "Pokemon com bazooka",
  "type": "shellfish",
  "attack": 40,
  "height": 0.5,
  "moves": [
    "desvio"
  ],
  "attacks": [
    "soco alto",
    "soco baixo"
  ]
}
{
  "_id": ObjectId("5642a5d24f9f678b0b9d94af"),
  "name": "Oddish",
  "description": "Cara de cebola",
  "type": "weed",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6614f9f678b0b9d94b0"),
  "name": "Gastly",
  "description": "Bola 8 da sinuca",
  "type": "gas",
  "attack": 20,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6c64f9f678b0b9d94b1"),
  "name": "Rattata",
  "description": "Ratata é bicho solto, ficar ligeiro ja faz parte do jogo",
  "type": "mouse",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 5 record(s) in 3ms
```


## 3 - Inserindo o AindaNaoExisteMon


### Criando um pokemon com valores null
```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> aindaNaoExisteMon = {name: 'AindaNaoExisteMon', description: "Sem maiores informacoes", type: null, attack: null, height: null, attacks: null, moves: null}
{
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informacoes",
  "type": null,
  "attack": null,
  "height": null,
  "attacks": null,
  "moves": null
}
```


### Inserindo o AindaNaoExisteMon

```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.update({name: 'AindaNaoExisteMon'}, {$setOnInsert: aindaNaoExisteMon}, {upsert: true})
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564e91e0fab1c1c7d73bc5bc")
})

jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({name: /aindanaoexistemon/i})
{
  "_id": ObjectId("564e91e0fab1c1c7d73bc5bc"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informacoes",
  "type": null,
  "attack": null,
  "height": null,
  "attacks": null,
  "moves": null
}
Fetched 1 record(s) in 0ms
```


## 4 - Pokemons com ataque investida e mais um que adicionei (soco baixo)

```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({attacks: {$in: ['investida', 'soco baixo']}});
{
  "_id": ObjectId("5642a5844f9f678b0b9d94ae"),
  "name": "Blastoise",
  "description": "Pokemon com bazooka",
  "type": "shellfish",
  "attack": 40,
  "height": 0.5,
  "moves": [
    "desvio"
  ],
  "attacks": [
    "soco alto",
    "soco baixo"
  ]
}
{
  "_id": ObjectId("5642a5d24f9f678b0b9d94af"),
  "name": "Oddish",
  "description": "Cara de cebola",
  "type": "weed",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6c64f9f678b0b9d94b1"),
  "name": "Rattata",
  "description": "Ratata é bicho solto, ficar ligeiro ja faz parte do jogo",
  "type": "mouse",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 3 record(s) in 1ms

```

## 5 - Todos os pokemons com os ataques que adicionei

```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({attacks: {$all: ['soco alto', 'soco baixo']}});
{
  "_id": ObjectId("5642a5844f9f678b0b9d94ae"),
  "name": "Blastoise",
  "description": "Pokemon com bazooka",
  "type": "shellfish",
  "attack": 40,
  "height": 0.5,
  "moves": [
    "desvio"
  ],
  "attacks": [
    "soco alto",
    "soco baixo"
  ]
}
{
  "_id": ObjectId("5642a5d24f9f678b0b9d94af"),
  "name": "Oddish",
  "description": "Cara de cebola",
  "type": "weed",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6c64f9f678b0b9d94b1"),
  "name": "Rattata",
  "description": "Ratata é bicho solto, ficar ligeiro ja faz parte do jogo",
  "type": "mouse",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ]
}
Fetched 3 record(s) in 1ms
```

## 6 - Todos pokemons que não são do tipo shellfish
```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({type: {$ne: 'shellfish'}});
{
  "_id": ObjectId("5642a5354f9f678b0b9d94ad"),
  "name": "Snorlax",
  "description": "Pokemon preguiçoso",
  "type": "sleeping",
  "attack": 60,
  "height": 0.6,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a5d24f9f678b0b9d94af"),
  "name": "Oddish",
  "description": "Cara de cebola",
  "type": "weed",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6614f9f678b0b9d94b0"),
  "name": "Gastly",
  "description": "Bola 8 da sinuca",
  "type": "gas",
  "attack": 20,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("5642a6c64f9f678b0b9d94b1"),
  "name": "Rattata",
  "description": "Ratata é bicho solto, ficar ligeiro ja faz parte do jogo",
  "type": "mouse",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("564e91e0fab1c1c7d73bc5bc"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informacoes",
  "type": null,
  "attack": null,
  "height": null,
  "attacks": null,
  "moves": null
}
Fetched 5 record(s) in 1ms
```

## 7 - Pokemons com defesa > 49 e com ataque 'soco alto'

```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({$and: [{attacks: {$in: ['soco alto']}}, {defense: {$gt: 49}}]});
{
  "_id": ObjectId("5642a6c64f9f678b0b9d94b1"),
  "name": "Rattata",
  "description": "Ratata é bicho solto, ficar ligeiro ja faz parte do jogo",
  "type": "mouse",
  "attack": 30,
  "height": 0.1,
  "attacks": [
    "soco alto",
    "soco baixo"
  ],
  "moves": [
    "desvio"
  ],
  "defense": 68
}
Fetched 1 record(s) in 1ms

```


## 8 - Removendo pokemon do tipo gas e com ataque menor que 50

```
jonathas-desktop(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove({$and: [{type: 'gas'}, {attack: {$lt: 50}}]});
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})

```




