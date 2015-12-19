# MongoDB - Aula 02 - Exercício
autor: Marco Tanaka

## Criando o DB (passo 1)

```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)

```
> show dbs
be-mean  0.078GB
local    0.078GB
```

## Listagem das coleções (passo 3)

```
> show collections
```

## Cadastro dos pokemons (passo 4)

```
> var pokemons = [{name: 'Suissamon', description: 'Pokemon Hacker', type: 'hacker', attack: 8001, defense: 8000, height: 1.69},{name: 'Dilmamon', description: 'Pokemon presidANTA', type: 'besta', attack: 1, defense: 1, height: 1.60},{name: 'Cunhamon', description: 'Filho da puta', type: 'besta', attack: 9990, defense: 9999, height: 1.80},{name: 'Calheirosmon', description: 'Irmão do filho da PUTA', type: 'besta', attack: 8500, defense: 9999, height: 1.79},{name: 'FeliciANUS', description: 'Pastor baitola', type: 'besta', attack: 666, defense: 666, height: 1.70}]
> db.pokemons.save(pokemons)
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
{ "_id" : ObjectId("5646b0335fcbd7a122583a7a"), "name" : "Suissamon", "description" : "Pokemon Hacker", "type" : "hacker", "attack" : 8001, "defense" : 8000, "height" : 1.69 }
{ "_id" : ObjectId("5646b0335fcbd7a122583a7b"), "name" : "Dilmamon", "description" : "Pokemon presidANTA", "type" : "besta", "attack" : 1, "defense" : 1, "height" : 1.6 }
{ "_id" : ObjectId("5646b0335fcbd7a122583a7c"), "name" : "Cunhamon", "description" : "Filho da puta", "type" : "besta", "attack" : 9990, "defense" : 9999, "height" : 1.8 }
{ "_id" : ObjectId("5646b0335fcbd7a122583a7d"), "name" : "Calheirosmon", "description" : "Irmão do filho da PUTA", "type" : "besta", "attack" : 8500, "defense" : 9999, "height" : 1.79 }
{ "_id" : ObjectId("5646b0335fcbd7a122583a7e"), "name" : "FeliciANUS", "description" : "Pastor baitola", "type" : "besta", "attack" : 666, "defense" : 666, "height" : 1.7 }
```

## Pokemon (passo 6)

```
> var poke = db.pokemons.findOne({name: "Dilmamon"})
> poke
{
  "_id" : ObjectId("5646b0335fcbd7a122583a7b"),
  "name" : "Dilmamon",
  "description" : "Pokemon presidANTA",
  "type" : "besta",
  "attack" : 1,
  "defense" : 1,
  "height" : 1.6
}
```

## Atualização do Pokemon (passo 7)

```
> poke.description = "Pokemon sem metas"
Pokemon sem metas
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> poke
{
  "_id" : ObjectId("5646b0335fcbd7a122583a7b"),
  "name" : "Dilmamon",
  "description" : "Pokemon sem metas",
  "type" : "besta",
  "attack" : 1,
  "defense" : 1,
  "height" : 1.6
}
```