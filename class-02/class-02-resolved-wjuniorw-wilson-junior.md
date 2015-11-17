# MongoDB - Aula 02 - Exercício
autor: wilson junior

##Criando db (1)
```
> use be-mean-instagram
switched to db be-mean-pokemons
```

## Listagem das databases (2)

````
> show dbs
be-mean
be-mean-instagram
local
teste
```

## Listagem das coleções (3)

```
switched to db be-mean-pokemons
> show collections
> 

```

## Cadastro dos pokemons (4)

```
wjuniorw:/ $ clear
> var pokemons = [{name: 'Charizard', description: 'Meu pokemon favorito haha', type: 'fire', attack: 40, defense: 30, height: 1.70}, 
... {name: 'Blastoise ', description: 'Tartaruga bombada huehue', type: 'water', attack: 40, defense: 40, height: 1.60}, 
... {name: 'ioda', description: 'et jedi pokemon', type: 'et', attack: 60, defense: 45, height: 0.30}, 
... {name: 'psyduck', description: 'Pato loko', type: 'water', attack: 45, defense: 60, height: 0.80},
... {name: 'pediot', description: 'passarinho do ash', type: 'flying', attack: 55, defense: 65, height: 0.25}]
> pokemons
[
        {
                "name" : "Charizard",
                "description" : "Meu pokemon favorito haha",
                "type" : "fire",
                "attack" : 40,
                "defense" : 30,
                "height" : 1.7
        },
        {
                "name" : "Blastoise ",
                "description" : "Tartaruga bombada huehue",
                "type" : "water",
                "attack" : 40,
                "defense" : 40,
                "height" : 1.6
        },
        {
                "name" : "ioda",
                "description" : "et jedi pokemon",
                "type" : "et",
                "attack" : 60,
                "defense" : 45,
                "height" : 0.3
        },
        {
                "name" : "psyduck",
                "description" : "Pato loko",
                "type" : "water",
                "attack" : 45,
                "defense" : 60,
                "height" : 0.8
        },
        {
                "name" : "pediot",
                "description" : "passarinho do ash",
                "type" : "flying",
                "attack" : 55,
                "defense" : 65,
                "height" : 0.25
        }
]
> db.pokemons.insert(pokemons)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 5,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})
> 

```

## Lista dos pokemons (5)

```
> db.pokemons.find().pretty()
{
        "_id" : ObjectId("56476f56794c3079ef771073"),
        "name" : "Charizard",
        "description" : "Meu pokemon favorito haha",
        "type" : "fire",
        "attack" : 40,
        "defense" : 30,
        "height" : 1.7
}
{
        "_id" : ObjectId("56476f56794c3079ef771074"),
        "name" : "Blastoise ",
        "description" : "Tartaruga bombada huehue",
        "type" : "water",
        "attack" : 40,
        "defense" : 40,
        "height" : 1.6
}
{
        "_id" : ObjectId("56476f56794c3079ef771075"),
        "name" : "ioda",
        "description" : "et jedi pokemon",
        "type" : "et",
        "attack" : 60,
        "defense" : 45,
        "height" : 0.3
}
{
        "_id" : ObjectId("56476f56794c3079ef771076"),
        "name" : "psyduck",
        "description" : "Pato loko",
        "type" : "water",
        "attack" : 45,
        "defense" : 60,
        "height" : 0.8
}
{
        "_id" : ObjectId("56476f56794c3079ef771077"),
        "name" : "pediot",
        "description" : "passarinho do ash",
        "type" : "flying",
        "attack" : 55,
        "defense" : 65,
        "height" : 0.25
}
> 

```

## Charizard (6)
```
wjuniorw:~/workspace (master) $ mongo
> var query = {'name':'Charizard'}
> var poke = db.pokemons.findOne(query)
> poke
{
        "_id" : ObjectId("56476f56794c3079ef771073"),
        "name" : "Charizard",
        "description" : "Meu pokemon favorito haha",
        "type" : "fire",
        "attack" : 40,
        "defense" : 30,
        "height" : 1.7
}

```

## Atualização do pokemon (7)
```
> query
{ "name" : "Charizard" }
> var poke = db.pokemons.findOne(query)
> poke
{
        "_id" : ObjectId("56476f56794c3079ef771073"),
        "name" : "Charizard",
        "description" : "Meu pokemon favorito haha",
        "type" : "fire",
        "attack" : 40,
        "defense" : 30,
        "height" : 1.7
}
> poke.description
Meu pokemon favorito haha
> poke.description = 'pokemom tipo fogo e voador'
pokemom tipo fogo e voador
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.findOne(query)
{
        "_id" : ObjectId("56476f56794c3079ef771073"),
        "name" : "Charizard",
        "description" : "pokemom tipo fogo e voador",
        "type" : "fire",
        "attack" : 40,
        "defense" : 30,
        "height" : 1.7
}
> 

```

