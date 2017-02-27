# MongoDB - Aula 02 - Exercício
autor: Edison Ferraz

## Crie uma database chamada be-mean-pokemons
```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Liste quais databases você possui nesse servidor
```
show dbs

be-mean              0.005GB
be-mean-instagram    0.000GB
local                0.000GB
test                 0.000GB
teste                0.000GB
```

## Liste quais databases você possui nesse servidor
```
show collections
```

## Insira pelo menos 5 pokemons
```
db.pokemons.insert({"name": "Charizard", "description": "Pokemon de fogo", "attack": 66, "defense": 44, "height": 1,7})
db.pokemons.insert({"name": "Wartortle", "description": "Pokemon de água", "attack": 49, "defense": 88, "height": 1,0})
db.pokemons.insert({"name": "Metapod", "description": "Pokemon inseto", "attack": 22, "defense": 70, "height": 0,7})
db.pokemons.insert({"name": "Beedrill", "description": "Pokemon abelha venenosa", "attack": 55, "defense": 33, "height": 1,0"})
db.pokemons.insert({"name": "Cosmoem", "description": "Pokemon psiquico", "attack": 77, "defense": 77, "height": 0,1})
```

## Liste os pokemons existentes na sua coleção
```
db.pokemons.find()

{ "_id" : ObjectId("58b340702a7c86562c34f784"), "name" : "Charizard", "description" : "Pokemon de fogo", "attack" : 66, "defense" : 44, "height" : 1.7 }
{ "_id" : ObjectId("58b3440f2a7c86562c34f785"), "name" : "Wartortle", "description" : "Pokemon de água", "attack" : 49, "defense" : 88, "height" : 1 }
{ "_id" : ObjectId("58b344132a7c86562c34f786"), "name" : "Metapod", "description" : "Pokemon Inseto", "attack" : 22, "defense" : 70, "height" : 0.7 }
{ "_id" : ObjectId("58b344172a7c86562c34f787"), "name" : "Beedrill", "description" : "Pokemon abelha venenosa", "attack" : 55, "defense" : 33, "height" : 1 }
{ "_id" : ObjectId("58b3441a2a7c86562c34f788"), "name" : "Cosmoem", "description" : "Pokemon psiquico", "attack" : 77, "defense" : 77, "height" : 0.1 }
```

## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`
```
var poke = db.pokemons.findOne({"name" : "Metapod"})
```

## Modifique sua `description` e salvê-o
```
poke.description = "Pokemon Inseto de casco duro"
db.pokemons.save(poke)
```