# MongoDB - Aula 02 - Exercício
autor: Deyves Carvalho

## Criação da database (passo 1)

    deyves-dev-NE56R(mongod-2.4.9) test> use be-mean-pokemons
    switched to db be-mean-pokemons


## Listagem das databases (passo 2)

    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> show dbs
    MEAN              → 0.203GB
    be-mean           → 0.203GB
    be-mean-instagram → 0.203GB
    deyves            → 0.203GB
    local             → 0.078GB
    test              → 0.203GB


## Listagem das coleções (passo 3)
    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> show collections

## Cadastro dos pokemons (passo 4)

    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var pokemons = [{name: 'Alakazam',description: 'Esse mago, é um mago mui loco', attack:30, defense: 20, height: 1.5}, {name: 'Psyduck',description: 'Pato, que manja das magias mais fodas.', attack:30, defense: 20, height: 0.8}, {name: 'Nidorino',description: 'Rinoceronte roxo pra craleo.', attack:40, defense: 30, height: 0.9}, {name: 'Rattata',description: 'Rato, que pode infectar facilmente seus oponentes.', attack:30, defense: 20, height: 0.3}, {name: 'Butterfree',description: 'Borboleta com super ataque, através dos seus olhos de BLACK KAMEN RIDER.', attack:20, defense: 20, height: 1.1}]
    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.save(pokemons)
    Inserted 1 record(s) in 12ms

## Lista dos pokemons (passo 5)

    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find()
    {
      "_id": ObjectId("56e2500c7a4c407e4ead4da9"),
      "name": "Alakazam",
      "description": "Esse mago, é um mago mui loco",
      "attack": 30,
      "defense": 20,
      "height": 1.5
    }
    {
      "_id": ObjectId("56e2500c7a4c407e4ead4daa"),
      "name": "Psyduck",
      "description": "Pato, que manja das magias mais fodas.",
      "attack": 30,
      "defense": 20,
      "height": 0.8
    }
    {
      "_id": ObjectId("56e2500c7a4c407e4ead4dab"),
      "name": "Nidorino",
      "description": "Rinoceronte roxo pra craleo.",
      "attack": 40,
      "defense": 30,
      "height": 0.9
    }
    {
      "_id": ObjectId("56e2500c7a4c407e4ead4dac"),
      "name": "Rattata",
      "description": "Rato, que pode infectar facilmente seus oponentes.",
      "attack": 30,
      "defense": 20,
      "height": 0.3
    }
    {
      "_id": ObjectId("56e2500c7a4c407e4ead4dad"),
      "name": "Butterfree",
      "description": "Borboleta com super ataque, através dos seus olhos de BLACK KAMEN RIDER.",
      "attack": 20,
      "defense": 20,
      "height": 1.1
    }
    Fetched 5 record(s) in 2ms

## Nidorino (passo 6)

    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> var poke = db.pokemons.findOne({name:'Nidorino'})
    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> poke
    {
      "_id": ObjectId("56e2500c7a4c407e4ead4dab"),
      "name": "Nidorino",
      "description": "Rinoceronte roxo pra craleo.",
      "attack": 40,
      "defense": 30,
      "height": 0.9
    }

## Atualização do Nidorino (passo 7)
    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> poke.description = 'Rinoceronte muito malandro'
    Rinoceronte muito malandro
    deyves-dev-NE56R(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(poke)
    {
      "_id": ObjectId("56e2500c7a4c407e4ead4dab"),
      "name": "Nidorino",
      "description": "Rinoceronte muito malandro",
      "attack": 40,
      "defense": 30,
      "height": 0.9
    }
    Fetched 1 record(s) in 2ms

