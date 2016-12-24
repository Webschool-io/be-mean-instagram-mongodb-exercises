# MongoDB - Aula 02 - Exercício
autor: Pedro Germano

## Criando database be-mean-pokemons
```
pedro@pedro:~$ mongo be-mean-instagram
MongoDB shell version: 3.0.12
connecting to: be-mean-instagram
Mongo-Hacker 0.0.13
Server has startup warnings:
2016-08-25T17:01:29.115-0300 I CONTROL  
2016-08-25T17:01:29.115-0300 I CONTROL   
2016-08-25T17:01:29.115-0300 I CONTROL  
2016-08-25T17:01:29.115-0300 I CONTROL  
2016-08-25T17:01:29.115-0300 I CONTROL  
2016-08-25T17:01:29.115-0300 I CONTROL  
2016-08-25T17:01:29.115-0300 I CONTROL  
2016-08-25T17:01:29.115-0300 I CONTROL  
2016-08-25T17:01:29.115-0300 I CONTROL  
pedro(mongod-3.0.12) be-mean-instagram>

```

## Listando as databases
```
pedro(mongod-3.0.12) be-mean-instagram> show dbs
be-mean         → 0.078GB
be-mean-pokemon → 0.078GB
local           → 0.078GB
pedro(mongod-3.0.12) be-mean-instagram>

```

## Listando as coleções
```
pedro(mongod-3.0.12) be-mean-instagram> show collections
pokemons       → 0.000MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
pedro(mongod-3.0.12) be-mean-instagram>

```

## Inserindo os pokemons
```
pedro(mongod-3.0.12) be-mean-instagram> var pokemon = {"name" : "Pidgey", "description" : "Pássaro", "attack" : 2, "defense" : 2, "height" : 0.3 }
pedro(mongod-3.0.12) be-mean-instagram> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 490ms
WriteResult({
  "nInserted": 1
})

pedro(mongod-3.0.12) be-mean-instagram> var pokemon1 = {'name':'Machamp','description':'Seus quatro braços musculosos vão bater e socar','type': 'Pokèmon Força', attack: 130, height: 1.6}
pedro(mongod-3.0.12) be-mean-instagram> db.pokemons.insert(pokemon1)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
pedro(mongod-3.0.12) be-mean-instagram> var pokemon2 = {'name':'Zubat','description':'Nao precisa de olhos porque pode emitir uma onda ultra sonica','type': 'Bat Pokèmon', attack: 45, height: 0.8}
pedro(mongod-3.0.12) be-mean-instagram> db.pokemons.insert(pokemon2)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
pedro(mongod-3.0.12) be-mean-instagram> var pokemon3 = {'name':'Nidoran','description':'uma gota de veneno pode ser fatal','type': 'Poison Pin Pokèmon', attack: 47, height: 0.4}
pedro(mongod-3.0.12) be-mean-instagram> db.pokemons.insert(pokemon3)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
pedro(mongod-3.0.12) be-mean-instagram> var pokemon4 = {name: "Venusaur", description: "There is a large flower on Venusaur's back", attack: 4, defense: 4, height: 6.07}
pedro(mongod-3.0.12) be-mean-instagram> db.pokemons.insert(pokemon4)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
pedro(mongod-3.0.12) be-mean-instagram> var pokemon5 = {name: "Charmander", description: "The flame that burns at the tip of its tail is an indication of its emotions", attack: 3, defense: 2, height: 2.00}
pedro(mongod-3.0.12) be-mean-instagram> db.pokemons.insert(pokemon5)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

```

## Listando os pokemons
```
pedro(mongod-3.0.12) be-mean-instagram> db.pokemons.find()
{
  "_id": ObjectId("57bf4fa55832015b2bad5fdd"),
  "name": "Pidgey",
  "description": "Pássaro",
  "attack": 2,
  "defense": 2,
  "height": 0.3
}
{
  "_id": ObjectId("57bf512a5832015b2bad5fde"),
  "name": "Machamp",
  "description": "Seus quatro braços musculosos vão bater e socar",
  "type": "Pokèmon Força",
  "attack": 130,
  "height": 1.6
}
{
  "_id": ObjectId("57bf51485832015b2bad5fdf"),
  "name": "Zubat",
  "description": "Nao precisa de olhos porque pode emitir uma onda ultra sonica",
  "type": "Bat Pokèmon",
  "attack": 45,
  "height": 0.8
}
{
  "_id": ObjectId("57bf516b5832015b2bad5fe0"),
  "name": "Nidoran",
  "description": "uma gota de veneno pode ser fatal",
  "type": "Poison Pin Pokèmon",
  "attack": 47,
  "height": 0.4
}
{
  "_id": ObjectId("57bf51c75832015b2bad5fe1"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "attack": 4,
  "defense": 4,
  "height": 6.07
}
{
  "_id": ObjectId("57bf51ee5832015b2bad5fe2"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "attack": 3,
  "defense": 2,
  "height": 2
}
Fetched 6 record(s) in 2ms
pedro(mongod-3.0.12) be-mean-instagram>

```

## Buscando o 'Charmander' para a variável poke
```
pedro(mongod-3.0.12) be-mean-instagram> var query = {name: "Charmander"}
pedro(mongod-3.0.12) be-mean-instagram> var poke = db.pokemons.findOne(query)
pedro(mongod-3.0.12) be-mean-instagram> poke
{
  "_id": ObjectId("57bf51ee5832015b2bad5fe2"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "attack": 3,
  "defense": 2,
  "height": 2
}
pedro(mongod-3.0.12) be-mean-instagram>

```

## Modificando a description e salvando
```
 poke.description = "Charmander pokemon de fogo"


pedro(mongod-3.0.12) be-mean-instagram> db.pokemons.save(poke)
Updated 1 existing record(s) in 43ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```
