# MongoDB - Aula 02 - Exercício
autor: Márcio Dias (https://github.com/spaceonline)

## Criando o database
```
marcio-mac:class-01 marciodias$ mongo
MongoDB shell version: 3.0.7
connecting to: test
Server has startup warnings: 
2015-11-16T15:01:06.476-0200 I CONTROL  [initandlisten] ** WARNING: You are running this process as the root user, which is not recommended.
2015-11-16T15:01:06.476-0200 I CONTROL  [initandlisten] 
2015-11-16T15:01:06.476-0200 I CONTROL  [initandlisten] 
2015-11-16T15:01:06.476-0200 I CONTROL  [initandlisten] ** WARNING: soft rlimits too low. Number of files is 256, should be at least 1000
> show dbs
be-mean  0.078GB
local    0.078GB
> use be-mean-pokemons
switched to db be-mean-pokemons
> 

## Listando coleções
```
> show dbs
be-mean  0.078GB
local    0.078GB
> use be-mean-pokemons
switched to db be-mean-pokemons


## Inserindo pokemons
```
> db.pokemons.insert({nome: "Shiny Scyther", description: "Inseto voador gigante boladão ceifador de vidas", attack: 333, defense: 100, height: 30.00})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({nome: "AecioSnows", description: "Tipo voador, nariz com coloração branca", attack: 2, defense: 8001, height: 80.00})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({nome: "Dilmee", description: "Parente do slowking, so fica boiando e repetindo coisas sem sentido", attack: 0.13, defense: 0, height: 88.00})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({nome: "Scizor", description: "Evolução do scyther nem sei qual é mais bolado", attack: 999, defense: 999, height: 33.33})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({nome: "Hitmonlee", description: "Homenagem ao mestre bruce lee, da vuadora até na sombra", attack: 9999999, defense: 999999, height: 60.33})
WriteResult({ "nInserted" : 1 })


## Listando pokemons
```
> db.pokemons.find()
{ "_id" : ObjectId("564a15dbe04cfaaf2d151dca"), "nome" : "Shiny Scyther", "description" : "Inseto voador gigante boladão ceifador de vidas", "attack" : 333, "defense" : 100, "height" : 30 }
{ "_id" : ObjectId("564a15e3e04cfaaf2d151dcb"), "nome" : "AecioSnows", "description" : "Tipo voador, nariz com coloração branca", "attack" : 2, "defense" : 8001, "height" : 80 }
{ "_id" : ObjectId("564a15e7e04cfaaf2d151dcc"), "nome" : "Dilmee", "description" : "Parente do slowking, so fica boiando e repetindo coisas sem sentido", "attack" : 0.13, "defense" : 0, "height" : 88 }
{ "_id" : ObjectId("564a15ede04cfaaf2d151dcd"), "nome" : "Scizor", "description" : "Evolução do scyther nem sei qual é mais bolado", "attack" : 999, "defense" : 999, "height" : 33.33 }
{ "_id" : ObjectId("564a15f0e04cfaaf2d151dce"), "nome" : "Hitmonlee", "description" : "Homenagem ao mestre bruce lee, da vuadora até na sombra", "attack" : 9999999, "defense" : 999999, "height" : 60.33 }


## Buscando pokemon
```
> var query = {nome: "Shiny Scyther"}
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("564a15dbe04cfaaf2d151dca"),
	"nome" : "Shiny Scyther",
	"description" : "Inseto voador gigante boladão ceifador de vidas",
	"attack" : 333,
	"defense" : 100,
	"height" : 30
}


## Alterando Pokemon
```

> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
