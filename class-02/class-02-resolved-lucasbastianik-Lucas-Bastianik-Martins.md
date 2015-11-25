# MongoDB - Aula 02 - Exercício
autor: Lucas Bastianik

## Listagem das databases 
```
mbp-lucasbastianik(mongod-3.0.7) test> show databases
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
```

## Listagem das coleções 
```
mbp-lucasbastianik(mongod-3.0.7) be-mean> show collections
restaurantes   → 14.012MB / 21.465MB
system.indexes →  0.000MB /  0.008MB
```

## Cadastro dos pokemons 
```
var pokemons = [
	{name: "Charizard", description: "Fire", attack: 84, defense: 78, heigth: 1.70}, 
	{name: "Butterfree", description: "Flying", attack: 45, defense: 50, heigth: 1.09},
	{name: "Pidgeot", description: "Flying", attack: 80, defense: 75, heigth: 1.50},
	{name: "Rattatá", description: "Normal", attack: 56, defense: 35, heigth: 0.30},
	{name: "Raticate", description: "Normal", attack: 81, defense: 60, heigth: 0.71} 
]
```
```
db.pokemons.insert(pokemons)
```

## Lista dos pokemons
``` 
mbp-lucasbastianik(mongod-3.0.7) be-mean> db.pokemons.find()
{
  "_id": ObjectId("56551572a3dc1f0617393af2"),
  "name": "Charizard",
  "description": "Fire",
  "attack": 84,
  "defense": 78,
  "heigth": 1.7
}
{
  "_id": ObjectId("56551572a3dc1f0617393af3"),
  "name": "Butterfree",
  "description": "Flying",
  "attack": 45,
  "defense": 50,
  "heigth": 1.09
}
{
  "_id": ObjectId("56551572a3dc1f0617393af4"),
  "name": "Pidgeot",
  "description": "Flying",
  "attack": 80,
  "defense": 75,
  "heigth": 1.5
}
{
  "_id": ObjectId("56551572a3dc1f0617393af5"),
  "name": "Rattatá",
  "description": "Normal",
  "attack": 56,
  "defense": 35,
  "heigth": 0.3
}
{
  "_id": ObjectId("56551572a3dc1f0617393af6"),
  "name": "Raticate",
  "description": "Normal",
  "attack": 81,
  "defense": 60,
  "heigth": 0.71
}
Fetched 5 record(s) in 5ms
```

## Procurando Pokemon
``` 
mbp-lucasbastianik(mongod-3.0.7) be-mean> var poke = db.pokemons.findOne({name: "Charizard"})
```

## Atualização da propriedade
``` 
mbp-lucasbastianik(mongod-3.0.7) be-mean> poke.description = "Whatafuck is going on?"
Whatafuck is going on?
mbp-lucasbastianik(mongod-3.0.7) be-mean> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
