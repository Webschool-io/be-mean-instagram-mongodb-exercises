# MongoDB - Aula 02 - Exercício
autor: GEISSON CARLOS ROSARIO DA SILVA

## Criando database be-mean-pokemons
```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando as databases
```
show dbs
local    0.078GB
mongodb  0.078GB
```

## Listando as coleções
```
show collections
nada
```

## Inserindo os pokemons
```
 
> db.pokemons.insert({name: "Bulbasaur", description: "Bulbasaur can be seen napping in bright sunlight", attack: 3, def
ense: 2, height: 2.04})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({name: "Ivysaur", description: "There is a bud on this Pokémon's back", attack: 3, defense: 3, heig
ht: 3.03})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({name: "Charmander", description: "The flame that burns at the tip of its tail is an indication of
its emotions", attack: 3, defense: 2, height: 2.00})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({name: "Charmeleon", description: "Charmeleon mercilessly destroys its foes using its sharp claws",
 attack: 3, defense: 3, height: 3.07})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({name: "Venusaur", description: "There is a large flower on Venusaur's back", attack: 4, defense: 4
, height: 6.07})
WriteResult({ "nInserted" : 1 })

```

## Listando os pokemons
```
db.pokemons.find()
> db.pokemons.find().pretty()
{
        "_id" : ObjectId("57a88589e96c5bf67969b2e4"),
        "name" : "Bulbasaur",
        "description" : "Bulbasaur can be seen napping in bright sunlight",
        "attack" : 3,
        "defense" : 2,
        "height" : 2.04
}
{
        "_id" : ObjectId("57a885ade96c5bf67969b2e5"),
        "name" : "Ivysaur",
        "description" : "There is a bud on this Pokémon's back",
        "attack" : 3,
        "defense" : 3,
        "height" : 3.03
}
{
        "_id" : ObjectId("57a885ade96c5bf67969b2e6"),
        "name" : "Charmander",
        "description" : "The flame that burns at the tip of its tail is an indica
        "attack" : 3,
        "defense" : 2,
        "height" : 2
}
{
        "_id" : ObjectId("57a885ade96c5bf67969b2e7"),
        "name" : "Charmeleon",
        "description" : "Charmeleon mercilessly destroys its foes using its sharp
        "attack" : 3,
        "defense" : 3,
        "height" : 3.07
}
{
        "_id" : ObjectId("57a885ade96c5bf67969b2e8"),
        "name" : "Venusaur",
        "description" : "There is a large flower on Venusaur's back",
        "attack" : 4,
        "defense" : 4,
        "height" : 6.07
}

```

## Buscando o 'Charmeleon' para a variável poke
```
> var poke = db.pokemons.find({name: "Charmeleon"}).pretty()
> poke
{
        "_id" : ObjectId("57a885ade96c5bf67969b2e7"),
        "name" : "Charmeleon",
        "description" : "Charmeleon mercilessly destroys its foes using its sharp claws",
        "attack" : 3,
        "defense" : 3,
        "height" : 3.07
}
>
```

## Modificando a description e salvando
```
> var poke = db.pokemons.findOne({name: "Charmeleon"})
> poke
{
        "_id" : ObjectId("57a885ade96c5bf67969b2e7"),
        "name" : "Charmeleon",
        "description" : "Charmeleon mercilessly destroys its foes using its sharp claws",
        "attack" : 3,
        "defense" : 3,
        "height" : 3.07
}
> poke.description = "Dinosauro cheio de Fogo no Rabo!!"
Dinosauro cheio de Fogo no Rabo!!
>

> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```