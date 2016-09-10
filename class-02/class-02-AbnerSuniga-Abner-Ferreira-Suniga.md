# MongoDB - Aula 02 - Exercício resolvido
autor: Abner Ferreira Suniga

## 1. Criar uma database chamada be-mean-pokemons

```
> use be-mean-pokemons
switched to db be-mean-pokemons

```

## 2. Liste quais databases você possui nesse servidor

```
> show dbs
be-mean            0.005GB
be-mean-instagram  0.000GB
local              0.000GB

```

## 3. Liste quais coleções você possui nessa database

```
> show collections

```

## 4. Insira pelo menos 5 pokemons

```
> db.pokemons.insert({ "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4 })
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({ "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49,
"height" : 0.4 })
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({ "name" : "Charmander", "description" : "Esse e o cao chupando manga de fofinho", "type" : "fogo","attack" : 52, "height" : 0.6 })
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({ "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5 })
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({ "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height": 0.3, "defense" : 35 })
WriteResult({ "nInserted" : 1 })
```

## 5. Liste os pokemons existentes na sua coleção

```
> db.pokemons.find()
{ "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("57d43186c953b335c0afd7bd"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("57d431cfc953b335c0afd7be"), "name" : "Charmander", "description" : "Esse e o cao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
{ "_id" : ObjectId("57d431e7c953b335c0afd7bf"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("57d431fac953b335c0afd7c0"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
>

```

## 6. Busque um pokemon e armazene-o em uma variável chamada "poke"

```
> var query = {name:'Pikachu'}
> var poke = db.pokemons.findOne(query)
> poke
{
        "_id" : ObjectId("57d41812c953b335c0afd7b8"),
        "name" : "Pikachu",
        "description" : "Raio eletrico bem fofinho",
        "type" : "eletric",
        "attack" : 55,
        "height" : 0.4
}

```

## 7. Modifique sua "description" e salve-o

```
> poke.description = "Pika Pikaaaaaaaaaa"
Pika Pikaaaaaaaaaa
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

```
