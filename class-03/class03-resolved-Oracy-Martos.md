# MongoDB - Aula 03 - Exercício
Autor: Oracy Martos

Be-mean

# Mostrando a base atual

```
> db.pokemons.find().pretty()
{
    "_id" : ObjectId("58ba21795b5ff56963b2f5d8"),
    "name" : "Pikachu",
    "description" : "Rato elétrico foda",
    "type" : "eletric",
    "attack" : 55,
    "height" : 0.4
}
{
    "_id" : ObjectId("58ba221d5b5ff56963b2f5d9"),
    "name" : "Squirtle",
    "description" : "Tartaruga da água foda",
    "type" : "water",
    "attack" : 45,
    "height" : 0.4
}
{
    "_id" : ObjectId("58ba22395b5ff56963b2f5da"),
    "name" : "Charmander",
    "description" : "Réptil de fogo foda",
    "type" : "fire",
    "attack" : 65,
    "height" : 0.4
}
{
    "_id" : ObjectId("58ba22745b5ff56963b2f5db"),
    "name" : "Bulbassauro",
    "description" : "Chicoteiro foda",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4
}
{
    "_id" : ObjectId("58ba231b5b5ff56963b2f5dc"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35,
    "active" : true
}
{
    "_id" : ObjectId("58bcb673b09060a8eba34f6d"),
    "active" : true,
    "name" : "NaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "Sem maiores informações"
}
```

# 1- Adicionar 2 ataques ao mesmo tempo para 3 pokemons.
```
> var query ={name: {$in: [ /pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i]}}
> query
{
    "name" : {
        "$in" : [
            /pikachu/i,
            /squirtle/i,
            /bulbassauro/i,
            /charmander/i
        ]
    }
}

> var mod = {$pushAll: {moves: ["Investida", "Rabada"] }}
> mod
{ "$pushAll" : { "moves" : [ "Investida", "Rabada" ] } }

> var options = {multi: true}
> options
{ "multi" : true }

> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("58ba21795b5ff56963b2f5d8"),
    "name" : "Pikachu",
    "description" : "Rato elétrico foda",
    "type" : "eletric",
    "attack" : 55,
    "height" : 0.4,
    "moves" : [
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba221d5b5ff56963b2f5d9"),
    "name" : "Squirtle",
    "description" : "Tartaruga da água foda",
    "type" : "water",
    "attack" : 45,
    "height" : 0.4,
    "moves" : [
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba22395b5ff56963b2f5da"),
    "name" : "Charmander",
    "description" : "Réptil de fogo foda",
    "type" : "fire",
    "attack" : 65,
    "height" : 0.4,
    "moves" : [
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba22745b5ff56963b2f5db"),
    "name" : "Bulbassauro",
    "description" : "Chicoteiro foda",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "moves" : [
        "Investida",
        "Rabada"
    ]
}
```

# 2- Adicionar 1 movimento em todos os pokemons.
```
> var query = {}
> query
{ }
> var mod = {$push: {moves: ['desvio']}}
> var options = {multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 6, "nUpserted" : 0, "nModified" : 6 })
> db.pokemons.find().pretty()
{
    "_id" : ObjectId("58ba21795b5ff56963b2f5d8"),
    "name" : "Pikachu",
    "description" : "Rato elétrico foda",
    "type" : "eletric",
    "attack" : 55,
    "height" : 0.4,
    "moves" : [
        "desvio"
    ]
}
{
    "_id" : ObjectId("58ba221d5b5ff56963b2f5d9"),
    "name" : "Squirtle",
    "description" : "Tartaruga da água foda",
    "type" : "water",
    "attack" : 45,
    "height" : 0.4,
    "moves" : [
        "desvio"
    ]
}
{
    "_id" : ObjectId("58ba22395b5ff56963b2f5da"),
    "name" : "Charmander",
    "description" : "Réptil de fogo foda",
    "type" : "fire",
    "attack" : 65,
    "height" : 0.4,
    "moves" : [
        "desvio"
    ]
}
{
    "_id" : ObjectId("58ba22745b5ff56963b2f5db"),
    "name" : "Bulbassauro",
    "description" : "Chicoteiro foda",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "moves" : [
        "desvio"
    ]
}
{
    "_id" : ObjectId("58ba231b5b5ff56963b2f5dc"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35,
    "active" : true,
    "moves" : [
        "desvio"
    ]
}
{
    "_id" : ObjectId("58bcb673b09060a8eba34f6d"),
    "active" : true,
    "name" : "NaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "Sem maiores informações",
    "moves" : [
        "desvio"
    ]
}
```
# 3- Adicionar o Pokemon AindaNaoExisteMon
```
> var query = {name: /AindaNaoExisteMon/i}
> query
{ "name" : /AindaNaoExisteMon/i }

> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', attack: null, defense: null, height: null, description: "Sem maiores informações"}}
> var options = {upsert: true}

> db.pokemons.update(query, mod, options)
WriteResult({
    "nMatched" : 0,
    "nUpserted" : 1,
    "nModified" : 0,
    "_id" : ObjectId("58bd5c76a3d7190b084da999")
})

> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("58bd5c76a3d7190b084da999"),
    "name" : "AindaNaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "Sem maiores informações"
}
```
# 4- Pesquisar todos Pokemons com ataque Investida e +1 de escolha.
```
> var query = {$or: [{moves: /investida/i},{name: /caterpie/i}]}
> query
{
    "$or" : [
        {
            "moves" : /investida/i
        },
        {
            "name" : /caterpie/i
        }
    ]
}
> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("58ba21795b5ff56963b2f5d8"),
    "name" : "Pikachu",
    "description" : "Rato elétrico foda",
    "type" : "eletric",
    "attack" : 55,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada",
    ]
}
{
    "_id" : ObjectId("58ba221d5b5ff56963b2f5d9"),
    "name" : "Squirtle",
    "description" : "Tartaruga da água foda",
    "type" : "water",
    "attack" : 45,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba22395b5ff56963b2f5da"),
    "name" : "Charmander",
    "description" : "Réptil de fogo foda",
    "type" : "fire",
    "attack" : 65,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba22745b5ff56963b2f5db"),
    "name" : "Bulbassauro",
    "description" : "Chicoteiro foda",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba231b5b5ff56963b2f5dc"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35,
    "active" : true,
    "moves" : [
        "desvio"
    ]
}
```

