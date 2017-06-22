# MongoDB - Aula 03 - Exercício
autor: Cleyton Antonio dos Santos

## Listando Pokemons com altura menor que 0.5 (Passo 1)
```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)

{
  "_id": ObjectId("57643a3ad7ba6d657212bc45"),
  "name": "Pidgey",
  "description": "Pidgey tem um extremo senso de direção",
  "type": "voador",
  "attack": 2,
  "height": 0.3
}

```
## Listando Pokemons com altura maior ou igual que 0.5 (Passo 2)

```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)

{
  "_id:" ObjectId("57643a3ad7ba6d657212bc44"),
  "name": "Metapod",
  "description": "The shell covering this Pokémon's body is as hard as an iron slab",
  "type": "inseto",
  "attack": 1,
  "height": 0.7
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc46"),
  "name": "Jigglypuff",
  "description": "Esse pokemon pode cantar",
  "type": "fada",
  "attack": 2,
  "height": 0.5
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc47"),
  "name": "Growlithe",
  "description": "Cachorro louco monstrão",
  "type": "fogo",
  "attack": 4,
  "height": 0.7
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc48"),
  "name": "Psyduck",
  "description": "Psyduck tem um poder misterioso",
  "type": "agua",
  "attack": 3,
  "height": 0.8
}
Fetched 4 record(s) in 2ms
```

## Listando Pokemons com altura menor ou igual que 0.5 E do tipo grama (ou a sua escolha) (Passo 3)
```
var query = {$and: [{height: {$lte: 0.5}}, {type: "voador"}] }
db.pokemons.find(query)


{
  "_id": ObjectId("57643a3ad7ba6d657212bc45"),
  "name": "Pidgey",
  "description": "Pidgey tem um extremo senso de direção",
  "type": "voador",
  "attack": 2,
  "height": 0.3
}
 
```
## Listando Pokemons com o name 'Pìkachu' OU com attack menor ou igual que 2 (Passo 4)
```
var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 2}}]}
db.pokemons.find(query)

{
  "_id": ObjectId("57643a3ad7ba6d657212bc44"),
  "name": "Metapod",
  "description": "The shell covering this Pokémon's body is as hard as an iron slab",
  "type": "inseto",
  "attack": 1,
  "height": 0.7
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc45"),
  "name": "Pidgey",
  "description": "Pidgey tem um extremo senso de direção",
  "type": "voador",
  "attack": 2,
  "height": 0.3
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc46"),
  "name": "Jigglypuff",
  "description": "Esse pokemon pode cantar",
  "type": "fada",
  "attack": 2,
  "height": 0.5
}
Fetched 3 record(s) in 2ms
```
## Listando Pokemons com attack maior ou igual que 2 E com altura menor ou igual que 0.5 (Passo 5)
```
var query = {$and: [{attack: {$gte: 2}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)

{
  "_id": ObjectId("57643a3ad7ba6d657212bc45"),
  "name": "Pidgey",
  "description": "Pidgey tem um extremo senso de direção",
  "type": "voador",
  "attack": 2,
  "height": 0.3
}
{
  "_id": ObjectId("57643a3ad7ba6d657212bc46"),
  "name": "Jigglypuff",
  "description": "Esse pokemon pode cantar",
  "type": "fada",
  "attack": 2,
  "height": 0.5
}
Fetched 2 record(s) in 1ms

```
