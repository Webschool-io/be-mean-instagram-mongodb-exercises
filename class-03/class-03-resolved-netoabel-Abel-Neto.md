# MongoDB - Aula 03 - Exercício
User: [netoabel](http://www.github.com/netoabel)

Autor: Abel Neto

## Pokémons com altura menor que 0.5

```
be-mean-pokemons> var query = { height: { $lt: 0.5 } }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d05603e77fb046dc9bcd0"),
  "name": "Bulbassaur",
  "description": "Um sapo com folhas",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grass"
}
Fetched 1 record(s) in 3ms
```

## Pokémons com altura maior ou igual a 0.5

```
be-mean-pokemons> var query = { height: { $gte: 0.5 } }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d05603e77fb046dc9bcd1"),
  "name": "Ivysaur",
  "description": "Um sapo com uma bromélia",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "type": "grass"
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd2"),
  "name": "Venusaur",
  "description": "Um sapo com um coqueiro",
  "attack": 40,
  "defense": 40,
  "height": 2,
  "type": "grass"
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd3"),
  "name": "Charmander",
  "description": "Um filhote de dinossauro com o rabo pegando fogo",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire"
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd4"),
  "name": "Charmeleon",
  "description": "Um pterodáctilo sem asas com o rabo pegando fogo",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "type": "fire"
}
Fetched 4 record(s) in 5ms
```

## Pokémons com altura menor ou igual a 0.5 e do tipo grama

```
be-mean-pokemons> var query = { $and: [{ height: { $lte: 0.5 } }, { type: 'grass' }] }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d05603e77fb046dc9bcd0"),
  "name": "Bulbassaur",
  "description": "Um sapo com folhas",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grass"
}
Fetched 1 record(s) in 3ms
```

## Pokémons com nome 'Pikachu' ou com attack menor ou igual a 0.5

```
be-mean-pokemons> var query = { $or: [{ attack: { $lte: 0.5 } }, { name: 'Pikachu' }] }
be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Pokémons com nome attack maior ou igual a 48 e altura menor ou igual a 0.5

```
be-mean-pokemons> var query = { $and: [{ attack: { $gte: 48 } }, { height: { $lte: 0.5 } }] }
be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
