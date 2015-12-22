# MongoDB - Aula 04 - Exercício
autor: Rafael Taro Osako

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> query = {name: {$in:[/pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i]}}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> mod = {$pushAll: {moves:['soco na cara', 'chute no saco']}}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var options={multi:true}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 2 existing record(s) in 5ms
WriteResult({
  "nMatched": 2,
  "nUpserted": 0,
  "nModified": 2
})

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5675c77b0c3a1f4a9d9e3af6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "soco na cara",
    "chute no saco"
  ]
}
{
  "_id": ObjectId("5668ba12d9bf505f036304d3"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 120,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "soco na cara",
    "chute no saco",
    "soco na cara",
    "chute no saco"
  ],
  "active": false
}
Fetched 2 record(s) in 1ms



## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> query = {}
{
  
}
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var mod = {$push:{moves:'desvio'}}
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> options
{
  "multi": true
}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 8 existing record(s) in 1ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5668b7d5d9bf505f036304ce"),
  "name": "Blastoise",
  "description": "tartaruga tanque",
  "attack": 40,
  "defense": 40,
  "height": 1.6,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668b82dd9bf505f036304cf"),
  "name": "Butterfree",
  "description": "Borboletinha",
  "attack": 20,
  "defense": 20,
  "height": 1.1,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668b84cd9bf505f036304d0"),
  "name": "Pidgey",
  "description": "Pássaro com super senso de direção",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668b856d9bf505f036304d1"),
  "name": "Zubat",
  "description": "Morcego, se queima no sol",
  "attack": 20,
  "defense": 20,
  "height": 0.8,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668b85dd9bf505f036304d2"),
  "name": "Bellsprout",
  "description": "Plants vs zombies",
  "attack": 40,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566cb8cc44d628a7d9d561fc"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attach": 8001,
  "defense": 8000,
  "attack": 1,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5675c77b0c3a1f4a9d9e3af6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668ba12d9bf505f036304d3"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 120,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "active": false
}
Fetched 8 record(s) in 8ms


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var mod = { $set:{name:'AindaNaoExisteMon'}, $setOnInsert:{attack:null, height:null, defende:null, description:'Sem maiores informações'}}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var options = {upsert:true}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 7ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("5675f3af0c3a1f4a9d9e3af8")
})

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5675f3af0c3a1f4a9d9e3af8"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defende": null,
  "description": "Sem maiores informações"
}


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in:[/investida/i, /pulo do gato/i]}}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5668b7d5d9bf505f036304ce"),
  "name": "Blastoise",
  "description": "tartaruga tanque",
  "attack": 40,
  "defense": 40,
  "height": 1.6,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668b82dd9bf505f036304cf"),
  "name": "Butterfree",
  "description": "Borboletinha",
  "attack": 20,
  "defense": 20,
  "height": 1.1,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668b84cd9bf505f036304d0"),
  "name": "Pidgey",
  "description": "Pássaro com super senso de direção",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668b856d9bf505f036304d1"),
  "name": "Zubat",
  "description": "Morcego, se queima no sol",
  "attack": 20,
  "defense": 20,
  "height": 0.8,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668b85dd9bf505f036304d2"),
  "name": "Bellsprout",
  "description": "Plants vs zombies",
  "attack": 40,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566cb8cc44d628a7d9d561fc"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attach": 8001,
  "defense": 8000,
  "attack": 1,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5675c77b0c3a1f4a9d9e3af6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5668ba12d9bf505f036304d3"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 120,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5675f3af0c3a1f4a9d9e3af8"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defende": null,
  "description": "Sem maiores informações",
  "moves": [
    "pulo do gato",
    "mordida do cachorro louco"
  ]
}


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

ACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: [/pulo do gato/i, /mordida do cachorro louco/i]}}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5675f3af0c3a1f4a9d9e3af8"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defende": null,
  "description": "Sem maiores informações",
  "moves": [
    "pulo do gato",
    "mordida do cachorro louco"
  ]
}
Fetched 1 record(s) in 1ms


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var query = {type: {$not: /elétrico/i}}

MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var query = {type: {$not: /eletrico/i}}
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5668ba12d9bf505f036304d3"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 120,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "active": false,
  "type": "elétrico"
}
{
  "_id": ObjectId("5675f3af0c3a1f4a9d9e3af8"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defende": null,
  "description": "Sem maiores informações",
  "moves": [
    "pulo do gato",
    "mordida do cachorro louco"
  ],
  "type": "grama"
}
{
  "_id": ObjectId("5668b7d5d9bf505f036304ce"),
  "name": "Blastoise",
  "description": "tartaruga tanque",
  "attack": 40,
  "defense": 40,
  "height": 1.6,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "type": "grama"
}
{
  "_id": ObjectId("5668b82dd9bf505f036304cf"),
  "name": "Butterfree",
  "description": "Borboletinha",
  "attack": 20,
  "defense": 20,
  "height": 1.1,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "type": "grama"
}
{
  "_id": ObjectId("5668b84cd9bf505f036304d0"),
  "name": "Pidgey",
  "description": "Pássaro com super senso de direção",
  "attack": 20,
  "defense": 20,
  "height": 0.3,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "type": "grama"
}
{
  "_id": ObjectId("5668b856d9bf505f036304d1"),
  "name": "Zubat",
  "description": "Morcego, se queima no sol",
  "attack": 20,
  "defense": 20,
  "height": 0.8,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "type": "grama"
}
{
  "_id": ObjectId("5668b85dd9bf505f036304d2"),
  "name": "Bellsprout",
  "description": "Plants vs zombies",
  "attack": 40,
  "defense": 20,
  "height": 0.7,
  "type": "grama",
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("566cb8cc44d628a7d9d561fc"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attach": 8001,
  "defense": 8000,
  "attack": 1,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "type": "grama"
}
{
  "_id": ObjectId("5675c77b0c3a1f4a9d9e3af6"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "type": "grama"
}


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in:['investida']}}, {attack:{$not:{$lte:49}}}]}
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5668ba12d9bf505f036304d3"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "attack": 120,
  "defense": 20,
  "height": 0.4,
  "moves": [
    "soco na cara",
    "chute no saco",
    "investida",
    "desvio"
  ],
  "active": false,
  "type": "elétrico"
}
Fetched 1 record(s) in 1ms

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{type:/água/i}, {attack: {$lt:50}}]}
MACBOOK-PRO(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})

## Demonstre qual a diferença entre os operadores $ne e $not.

MacBook-Pro(mongod-3.0.7) be-mean> var query = {name: {$ne: 'pikachu' }}
MacBook-Pro(mongod-3.0.7) be-mean> var mod = {name:1, _id:0}
MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find(query, mod)
{
  "name": "Rattata"
}
{
  "name": "Caterpie"
}
{
  "name": "Metapod"
}
{
  "name": "Wartortle"
}
{
  "name": "Blastoise"
}
{
  "name": "Butterfree"
}
{
  "name": "Charmeleon"
}
{
  "name": "Spearow"
}
{
  "name": "Farfetchd"
}
{
  "name": "Kakuna"
}
{
  "name": "Charmander"
}
{
  "name": "Magneton"
}
{
  "name": "Doduo"
}
{
  "name": "Magnemite"
}
{
  "name": "Seel"
}
{
  "name": "Dewgong"
}
{
  "name": "Dodrio"
}
{
  "name": "Gastly"
}
{
  "name": "Poliwag"
}
{
  "name": "Poliwhirl"
}

# Possivel realizar operações lógicas como abaixo, que realiza a negação de valores abaixo de 200 para defesa.
MacBook-Pro(mongod-3.0.7) be-mean> var query = {defense: {$not: {$lt:200 }}}
MacBook-Pro(mongod-3.0.7) be-mean> var mod = {name:1, _id:0}
MacBook-Pro(mongod-3.0.7) be-mean> db.pokemons.find(query, mod)
{
  "name": "Shuckle"
}
{
  "name": "Regirock"
}
{
  "name": "Steelix"
}
Fetched 3 record(s) in 1ms






