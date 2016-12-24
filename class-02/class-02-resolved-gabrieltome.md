# MongoDB - Aula 02 - Exercício
autor: **Gabriel Tomé**


##Criação da database (passo 1) 

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) test> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
admin             → (empty)
be-mean-pokemons  → (empty) 

```

## Listagem das coleções (passo 3)

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> show collections
pokemons       → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
```

## Cadastro dos pokemons (passo 4)

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var pokemons = [{'name': 'Magikarp', 'description':'Pokemon doidão', 'type': 'Água', 'attack':10, 'defense':10, 'height':0.5}, {'name':'Togepi','description': 'O mais bonitinho', 'type':'Fairy', 'attack':10, 'defense':30, 'height':0.3}, {'name': 'Butterfree', 'description':'Brabuleta endiabrada', 'type':'inseto/fly', 'attack':20, 'defense':20, 'height':1.1}, {'name':'Mewtwo', 'description':'Esse é fodão!', 'type':'psicoloco', 'attack':100, 'defense':99, 'height':2.1}, {'name':'Mew', 'description':'gato modificado geneticamente','type':'psicoloco', 'attack':88, 'defense':99, 'height':0.4}]


MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.save(pokemons)
Inserted 1 record(s) in 1543ms
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
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56551778c6086b7b42449018"),
  "name": "Magikarp",
  "description": "Pokemon doidão",
  "type": "Água",
  "attack": 10,
  "defense": 10,
  "height": 0.5
}
{
  "_id": ObjectId("56551778c6086b7b42449019"),
  "name": "Togepi",
  "description": "O mais bonitinho",
  "type": "Fairy",
  "attack": 10,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("56551778c6086b7b4244901a"),
  "name": "Butterfree",
  "description": "Brabuleta endiabrada",
  "type": "inseto/fly",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
{
  "_id": ObjectId("56551778c6086b7b4244901b"),
  "name": "Mewtwo",
  "description": "Esse é fodão!",
  "type": "psicoloco",
  "attack": 100,
  "defense": 99,
  "height": 2.1
}
{
  "_id": ObjectId("56551778c6086b7b4244901c"),
  "name": "Mew",
  "description": "gato modificado geneticamente",
  "type": "psicoloco",
  "attack": 88,
  "defense": 99,
  "height": 0.4
}
Fetched 5 record(s) in 14ms
```


## Busca Pokemon (passo 6)

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {name:'Mew'}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var poke = db.pokemons.findOne(query)
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> poke
{
  "_id": ObjectId("56551778c6086b7b4244901c"),
  "name": "Mew",
  "description": "gato modificado geneticamente",
  "type": "psicoloco",
  "attack": 88,
  "defense": 99,
  "height": 0.4
}
```

## Atualização do Pokemon (passo 7)


```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> poke.description = "Só tem cara de bonzinho, mas bota o terror!"
Só tem cara de bonzinho, mas bota o terror!
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 431ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


```