# MongoDB - Aula 04 - Exercício

**Autor**: *Jean Scussel*

## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: /pikachu/i},{name: /squirtle/i}, {name: /bulbassauro/i},{name: /charmander/i}]}

jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var attacks = ['Falsa ofensiva', 'Revide']
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}

jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 1ms
WriteResult({
  	"nMatched": 4,
  	"nUpserted": 0,
  	"nModified": 4
})

jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56466aa09f352f3891c8ccbd"),
  "name": "Pikachu",
  "description": "Coelho amarelo que atira raios",
  "type": "electric",
  "attack": 65,
  "defense": 55,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Choque do trovão",
    "Falsa ofensiva",
    "Revide",
  ]
}
{
  "_id": ObjectId("564dc3f7155300a2118f1cb9"),
  "name": "Bulbassauro",
  "description": "Sapo do mato",
  "type": "grama",
  "attack": 48,
  "defense": 40,
  "height": 1.2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Chicote de trepadeira",
    "Falsa ofensiva",
    "Revide"
  ]
}
{
  "_id": ObjectId("564dc466155300a2118f1cba"),
  "name": "Squirtle",
  "description": "Tartaruga ninja pokemon",
  "type": "água",
  "attack": 48,
  "defense": 40,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Hidro bomba",
    "Falsa ofensiva",
    "Revide"
  ]
}
{
  "_id": ObjectId("564dc4cd155300a2118f1cbb"),
  "name": "Charmander",
  "description": "Dragãozinho de laranjado",
  "type": "fogo",
  "attack": 58,
  "defense": 50,
  "height": 2.1,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Bafo bahiano",
    "Falsa ofensiva",
    "Revide"
  ]
}
Fetched 4 record(s) in 3ms
```

## Adicionar 1 movimento em todos os pokemons: `desvio`.

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 20 existing record(s) in 4ms
WriteResult({
  "nMatched": 20,
  "nUpserted": 0,
  "nModified": 20
})


APENAS UM EXEMPLO DE REGISTRO, POIS SÃO 20 NO TOTAL: 

jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5643ccee5805a8c729a735e8"),
  "name": "Seadra",
  "description": "Cavalo marinho cuspidor",
  "type": "água",
  "attack": 55,
  "defense": 45,
  "height": 1.2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
```

## Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$set: {active: true}, $setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564dcf42322743e7e55c1e80")
})
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564dcf42322743e7e55c1e80"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 0ms

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /bafo bahiano/i]}}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643ccee5805a8c729a735e8"),
  "name": "Seadra",
  "description": "Cavalo marinho cuspidor",
  "type": "água",
  "attack": 55,
  "defense": 45,
  "height": 1.2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643cd355805a8c729a735e9"),
  "name": "Articuno",
  "description": "Pokémon lendário que controla o gelo",
  "type": "gelo",
  "attack": 92,
  "defense": 100,
  "height": 1.7,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643cdeb5805a8c729a735eb"),
  "name": "Rayquaza",
  "description": "Dragão da atmosfera que defende a terra",
  "type": "dragão",
  "attack": 158,
  "defense": 85,
  "height": 7,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}

