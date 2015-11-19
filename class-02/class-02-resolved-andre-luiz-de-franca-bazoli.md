# MongoDB - Aula 02 - Exercício
autor: André Luiz de França Bazoli

## Criando DB Pokemons
```
MongoDB shell version: 3.0.4
connecting to: test
> use be-mean-pokemon
switched to db be-mean-pokemon
```

## Listagem de DBs
```
> show dbs
admin              0.078GB
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
test               0.078GB
```

## Listagem de Collections
```
> show collections
>
```

## Cadastro dos pokemons
```

var pks = [
    {name: 'Charizard', description: 'Pokemon grande e mau humorado', attack: 4 ,defense: 78, height: 1.7},
    {name: 'Rayquaza', description:'Bixão grandão que voa', attack:2, defense:1, height:1.6},
    {name: 'Blastoise ', description:'Blastoooooooiiissee', attack:5, defense:5, height:1.6},
    {name: 'Mega Blastoise', description:'Com 3 canhõeees', attack:150, defense:90, height:1},
    {name: 'Magmar', description:'Pato fogoso', attack:5, defense:3, height:1.3},
    {name: 'Magmortar', description:'Ovo maldoso de fogo', attack:5, defense:3, height:1.6}
]
> db.pokemons.save(pks)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 6,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})
```

## Lista dos pokemons
```
> db.pokemons.find({})
{ "_id" : ObjectId("564ddeb7c71b9fc59d7b4103"), "name" : "Charizard", "description" : "Pokemon grande e mau humorado", "attack" : 4, "defense" : 78, "height" : 1.7 }
{ "_id" : ObjectId("564ddeb7c71b9fc59d7b4104"), "name" : "Rayquaza", "description" : "Bixão grandão que voa", "attack" : 2, "defense" : 1, "height" : 1.6 }
{ "_id" : ObjectId("564ddeb7c71b9fc59d7b4105"), "name" : "Blastoise ", "description" : "Blastoooooooiiissee", "attack" : 5, "defense" : 5, "height" : 1.6 }
{ "_id" : ObjectId("564ddeb7c71b9fc59d7b4106"), "name" : "Mega Blastoise", "description" : "Com 3 canhõeees", "attack" : 150, "defense" : 90, "height" : 1 }
{ "_id" : ObjectId("564ddeb7c71b9fc59d7b4107"), "name" : "Magmar", "description" : "Pato fogoso", "attack" : 5, "defense" : 3, "height" : 1.3 }
{ "_id" : ObjectId("564ddeb7c71b9fc59d7b4108"), "name" : "Magmortar", "description" : "Ovo maldoso de fogo", "attack" : 5, "defense" : 3, "height" : 1.6 }
```

## Procurando Pokemon

```
var poke = db.pokemons.findOne({name: "Magmortar"})
```

## Atualização da descrição
```
> poke.description = 'Agora este é fraquinho'
Agora este é fraquinho
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```
