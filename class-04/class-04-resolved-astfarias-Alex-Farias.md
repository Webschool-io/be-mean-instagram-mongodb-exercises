# MongoDB - Aula 04 - Exercício
autor: Alex Farias

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
    //Configurando query de busca com os parâmetros de nome solicitados
    be-mean-pokemons> var query = {$or:[{name: 'Pikachu'}, {name: 'Squirtle'}, {name: 'Bulbasaur'}, {name: 'Charmander'}]}

    be-mean-pokemons> query
    {
        "$or": [
            {
              "name": "Pikachu"
            },
            {
              "name": "Squirtle"
            },
            {
              "name": "Bulbassauro"
            },
            {
              "name": "Charmander"
            }
        ]
    }

    //Configurando o modificador com os ataques solicitados
    be-mean-pokemons> var mod = {$pushAll:{move: ['Contra-Ataque', 'Rebatida']}}
    be-mean-pokemons> mod
    {
      "$pushAll": {
        "move": [
          "Contra-Ataque",
          "Rebatida"
        ]
      }
    }

    //Habilitando a multi alteração
    be-mean-pokemons> var option = {multi:true}

    //Executando a query para alteração
    be-mean-pokemons> db.pokemons.update(query, mod, option)
    Updated 4 existing record(s) in 1ms
    WriteResult({
      "nMatched": 4,
      "nUpserted": 0,
      "nModified": 4
    })

    //Listagem dos pokemons alterados
    be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("56671abd461abd4f9ba89b1d"),
      "name": "Charmander",
      "description": "Esse é o cão chupando manga de fofinho",
      "type": "fogo",
      "attack": 52,
      "height": 0.6,
      "move": [
        "investida",
        "Contra-Ataque",
        "Rebatida"
      ],
      "active": false
    }
    {
      "_id": ObjectId("56439d6abdda6aabca5a7fd1"),
      "name": "Squirtle",
      "description": "Shell is not merely for protection",
      "attack": 48,
      "defense": 65,
      "height": 0.5,
      "type": "Water",
      "active": false,
      "move": [
        "investida",
        "hidro bomba",
        "Contra-Ataque",
        "Rebatida",
        "Contra-Ataque",
        "Rebatida"
      ]
    }
    {
      "_id": ObjectId("56463238a560e80191083d44"),
      "name": "Bulbasaur",
      "description": "Bicho verde que solta folha q corta",
      "attack": 49,
      "defense": 49,
      "height": 2.4,
      "type": "Grass",
      "active": false,
      "move": [
        "investida",
        "folha navalha",
        "Contra-Ataque",
        "Rebatida"
      ]
    }
    {
      "_id": ObjectId("564637533cb365fe72ce44cb"),
      "name": "Pikachu",
      "description": "Rato amarelo q solta raio",
      "attack": 55,
      "defense": 40,
      "height": 1.4,
      "type": "Electric",
      "active": false,
      "move": [
        "investida",
        "choque eletrico",
        "Contra-Ataque",
        "Rebatida"
      ]
    }
    Fetched 4 record(s) in 1ms
```



## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
    //Selecionando todos
    be-mean-pokemons> var query = {}

    //Alterando modificador para inserir o movimento
    be-mean-pokemons> var mod = {$push: {move: 'desvio'}}
    be-mean-pokemons> mod
    {
      "$push": {
        "move": "desvio"
      }
    }

    //Atualizando os pokemons
    db.pokemons.update(query, mod, option)
    Updated 14 existing record(s) in 3ms
    WriteResult({
      "nMatched": 14,
      "nUpserted": 0,
      "nModified": 14
    })
```



## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
    //Configurando a query de busca
    be-mean-pokemons> var query = {name:/AindaNaoExisteMon/i}

    //Configurando o modificador com os parâmetros neutros
    be-mean-pokemons> var mod = {$set:{name:'AindaNaoExisteMon', description:'Sem maiores informações', attack:null, defense: null, height: null,type: null, active: false, move:[]}}

    be-mean-pokemons>  mod
    {
      "$set": {
        "name": "AindaNaoExisteMon",
        "description": "Sem maiores informações",
        "attack": null,
        "defense": null,
        "height": null,
        "type": null,
        "active": false,
        "move": [ ]
      }
    }

    //Habilitando o upsert para insersão caso não encontre
    be-mean-pokemons> var option: {upsert: true}

    //Executando alteração
    be-mean-pokemons> db.pokemons.update(query, mod, option)
    Updated 1 new record(s) in 2ms
    WriteResult({
      "nMatched": 0,
      "nUpserted": 1,
      "nModified": 0,
      "_id": ObjectId("566727eedc8a239108883672")
    })

    //Listando o novo pokemon
    be-mean-pokemons> db.pokemons.find({"_id": ObjectId("566727eedc8a239108883672")})
    {
      "_id": ObjectId("566727eedc8a239108883672"),
      "name": "AindaNaoExisteMon",
      "description": "Sem maiores informações",
      "attack": null,
      "defense": null,
      "height": null,
      "type": null,
      "active": false,
      "move": [ ]
    }
    Fetched 1 record(s) in 0ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
    //Configurando query de busca
    be-mean-pokemons> var query = {move: {$in: ['investida','choque eletrico']}}
    //Buscando
    db.pokemons.find(query)
    //A listagem foi removida por conter 14 elementos
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
    //Configurando query de busca
    be-mean-pokemons> var query = {move: {$in: [/hidro bomba/i, /choque do trovão/i]}}

    //Listagem
    be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("564a241881a23df330cbccde"),
      "name": "Testemon",
      "attack": 8000,
      "defense": 8000,
      "height": 2.1,
      "description": "Pokemon de teste",
      "move": [
        "investida",
        "Choque elétrico",
        "Choque do Trovão",
        "investida",
        "desvio"
      ],
      "active": false
    }
    {
      "_id": ObjectId("56439d6abdda6aabca5a7fd1"),
      "name": "Squirtle",
      "description": "Shell is not merely for protection",
      "attack": 48,
      "defense": 65,
      "height": 0.5,
      "type": "Water",
      "active": false,
      "move": [
        "investida",
        "hidro bomba",
        "Contra-Ataque",
        "Rebatida",
        "Contra-Ataque",
        "Rebatida",
        "desvio"
      ]
    }
    Fetched 2 record(s) in 1ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
    //Configurando a query de busca
    be-mean-pokemons> var query = {type: {$ne:'Electric'}}

    be-mean-pokemons> query
    {
      "type": {
        "$ne": "Electric"
      }
    }
    //Listagem
     be-mean-pokemons> db.pokemons.find(query)
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
    //Configurando query de busca para movimento
    var queryMove = {move: {$in: ['investida']}}
    be-mean-pokemons> queryMove
    {
      "move": {
        "$in": "investida"
      }
    }

    //Configurando query de busca para defesa
    var queryDef = {defense: {$not: {$lte: 49}}}
    be-mean-pokemons> queryDef
    {
      "defense": {
        "$not": {
          "$lte": 49
        }
      }
    }

    //Setando query de busca final
    be-mean-pokemons> var query = {$and: [queryMove, queryDef]}

    be-mean-pokemons> query
    {
      "$and": [
        {
          "move": {
            "$in": [
                "investida"
            ]
          }
        },
        {
          "defense": {
            "$not": {
              "$lte": 49
            }
          }
        }
      ]
    }
    //Listagem
    be-mean-pokemons> db.pokemons.find(query)

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
    
```
    //Configurando query de busca de type
    be-mean-pokemons> var queryType = {type:/water/i}
    //Configurando query de busca de Attack
    be-mean-pokemons> var queryAttack = {attack: {$lte: 50}}
    //Configurando query final
    be-mean-pokemons> var query = {$and: [queryType, queryAttack]}
    be-mean-pokemons> query
    {
      "$and": [
        {
          "type": /water/i
        },
        {
          "attack": {
            "$lte": 50
          }
        }
      ]
    }
    //Listando
    be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("5643a00ebdda6aabca5a7fd3"),
      "name": "Blastoise",
      "description": "Monxtrão que tem canhão de água",
      "attack": 40,
      "defense": 40,
      "height": 1.6,
      "type": "Water",
      "active": false,
      "move": [
        "investida",
        "desvio"
      ]
    }
    {
      "_id": ObjectId("56439d6abdda6aabca5a7fd1"),
      "name": "Squirtle",
      "description": "Shell is not merely for protection",
      "attack": 48,
      "defense": 65,
      "height": 0.5,
      "type": "Water",
      "active": false,
      "move": [
        "investida",
        "hidro bomba",
        "Contra-Ataque",
        "Rebatida",
        "Contra-Ataque",
        "Rebatida",
        "desvio"
      ]
    }
    Fetched 2 record(s) in 1ms

    //Removendo
    be-mean-pokemons> db.pokemons.remove(query)
    Removed 2 record(s) in 6ms
    WriteResult({
      "nRemoved": 2
    })
    //istando
    be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 0ms
```