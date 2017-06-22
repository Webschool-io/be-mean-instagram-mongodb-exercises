# MongoDB - Aula 02 - Exercício
autor: Mike Job Santos Pereira da Silva

## Listando pokémons com altura menor que 0.5 (passo 1)
```
var query = { height: { $lt: 0.5 } }
db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listando pokémons com altura maior ou igual a 0.5 (passo 2)
```
query = { height: { $gte: 0.5 } }
db.pokemons.find(query)
{
  "_id": ObjectId("56456541b58d169ca247d57d"),
  "name": "Ekans",
  "description": "Impossível não lembrar de Equipe Rocket!",
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
Fetched 4 record(s) in 2ms
```

## Listando as pokémons com altura menor ou igual a 0.5 e do tipo grama (passo 3)
```
query = { $and: [{height: { $lte: 0.5 }}, { type: "grama" }] }
db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Listando pokémons com o nome Pikachu ou com attack menor ou igual a 0.5 (passo 4)
```
query = { $or: [{ name: "Pikachu" }, { attack: { $lte: 0.5 } }] }
db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listando os pokémons com attack maior ou igual a 48 e com height menor que 0.5 (passo 5)
```
query = { $and: [{ attack: { $gte: 48 } }, { height: { $lte: 0.5 } }] }
db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```
