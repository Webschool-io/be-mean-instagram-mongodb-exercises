# MongoDB - Aula 02 - Exercício
autor: Adejair Júnior

## Listagem das databases
```
show databases 

adejair(mongod-2.4.9) be-mean-pokemons> show databases
be-mean-pokemons  → 0.203GB
be-mean-instagram → 0.203GB
test              → 0.203GB
local             → 0.078GB
```

## Listagem das coleções :notebook_with_decorative_cover:
```
show collections
```

## Cadastro dos pokemons :pencil2:
``` JavaScript
var registerPokemon = [
	{name: "Charizard", description: "Fire", attack: 84, defense: 78, heigth: 1.70},
	{name: "Butterfree", description: "Flying", attack: 45, defense: 50, heigth: 1.09},
	{name: "Pidgeot", description: "Flying", attack: 80, defense: 75, heigth: 1.50},
	{name: "Rattatá", description: "Normal", attack: 56, defense: 35, heigth: 0.30},
	{name: "Raticate", description: "Normal", attack: 81, defense: 60, heigth: 0.71}
]
```
```
db.pokemons.insert(registerPokemon)
adejair(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert(registerPokemon)
Inserted 1 record(s) in 93ms
```

## Lista dos pokemons :page_facing_up:
``` JavaScript
db.pokemons.find()

adejair(mongod-2.4.9) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5644f0f9ad609303b2baf806"),
  "name": "Charizard",
  "description": "Fire",
  "attack": 84,
  "defense": 78,
  "heigth": 1.7
}
{
  "_id": ObjectId("5644f0f9ad609303b2baf807"),
  "name": "Butterfree",
  "description": "Flying",
  "attack": 45,
  "defense": 50,
  "heigth": 1.09
}
{
  "_id": ObjectId("5644f0f9ad609303b2baf808"),
  "name": "Pidgeot",
  "description": "Flying",
  "attack": 80,
  "defense": 75,
  "heigth": 1.5
}
{
  "_id": ObjectId("5644f0f9ad609303b2baf809"),
  "name": "Rattatá",
  "description": "Normal",
  "attack": 56,
  "defense": 35,
  "heigth": 0.3
}
{
  "_id": ObjectId("5644f0f9ad609303b2baf80a"),
  "name": "Raticate",
  "description": "Normal",
  "attack": 81,
  "defense": 60,
  "heigth": 0.71
}
Fetched 5 record(s) in 6ms

```

## Procurando pelo pokemon "Butterfree" :mag_right:
``` JavaScript
var poke = db.pokemons.findOne({name: "Butterfree"})
```

## Atualização da propiedade :rocket:
``` JavaScript
poke.description = "Alterado"
Alterado

```

## Salvando a propiedade :cloud:

``` JavaScript
db.pokemons.save(poke)
adejair(mongod-2.4.9) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 0ms
```
