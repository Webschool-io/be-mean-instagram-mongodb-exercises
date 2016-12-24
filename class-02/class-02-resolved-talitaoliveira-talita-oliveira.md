# MongoDB - Aula 02 - Exercício
autor: Talita Oliveira

## Listagem das databases (passo 2)
```
use be-mean-pokemons
switched to db be-mean-pokemons

show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
database           0.078GB
local              0.078GB
```

## Listagem das coleções (passo 3)
```
show collections

```
## Cadastro dos pokemons (passo 4)
```
var meus_pokemons = [{"name":"Rattata","description":"É bicho solto","type":"normal",attack:56,defense:35,height:0.3},{"name":"Butterfree","description":"Manteiga livre","type":"inseto",attack:45,defense:50,height:1.1},{"name":"Metapod","description":"Não se mexe muito","type":"inseto",attack:20,defense:55,height:0.7},{"name":"Ekans","description":"Snake ao contrário","type":"veneno",attack:60,defense:44,height:2.0},{"name":"Dugtrio","description":"Toupera de três cabeças megalomaníaca","type":"terra",defense:50,attack:80,height:0.7}]

meus_pokemons
[
        {
                "name" : "Rattata",
                "description" : "É bicho solto",
                "type" : "normal",
                "attack" : 56,
                "defense" : 35,
                "height" : 0.3
        },
        {
                "name" : "Butterfree",
                "description" : "Manteiga livre",
                "type" : "inseto",
                "attack" : 45,
                "defense" : 50,
                "height" : 1.1
        },
        {
                "name" : "Metapod",
                "description" : "Não se mexe muito",
                "type" : "inseto",
                "attack" : 20,
                "defense" : 55,
                "height" : 0.7
        },
        {
                "name" : "Ekans",
                "description" : "Snake ao contrário",
                "type" : "veneno",
                "attack" : 60,
                "defense" : 44,
                "height" : 2
        },
        {
                "name" : "Dugtrio",
                "description" : "Toupera de três cabeças megalomaníaca",
                "type" : "terra",
                "defense" : 50,
                "attack" : 80,
                "height" : 0.7
        }
]

db.pokemons.insert(meus_pokemons)
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
## Lista dos pokemons (passo 5)
```

db.pokemons.find()
{ "_id" : ObjectId("566dfd91e586e1877b4a7539"), "name" : "Rattata", "description" : "É bicho solto", "type" : "normal", "attack" : 56, "defense" : 35, "height" : 0.3 }
{ "_id" : ObjectId("566dfd91e586e1877b4a753a"), "name" : "Butterfree", "description" : "Manteiga livre", "type" : "inseto", "attack" : 45, "defense" : 50, "height" : 1.1 }
{ "_id" : ObjectId("566dfd91e586e1877b4a753b"), "name" : "Metapod", "description" : "Não se mexe muito", "type" : "inseto", "attack" : 20, "defense" : 55, "height" : 0.7 }
{ "_id" : ObjectId("566dfd91e586e1877b4a753c"), "name" : "Ekans", "description" : "Snake ao contrário", "type" : "veneno", "attack" : 60, "defense" : 44, "height" : 2 }
{ "_id" : ObjectId("566dfd91e586e1877b4a753d"), "name" : "Dugtrio", "description" : "Toupera de três cabeças megalomaníaca", "type" : "terra", "defense" : 50, "attack" : 80, "height" : 0.7 }

```

## Pokemon (passo 6)
```
var poke = db.pokemons.findOne({"name":"Butterfree"})
poke
{
        "_id" : ObjectId("566dfd91e586e1877b4a753a"),
        "name" : "Butterfree",
        "description" : "Manteiga livre",
        "type" : "inseto",
        "attack" : 45,
        "defense" : 50,
        "height" : 1.1
}

```

## Atualização do Pokemon (passo 6)
```
poke.description
Manteiga livre
poke.description = "Borboleta manteiga livre"
Borboleta manteiga livre
db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
db.pokemons.findOne({"name":"Butterfree"})
{
        "_id" : ObjectId("566dfd91e586e1877b4a753a"),
        "name" : "Butterfree",
        "description" : "Borboleta manteiga livre",
        "type" : "inseto",
        "attack" : 45,
        "defense" : 50,
        "height" : 1.1
}

```

