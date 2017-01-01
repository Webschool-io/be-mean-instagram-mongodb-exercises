# MongoDB - Aula 04 - Exercício
autor: Henrique Nascimento

##Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikacu, Squirtle, Bulbassauro, Charmander

    be-mean-instagram> var query = {name: /pikachu/i}
    be-mean-instagram> var mod = {$pushAll:{moves:['esfera elétrica', 'investida do trovão']}}
    be-mean-instagram> db.pokemon.update(query, mod)

    be-mean-instagram> var query = {name:/squirtle/i}
    be-mean-instagram> var mod = {$pushAll:{moves:['raio de gelo', 'giro rápido']}}
    be-mean-instagram> db.pokemon.update(query, mod)

    be-mean-instagram> var query = {name: /bulbassauro/i}
    be-mean-instagram> var mod = {$pushAll:{moves:['raio solar', 'dança de pélotas']}}
    be-mean-instagram> db.pokemon.update(query, mod)

    be-mean-instagram> var query = {name: /charmander/i}
    be-mean-instagram> var mod = {$pushAll:{moves:['brasas', 'encarar']}}
    be-mean-instagram> db.pokemon.update(query, mod)

##Adiciona um movimento a todos os pokemons: 'desvio'

    be-mean-instagram> var query = {}
    be-mean-instagram> var mod = {$push:{moves: 'desvio'}}
    be-mean-instagram> var op = {multi: true}
    be-mean-instagram> db.pokemon.update(query, mod, op)

##Adicionar o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição 'Sem maiores informações'

    be-mean-instagram> var query = {name: /AindaNaoExisteMon/i}
    be-mean-instagram> var mod = {$setOnInsert:{name:'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
    be-mean-instagram> var op = {upsert: true}
    be-mean-instagram> db.pokemon.update(query, mod, op)

##Pesquisar todos os pokemons que tem o ataque 'investida' e mais um que vocẽ adicionou, escolha seu pokemon favorito

    be-mean-instagram> var query = {moves:{$in:['investida', 'encarar']}}
    be-mean-instagram> db.pokemon.find(query)

##Pesquisar todos os pokemons que tenha o ataque que você adicionou, escolha seu pokemon favorito

    be-mean-instagram> var query ={moves:{$all:['hidro-bomba', 'raio de gelo']}}
    be-mean-instagram> db.pokemon.find(query)
    {
        "_id": ObjectId("5861c6b2ad23d4a5b040e7ca"),
        "name": "Squirtle",
        "description": "Ejeta água, chicotes e cementes",
        "type": "água",
        "attack": 48,
        "height": 0.5,
        "active": true,
        "moves": [
            "investida",
            "hidro-bomba",
            "raio de gelo",
            "giro rápido",
            "desvio"
        ]
    }

##Pesquisar todos os pokemons que não são do tipo eletrico

    be-mean-instagram> var query = {type:{$not: /elétrico/i}}
    be-mean-instagram> db.pokemon.find(query)be-mean-instagram> db.pokemon.find(query)
    {
        "_id": ObjectId("5861c5e3ad23d4a5b040e7c8"),
        "name": "Bulbassauro",
        "description": "Chicote de trepadeira",
        "type": "grama",
        "attack": 49,
        "height": 0.4,
        "active": true,
        "moves": [
            "investida",
            "folha-navalha",
            "raio solar",
            "dança de pélotas",
            "desvio"
        ]
    }

    {
        "_id": ObjectId("5861c651ad23d4a5b040e7c9"),
        "name": "Charmander",
        "description": "Esse é o pokemon do fogo",
        "type": "fogo",
        "attack": 52,
        "height": 0.6,
        "active": true,
        "moves": [
            "investida",
            "lança-chamas",
            "brasas",
            "encarar",
            "desvio"
        ]
    }

    {
        "_id": ObjectId("5861c6b2ad23d4a5b040e7ca"),
        "name": "Squirtle",
        "description": "Ejeta água, chicotes e cementes",
        "type": "água",
        "attack": 48,
        "height": 0.5,
        "active": true,
        "moves": [
            "investida",
            "hidro-bomba",
            "raio de gelo",
            "giro rápido",
            "desvio"
        ]
    }

    {
        "_id": ObjectId("5869440d8f88ed025b65d22f"),
        "name": "AindaNaoExisteMon",
        "type": null,
        "attack": null,
        "defense": null,
        "height": null,
        "description": "Sem maiores informações"
    }
        Fetched 4 record(s) in 2ms

##Pesquisar todos os pokemons com ataque 'investida' e com attack não menor ou igual a 49

    var query = {$and:[{moves:{$in:['investida']}},{attack:{$not:{$lte: 49}}}]}
    be-mean-instagram> db.pokemon.find(query)
    {
        "_id": ObjectId("5861c37fad23d4a5b040e7c7"),
        "description": "Rato elétrico bem fofinho",
        "type": "elétrico",
        "attack": 55,
        "height": 0.4,
        "active": true,
        "name": "Pikachu",
        "moves": [
            "investida",
            "choque do trovão",
            "esfera elétrica",
            "investida do trovão",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("5861c651ad23d4a5b040e7c9"),
        "name": "Charmander",
        "description": "Esse é o pokemon do fogo",
        "type": "fogo",
        "attack": 52,
        "height": 0.6,
        "active": true,
        "moves": [
            "investida",
            "lança-chamas",
            "brasas",
            "encarar",
            "desvio"
        ]
    }
    Fetched 2 record(s) in 1ms

##Remover todos os pokemons do tipo água e com ataque menor que 50

    var query = {$and:[{type: /água/i},{attack:{$lt: 50}}]}
    be-mean-instagram> db.pokemon.remove(query)