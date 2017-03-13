# MongoDb - Aula 02 - Exercício
autor Lucas Frutig

## Criar Database chamada be-mean-pokemons
```
	> use be-mean-pokemons
switched to db be-mean-pokemons	

```

## Listar quais databases possuo no servidor
```
> show dbs
admin              0.000GB
be-mean-instagram  0.000GB
local              0.000GB
test               0.000GB
teste              0.005GB

```

## Listar quais coleções possuo nesta database
```
> show collections
> 0.005GB

```

## Insirer pelo menos 5 pokemons na database
```
> var poks = [
... {
... name:"Charizard",
... description:"dragão do fogo",
... type:"Fire",
... attack:100,
... defense:55,
... height:1.7
... },
... {
... name:"Blastoise ",
... description:"dragão da água",
... type:"Water",
... attack:30,
... defense:44,
... height:0.5
... },
... {
... name:"Metapod ",
... description:"Bichinho bonito verdinho",
... type:"Bug",
... attack:45,
... defense:22,
... height:0.7
... },
... {
... name:"Charmeleon",
... description:"Bichinho do fogo",
... type:"Fire",
... attack:30,
... defense:66,
... height:1.1
... },
... {
... name:"Caterpie  ",
... description:"Bichinho bonito verdinho estran
... type:"Bug",
... attack:55,
... defense:35,
... height:0.3
... },
...
... ]
> poks
[
        {
                "name" : "Charizard",
                "description" : "dragão do fogo"
                "type" : "Fire",
                "attack" : 100,
                "defense" : 55,
                "height" : 1.7
        },
        {
                "name" : "Blastoise ",
                "description" : "dragão da água"
                "type" : "Water",
                "attack" : 30,
                "defense" : 44,
                "height" : 0.5
        },
        {
                "name" : "Metapod ",
                "description" : "Bichinho bonito
                "type" : "Bug",
                "attack" : 45,
                "defense" : 22,
                "height" : 0.7
        },
        {
                "name" : "Charmeleon",
                "description" : "Bichinho do fog
                "type" : "Fire",
                "attack" : 30,
                "defense" : 66,
                "height" : 1.1
        },
        {
                "name" : "Caterpie  ",
                "description" : "Bichinho bonito
                "type" : "Bug",
                "attack" : 55,
                "defense" : 35,
                "height" : 0.3
        }
]
> db.pokemons.save(poks)
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

## Listar pokemons existentes na coleção
```
> db.pokemons.find()
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e1"), "name" : "Charizard", "description" : "dragão do fogo", "type" : "Fire",
 "attack" : 100, "defense" : 55, "height" : 1.7 }
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e2"), "name" : "Blastoise ", "description" : "dragão da água", "type" : "Water
", "attack" : 30, "defense" : 44, "height" : 0.5 }
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e3"), "name" : "Metapod ", "description" : "Bichinho bonito verdinho", "type"
: "Bug", "attack" : 45, "defense" : 22, "height" : 0.7 }
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e4"), "name" : "Charmeleon", "description" : "Bichinho do fogo", "type" : "Fir
e", "attack" : 30, "defense" : 66, "height" : 1.1 }
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e5"), "name" : "Caterpie  ", "description" : "Bichinho bonito verdinho estranh
o", "type" : "Bug", "attack" : 55, "defense" : 35, "height" : 0.3 }

```

## Buscando pokemon
```
> var q = db.pokemons.findOne({name:"Charmeleon"})
> q
{
        "_id" : ObjectId("58c6e1768d11b5bc504a27e4"),
        "name" : "Charmeleon",
        "description" : "Bichinho do fogo",
        "type" : "Fire",
        "attack" : 30,
        "defense" : 66,
        "height" : 1.1
}

```

## Modifique sua description e salve-o
```
> q.description = q.description + " fela"
Bichinho do fogo fela
>

```


