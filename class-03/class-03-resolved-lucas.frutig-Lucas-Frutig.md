# MongoDb - Aula 03 - Exercício
autor Lucas Frutig

## Listar todos pokemons com altura menor que 0.5
```
> var query = {height:{$lt:0.5}}
> query
{ "height" : { "$lt" : 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e5"), "name" : "Caterpie  ",
o", "type" : "Bug", "attack" : 55, "defense" : 35, "height" : 0.3 }

```

## Listar todos pokemons com altura maior ou igual a 0.5
```
> var query = {height:{$gte:0.5}}
> query
{ "height" : { "$gte" : 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e1"), "name" :
 "attack" : 100, "defense" : 55, "height" : 1.7 }
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e2"), "name" :
", "attack" : 30, "defense" : 44, "height" : 0.5 }
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e3"), "name" :
: "Bug", "attack" : 45, "defense" : 22, "height" : 0.7 }
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e4"), "name" :
e", "attack" : 30, "defense" : 66, "height" : 1.1 }            0.005GB

```

## Listar todos pokemons com altura menor ou igual que 0.5 E do tipo grama
```
> var query = {
... $and:
... [
... {height: {$lte: 0.5}},
... {tipo: "grama"}
... ]
... }
> query
{
        "$and" : [
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "tipo" : "grama"
                }
        ]
}
> db.pokemons.find(query)
>

```

## Listar todos pokemons com nome 'Pikachu' ou com attack menor ou igual que 0.5
```
>> var query = {
... $or: [
... {name:'Pikachu'},
... {attack:{
... $lte:0.5
... }}
... ]
... }
> query
{
        "$or" : [
                {
                        "name" : "Pikachu"
                },
                {
                        "attack" : {
                                "$lte" : 0.5
                        }
                }
        ]
}
> db.pokemons.find(query)

```

## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5
```
> var query = { $and: [ {attack: {$gte:48}}, {height:{$lte:0.5}}] }
> query
{
        "$and" : [
                {
                        "attack" : {
                                "$gte" : 48
                        }
                },
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                }
        ]
}
> db.pokemons.find(query)
{ "_id" : ObjectId("58c6e1768d11b5bc504a27e5"), "name" : "Caterpie  ", "de
o", "type" : "Bug", "attack" : 55, "defense" : 35, "height" : 0.3 }

```


