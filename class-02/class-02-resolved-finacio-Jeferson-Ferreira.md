# MongoDB - Aula 02 - Exercício

Autor: Jeferson Ferreira

## Listagem das databases (passo 2)

```shell
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-teste> use be-mean-pokemons

switched to db be-mean-pokemons

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> show dbs

be-mean       → 0.004GB
be-mean-teste → 0.000GB
crunchbase    → 0.034GB
local         → 0.000GB
```
## Listagem das coleções (passo 3)

```
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> show collections

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> 
```
## Cadastro dos pokemons (passo 4)
```
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var primeape = {'name':'primeape','description':'When Primeape becomes furious, its blood circulation is boosted','type':'fighting', 'attack':'105','height':'10'}

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.insert(primeape)
Inserted 1 record(s) in 504ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> show collections
pokemons → 0.000MB / 0.004MB

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var ninetales = {'name':'ninetales','description':'This Pokémon is said to live for a thousand years.','type':'fire','attack':'76','height':'11'}
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.insert(ninetales)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var blastoise = {'name':'Blastoise','description':'Blastoise has water spouts that protrude from its shell','type':'water','attack':'83','height':'16'}

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.insert(blastoise)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var charizard = {'name':'Charizard','description':'It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself','type':'flying','attack':'84','height':'17'}

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.insert(charizard)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var squirtle = {'name':'Squirtle','description':'Ejeta água que passarinho não bebe','type': 'água', 'attack': 48, height: 0.5 }

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.insert(squirtle)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var charmander = {'name':'Charmander','description':'Esse é o cão chupando manga de fofinho','type': 'fogo', 'attack': 52, height: 0.6 }

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.insert(charmander)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var bulbassauro = {'name':'Bulbassauro','description':'Chicote de trepadeira','type': 'grama', 'attack': 49, height: 0.4 }

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.insert(bulbassauro)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var pokemon = {'name':'Pikachu','description':'Rato elétrico bem fofinho', 'type':'eletric', attack:55, height:0.4}

MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```
## Lista dos pokemons (passo 5)
```
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56dc2d3579e3f37dd50de6a6"),
  "name": "primeape",
  "description": "When Primeape becomes furious, its blood circulation is boosted",
  "type": "fighting",
  "attack": "105",
  "height": "10"
}
{
  "_id": ObjectId("56dc2d6079e3f37dd50de6a7"),
  "name": "ninetales",
  "description": "This Pokémon is said to live for a thousand years.",
  "type": "fire",
  "attack": "76",
  "height": "11"
}
{
  "_id": ObjectId("56dc2d7979e3f37dd50de6a8"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "water",
  "attack": "83",
  "height": "16"
}
{
  "_id": ObjectId("56dc2d9679e3f37dd50de6a9"),
  "name": "Charizard",
  "description": "It breathes fire of such great heat that it melts anything. However, it never turns its fiery breath on any opponent weaker than itself",
  "type": "flying",
  "attack": "84",
  "height": "17"
}
{
  "_id": ObjectId("56dc2db579e3f37dd50de6aa"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56dc2dc779e3f37dd50de6ab"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56dc2ddf79e3f37dd50de6ac"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56dc2df679e3f37dd50de6ad"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 9 record(s) in 6ms
```
## Pokemons (passo 6)
```
var queryBusca = {'name':'Bulbassauro'}
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> var poke = db.pokemons.findOne(queryBusca)
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> poke
{
  "_id": ObjectId("56dc2ddf79e3f37dd50de6ac"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
```
## Atualização do Pokemon (Passo 7)
```
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> poke.description
Chicote de trepadeira
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> poke.description = "Chicote de trepadeira/Jeferson"
Chicote de trepadeira/Jeferson
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
MacBook-Pro-de-finacio(mongod-3.3.1) be-mean-pokemons> db.pokemons.findOne(queryBusca)
{
  "_id": ObjectId("56dc2ddf79e3f37dd50de6ac"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira/Jeferson",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
``