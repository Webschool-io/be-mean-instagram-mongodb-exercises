# MongoDB - Aula 03 - Exercício
Geisson Carlos Rosario da Silva


## Listagem de todos os Pokemons com a altura menor que 0.5 

```
 var query = {height : {$lt: 0.5}}
 db.pokemons.find(query).pretty()

       "_id" : ObjectId("57a1f0ec3f967098188c3c46"),
       "name" : "Pikachu",
       "description" : "Rato Bobo",
       "Type" : "electric",
       "attack" : 55,
       "height" : 0.4


       "_id" : ObjectId("57a1f3eb3f967098188c3c47"),
       "name" : "Bubasauro",
       "description" : "chicote de trepadeira",
       "Type" : "grama",
       "attack" : 49,
       "height" : 0.4


       "_id" : ObjectId("57a1f79e3f967098188c3c4a"),
       "name" : "Caterpie",
       "description" : "Larva Lutadora",
       "Type" : "Inseto",
       "attack" : 30,
       "height" : 0.3



```

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5

```
> var query = {height : {$gte: 0.5}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("57a1f5d33f967098188c3c48"),
        "name" : "Charmander",
        "description" : "Taca Fogo nos outros",
        "Type" : "fogo",
        "attack" : 52,
        "height" : 0.6
}
{
        "_id" : ObjectId("57a1f6693f967098188c3c49"),
        "name" : "Squirtle",
        "description" : "Taca Agua em tudo",
        "Type" : "agua",
        "attack" : 48,
        "height" : 0.5
}
>

```

## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 **E** do tipo grama

```
> var query = {$and: [{height: {$lte: 0.5}}, {Type: "grama"}]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("57a1f3eb3f967098188c3c47"),
        "name" : "Bubasauro",
        "description" : "chicote de trepadeira",
        "Type" : "grama",
        "attack" : 49,
        "height" : 0.4
}
```

## Listagem de todos os Pokemons com o nome Pikachu **OU** com attack menor ou igual que 0.5

```
> var query ={$or:[ {name: "Pikachu"}, {attack:{$lte:0.5}}]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("57a1f0ec3f967098188c3c46"),
        "name" : "Pikachu",
        "description" : "Rato Bobo",
        "Type" : "electric",
        "attack" : 55,
        "height" : 0.4
}
>
```

## Listagem de todos os Pokemons com o attack maior ou igual que 48 **E** com height menor ou igual que 0.5

```
> var query ={$and:[ {attack:{$gte:48}},{height:{$lte: 0.5} }]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("57a1f0ec3f967098188c3c46"),
        "name" : "Pikachu",
        "description" : "Rato Bobo",
        "Type" : "electric",
        "attack" : 55,
        "height" : 0.4
}
{
        "_id" : ObjectId("57a1f3eb3f967098188c3c47"),
        "name" : "Bubasauro",
        "description" : "chicote de trepadeira",
        "Type" : "grama",
        "attack" : 49,
        "height" : 0.4
}
{
        "_id" : ObjectId("57a1f6693f967098188c3c49"),
        "name" : "Squirtle",
        "description" : "Taca Agua em tudo",
        "Type" : "agua",
        "attack" : 48,
        "height" : 0.5
}
>

```