# 5- Pesquisar todos os pokemons que possuam ataques que voce adicionou, escolha o seu favorito
```
> var query = {moves:{$in: [/investida/i, /rabada/i]}}
> query
{ "moves" : { "$in" : [ /investida/i, /rabada/i ] } }
> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("58ba21795b5ff56963b2f5d8"),
    "name" : "Pikachu",
    "description" : "Rato elétrico foda",
    "type" : "eletric",
    "attack" : 55,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada",
    ]
}
{
    "_id" : ObjectId("58ba221d5b5ff56963b2f5d9"),
    "name" : "Squirtle",
    "description" : "Tartaruga da água foda",
    "type" : "water",
    "attack" : 45,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba22395b5ff56963b2f5da"),
    "name" : "Charmander",
    "description" : "Réptil de fogo foda",
    "type" : "fire",
    "attack" : 65,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba22745b5ff56963b2f5db"),
    "name" : "Bulbassauro",
    "description" : "Chicoteiro foda",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
```
# 6- Pesquisar Pokemons Elétricos
```
> var query = {type: {$nin:[/eletric/i]}}
> query
{ "type" : { "$nin" : [ /eletric/i ] } }
> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("58ba221d5b5ff56963b2f5d9"),
    "name" : "Squirtle",
    "description" : "Tartaruga da água foda",
    "type" : "water",
    "attack" : 45,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba22395b5ff56963b2f5da"),
    "name" : "Charmander",
    "description" : "Réptil de fogo foda",
    "type" : "fire",
    "attack" : 65,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba22745b5ff56963b2f5db"),
    "name" : "Bulbassauro",
    "description" : "Chicoteiro foda",
    "type" : "grama",
    "attack" : 49,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ]
}
{
    "_id" : ObjectId("58ba231b5b5ff56963b2f5dc"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30,
    "height" : 0.3,
    "defense" : 35,
    "active" : true,
    "moves" : [
        "desvio"
    ]
}
{
    "_id" : ObjectId("58bcb673b09060a8eba34f6d"),
    "active" : true,
    "name" : "NaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "Sem maiores informações",
    "moves" : [
        "desvio"
    ]
}
{
    "_id" : ObjectId("58bd5c76a3d7190b084da999"),
    "name" : "AindaNaoExisteMon",
    "attack" : null,
    "defense" : null,
    "height" : null,
    "description" : "Sem maiores informações"
}
```
# 7- Pesquisar todos os Pokemons que tenha ataque Investida e tenha defesa não menor ou igual a 49
```
> var query = {$and: [{moves: /investida/i}, {$and: [{defense: {$ne: 49}},{defense: {$gt: 49}}]}]}
> query
{
    "$and" : [
        {
            "moves" : /investida/i
        },
        {
            "$and" : [
                {
                    "defense" : {
                        "$ne" : 49
                    }
                },
                {
                    "defense" : {
                        "$gt" : 49
                    }
                }
            ]
        }
    ]
}

> db.pokemons.find(query).pretty()
{
    "_id" : ObjectId("58ba221d5b5ff56963b2f5d9"),
    "name" : "Squirtle",
    "description" : "Tartaruga da água foda",
    "type" : "water",
    "attack" : 45,
    "height" : 0.4,
    "moves" : [
        "desvio",
        "Investida",
        "Rabada"
    ],
    "defense" : 50
}
```

# 8- Remover todos os pokemons do tipo água com ataque menor que 50
```
> var query = {$and: [{type: /water/i}, {attack: {$lt: 50}}]}
> query
{
    "$and" : [
        {
            "type" : /water/i
        },
        {
            "attack" : {
                "$lt" : 50
            }
        }
    ]
}
> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })
```