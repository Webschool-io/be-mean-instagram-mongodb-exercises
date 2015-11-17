
# MongoDB - Aula 02 - Exercício
autor: Fernando de Albuquerque Ponte Filho

## Criar database 'be-mean-pokemons' (passo 1)

```
macsobra(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons
macsobra(mongod-3.0.7) be-mean-pokemons>
```

## Listagem das databases (passo 2)

```
macsobra(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-teste       0.078GB
local               0.078GB
sistema-mercadinho  0.078GB
be-mean-instagram   0.078GB
be-mean             0.078GB

```

## Listagem das coleções (passo 3)

```
macsobra(mongod-3.0.7) be-mean-pokemons> show collections
macsobra(mongod-3.0.7) be-mean-pokemons>
```

## Cadastro dos pokemons (passo 4)

```
macsobra(mongod-3.0.7) be-mean-pokemons> var pokemons = [{name: 'Fernandomon', description:'Pokemon Estudante Eterno', type: 'bombril', attack: 443, defense: 2222, height: 1.75}, {name: 'Brahmomon', description:'Pokemon de Pilsen fake', type: 'cerveja', attack: 5000, defense: 3000, height: 3.55}, {name: 'Skolomon', description:'Pokemon de Pilsen fake tambem', type: 'cerveja', attack: 6000, defense: 4000, height: 3.55},{name: 'Heinekenmon', description:'Pokemon Premium', type: 'cerveja', attack: 8000, defense: 5000, height: 3.55},{name: 'BadenWeissmon', description:'Pokemon de melhor custo beneficio', type: 'cerveja', attack: 9000, defense: 8000, height: 6.00}]
macsobra(mongod-3.0.7) be-mean-pokemons> pokemons
[
  {
    "name": "Fernandomon",
    "description": "Pokemon Estudante Eterno",
    "type": "bombril",
    "attack": 443,
    "defense": 2222,
    "height": 1.75
  },
  {
    "name": "Brahmomon",
    "description": "Pokemon de Pilsen fake",
    "type": "cerveja",
    "attack": 5000,
    "defense": 3000,
    "height": 3.55
  },
  {
    "name": "Skolomon",
    "description": "Pokemon de Pilsen fake tambem",
    "type": "cerveja",
    "attack": 6000,
    "defense": 4000,
    "height": 3.55
  },
  {
    "name": "Heinekenmon",
    "description": "Pokemon Premium",
    "type": "cerveja",
    "attack": 8000,
    "defense": 5000,
    "height": 3.55
  },
  {
    "name": "BadenWeissmon",
    "description": "Pokemon de melhor custo beneficio",
    "type": "cerveja",
    "attack": 9000,
    "defense": 8000,
    "height": 6
  }
]

macsobra(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 493ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Lista dos pokemons (passo 5)

```
macsobra(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564b89c7ce0395086dc46c74"),
  "name": "Fernandomon",
  "description": "Pokemon Estudante Eterno",
  "type": "bombril",
  "attack": 443,
  "defense": 2222,
  "height": 1.75
}
{
  "_id": ObjectId("564b89c7ce0395086dc46c75"),
  "name": "Brahmomon",
  "description": "Pokemon de Pilsen fake",
  "type": "cerveja",
  "attack": 5000,
  "defense": 3000,
  "height": 3.55
}
{
  "_id": ObjectId("564b89c7ce0395086dc46c76"),
  "name": "Skolomon",
  "description": "Pokemon de Pilsen fake tambem",
  "type": "cerveja",
  "attack": 6000,
  "defense": 4000,
  "height": 3.55
}
{
  "_id": ObjectId("564b89c7ce0395086dc46c77"),
  "name": "Heinekenmon",
  "description": "Pokemon Premium",
  "type": "cerveja",
  "attack": 8000,
  "defense": 5000,
  "height": 3.55
}
{
  "_id": ObjectId("564b89c7ce0395086dc46c78"),
  "name": "BadenWeissmon",
  "description": "Pokemon de melhor custo beneficio",
  "type": "cerveja",
  "attack": 9000,
  "defense": 8000,
  "height": 6
}
Fetched 5 record(s) in 5ms

```

## Pokemon (passo 6)

```
macsobra(mongod-3.0.7) be-mean-pokemons> var query = {"name": "Heinekenmon"}
macsobra(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
macsobra(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564b89c7ce0395086dc46c77"),
  "name": "Heinekenmon",
  "description": "Pokemon Premium",
  "type": "cerveja",
  "attack": 8000,
  "defense": 5000,
  "height": 3.55
}
```

## Atualização do Pokemon (passo 7)

```
macsobra(mongod-3.0.7) be-mean-pokemons> poke.description
Pokemon Premium
macsobra(mongod-3.0.7) be-mean-pokemons> poke.description = "Pokemon Premium/Verdinho"
Pokemon Premium/Verdinho
macsobra(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
macsobra(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("564b89c7ce0395086dc46c77"),
  "name": "Heinekenmon",
  "description": "Pokemon Premium/Verdinho",
  "type": "cerveja",
  "attack": 8000,
  "defense": 5000,
  "height": 3.55
}
```
