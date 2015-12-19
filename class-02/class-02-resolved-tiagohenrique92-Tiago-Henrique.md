# MongoDB - Aula 02 - Exercício
autor: Tiago Henrique

## Listagem das databases (passo 2)

```
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram  0.078GB
be-mean            0.078GB
local              0.078GB

```

## Listagem das coleções (passo 3)

```
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> show collections
t2-lubuntu(mongod-3.0.7) be-mean-pokemons>

```

## Cadastro dos pokemons (passo 4)

```
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> var pokemon = {name:"Charmeleon", description:"Forma evoluida do Charmander", type:"fogo", attack:64, height:11, defense:58}
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 366ms
WriteResult({
  "nInserted": 1
})
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> var pokemon = {name:"Wartortle", description:"Forma evoluida do Squirtle", type:"água", attack:63, height:10, defense:80}
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> var pokemon = {name:"Ivysaur", description:"Forma evoluida do Bulbassauro", type:"grama", attack:62, height:10, defense:63}
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> var pokemon = {name:"Metapod", description:"Forma evoluida do Caterpie", type:"inseto", attack:20, height:7, defense:55}
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> var pokemon = {name:"Butterfree", description:"Forma evoluida do Metapod", type:"inseto", attack:45, height:11, defense:50}
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

```

## Lista dos pokemons (passo 5)

```
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564941aadc1292db41792267"),
  "name": "Charmeleon",
  "description": "Forma evoluida do Charmander",
  "type": "fogo",
  "attack": 64,
  "height": 11,
  "defense": 58
}
{
  "_id": ObjectId("56494248dc1292db41792268"),
  "name": "Wartortle",
  "description": "Forma evoluida do Squirtle",
  "type": "água",
  "attack": 63,
  "height": 10,
  "defense": 80
}
{
  "_id": ObjectId("564942b3dc1292db41792269"),
  "name": "Ivysaur",
  "description": "Forma evoluida do Bulbassauro",
  "type": "grama",
  "attack": 62,
  "height": 10,
  "defense": 63
}
{
  "_id": ObjectId("564942ebdc1292db4179226a"),
  "name": "Metapod",
  "description": "Forma evoluida do Caterpie",
  "type": "inseto",
  "attack": 20,
  "height": 7,
  "defense": 55
}
{
  "_id": ObjectId("56494332dc1292db4179226b"),
  "name": "Butterfree",
  "description": "Forma evoluida do Metapod",
  "type": "inseto",
  "attack": 45,
  "height": 11,
  "defense": 50
}
Fetched 5 record(s) in 5ms

```

## Pikachu (passo 6)

```
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> var query = {name: "Charmeleon"}
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564941aadc1292db41792267"),
  "name": "Charmeleon",
  "description": "Forma evoluida do Charmander",
  "type": "fogo",
  "attack": 64,
  "height": 11,
  "defense": 58
}

```

## Atualização do Pikachu (passo 6)

```
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> poke.description = "Forma evoluida do Charmander com mais poder de fogo"
Forma evoluida do Charmander com mais poder de fogo
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564941aadc1292db41792267"),
  "name": "Charmeleon",
  "description": "Forma evoluida do Charmander com mais poder de fogo",
  "type": "fogo",
  "attack": 64,
  "height": 11,
  "defense": 58
}
t2-lubuntu(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```