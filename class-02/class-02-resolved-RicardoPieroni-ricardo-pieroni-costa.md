
# MongoDB - Aula 02 - Exercício
autor: Ricardo Pieroni Costa

## 1. Criar uma database chamada be-mean-pokemons --

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## 2. Liste quais databases você possui nesse servidor
```

show dbs
be-mean           0.078GB
be-mean-istagram  0.078GB
local             0.078GB
test              0.078GB
```

## 3. Liste quais coleções você possui nessa database
```
show collections

```
## 4. Insira pelo menos 5 pokemons

```
var pokemon = {nome:"Charizard",description:"Dragão",type:"Flame",atack:60,height:1.7,defense:50}
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

var pokemon = {nome:"Blastoise",description:"Cabeça das tartarugas",type:"Shellfish",atack:40,height:1.6,defense:50}
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

var pokemon = {nome:"Beedrill",description:"Abelha do CV",type:"Bug, poison",atack:42,height:1,defense:30}
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

var pokemon = {nome:"Pidgeot",description:"Gavião",type:"Flying",atack:38,height:1.5,defense:40}
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

var pokemon = {nome:"Sandslash",description:"Rato",type:"Ground",atack:40,height:1,defense:45}
db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })


```


## 5. Liste os pokemons existentes na sua coleção

```
db.pokemons.find()
{ "_id" : ObjectId("56f1f86073ed2430c3fed72b"), "nome" : "Charizard", "description" : "Dragao", "type" : "flame", "atack
" : 60, "height" : 1.7, "defense" : 50 }
{ "_id" : ObjectId("56f28653cc5cba5a6e01385f"), "nome" : "Blastoise", "description" : "Cabeça das tartarugas", "type" :
"Shellfish", "atack" : 40, "height" : 1.6, "defense" : 50 }
{ "_id" : ObjectId("56f28746cc5cba5a6e013860"), "nome" : "Beedrill", "description" : "Abelha do CV", "type" : "Bug, pois
on", "atack" : 42, "height" : 1, "defense" : 30 }
{ "_id" : ObjectId("56f28862cc5cba5a6e013861"), "nome" : "Pidgeot", "description" : "Gavião", "type" : "Flying", "atack"
 : 38, "height" : 1.5, "defense" : 40 }
{ "_id" : ObjectId("56f288eecc5cba5a6e013862"), "nome" : "Sandslash", "description" : "Rato", "type" : "Ground", "atack"
 : 40, "height" : 1, "defense" : 45 }

```

## 6. Busque um pokemon e armazene-o em uma variável chamada "poke"

```

 var query = {nome:"Charizard"}
 var poke = db.pokemons.findOne(query)
 poke
{
        "_id" : ObjectId("56f1f86073ed2430c3fed72b"),
        "nome" : "Charizard",
        "description" : "Dragao",
        "type" : "flame",
        "atack" : 60,
        "height" : 1.7,
        "defense" : 50
}

```

## 7. Modifique sua "description" e salve-o

```
 var query = {nome:"Charizard"}
 var poke = db.pokemons.findOne(query)
 poke
{
        "_id" : ObjectId("56f1f86073ed2430c3fed72b"),
        "nome" : "Charizard",
        "description" : "Dragao",
        "type" : "flame",
        "atack" : 60,
        "height" : 1.7,
        "defense" : 50
}
 poke.description = "Lagartão do mangue"
Lagartão do mangue
poke
{
        "_id" : ObjectId("56f1f86073ed2430c3fed72b"),
        "nome" : "Charizard",
        "description" : "Lagartão do mangue",
        "type" : "flame",
        "atack" : 60,
        "height" : 1.7,
        "defense" : 50
}
 db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
 var aux = db.pokemons.findOne(query)
 aux
{
        "_id" : ObjectId("56f1f86073ed2430c3fed72b"),
        "nome" : "Charizard",
        "description" : "Lagartão do mangue",
        "type" : "flame",
        "atack" : 60,
        "height" : 1.7,
        "defense" : 50
}

```