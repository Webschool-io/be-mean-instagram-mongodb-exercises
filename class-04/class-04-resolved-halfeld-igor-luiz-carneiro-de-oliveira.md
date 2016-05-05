# MongoDB - Aula 04 - Exercício
Autor: Igor luíz


## Adicionar dois ataques ao mesmo tempo para os pokemons: __Pikachu__, __Squirtle__, __Bulbassauro__ e __Charmander__

```sh
localhost(mongod-3.0.8) be-mean-pokemons> query
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "name": /squirtle/i
    },
    {
      "name": /bulbassauro/i
    },
    {
      "name": /charmander/i
    }
  ]
}

localhost(mongod-3.0.8) be-mean-pokemons> mod
{
  "$push": {
    "moves": "pular"
  }
}

localhost(mongod-3.0.8) be-mean-pokemons> options
{
  "multi": true
}

localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 3ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```


## Adicionar movimento __desvio__ em todos os pokemons

```sh
localhost(mongod-3.0.8) be-mean-pokemons> mod
{
  "$push": {
    "moves": "desvio"
  }
}

localhost(mongod-3.0.8) be-mean-pokemons> options
{
  "multi": true
}

localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.update({}, mod, options)
Updated 12 existing record(s) in 3ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})
```

## Adicionar o pokemon __AindaNaoExisteMon__, caso ele ainda nao existe com todos os dados com valor __null__ e a descrição: "Sem maiores informações"

```sh
localhost(mongod-3.0.8) be-mean-pokemons> query
{
  "name": /AindaNaoExisteMon/i
}

localhost(mongod-3.0.8) be-mean-pokemons> mod
{
  "$setOnInsert": {
    "name": "AindaNaoExisteMon",
    "attack": null,
    "defense": null,
    "height": null,
    "moves": null,
    "description": "Sem maiores informações"
  }
}

localhost(mongod-3.0.8) be-mean-pokemons> options
{
  "upsert": true
}

localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56b2c1c7b3d4234aa00a696a")
})
```

## Pesquisar todos os pokemons que possuam o ataque __investida__ e mais um que você adicionou, escolha seu pokemon favorito

```sh
localhost(mongod-3.0.8) be-mean-pokemons> query
{
  "moves": {
    "$in": [
      /investida/i,
      /pedrada/i
    ]
  }
}

localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b1385b21f82f17b072ce4f"),
  "name": "Ivysaur",
  "description": "bananeira ambulante, porém muito habilidoso",
  "attack": 50,
  "defense": 50,
  "height": 1,
  "type": "grama",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b1390d21f82f17b072ce50"),
  "name": "Blastoise",
  "description": "pokemon 'Vem monstro!'",
  "attack": 60,
  "defense": 60,
  "height": 1.6,
  "type": "agua",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b139e721f82f17b072ce51"),
  "name": "Butterfree",
  "description": "pokemon 'cuti cuti'",
  "attack": 35,
  "defense": 40,
  "height": 1.1,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13a4d21f82f17b072ce52"),
  "name": "Pidgeotto",
  "description": "O que voa e bota moral",
  "attack": 40,
  "defense": 35,
  "height": 1.1,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13ad721f82f17b072ce53"),
  "name": "Ninetales",
  "description": "O que tem nove caldas",
  "attack": 50,
  "defense": 50,
  "height": 1.1,
  "type": "fogo",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13b3721f82f17b072ce54"),
  "name": "Psyduck",
  "description": "Fica doidão, aí solta o poder",
  "attack": 35,
  "defense": 30,
  "height": 0.8,
  "type": "agua",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b173ecf3bf0cb1edd0f06d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b28a4324793cc8da6b06b2"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b17446f3bf0cb1edd0f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 50,
  "moves": [
    "investida",
    "choque do trovão",
    "pular",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b29c46b3d4234aa00a6968"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b137c521f82f17b072ce4e"),
  "name": "Charmander",
  "description": "pokemon de fogo mais que lokão!!!",
  "attack": 45,
  "defense": 49,
  "height": 0.6,
  "type": "fogo",
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b1741cf3bf0cb1edd0f06e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5,
  "defense": 37,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b2c42f24793cc8da6b06b3"),
  "name": "Onix",
  "description": "Pedregulio ambulante",
  "type": "pedra",
  "attack": 25,
  "height": 8.8,
  "defense": 100,
  "active": false,
  "moves": [
    "investida",
    "pular",
    "pedrada"
  ]
}
Fetched 13 record(s) in 2ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou

```sh
localhost(mongod-3.0.8) be-mean-pokemons> query
{
  "moves": {
    "$in": [
      /desvio/i,
      /pular/i,
      /pedrada/i
    ]
  }
}

localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b1385b21f82f17b072ce4f"),
  "name": "Ivysaur",
  "description": "bananeira ambulante, porém muito habilidoso",
  "attack": 50,
  "defense": 50,
  "height": 1,
  "type": "grama",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b1390d21f82f17b072ce50"),
  "name": "Blastoise",
  "description": "pokemon 'Vem monstro!'",
  "attack": 60,
  "defense": 60,
  "height": 1.6,
  "type": "agua",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b139e721f82f17b072ce51"),
  "name": "Butterfree",
  "description": "pokemon 'cuti cuti'",
  "attack": 35,
  "defense": 40,
  "height": 1.1,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13a4d21f82f17b072ce52"),
  "name": "Pidgeotto",
  "description": "O que voa e bota moral",
  "attack": 40,
  "defense": 35,
  "height": 1.1,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13ad721f82f17b072ce53"),
  "name": "Ninetales",
  "description": "O que tem nove caldas",
  "attack": 50,
  "defense": 50,
  "height": 1.1,
  "type": "fogo",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13b3721f82f17b072ce54"),
  "name": "Psyduck",
  "description": "Fica doidão, aí solta o poder",
  "attack": 35,
  "defense": 30,
  "height": 0.8,
  "type": "agua",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b173ecf3bf0cb1edd0f06d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b28a4324793cc8da6b06b2"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b17446f3bf0cb1edd0f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 50,
  "moves": [
    "investida",
    "choque do trovão",
    "pular",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b29c46b3d4234aa00a6968"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b137c521f82f17b072ce4e"),
  "name": "Charmander",
  "description": "pokemon de fogo mais que lokão!!!",
  "attack": 45,
  "defense": 49,
  "height": 0.6,
  "type": "fogo",
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b1741cf3bf0cb1edd0f06e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5,
  "defense": 37,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b2c42f24793cc8da6b06b3"),
  "name": "Onix",
  "description": "Pedregulio ambulante",
  "type": "pedra",
  "attack": 25,
  "height": 8.8,
  "defense": 100,
  "active": false,
  "moves": [
    "investida",
    "pular",
    "pedrada"
  ]
}
Fetched 13 record(s) in 5ms
```

# Pesquisar todos os pokemons que não são do tipo elétrico

```sh
localhost(mongod-3.0.8) be-mean-pokemons> query
{
  "type": {
    "$ne": "elétrico"
  }
}

localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b1385b21f82f17b072ce4f"),
  "name": "Ivysaur",
  "description": "bananeira ambulante, porém muito habilidoso",
  "attack": 50,
  "defense": 50,
  "height": 1,
  "type": "grama",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b1390d21f82f17b072ce50"),
  "name": "Blastoise",
  "description": "pokemon 'Vem monstro!'",
  "attack": 60,
  "defense": 60,
  "height": 1.6,
  "type": "agua",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b139e721f82f17b072ce51"),
  "name": "Butterfree",
  "description": "pokemon 'cuti cuti'",
  "attack": 35,
  "defense": 40,
  "height": 1.1,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13a4d21f82f17b072ce52"),
  "name": "Pidgeotto",
  "description": "O que voa e bota moral",
  "attack": 40,
  "defense": 35,
  "height": 1.1,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13ad721f82f17b072ce53"),
  "name": "Ninetales",
  "description": "O que tem nove caldas",
  "attack": 50,
  "defense": 50,
  "height": 1.1,
  "type": "fogo",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13b3721f82f17b072ce54"),
  "name": "Psyduck",
  "description": "Fica doidão, aí solta o poder",
  "attack": 35,
  "defense": 30,
  "height": 0.8,
  "type": "agua",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b173ecf3bf0cb1edd0f06d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b28a4324793cc8da6b06b2"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b17446f3bf0cb1edd0f06f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 50,
  "moves": [
    "investida",
    "choque do trovão",
    "pular",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b29c46b3d4234aa00a6968"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b137c521f82f17b072ce4e"),
  "name": "Charmander",
  "description": "pokemon de fogo mais que lokão!!!",
  "attack": 45,
  "defense": 49,
  "height": 0.6,
  "type": "fogo",
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b1741cf3bf0cb1edd0f06e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5,
  "defense": 37,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b2c1c7b3d4234aa00a696a"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "moves": null,
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("56b2c42f24793cc8da6b06b3"),
  "name": "Onix",
  "description": "Pedregulio ambulante",
  "type": "pedra",
  "attack": 25,
  "height": 8.8,
  "defense": 100,
  "active": false,
  "moves": [
    "investida",
    "pular",
    "pedrada"
  ]
}
Fetched 14 record(s) in 9ms
```

# Pesquisar todos os pokemons que tenham o ataque __investida__ e tenham a defesa não __menor ou igual a 49__

```sh
localhost(mongod-3.0.8) be-mean-pokemons> query
{
  "$and": [
    {
      "moves": {
        "$in": [
          /investida/i
        ]
      }
    },
    {
      "defense": {
        "$lte": 49
      }
    }
  ]
}

localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b139e721f82f17b072ce51"),
  "name": "Butterfree",
  "description": "pokemon 'cuti cuti'",
  "attack": 35,
  "defense": 40,
  "height": 1.1,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13a4d21f82f17b072ce52"),
  "name": "Pidgeotto",
  "description": "O que voa e bota moral",
  "attack": 40,
  "defense": 35,
  "height": 1.1,
  "type": "voador",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b13b3721f82f17b072ce54"),
  "name": "Psyduck",
  "description": "Fica doidão, aí solta o poder",
  "attack": 35,
  "defense": 30,
  "height": 0.8,
  "type": "agua",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b137c521f82f17b072ce4e"),
  "name": "Charmander",
  "description": "pokemon de fogo mais que lokão!!!",
  "attack": 45,
  "defense": 49,
  "height": 0.6,
  "type": "fogo",
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "pular",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b1741cf3bf0cb1edd0f06e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5,
  "defense": 37,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "pular",
    "desvio"
  ]
}
Fetched 5 record(s) in 8ms
```

# Remova todos os pokemons do tipo __água__ e com attack __menor que 50__

```sh
localhost(mongod-3.0.8) be-mean-pokemons> query
{
  "$and": [
    {
      "type": /agua/i
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}

localhost(mongod-3.0.8) be-mean-pokemons> db.pokemons.remove(query)
Removed 2 record(s) in 12ms
WriteResult({
  "nRemoved": 2
})
```