{
  "_id": ObjectId("564dc4cd155300a2118f1cbb"),
  "name": "Charmander",
  "description": "Dragãozinho de laranjado",
  "type": "fogo",
  "attack": 58,
  "defense": 50,
  "height": 2.1,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Bafo bahiano",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
Fetched 4 record(s) in 1ms
```

## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: [/Falsa ofensiva/i, /Revide/i]}}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56466aa09f352f3891c8ccbd"),
  "name": "Pikachu",
  "description": "Coelho amarelo que atira raios",
  "type": "electric",
  "attack": 65,
  "defense": 55,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Choque do trovão",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dc3f7155300a2118f1cb9"),
  "name": "Bulbassauro",
  "description": "Sapo do mato",
  "type": "grama",
  "attack": 48,
  "defense": 40,
  "height": 1.2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Chicote de trepadeira",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dc466155300a2118f1cba"),
  "name": "Squirtle",
  "description": "Tartaruga ninja pokemon",
  "type": "água",
  "attack": 48,
  "defense": 40,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Hidro bomba",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dc4cd155300a2118f1cbb"),
  "name": "Charmander",
  "description": "Dragãozinho de laranjado",
  "type": "fogo",
  "attack": 58,
  "defense": 50,
  "height": 2.1,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Bafo bahiano",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
Fetched 4 record(s) in 1ms

```

## Pesquisar todos os pokemons que não são do tipo `elétrico`.

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {type: {$not: /electric/i}}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643cd355805a8c729a735e9"),
  "name": "Articuno",
  "description": "Pokémon lendário que controla o gelo",
  "type": "gelo",
  "attack": 92,
  "defense": 100,
  "height": 1.7,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643cdeb5805a8c729a735eb"),
  "name": "Rayquaza",
  "description": "Dragão da atmosfera que defende a terra",
  "type": "dragão",
  "attack": 158,
  "defense": 85,
  "height": 7,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("564d173367cb00e0960492b5"),
  "active": false,
  "name": "naoExiste",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "empty",
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643cc435805a8c729a735e6"),
  "name": "Blastoise",
  "description": "Canhão de água ambulante",
  "type": "água",
  "attack": 58,
  "defense": 60,
  "height": 1.6,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Canhão de água",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dc3f7155300a2118f1cb9"),
  "name": "Bulbassauro",
  "description": "Sapo do mato",
  "type": "grama",
  "attack": 48,
  "defense": 40,
  "height": 1.2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Chicote de trepadeira",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dc466155300a2118f1cba"),
  "name": "Squirtle",
  "description": "Tartaruga ninja pokemon",
  "type": "água",
  "attack": 48,
  "defense": 40,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Hidro bomba",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dc4cd155300a2118f1cbb"),
  "name": "Charmander",
  "description": "Dragãozinho de laranjado",
  "type": "fogo",
  "attack": 58,
  "defense": 50,
  "height": 2.1,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Bafo bahiano",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dcf42322743e7e55c1e80"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
{
  "_id": ObjectId("5643cbcc5805a8c729a735e5"),
  "name": "Charizard",
  "description": "Dragão de fogo valentão",
  "type": "fogo",
  "attack": 80,
  "defense": 60,
  "height": 1.7,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Lança chama",
    "desvio"
  ]
}
{
  "_id": ObjectId("5643cd975805a8c729a735ea"),
  "name": "Mewtwo",
  "description": "Pokémon mais poderoso, criado em laboratório",
  "type": "psiquico",
  "attack": 168,
  "defense": 85,
  "height": 2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
Fetched 10 record(s) in 2ms

```

## Pesquisar todos os pokemons que tenham o ataque `investida` E tenham a defesa não menor ou igual a 49.

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: /investida/i}, {defense: {$lte: 49}}]}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643ccee5805a8c729a735e8"),
  "name": "Seadra",
  "description": "Cavalo marinho cuspidor",
  "type": "água",
  "attack": 55,
  "defense": 45,
  "height": 1.2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56466a619f352f3891c8ccbc"),
  "name": "Treeglass",
  "description": "Ataca com folhas afiadas",
  "type": "grama",
  "attack": 35,
  "defense": 40,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccbf"),
  "name": "Fearow",
  "description": "Frando voador",
  "type": "air",
  "attack": 50,
  "defense": 30,
  "height": 1.2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccc1"),
  "name": "Raticate",
  "description": "Ratão do banhado",
  "type": "normal",
  "attack": 20,
  "defense": 25,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccc2"),
  "name": "Bridgebear",
  "description": "Urso de pedra",
  "type": "rock",
  "attack": 45,
  "defense": 40,
  "height": 1.3,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ]
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccc3"),
  "name": "Venomito",
  "description": "Bichinho muito feio",
  "type": "poison",
  "attack": 15,
  "defense": 10,
  "height": 0.5,
  "moves": [
    "Investida",
    "Ataque rápido",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564dc3f7155300a2118f1cb9"),
  "name": "Bulbassauro",
  "description": "Sapo do mato",
  "type": "grama",
  "attack": 48,
  "defense": 40,
  "height": 1.2,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Chicote de trepadeira",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dc466155300a2118f1cba"),
  "name": "Squirtle",
  "description": "Tartaruga ninja pokemon",
  "type": "água",
  "attack": 48,
  "defense": 40,
  "height": 0.5,
  "active": false,
  "moves": [
    "Investida",
    "Ataque rápido",
    "Hidro bomba",
    "Falsa ofensiva",
    "Revide",
    "desvio"
  ]
}
Fetched 8 record(s) in 2ms
```

## Remova todos os pokemons do tipo água e com attack menor que 50.

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type: /água/i}, {attack: {$lt: 50}}]}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})

```