# MongoDB - Aula 01 - Exercício
Autor: Oracy Martos

Be-mean

# Mostrando a base atual

```
> db.be_mean_pokemons.find().pretty()
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b1"),
    "name" : "Gardevoir",
    "description" : "Pokemon gay que voa",
    "attack" : 79,
    "defense" : 30,
    "height" : 0.5
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b2"),
    "name" : "Mew",
    "description" : "Pokemon gay que voa também e rosa",
    "attack" : 150,
    "defense" : 130,
    "height" : 0.4
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b3"),
    "name" : "Rayquaza",
    "description" : "Pokemon elétrico forte",
    "attack" : 160,
    "defense" : 100,
    "height" : 1.5
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b4"),
    "name" : "Emboar",
    "description" : "Pokemon lança chamas",
    "attack" : 95,
    "defense" : 45,
    "height" : 0.7
}
{
    "_id" : ObjectId("58bb286b751a098a8c3f82b5"),
    "name" : "Golduck",
    "description" : "Pokemon evolução do pato chato",
    "attack" : 59,
    "defense" : 31,
    "height" : 0.6
}
```

# 1- Pokemon com altura menor que 0.5
```
> var query = {height: {$lt: 0.5}}
> query
{ "height" : { "$lt" : 0.5 } }
> db.be_mean_pokemons.find(query).pretty()
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b2"),
    "name" : "Mew",
    "description" : "Pokemon gay que voa também e rosa",
    "attack" : 150,
    "defense" : 130,
    "height" : 0.4
}
```

# 2- Pokemon com altura maior ou igual que 0.5
```
> var query = {height: {$gte: 0.5}}
> query
{ "height" : { "$gte" : 0.5 } }
> db.be_mean_pokemons.find(query).pretty()
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b1"),
    "name" : "Gardevoir",
    "description" : "Pokemon gay que voa",
    "attack" : 79,
    "defense" : 30,
    "height" : 0.5
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b3"),
    "name" : "Rayquaza",
    "description" : "Pokemon elétrico forte",
    "attack" : 160,
    "defense" : 100,
    "height" : 1.5
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b4"),
    "name" : "Emboar",
    "description" : "Pokemon lança chamas",
    "attack" : 95,
    "defense" : 45,
    "height" : 0.7
}
{
    "_id" : ObjectId("58bb286b751a098a8c3f82b5"),
    "name" : "Golduck",
    "description" : "Pokemon evolução do pato chato",
    "attack" : 59,
    "defense" : 31,
    "height" : 0.6
}
```

# 3- Pokemon com altura menor ou igual que 0.5
```
> var query = {$and: [{type: 'grass'}, {height: {$lte: 0.5}}]}
> db.be_mean_pokemons.find(query).pretty()
```
Alterei a condição da query, só pra ver se tava funcionando 100%
```
> var query = {$and: [{type: 'fire'}, {height: {$gte: 0.5}}]}
> db.be_mean_pokemons.find(query).pretty()
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b1"),
    "name" : "Gardevoir",
    "description" : "Pokemon gay que voa",
    "attack" : 79,
    "defense" : 30,
    "height" : 0.5,
    "type" : "fire"
}
```

# 4- Pokemon com nome de Pikachu, ou ataque maior igual a 50
```
> var query = {$or: [{name: 'Pikachu'}, {attack: {$gte: 50}}] }
> query
{
    "$or" : [
        {
            "name" : "Pikachu"
        },
        {
            "attack" : {
                "$gte" : 50
            }
        }
    ]
}
> db.be_mean_pokemons.find(query).pretty()
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b1"),
    "name" : "Gardevoir",
    "description" : "Pokemon gay que voa",
    "attack" : 79,
    "defense" : 30,
    "height" : 0.5,
    "type" : "fire"
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b2"),
    "name" : "Mew",
    "description" : "Pokemon gay que voa também e rosa",
    "attack" : 150,
    "defense" : 130,
    "height" : 0.4
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b3"),
    "name" : "Rayquaza",
    "description" : "Pokemon elétrico forte",
    "attack" : 160,
    "defense" : 100,
    "height" : 1.5
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b4"),
    "name" : "Emboar",
    "description" : "Pokemon lança chamas",
    "attack" : 95,
    "defense" : 45,
    "height" : 0.7
}
{
    "_id" : ObjectId("58bb286b751a098a8c3f82b5"),
    "name" : "Golduck",
    "description" : "Pokemon evolução do pato chato",
    "attack" : 59,
    "defense" : 31,
    "height" : 0.6
}
```

# 5- Pokemon com ataque maior ou igual que 48 e altura menor ou igual a 0.5
```
> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}] }
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
> db.be_mean_pokemons.find(query).pretty()
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b1"),
    "name" : "Gardevoir",
    "description" : "Pokemon gay que voa",
    "attack" : 79,
    "defense" : 30,
    "height" : 0.5,
    "type" : "fire"
}
{
    "_id" : ObjectId("58bb2869751a098a8c3f82b2"),
    "name" : "Mew",
    "description" : "Pokemon gay que voa também e rosa",
    "attack" : 150,
    "defense" : 130,
    "height" : 0.4
}
> 
```