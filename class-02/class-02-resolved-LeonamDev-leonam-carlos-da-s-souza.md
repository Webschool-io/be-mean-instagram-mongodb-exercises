# MongoDB - Aula 02 - Exercício
autor: Leonam Souza

## Criar database (passo 1)

```
use be-mean-pokemons

```

## Listagem das databases (passo 2)

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> show dbs
local             → 0.078GB
be-mean-instagram → 0.078GB
mydb              → 0.078GB
be-mean           → 0.078GB
be-mean-pokemons  → 0.078GB


```


## Listagem das coleções (passo 3)

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> show collections
pokemons       → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB

```

## Cadastro dos pokemons (passo 4)

```
be-mean-pokemons> var pokemon = {'name':'Persian','description':'Gato crazy','type': 'electric', attack: 55, height: 0.4 }
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 422ms
WriteResult({
  "nInserted": 1
})

be-mean-pokemons> var pokemon = {'name':'Poliwag','description':'Lobo peludi','type': 'terrestre', attack: 75, height: 0.4 }
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

 be-mean-pokemons> var pokemon = {'name':'Rapidash','description':'Veado de fogo','type': 'fogo', attack:65, height: 0.4 }
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> var pokemon = {'name':'Onix','description':'bixinho lindo roxo','type': 'water', attack: 25, height: 0.4 }
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

be-mean-pokemons> var pokemon = {'name':'Drowzee','description':'Cobra de pedra','type': 'terrestre', attack:15, height: 0.4 }
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})



```

## Lista dos pokemons (passo 5)

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5650afc2b5cb4e56bf3b8d51"),
  "name": "Persian",
  "description": "Gato crazy",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5650b01fb5cb4e56bf3b8d52"),
  "name": "Poliwag",
  "description": "Lobo peludi",
  "type": "terrestre",
  "attack": 75,
  "height": 0.4
}
{
  "_id": ObjectId("5650b06eb5cb4e56bf3b8d53"),
  "name": "Rapidash",
  "description": "Veado de fogo",
  "type": "fogo",
  "attack": 65,
  "height": 0.4
}
{
  "_id": ObjectId("5650b0c5b5cb4e56bf3b8d54"),
  "name": "Onix",
  "description": "bixinho lindo roxo",
  "type": "water",
  "attack": 25,
  "height": 0.4
}
{
  "_id": ObjectId("5650b104b5cb4e56bf3b8d55"),
  "name": "Drowzee",
  "description": "Cobra de pedra",
  "type": "terrestre",
  "attack": 15,
  "height": 0.4
}
Fetched 5 record(s) in 2ms


```

## Persian (passo 6)

```
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> var query = {"name": "Persian"}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5650afc2b5cb4e56bf3b8d51"),
  "name": "Persian",
  "description": "Gato crazy",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}


```

## Atualização do Persian (passo 7)

```
eonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> var query = {"name": "Persian"}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5650afc2b5cb4e56bf3b8d51"),
  "name": "Persian",
  "description": "Gato crazy",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> poke.descripstion
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> poke.description
Gato crazy
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> poke.description = "Cool Cat"
Cool Cat
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 7ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Leonam-IPMH61R3(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("5650afc2b5cb4e56bf3b8d51"),
  "name": "Persian",
  "description": "Cool Cat",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}


```
