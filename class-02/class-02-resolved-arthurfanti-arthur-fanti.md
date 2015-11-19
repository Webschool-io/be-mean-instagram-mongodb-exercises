# MongoDB - Aula 02 - Exercício
autor: ARTHUR FANTI

## Listagem das databases (passo 2)
```zsh
> use be-mean-pokemons
switched to db be-mean-pokemons

> show dbs
admin              0.078GB
be-mean            0.078GB
be-mean-instagram  0.078GB
be-mean-pokemons   0.078GB
duckapp-dev        0.078GB
fullstack-dev      0.078GB
local              0.078GB
myapp-dev          0.078GB
trainingapp-dev    0.078GB
```

## Listagem das coleções (passo 3)
```zsh
> show collections
pokemons
system.indexes
```

## Cadastro dos pokemons (passo 4)
```zsh
> var pikachu = {name:"Pikachu", description:"Rato elétrico bem fofinho", type:"eletric", attack:55, height:0.4}
> db.pokemons.insert(pikachu)
WriteResult({ "nInserted" : 1 })
> var bulba = {name:"Bulbassauro", description:"Chicote de trepadeira", type:"grama", attack:49, height:0.4}
> db.pokemons.insert(bulba)
WriteResult({ "nInserted" : 1 })
> var char = {name:"Charmander", description:"Esse é o cão chupando manga de fofinho", type:"fogo", attack:52, height:0.6}
> db.pokemons.insert(char)
WriteResult({ "nInserted" : 1 })
> var squi = {name:"Squirtle", description:"Ejeta água que passarinho não bebe", type:"água", attack:48, height:0.5}
> db.pokemons.insert(squi)
WriteResult({ "nInserted" : 1 })
```

## Lista dos pokemons (passo 5)
```zsh
> db.pokemons.find()
{ "_id" : ObjectId("5644a4a112150f4ff7f6186a"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("5644a57012150f4ff7f6186b"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("5644a5be12150f4ff7f6186c"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("5644a61012150f4ff7f6186d"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
```

## Caterpie (passo 6)
```zsh
> var larva = {name:"Caterpie", description:"Larva Lutadora", type:"inseto", attack:30, height:0.3}
> db.pokemons.insert(larva)
WriteResult({ "nInserted" : 1 })
```

## Atualização do Caterpie (passo 6)
```zsh
> var query = {name:"Caterpie"}
> var caterpie = db.pokemons.findOne(query)
> caterpie
{
  "_id" : ObjectId("5644a7c912150f4ff7f6186e"),
  "name" : "Caterpie",
  "description" : "Larva Lutadora",
  "type" : "inseto",
  "attack" : 30,
  "height" : 0.3
}
> caterpie.defense = 20
20
> caterpie
{
  "_id" : ObjectId("5644a7c912150f4ff7f6186e"),
  "name" : "Caterpie",
  "description" : "Larva Lutadora",
  "type" : "inseto",
  "attack" : 30,
  "height" : 0.3,
  "defense" : 20
}
> db.pokemons.save(caterpie)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> caterpie.description = "Larva lutadora zica do pantano, manja nada dos paranaue"
Larva lutadora zica do pantano, manja nada dos paranaue
> db.pokemons.save(caterpie)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> caterpie
{
  "_id" : ObjectId("5644a7c912150f4ff7f6186e"),
  "name" : "Caterpie",
  "description" : "Larva lutadora zica do pantano, manja nada dos paranaue",
  "type" : "inseto",
  "attack" : 30,
  "height" : 0.3,
  "defense" : 20
}
