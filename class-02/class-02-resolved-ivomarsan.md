# MongoDB - Aula 02 - Exercício
autor: Ivomar

## Listagem das databases (passo 2)

```
$ mongo be-mean-pokemons
MongoDB shell version: 3.0.5
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.8
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> show dbs
local   →  0.078GB
test    →  0.078GB
be-mean →  0.078GB
wiki    → 15.946GB
```

## Listagem das coleções (passo 3)

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> show collections

```

## Cadastro dos pokemons (passo 4)

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> var pokemon = {'name':'Pikachu','description':'Rato elétrico bem fofinho','type': 'electric', attack: 55, height: 0.4, defense: 40 }
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> var pokemon = {'name':'Squirtle','description':'Ejeta água que passarinho não bebe','type': 'água', 'attack': 48, height: 0.5, defense: 65 }
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> var pokemon = {'name':'Charmander','description':'Esse é o cão chupando manga de fofinho','type': 'fogo', 'attack': 52, height: 0.6, defense: 43 }
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> var pokemon = {'name':'Bulbassauro','description':'Chicote de trepadeira','type': 'grama', 'attack': 49, height: 0.4, defense: 63 }
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> var pokemon = {'name':'Bulbassauro','description':'Irmão mais velho do Bulba','type': 'grama', 'attack': 62, height: 1, defense: 63 }
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> var pokemon = {'name':'Venusaur','description':'Bulba super evoluído','type': 'grama', 'attack': 82, height: 2, defense: 83 }
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

## Lista dos pokemons (passo 5)

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56496157cbe279f611d7abe0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56496187cbe279f611d7abe1"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5649619bcbe279f611d7abe2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564961b6cbe279f611d7abe3"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564963d1cbe279f611d7abe4"),
  "name": "Bulbassauro",
  "description": "Irmão mais velho do Bulba",
  "type": "grama",
  "attack": 62,
  "height": 1
}
{
  "_id": ObjectId("564963edcbe279f611d7abe5"),
  "name": "Venusaur",
  "description": "Bulba super evoluído",
  "type": "grama",
  "attack": 82,
  "height": 2
}
Fetched 6 record(s) in 4ms
```

## Pikachu (passo 6)

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> var poke = db.pokemons.findOne({name: /pikachu/i})
```

## Atualização do Pikachu (passo 7)

```
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> poke.description = 'Nunca evolui esse FDP'
ASUS-K46CB(mongod-3.0.5) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
