# MongoDB - Aula 03 - Exercício
autor: Alessandro Barreto

## Listando Pokemons com altura menor que 0.5 (Passo 1)
```
> var query = {height: {$lt: 0.5} }
> db.pokemons.find(query)
{ "_id" : ObjectId("575f74104d619e056552f51f"), "name" : "DilmaMon", "description" : "Estraga tudo", "attack" : 100, "defense" : 50, "height" : 0.3 }

```

## Listando Pokemons com altura maior ou igual que 0.5 (Passo 2)
```

> var query= {height:{$gte:0.5 }}
> db.pokemons.find(query)
{ "_id" : ObjectId("575f6ef44d619e056552f51a"), "name" : "Bulbasaur", "description" : "Modificando a descricao", "attack" : 3, "defense" : 2, "height" : 2.04 }
{ "_id" : ObjectId("575f6f064d619e056552f51b"), "name" : "Ivysaur", "description" : "There is a bud on this Pokémon's back", "attack" : 3, "defense" : 3, "height" : 3.03 }
{ "_id" : ObjectId("575f6f104d619e056552f51c"), "name" : "Venusaur", "description" : "There is a large flower on Venusaur's back", "attack" : 4, "defense" : 4, "height" : 6.07 }
{ "_id" : ObjectId("575f6f1a4d619e056552f51d"), "name" : "Charmander", "description" : "The flame that burns at the tip of its tail is an indication of its emotions", "attack" : 3, "defense" : 2, "height" : 2 }
{ "_id" : ObjectId("575f6f214d619e056552f51e"), "name" : "Charmeleon", "description" : "Charmeleon mercilessly destroys its foes using its sharp claws", "attack" : 3, "defense" : 3, "height" : 3.07 }
>

```

## Listando Pokemons com altura menor ou igual que 0.5 E do tipo grama (Passo 3)
```

>  var query = {$and: [{height: {$lte:0.5}},{type:"grama"}] }
> query
{
        "$and" : [
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "type" : "grama"
                }
        ]
}
> db.pokemons.find(query)
>

```

## Listando Pokemons com o name 'Pìkachu' OU com attack menor ou igual que 0.5 (Passo 4)
```

> var query = {$or: [{name:"Pikachu"},{attack:{$lte:0.5}}  ]    }
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
{ "_id" : ObjectId("575f77264d619e056552f520"), "name" : "Pikachu", "description" : "bicho amarelo eletrico", "attack" : 30, "defense" : 25, "height" : 1, "type" : "eletrico" }
>


```

## Listando Pokemons com attack maior ou igual que 48 E com altura menor ou igual que 0.5 (Passo 5)
```

> var query = { $and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]  }
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
>

```