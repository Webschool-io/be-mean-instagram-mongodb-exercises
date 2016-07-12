# MongoDB - Aula 02 - Exercício
Autor: *Pablo Zaniolo*

## Crie uma database chamada be-mean-pokemons

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## 2. Liste quais databases você possui nesse servidor

```
be-mean-instagram → 0.000GB
local             → 0.000GB
```

## 3. Liste quais coleções você possui nessa database

```
show collections
```

## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA

```
var pokemon = {"name": "Charizard", "description" :"Breathing intense, hot flames, it can melt almost anything. Its breath inflicts terrible pain on enemies.", "type":"fire", "attack":84, "defense":78 }
> db.pokemons.save(pokemon)
WriteResult({ "nInserted" : 1 })
	
var pokemon = {"name":"Spearow", "description" :"Very protective of its territory, it flaps its short wings busily to dart around at high speed.", "type":"normal", "attack":60, "defense":30}
> db.pokemons.save(pokemon)
WriteResult({ "nInserted" : 1 })
	
var pokemon = {"name":"Venusaur", "description" :"Venusaur is a squat quadruped Pokémon with bumpy bluish green skin","type":"grass","attack":82,"defense":83}
> db.pokemons.save(pokemon)
WriteResult({ "nInserted" : 1 })
	
> var pokemon = {"name":"Metapod", "description" :"A steel-hard shell protects its tender body. It quietly endures hardships while awaiting evolution.s" ,"type":"bug", "attack":20,"defense":"55"}
> db.pokemons.save(pokemon)
WriteResult({ "nInserted" : 1 })
	
var pokemon = {"name":"Butterfree", "description" :"Water-repellent powder on its wings enables it to collect honey, even in the heaviest of rains.","type":"bug", "attack":45,"defense":50}
> db.pokemons.save(pokemon)
WriteResult({ "nInserted" : 1 })
```

## 5. Liste os pokemons existentes na sua coleção

```
{
  "_id": ObjectId("573c62e7373d0b218ea3f5b2"),
  "name": "Charizard",
  "description": "Breathing intense, hot flames, it can melt almost anything. Its breath inflicts terrible pain on enemies.",
  "type": "fire",
  "attack": 84,
  "defense": 78
}
{
  "_id": ObjectId("573c62fd373d0b218ea3f5b3"),
  "name": "Spearow",
  "description": "Very protective of its territory, it flaps its short wings busily to dart around at high speed.",
  "type": "normal",
  "attack": 60,
  "defense": 30
}
{
  "_id": ObjectId("573c631a373d0b218ea3f5b4"),
  "name": "Venusaur",
  "description": "Venusaur is a squat quadruped Pokémon with bumpy bluish green skin",
  "type": "grass",
  "attack": 82,
  "defense": 83
}
{
  "_id": ObjectId("573c6331373d0b218ea3f5b5"),
  "name": "Metapod",
  "description": "A steel-hard shell protects its tender body. It quietly endures hardships while awaiting evolution.s",
  "type": "bug",
  "attack": 20,
  "defense": "55"
}
{
  "_id": ObjectId("573c6343373d0b218ea3f5b6"),
  "name": "Butterfree",
  "description": "Water-repellent powder on its wings enables it to collect honey, even in the heaviest of rains.",
  "type": "bug",
  "attack": 45,
  "defense": 50
}
```

## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada 'poke'

```
var poke = {name: 'Metapod'}
db.pokemons.findOne(poke)
```

## 7. Modifique sua 'description' e salvê-o

```
var poke = {name: 'Metapod'}
var p = db.pokemons.findOne(poke)
p.description = "Alterando a descrição"
db.pokemons.save(p)
```


