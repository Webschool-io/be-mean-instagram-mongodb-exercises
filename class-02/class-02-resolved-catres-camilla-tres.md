# MongoDB - Aula 02 - Exercício
autor: Camilla Tres

## Criação da database (passo 1)

    camilla@camilla-Mean:~$ mongo be-mean-pokemons
    MongoDB shell version: 3.0.7
    connecting to: be-mean-pokemons

## Listagem das databases (passo 2)

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> show dbs
    be-mean-instagram → 0.078GB
    local             → 0.078GB

## Listagem das coleções (passo 3)
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> show collections
    camilla-Mean(mongod-3.0.7) be-mean-pokemons>

## Cadastro dos pokemons (passo 4)

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> var pokemons = [{'name':'Dragonair','description':'Diz que é um dragão mas parece o Seiya de Pegaso','type':'dragon','attack':40,'defense':30,'height':4.0},
    ... {'name':'Mr.Mime','description':'Palhaço estranho','type':'psychic','attack':20,'defense':30,'height':1.3},
    ... {'name':'Larvitar','description':'faz cara de mal mas é fofinho','type':'rock','attack':30,'defense':20,'height':0.6},
    ... {'name':'Shelgon','description':'Tatu concha', 'type':'dragon', 'attack':50,'defense':40,'height':1.1},
    ... {'name':'Gloom','description':'planta babona','type':'grass','attack':30,'defense':30,'height':0.8},
    ... {'name':'Glameow','description':'Um Meowth, com muito mais glamour','type':'normal','attack':30,'defense':20,'height':0.5}];
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
    Inserted 1 record(s) in 117ms
    BulkWriteResult({
      "writeErrors": [ ],
      "writeConcernErrors": [ ],
      "nInserted": 6,
      "nUpserted": 0,
      "nMatched": 0,
      "nModified": 0,
      "nRemoved": 0,
      "upserted": [ ]
    })

## Lista dos pokemons (passo 5)

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
    {
      "_id": ObjectId("564bedbb4464d07588af9ef1"),
      "name": "Dragonair",
      "description": "Diz que é um dragão mas parece o Seiya de Pegaso",
      "type": "dragon",
      "attack": 40,
      "defense": 30,
      "height": 4
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef2"),
      "name": "Mr.Mime",
      "description": "Palhaço estranho",
      "type": "psychic",
      "attack": 20,
      "defense": 30,
      "height": 1.3
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef3"),
      "name": "Larvitar",
      "description": "faz cara de mal mas é fofinho",
      "type": "rock",
      "attack": 30,
      "defense": 20,
      "height": 0.6
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef4"),
      "name": "Shelgon",
      "description": "Tatu concha",
      "type": "dragon",
      "attack": 50,
      "defense": 40,
      "height": 1.1
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef5"),
      "name": "Gloom",
      "description": "planta babona",
      "type": "grass",
      "attack": 30,
      "defense": 30,
      "height": 0.8
    }
    {
      "_id": ObjectId("564bedbb4464d07588af9ef6"),
      "name": "Glameow",
      "description": "Um Meowth, com muito mais glamour",
      "type": "normal",
      "attack": 30,
      "defense": 20,
      "height": 0.5
    }
    Fetched 6 record(s) in 6ms

## Larvitar (passo 6)

    camilla-Mean(mongod-3.0.7) be-mean-pokemons> var query = {'name':'Larvitar'}
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> poke
    {
      "_id": ObjectId("564bedbb4464d07588af9ef3"),
      "name": "Larvitar",
      "description": "faz cara de mal mas é fofinho",
      "type": "rock",
      "attack": 30,
      "defense": 20,
      "height": 0.6
    }

## Atualização do Larvitar (passo 7)
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> poke.description = 'tem um chifre que justifica a cara de mal'
    tem um chifre que justifica a cara de mal
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
    Updated 1 existing record(s) in 1ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    camilla-Mean(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("564bedbb4464d07588af9ef3"),
      "name": "Larvitar",
      "description": "tem um chifre que justifica a cara de mal",
      "type": "rock",
      "attack": 30,
      "defense": 20,
      "height": 0.6
    }
    Fetched 1 record(s) in 3ms
