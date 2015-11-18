# MongoDB - Aula 02 - Exercício
autor: Mike Job Santos Pereira da Silva

## Criando um database (passo 1)
```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando os databases do meu servidor (passo 2)
```
show dbs
local   → 0.078GB
be-mean → 0.203GB
test    → (empty)
```

O database be-mean-pokemons não aparece ainda porque não foi inicializado.

## Listando as coleções do meu database (passo 3)
```
show collections
```

O comando não mostra nenhuma coleção porque nenhuma foi inicializada ainda.

## Inserindo 5 pokémons (passo 4)
```
var beedrill = {name: 'Beedrill', description: 'Beedrill is extremely territorial. No one should ever approach its nest—this is for their own safety. If angered, they will attack in a furious swarm.', attack: 90, defense: 40, heigth: 1.0}
var ekans = {name: 'Ekans', description: 'Ekans curls itself up in a spiral while it rests. Assuming this position allows it to quickly respond to a threat from any direction with a glare from its upraised head.', attack: 60, defense: 44, height: 2.0}
var sandshrew = {name: 'Sandshrew', description: "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert. This Pokémon curls up to protect itself from its enemies.", attack: 75, defense: 85, height: 0.6}
var ninetales = {name: 'Ninetales', description: "Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's mind. This Pokémon is said to live for a thousand years.", attack: 76, defense: 75, height: 1.1}
var ponyta = {name: 'Ponyta', description: "Ponyta is very weak at birth. It can barely stand up. This Pokémon becomes stronger by stumbling and falling to keep up with its parent.", attack: 85, defense: 55, height: 1.0}

db.pokemons.save(beedrill)
Inserted 1 record(s) in 75ms

db.pokemons.save(ekans)
Inserted 1 record(s) in 1ms

db.pokemons.save(sandshrew)
Inserted 1 record(s) in 1ms

db.pokemons.save(ninetales)
Inserted 1 record(s) in 1ms

db.pokemons.save(ponyta)
Inserted 1 record(s) in 1ms
```

## Listando os pokémons da coleção (passo 5)
```
db.pokemons.find()
{
  "_id": ObjectId("56456539b58d169ca247d57c"),
  "name": "Beedrill",
  "description": "Beedrill is extremely territorial. No one should ever approach its nest—this is for their own safety. If angered, they will attack in a furious swarm.",
  "attack": 90,
  "defense": 40,
  "heigth": 1
}
{
  "_id": ObjectId("56456541b58d169ca247d57d"),
  "name": "Ekans",
  "description": "Ekans curls itself up in a spiral while it rests. Assuming this position allows it to quickly respond to a threat from any direction with a glare from its upraised head.",
  "attack": 60,
  "defense": 44,
  "height": 2
}
{
  "_id": ObjectId("5645654db58d169ca247d57e"),
  "name": "Sandshrew",
  "description": "Sandshrew's body is configured to absorb water without waste, enabling it to survive in an arid desert. This Pokémon curls up to protect itself from its enemies.",
  "attack": 75,
  "defense": 85,
  "height": 0.6
}
{
  "_id": ObjectId("5645655db58d169ca247d57f"),
  "name": "Ninetales",
  "description": "Ninetales casts a sinister light from its bright red eyes to gain total control over its foe's mind. This Pokémon is said to live for a thousand years.",
  "attack": 76,
  "defense": 75,
  "height": 1.1
}
{
  "_id": ObjectId("56456565b58d169ca247d580"),
  "name": "Ponyta",
  "description": "Ponyta is very weak at birth. It can barely stand up. This Pokémon becomes stronger by stumbling and falling to keep up with its parent.",
  "attack": 85,
  "defense": 55,
  "height": 1
}
Fetched 5 record(s) in 7ms
```

## Buscando um pokémon (passo 6)
```
var poke = db.pokemons.findOne({name: "Ekans"})
```

## Modificando a description e salvando (passo 7)
```
poke.description = "Impossível não lembrar de Equipe Rocket!"
Impossível não lembrar de Equipe Rocket!

db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
```
