# MongDB - Aula 02 - Exercício
Autor: Rodrigo Valente

## Criar database database be-mean-pokemons
```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem dos dbs
```
be-mean  0.004GB
local    0.000GB
test     0.000GB
```

## Listagem das collections
```
> db.createCollection('pokemons')
{ "ok" : 1 }
> show collections
```

## Inserir cinco pokémons
```
> var pokemons = [
                   {
                        'name': 'Charizard',
                        'description': 'Pokémon dragão de fogo',
                        'type': 'fire',
                        'attack': 84,
                        'height': 17
                    },
                    {
                        'name': 'Raichu',
                        'description': 'Rato metido a besta',
                        'type': 'electric',
                        'attack': 90,
                        'height': 8
                    },
                    {
                        'name': 'Psyduck',
                        'description':
                        'Pato que exagerou nas drogas',
                        'type': 'water',
                        'attack': 52,
                        'height': '8'
                    },
                    {
                        'name': 'Muk',
                        'description': 'Meleca de esgoto mutante',
                        'type': 'poison',
                        'attack': 105,
                        'height': 12
                    },
                    {
                        'name': 'Kingler',
                        'description': 'Ensopado de caranguejo gigante', 'type': 'water',
                        'attack': 130,
                        'height': 13
                    }
                ]

> db.pokemons.save(pokemons)
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
```

## Listar todos os pokémons
```
> db.pokemons.find().pretty()
{
    "_id" : ObjectId("5682ff652ebc7952c85ba8c7"),
    "name" : "Charizard",
    "description" : "Pokémon dragão de fogo",
    "type" : "fire",
    "attack" : 84,
    "height" : 17
}
{
    "_id" : ObjectId("5682ff652ebc7952c85ba8c8"),
    "name" : "Raichu",
    "description" : "Rato metido a besta",
    "type" : "electric",
    "attack" : 90,
    "height" : 8
}
{
    "_id" : ObjectId("5682ff652ebc7952c85ba8c9"),
    "name" : "Psyduck",
    "description" : "Pato que exagerou nas drogas",
    "type" : "water",
    "attack" : 52,
    "height" : "8"
}
{
    "_id" : ObjectId("5682ff652ebc7952c85ba8ca"),
    "name" : "Muk",
    "description" : "Meleca de esgoto mutante",
    "type" : "poison",
    "attack" : 105,
    "height" : 12
}
{
    "_id" : ObjectId("5682ff652ebc7952c85ba8cb"),
    "name" : "Kingler",
    "description" : "Ensopado de caranguejo gigante",
    "type" : "water",
    "attack" : 130,
    "height" : 13
}
```

## Buscar um pokémon
```
> var query = {'name': 'Charizard'}
> var charizard = db.pokemons.findOne(query)
> charizard
{
    "_id" : ObjectId("5682ff652ebc7952c85ba8c7"),
    "name" : "Charizard",
    "description" : "Pokémon dragão de fogo",
    "type" : "fire",
    "attack" : 84,
    "height" : 17
}
```

## Alterar a descrição do pokémon
```
> charizard.description += ', mas infelizmente não é um dragão de verdade'
Pokémon dragão de fogo, mas infelizmente não é um dragão de verdade
> db.pokemons.save(charizard)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```