# MongoDb - Aula 02 - Exercício
Autor: Thiago Santos de Amorim

## Criar database chamada be-mean-pokemons

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem de todas dbs

```
show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
be-mean-teste     → 0.000GB
local             → 0.000GB
```
  
## Listagem de todas as collections

```
show collections
    
## Criar cinco pokemons

```
db.pokemons.insert({name:'Butterfree', description: 'Search honey from flowers.', attack: 200, defense:200, height:1.1})

db.pokemons.insert({name:'Farfetch', description: 'Seen with a stalk from a plant of some sort.', attack: 300, defense:300, height:0.8})

db.pokemons.insert({name:'Persian', description:'Gato crazy',type: 'electric', attack: 55, height: 0.4 })

db.pokemons.insert({name:'Snorlax',description:'Sleeping',attack:6,defense: 3,height: 2.1})

db.pokemons.insert({name:'Meowth', description:'Scratch Cat', attack: 2, defense: 2, height: 0.4 })
```

## Listar todos os pokemons

```
db.pokemons.find()
{
  "_id": ObjectId("56c85eba98c479d4a18d6a5e"),
  "name": "Butterfree",
  "description": "Search honey from flowers.",
  "attack": 200,
  "defense": 200,
  "height": 1.1
}
{
  "_id": ObjectId("56c85ec098c479d4a18d6a5f"),
  "name": "Farfetch",
  "description": "Seen with a stalk from a plant of some sort.",
  "attack": 300,
  "defense": 300,
  "height": 0.8
}
{
  "_id": ObjectId("56c85ec798c479d4a18d6a60"),
  "name": "Persian",
  "description": "Gato crazy",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56c85ecd98c479d4a18d6a61"),
  "name": "Snorlax",
  "description": "Sleeping",
  "attack": 6,
  "defense": 3,
  "height": 2.1
}
{
  "_id": ObjectId("56c85ee698c479d4a18d6a62"),
  "name": "Meowth",
  "description": "Scratch Cat",
  "attack": 2,
  "defense": 2,
  "height": 0.4
}
```
  
## Buscar um pokemon

```
linux-atsn(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne({name: 'Persian'})
linux-atsn(mongod-3.2.1) be-mean-pokemons> poke
{
  "_id": ObjectId("56c85ec798c479d4a18d6a60"),
  "name": "Persian",
  "description": "Gato crazy",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
```
   
## Editar a description do pokemon escolhido

```
linux-atsn(mongod-3.2.1) be-mean-pokemons> poke.description = "Gato louco"
Gato louco
linux-atsn(mongod-3.2.1) be-mean-pokemons> poke
{
  "_id": ObjectId("56c85ec798c479d4a18d6a60"),
  "name": "Persian",
  "description": "Gato louco",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
linux-atsn(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke);
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
