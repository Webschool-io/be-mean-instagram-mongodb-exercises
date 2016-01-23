# MongoDB - Aula 03 - Exercício
	autor: Alan Siqueira

## Selecionando o banco be-mean-pokemons criado na aula 02 (passo 1)
```
DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> use pokemons
switched to db pokemons
```

## Listagem de todos os Pokemons com a altura menor que 0.5 (passo 2)

```
DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> var query = {height: {$lt: 0.5}}
DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("567b40ed4527a432ae8ac232"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("567b42024527a432ae8ac234"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("567b43294527a432ae8ac237"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 13ms
```

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5 (passo 3)

```
DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> var query = {height: {$gte: 0.5}}
DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("567b41654527a432ae8ac233"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("567b42344527a432ae8ac235"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 8ms

## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 4)

DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> var query = {$and: [{type:'grama'},{height: {$lte: 0.5}}]}
DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("567b42024527a432ae8ac234"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 4ms

## Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5 (passo 5)

DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> var query = {$or: [{name:'Pikachu'},{attack: {$lte: 0.5}}]}
DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("567b40ed4527a432ae8ac232"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 4ms

## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 6)

DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> var query = {$and: [{attack: {$gte: 48} },{height: {$lte: 0.5}}]}
DESKTOP-JV9Q1A8(mongodb\bin\mongod.exe-3.0.4) pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("567b40ed4527a432ae8ac232"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("567b42024527a432ae8ac234"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("567b42344527a432ae8ac235"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 13ms
```