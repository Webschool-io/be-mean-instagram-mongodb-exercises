# MongoDb - Aula 02 - Exercício
autor: Nicolas Serrato

## Importando os restaurantes

```
>use be-mean-pokemons
switched to db be-mean-pokemons
```
## Listagem das databases(passo 2)

```
> show dbs
be-mean → 0.203GB
local   → 0.078GB

```

## Listando Collections
```
show collections
```

## Cadastrando Pokemons
```
> var pokemons = [
	{name: "Charmeleon", description: "Fire", attack: 30, defense: 30, heigth: 1.1}, 
	{name: "Wartortle", description: "Water", attack: 30, defense: 40, heigth: 1.0},
	{name: "Ivysaur", description: "Grass, Poison", attack: 30, defense: 30, heigth: 1.0},
	{name: "Metapod", description: "Bug", attack: 10, defense: 30, heigth: 0.7},
	{name: "Kakuna", description: "Bug, Poison", attack: 10, defense: 20, heigth: 0.6} 
]
```
```

> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 439ms

```

## Listagem dos Pokemons
``` 
> db.pokemons.find()
{
  "_id": ObjectId("587c325b58c60dbd067167b6"),
  "name": "Charmeleon",
  "description": "Fire",
  "attack": 30,
  "defense": 30,
  "heigth": 1.1
}
{
  "_id": ObjectId("587c325b58c60dbd067167b7"),
  "name": "Wartortle",
  "description": "Water",
  "attack": 30,
  "defense": 40,
  "heigth": 1
}
{
  "_id": ObjectId("587c325b58c60dbd067167b8"),
  "name": "Ivysaur",
  "description": "Grass, Poison",
  "attack": 30,
  "defense": 30,
  "heigth": 1
}
{
  "_id": ObjectId("587c325b58c60dbd067167b9"),
  "name": "Metapod",
  "description": "Bug",
  "attack": 10,
  "defense": 30,
  "heigth": 0.7
}
{
  "_id": ObjectId("587c325b58c60dbd067167ba"),
  "name": "Kakuna",
  "description": "Bug, Poison",
  "attack": 10,
  "defense": 20,
  "heigth": 0.6
}
Fetched 5 record(s) in 23ms

```

## Procurando Pokemon Kakuna
``` 
> var poke = db.pokemons.findOne({name: "Kakuna"})
```

## Atualização da propiedade para Fight
``` 
> poke.description = "Poison"
Poison

> db.ponkemons.save(poke)
Updated 1 new record(s) in 33ms

```
