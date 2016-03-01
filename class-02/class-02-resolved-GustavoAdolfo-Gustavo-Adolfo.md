# MongoDB - Aula 02 - Exercício
autor: Gustavo Adolfo

## Criacao do database
> use be-mean-pokemons
switched to db be-mean-pokemons

## Listagem das databases
```
> show dbs
ExemploCSharp  0.000GB
be-mean        0.004GB
local          0.000GB
```

## Listagem das coleções
```
> show collections
```

## Cadastro dos pokemons 
```
> var pokes = [ { "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4},{ "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4},{ "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6},{ "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5},{ "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3} ];

> pokes
[
        {
                "name" : "Pikachu",
                "description" : "Rato elétrico bem fofinho",
                "type" : "electric",
                "attack" : 100,
                "height" : 0.4
        },
        {
                "name" : "Bulbassauro",
                "description" : "Chicote de trepadeira",
                "type" : "grama",
                "attack" : 49,
                "height" : 0.4
        },
        {
                "name" : "Charmander",
                "description" : "Esse é o cão chupando manga de fofinho",
                "type" : "fogo",
                "attack" : 52,
                "height" : 0.6
        },
        {
                "name" : "Squirtle",
                "description" : "Ejeta água que passarinho não bebe",
                "type" : "água",
                "attack" : 48,
                "height" : 0.5
        },
        {
                "name" : "Caterpie",
                "description" : "Larva lutadora",
                "type" : "inseto",
                "attack" : 30,
                "height" : 0.3
        }
]

> db.be-mean-pokemons.save(pokes)
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

## Listagem dos pokemons
```
> db.be-mean-pokemons.find()
{ "_id" : ObjectId("56c860be06d4893022ac072c"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4 }
{ "_id" : ObjectId("56c860be06d4893022ac072d"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("56c860be06d4893022ac072e"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("56c860be06d4893022ac072f"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("56c860be06d4893022ac0730"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3 }
```

## Atualizando
```
> var revisao = db.be-mean-pokemons.findOne({name:'Squirtle'})
> revisao
{
        "_id" : ObjectId("56c860be06d4893022ac072f"),
        "name" : "Squirtle",
        "description" : "Ejeta água que passarinho não bebe",
        "type" : "água",
        "attack" : 48,
        "height" : 0.5
}
> revisao.description = "Pokemon mijão"
Pokemon mijão

> db.be-mean-pokemons.save(revisao)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
>
> db.be-mean-pokemons.find({ name:"Squirtle"}).pretty()
{
        "_id" : ObjectId("56c860be06d4893022ac072f"),
        "name" : "Squirtle",
        "description" : "Pokemon mijão",
        "type" : "água",
        "attack" : 48,
        "height" : 0.5
}
```