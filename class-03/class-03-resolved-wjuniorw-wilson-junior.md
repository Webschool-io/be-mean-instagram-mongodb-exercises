#MongoDB - Aula 03 - Exercício

Autor: **Wilson Junior**

## Liste todos os pokemons com altura menor que 0.5 - (1)
```
> var query = {height:{$lt:0.5}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("56476f56794c3079ef771075"),
        "name" : "ioda",
        "description" : "et jedi pokemon",
        "type" : "et",
        "attack" : 60,
        "defense" : 45,
        "height" : 0.3
}

```
##liste todos os pokemons com altura maior ou igual que 0.5 - (2)

```
> var query = {height:{$gte:0.5}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("56476f56794c3079ef771073"),
        "name" : "Charizard",
        "description" : "pokemom tipo fogo e voador",
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
        "height" : 0.5,
        "heith" : 0.5
}

```

## Liste todos os pokemons com altura menor ou igual que 0.5 ***E** do tipo grama - (3)

```
> var query = {$and:[{height:{$lte:0.5}},{type:/grama/}]}
> query
{
        "$and" : [
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "type" : /grama/
                }
        ]
}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564cc2e2f0fd2e9299f996e1"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4
}

```
## liste todos os pokemons com nome 'pikachu' **OU** com attack menor ou igual que 0.5 -(4)

```
> var query = {$or:[{attack:{$lte:0.5}},{name:/Pikachu/}]}
> query
{
        "$or" : [
                {
                        "attack" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "name" : /Pikachu/i
                }
        ]
}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564cc88af0fd2e9299f996e2"),
        "name" : "Pikachu",
        "description" : "ratim de estimacao do ash",
        "type" : "eletric",
        "attack" : 100,
        "height" : 0.4
}
> 

```

## liste todos os pokemons com attack **maior ou igual** que 48 **E** com height **menor ou igual que** 0.5 -(exercise 5)

```
> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
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
> db.pokemons.find(query).pretty()
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
        "_id" : ObjectId("56476f56794c3079ef771077"),
        "name" : "pediot",
        "description" : "passarinho do ash",
        "type" : "flying",
        "attack" : 55,
        "defense" : 65,
        "height" : 0.5,
        "heith" : 0.5
}
{
        "_id" : ObjectId("564cc2e2f0fd2e9299f996e1"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4
}
{
        "_id" : ObjectId("564cc88af0fd2e9299f996e2"),
        "name" : "Pikachu",
        "description" : "ratim de estimacao do ash",
        "type" : "eletric",
        "attack" : 100,
        "height" : 0.4
}

```

