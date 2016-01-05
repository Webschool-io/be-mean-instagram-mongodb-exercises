# MongoDB - Aula 02 - Exercício
Autor: Paulo Roberto
## Crie uma database chamada be-mean-pokemons (passo 1)
```
$mongo be-mean-pokemons
2015-12-23T18:41:37.601-0200 I CONTROL  [main] Hotfix KB2731284 or later update
is not installed, will zero-out data files
MongoDB shell version: 3.2.0
connecting to: be-mean-pokemons
```

## Listagem das databases (passo 2)
```
> show dbs
be-mean            0.004GB
be-mean-instagram  0.000GB
local              0.000GB
```

## Listagem das coleções (passo 3)
```
> show collections
```
## Cadastro dos pokemons (passo 4)
```
> db.pokemons.insert([
{'name': 'Meowth', 'description':'Serve pra nada', 'type':'normal', 'attack': 2, 'height':1.04, defense:2},
{'name': 'Quilava', 'description':'Parece uma foca, só que com fogo', 'type':'fogo', 'attack': 3, 'height':2.1, defense:3},
{'name': 'Vulpix', 'description':'Um esquilo que tem fogo', 'type':'fogo', 'attack': 2, 'height':2, defense:2},
{'name': 'Swellow', 'description':'Um passaro evoluido', 'type':'voador', 'attack': 3, 'height':2.04, defense:2},
{'name': 'Ninetales', 'description':'Evolução do esquilo', 'type':'Fogo', 'attack': 3, 'height':2.04, defense:2}])
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
> db.pokemons.find()
{ "_id" : ObjectId("567b2b43bae1746961f04c5e"), "name" : "Meowth", "description": "Serve pra nada", 
"type" : "normal", "attack" : 2, "height" : 1.04, "defense" : 2 }
{ "_id" : ObjectId("567b2b43bae1746961f04c5f"), "name" : "Quilava", "description" : "Parece uma foca, só que com fogo", 
"type" : "fogo", "attack" : 3, "height": 2.1, "defense" : 3 }
{ "_id" : ObjectId("567b2b43bae1746961f04c60"), "name" : "Vulpix", "description": "Um esquilo que tem fogo", "type" : "fogo", 
"attack" : 2, "height" : 2, "defense" : 2 }
{ "_id" : ObjectId("567b2b43bae1746961f04c61"), "name" : "Swellow", "description" : "Um passaro evoluido", 
"type" : "voador", "attack" : 3, "height" : 2.04, "defense" : 2 }
{ "_id" : ObjectId("567b2b43bae1746961f04c62"), "name" : "Ninetales", "description" : "Evolução do esquilo", "type" : "Fogo",
"attack" : 3, "height" : 2.04, "defense" : 2 }
>

```
## Busque um pokemon a sua escolha, e armazene-o em uma variável chamada poke (passo 6)
```
> var poke = db.pokemons.findOne({'name':'Meowth'})
> poke
{
        "_id" : ObjectId("567b2b43bae1746961f04c5e"),
        "name" : "Meowth",
        "description" : "Serve pra nada",
        "type" : "normal",
        "attack" : 2,
        "height" : 1.04,
        "defense" : 2
}
```
## Modifique sua description e salvê-o (passo 7)
```
> poke.description = 'ajuda a equipe rocket'
ajuda a equipe rocket
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```
