# MongoDB - Aula 02 - Exercício
autor: Laurindo Ferreira Lucio Junior

## Listagem das databases (passo 2)

```javascript
use be-mean-pokemons
db
show dbs
```

resultado

```shell
be-mean-instagram  0.078GB
be-mean            0.078GB
blog               0.078GB
course             0.078GB
demo               0.078GB
local              0.078GB
m101               0.078GB
school             0.078GB
test               0.078GB
weather            0.078GB
```

## Listagem das coleções (passo 3)

```javascript
show collections
```

resultado

```shell

```

## Cadastro dos pokemons (passo 4)

```javascript
var pokemon = {'name':'Charmeleon','description':'Charmeleon mercilessly destroys its foes using its sharp claws.','type':'fire','attack':64, height:11}
db.pokemons.insert(pokemon)
var pokemon = {'name':'Pidgeotto','description':'Pidgeotto claims a large area as its own territory.','type':'flying','attack':60, height:11}
db.pokemons.insert(pokemon)
var pokemon = {'name':'Psyduck','description':'Psyduck uses a mysterious power.','type':'water','attack':52, height:8}
db.pokemons.insert(pokemon)
var pokemon = {'name':'Growlithe','description':'Growlithe has a superb sense of smell.','type':'fire','attack':70, height:7}
db.pokemons.insert(pokemon)
var pokemon = {'name':'Magnemite','description':'Magnemite attaches itself to power lines to feed on electricity.','type':'electric','attack':35, height:3}
db.pokemons.insert(pokemon)
```

## Lista dos pokemons (passo 5)

```javascript
db.pokemons.find()
```

resultado

```shell
Junior-PC(mongod-3.0.6) be-mean-pokemons> db.pokemons.find()
{
    "_id": ObjectId("565687fadd1479dd7af9bc95"),
    "name": "Charmeleon",
    "description": "Charmeleon mercilessly destroys its foes using its sharp claws.",
    "type": "fire",
    "attack": 64,
    "height": 11
}
{
    "_id": ObjectId("565687fadd1479dd7af9bc96"),
    "name": "Pidgeotto",
    "description": "Pidgeotto claims a large area as its own territory.",
    "type": "flying",
    "attack": 60,
    "height": 11
}
{
    "_id": ObjectId("565687fadd1479dd7af9bc97"),
    "name": "Psyduck",
    "description": "Psyduck uses a mysterious power.",
    "type": "water",
    "attack": 52,
    "height": 8
}
{
    "_id": ObjectId("565687fadd1479dd7af9bc98"),
    "name": "Growlithe",
    "description": "Growlithe has a superb sense of smell.",
    "type": "fire",
    "attack": 70,
    "height": 7
}
{
    "_id": ObjectId("565687fcdd1479dd7af9bc99"),
    "name": "Magnemite",
    "description": "Magnemite attaches itself to power lines to feed on electricity.",
    "type": "electric",
    "attack": 35,
    "height": 3
}
Fetched 5 record(s) in 97ms
```

## Pikachu (passo 6)

```javascript
var query = {'name':'Psyduck'}
var poke = db.pokemons.findOne(query)
poke
```

resultado

```shell
Junior-PC(mongod-3.0.6) be-mean-pokemons> poke
{
    "_id": ObjectId("565687fadd1479dd7af9bc97"),
    "name": "Psyduck",
    "description": "Psyduck uses a mysterious power.",
    "type": "water",
    "attack": 52,
    "height": 8
}
```

## Atualização do Pikachu (passo 6)

```javascript
poke.description = 'Um pato meio maluco com dores de cabeça e aprontando altas confusões'
db.pokemons.save(poke)
db.pokemons.find()
```

resultado

```shell
Junior-PC(mongod-3.0.6) be-mean-pokemons> db.pokemons.find()
{
    "_id": ObjectId("565687fadd1479dd7af9bc95"),
    "name": "Charmeleon",
    "description": "Charmeleon mercilessly destroys its foes using its sharp claws.",
    "type": "fire",
    "attack": 64,
    "height": 11
}
{
    "_id": ObjectId("565687fadd1479dd7af9bc96"),
    "name": "Pidgeotto",
    "description": "Pidgeotto claims a large area as its own territory.",
    "type": "flying",
    "attack": 60,
    "height": 11
}
{
    "_id": ObjectId("565687fadd1479dd7af9bc97"),
    "name": "Psyduck",
    "description": "Um pato meio maluco com dores de cabeça e aprontando altas confusões",
    "type": "water",
    "attack": 52,
    "height": 8
}
{
    "_id": ObjectId("565687fadd1479dd7af9bc98"),
    "name": "Growlithe",
    "description": "Growlithe has a superb sense of smell.",
    "type": "fire",
    "attack": 70,
    "height": 7
}
{
    "_id": ObjectId("565687fcdd1479dd7af9bc99"),
    "name": "Magnemite",
    "description": "Magnemite attaches itself to power lines to feed on electricity.",
    "type": "electric",
    "attack": 35,
    "height": 3
}
Fetched 5 record(s) in 183ms
```
