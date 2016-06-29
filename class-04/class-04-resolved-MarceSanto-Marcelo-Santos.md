## Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = { $or : [{name: "Pikachu"}, {name: "Squirtle"}, {name : "Bulbassauro"}, {name : "Charmander"}]}
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var mod = {$pushAll: {moves: ['patada', 'esquiva']}}
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var options = { multi: true }
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.update(query, mod, options)
    Updated 4 existing record(s) in 86ms
    WriteResult({
        "nMatched": 4,
        "nUpserted": 0,
        "nModified": 4
    })


## Adicionar 1 movimento em todos os pokemons: desvio.
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {}
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var mod = {$push: {moves: 'desvio'}}
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> options
    {
        "multi": true
    }
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.update(query, mod, options)
    Updated 12 existing record(s) in 5ms
    WriteResult({
        "nMatched": 12,
        "nUpserted": 0,
        "nModified": 12
    })



## Adicionar o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações"

    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {name: /AindaNaoExisteMon/i}
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var options = {upsert: true}
    DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.update(query, mod, options)
    Updated 1 new record(s) in 3ms
    WriteResult({
        "nMatched": 0,
        "nUpserted": 1,
        "nModified": 0,
        "_id": ObjectId("5655048698c886b88654e8e9")
    })


## Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {moves: {$in: [/investida/i, /patada/i,]}}
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find(query)
        {
            "_id": ObjectId("5654fd5a522d248366d9bd65"),
            "name": "Bulbassauro",
            "description": "Chicote de trepadeira",
            "type": "grama",
            "attack": 49,
            "height": 0.4,
            "moves": [
                "patada",
                "esquiva",
                "desvio"
            ]
        }
        .... Fetched 12 record(s) in 172ms


## Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {moves:{$in: ['patada', 'esquiva']}}
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find(query)
        {
            "_id": ObjectId("5654fd40522d248366d9bd63"),
            "name": "Charmander",
            "description": "Esse é o cão chupando manga de fofinho",
            "type": "fogo",
            "attack": 52,
            "height": 0.6,
            "moves": [
                "patada",
                "esquiva",
                "desvio"
            ]
        }
        ...  Fetched 4 record(s) in 48ms
        
## Pesquisar todos os pokemons que não são do tipo elétrico
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {type: {$ne:'eletric'}}
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find(query)
        {
            "_id": ObjectId("5650b470cd80338cbd0902b9"),
            "name": "Geodude",
            "description": "Possui um soco forte",
            "type": "rocha",
            "attack": 80,
            "height": 0.4,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b480cd80338cbd0902ba"),
            "name": "Cubone",
            "description": "Ataque de Osso",
            "type": "Terra",
            "attack": 50,
            "height": 0.4,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b48ecd80338cbd0902bb"),
            "name": "Beedrill",
            "description": "Abelha extremamente nervosa",
            "type": "inseto",
            "attack": 90,
            "height": 1,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b49ccd80338cbd0902bc"),
            "name": "Pidgeotto",
            "description": "Rajada de Vento",
            "type": "Passaro",
            "attack": 60,
            "height": 1.1,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b4a7cd80338cbd0902bd"),
            "name": "Raichu",
            "description": "Evolução do pikachu",
            "type": "eletrico",
            "attack": 90,
            "height": 0.8,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b4b4cd80338cbd0902be"),
            "name": "Jigglypuff",
            "description": "Toca um cançao de dormi",
            "type": "fada",
            "attack": 45,
            "height": 0.5,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b4c9cd80338cbd0902bf"),
            "name": "Psyduck",
            "description": "Mais atrapalhado que o mister bean",
            "type": "agua",
            "attack": 52,
            "height": 0.8,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b4d9cd80338cbd0902c0"),
            "name": "Alakazam",
            "description": "Rei da hypnose",
            "type": "pisiquico",
            "attack": 50,
            "height": 1.5,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5654fd40522d248366d9bd63"),
            "name": "Charmander",
            "description": "Esse é o cão chupando manga de fofinho",
            "type": "fogo",
            "attack": 52,
            "height": 0.6,
            "moves": [
                "patada",
                "esquiva",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5654fd40522d248366d9bd64"),
            "name": "Squirtle",
            "description": "Ejeta água que passarinho não bebe",
            "type": "água",
            "attack": 48,
            "height": 0.5,
            "moves": [
                "patada",
                "esquiva",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5654fd5a522d248366d9bd65"),
            "name": "Bulbassauro",
            "description": "Chicote de trepadeira",
            "type": "grama",
            "attack": 49,
            "height": 0.4,
            "moves": [
                "patada",
                "esquiva",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650bd07ce06abea91711fe2"),
            "name": "Pikachu",
            "description": "Rato eletrico bem fofinho",
            "type": "electric",
            "attack": 100,
            "height": 0.4,
            "moves": [
                "investida",
                "choque do trovão",
                "patada",
                "esquiva",
                "desvio"
            ],
            "active": false
        }
        {
            "_id": ObjectId("5655048698c886b88654e8e9"),
            "name": "AindaNaoExisteMon",
            "type": null,
            "attack": null,
            "defense": null,
            "height": null,
            "description": "Sem maiores informações"
        }
        Fetched 13 record(s) in 187ms
        

## Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49
        
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {$and: [ {moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}} ]}
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.find(query)
        {
            "_id": ObjectId("5650b470cd80338cbd0902b9"),
            "name": "Geodude",
            "description": "Possui um soco forte",
            "type": "rocha",
            "attack": 80,
            "height": 0.4,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b480cd80338cbd0902ba"),
            "name": "Cubone",
            "description": "Ataque de Osso",
            "type": "Terra",
            "attack": 50,
            "height": 0.4,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b48ecd80338cbd0902bb"),
            "name": "Beedrill",
            "description": "Abelha extremamente nervosa",
            "type": "inseto",
            "attack": 90,
            "height": 1,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b49ccd80338cbd0902bc"),
            "name": "Pidgeotto",
            "description": "Rajada de Vento",
            "type": "Passaro",
            "attack": 60,
            "height": 1.1,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b4a7cd80338cbd0902bd"),
            "name": "Raichu",
            "description": "Evolução do pikachu",
            "type": "eletrico",
            "attack": 90,
            "height": 0.8,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b4c9cd80338cbd0902bf"),
            "name": "Psyduck",
            "description": "Mais atrapalhado que o mister bean",
            "type": "agua",
            "attack": 52,
            "height": 0.8,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650b4d9cd80338cbd0902c0"),
            "name": "Alakazam",
            "description": "Rei da hypnose",
            "type": "pisiquico",
            "attack": 50,
            "height": 1.5,
            "active": false,
            "moves": [
                "investida",
                "desvio"
            ]
        }
        {
            "_id": ObjectId("5650bd07ce06abea91711fe2"),
            "name": "Pikachu",
            "description": "Rato eletrico bem fofinho",
            "type": "electric",
            "attack": 100,
            "height": 0.4,
            "moves": [
                "investida",
                "choque do trovão",
                "patada",
                "esquiva",
                "desvio"
            ],
            "active": false
        }
        Fetched 8 record(s) in 111ms

## Remova todos os pokemons do tipo água E com attack menor que 50
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> var query = {$and: [ {type: /agua/i}, {attack: {$lt: 50}} ]}
        DESKTOP-SMEL8DV(C:\mongodb\bin\mongod.exe-3.0.7) be-mean> db.pokemons.remove(query)
        Removed 0 record(s) in 1ms
        WriteResult({
            "nRemoved": 0
        })
