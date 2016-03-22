# MongoDB - Aula 02 - Exercício
autor: Ronaldo Paggi

## Criando database

```
MongoDB shell version: 3.2.4
connecting to: test
Server has startup warnings: 
> use be-mean-pokemons
switched to db be-mean-pokemons

```

## Listando os DBs que tenho neste server

```
> show dbs
be-mean-pokemons  0.078GB
local             0.078GB
teste             0.078GB

```

## Listando as collections que tenho neste DB(be-mean-pokemons)

```
> show collections
pokemons
system.indexes

```


## Inserindo 5 pokémons a minha escolha

```
> db.pokemons.insert({"name":"Pidgey", "description":"Passarinho com topete maneiro", "attack":45, "defense":40, "height":0.3})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({"name":"Raticate", "description":"Ratazana descolada", "attack":81, "defense":60, "height":0.7})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({"name":"Ekans", "description":"Cobra roxa celestial e pomposa", "attack":60, "defense":44, "height":2.0})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({"name":"Jigglypuff", "description":"Bolotinha rosa fofinha e que canta legal", "attack":45, "defense":20, "height":0.5})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({"name":"Kadabra", "description":"Pokemón mágico com bigodão supimpa", "attack":35, "defense":30, "height":1.3})
WriteResult({ "nInserted" : 1 })


```


## Listando pokémons da minha database

```
> db.pokemons.find()
{ "_id" : ObjectId("56f1380673a1da36de837161"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56f1381973a1da36de837162"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("56f1385873a1da36de837163"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("56f13b8623c56da55ad43192"), "name" : "Pidgey", "description" : "Passarinho com topete maneiro", "attack" : 45, "defense" : 40, "height" : 0.3 }
{ "_id" : ObjectId("56f13c1b23c56da55ad43193"), "name" : "Raticate", "description" : "Ratazana descolada", "attack" : 81, "defense" : 60, "height" : 0.7 }
{ "_id" : ObjectId("56f13c7e23c56da55ad43194"), "name" : "Ekans", "description" : "Cobra roxa celestial e pomposa", "attack" : 60, "defense" : 44, "height" : 2 }
{ "_id" : ObjectId("56f13db623c56da55ad43195"), "name" : "Jigglypuff", "description" : "Bolotinha rosa fofinha e que canta legal", "attack" : 45, "defense" : 20, "height" : 0.5 }
{ "_id" : ObjectId("56f13e4f23c56da55ad43196"), "name" : "Kadabra", "description" : "Pokemón mágico com bigodão supimpa", "attack" : 35, "defense" : 30, "height" : 1.3 }


```


## Buscando pokémon e alterando sua description

```
> var poke = db.pokemons.findOne({"name":"Raticate"})
> poke.name
Raticate
> poke.description = "Ratazana descolada dos guetos"
Ratazana descolada dos guetos
> poke
{
    "_id" : ObjectId("56f13c1b23c56da55ad43193"),
    "name" : "Raticate",
    "description" : "Ratazana descolada dos guetos",
    "attack" : 81,
    "defense" : 60,
    "height" : 0.7
}
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })


```
