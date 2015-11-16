# MongoDB - Aula 02 - Exercício

    autor: Ezequiel França

## Listagem das databases (passo 2)

    MSMAC1(mongod-3.0.7) be-mean-pokemon> show dbs
    be-mean-instagram  0.078GB
    local              0.078GB
    test               0.078GB
    MSMAC1(mongod-3.0.7) be-mean-pokemon>


## Listagem das coleções (passo 3)

    MSMAC1(mongod-3.0.7) be-mean-pokemon> show collections
    MSMAC1(mongod-3.0.7) be-mean-pokemon>


## Cadastro dos pokemons (passo 4)

    MSMAC1(mongod-3.0.7) be-mean-pokemon> db.teste.insert(pok1, pok2, pok3, pok4, pok5)
    Inserted 1 record(s) in 1210ms
    WriteResult({
      "nInserted": 1
    })
    MSMAC1(mongod-3.0.7) be-mean-pokemon>


## Lista dos pokemons (passo 5)

    MSMAC1(mongod-3.0.7) be-mean-pokemon> db.teste.find()
    {
      "_id": ObjectId("564a04a72055b4a721dee500"),
      "name": "Bulbasaur",
      "description": "Tartaruga Planta",
      "attack": 49,
      "defense": 49,
      "height": 0.2
    }
    {
      "_id": ObjectId("564a053f2055b4a721dee501"),
      "name": "Ivysaur",
      "description": "Cavalo de fogo",
      "attack": 62,
      "defense": 63,
      "height": 0.3
    }
    {
      "_id": ObjectId("564a05472055b4a721dee502"),
      "name": "Venusaur",
      "description": "Bulbasaur zoado",
      "attack": 82,
      "defense": 83,
      "height": 0.3
    }
    {
      "_id": ObjectId("564a054a2055b4a721dee503"),
      "name": "Charmander",
      "description": "largato de fogo",
      "attack": 52,
      "defense": 43,
      "height": 0.6
    }
    {
      "_id": ObjectId("564a054d2055b4a721dee504"),
      "name": "Charmeleon",
      "description": "Evolucao do Charmander",
      "attack": 64,
      "defense": 58,
      "height": 1
    }
    Fetched 5 record(s) in 51ms
    MSMAC1(mongod-3.0.7) be-mean-pokemon>
    
    
    ## Pikachu (passo 6)
    
    MSMAC1(mongod-3.0.7) be-mean-pokemon> var query = {"name": "Bulbasaur"}
    MSMAC1(mongod-3.0.7) be-mean-pokemon> db.teste.findOne(query)
    {
      "_id": ObjectId("564a04a72055b4a721dee500"),
      "name": "Bulbasaur",
      "description": "Tartaruga Planta",
      "attack": 49,
      "defense": 49,
      "height": 0.2
    }
    MSMAC1(mongod-3.0.7) be-mean-pokemon> var p = db.teste.findOne(query)


## Atualização do Pikachu (passo 6)

    MSMAC1(mongod-3.0.7) be-mean-pokemon> var p = db.teste.findOne(query)
    MSMAC1(mongod-3.0.7) be-mean-pokemon> p.defense = 3000
    3000
    MSMAC1(mongod-3.0.7) be-mean-pokemon> p
    {
      "_id": ObjectId("564a04a72055b4a721dee500"),
      "name": "Bulbasaur",
      "description": "Tartaruga Planta",
      "attack": 49,
      "defense": 3000,
      "height": 0.2
    }
    MSMAC1(mongod-3.0.7) be-mean-pokemon> db.teste.save(p)
    Updated 1 existing record(s) in 3ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    MSMAC1(mongod-3.0.7) be-mean-pokemon> db.teste.findOne(query)
    {
      "_id": ObjectId("564a04a72055b4a721dee500"),
      "name": "Bulbasaur",
      "description": "Tartaruga Planta",
      "attack": 49,
      "defense": 3000,
      "height": 0.2
    }
    MSMAC1(mongod-3.0.7) be-mean-pokemon>
