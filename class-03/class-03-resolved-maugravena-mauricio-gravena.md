# MongoDB - Aula 03 - Exercício

Autor: Mauricio Gravena de Oliveira

## Listando pokemons com altura < 0.5

```
mau(mongod-2.6.11) be-mean-pokemons> var query = {heigth: {$lt: 0.5}}
mau(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565336551a2f9458cc48f477"),
  "name": "Eevee",
  "description": "Eevee tem uma composição genética instável que de repente se transforma devido ao ambiente em que vive.",
  "type": "normal",
  "attack": 33,
  "heigth": 0.3,
  "defense": 39
}
{
  "_id": ObjectId("565336551a2f9458cc48f479"),
  "name": "Cubone",
  "description": "Vendo a semelhança de sua mãe na lua cheia, ele chora.",
  "type": "ground",
  "attack": 43,
  "heigth": 0.4,
  "defense": 47
}
{
  "_id": ObjectId("565336551a2f9458cc48f47d"),
  "name": "Meowth",
  "description": "este Pokémon ama moedas brilhantes que brilham com a luz.",
  "type": "normal",
  "attack": 43,
  "heigth": 0.4,
  "defense": 41
}
Fetched 3 record(s) in 1ms
```

## Listando pokemons com altura >= 0.5

```

mau(mongod-2.6.11) be-mean-pokemons> var query = {heigth: {$gte: 0.5}}
mau(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565336551a2f9458cc48f475"),
  "name": "Chimchar",
  "description": "Macaco de fogo",
  "type": "fogo",
  "attack": 45,
  "heigth": 0.5,
  "defense": 47
}
{
  "_id": ObjectId("565336551a2f9458cc48f476"),
  "name": "Shinx",
  "description": "Ele brilha quando está em dificuldades.",
  "type": "electric",
  "attack": 40,
  "heigth": 0.5,
  "defense": 41
}
{
  "_id": ObjectId("565336551a2f9458cc48f478"),
  "name": "Aipom",
  "description": "Utiliza sua calda como principal arma.",
  "type": "normal",
  "attack": 39,
  "heigth": 0.8,
  "defense": 38
}
{
  "_id": ObjectId("565336551a2f9458cc48f47a"),
  "name": "Drowzee",
  "description": "Comedor de sonhos.",
  "type": "psychic",
  "attack": 46,
  "heigth": 1,
  "defense": 50
}
{
  "_id": ObjectId("565336551a2f9458cc48f47b"),
  "name": "Gastly",
  "description": "Gastly é em grande parte é composto de matéria gasosa.",
  "type": "ghost, poison",
  "attack": 50,
  "heigth": 1.3,
  "defense": 51
}
{
  "_id": ObjectId("565336551a2f9458cc48f47c"),
  "name": "Charmander",
  "description": "A chama que arde na ponta de sua cauda é uma indicação de suas emoções.",
  "type": "fire",
  "attack": 46,
  "heigth": 0.6,
  "defense": 44
}
{
  "_id": ObjectId("565336551a2f9458cc48f47e"),
  "name": "Mankey",
  "description": "é impossível para qualquer um de fugir a sua ira.",
  "type": "fighting",
  "attack": 48,
  "heigth": 0.5,
  "defense": 45
}
Fetched 7 record(s) in 5ms
```

## Listando pokemons com a altura <= 0.5 E tipo grama

```
mau(mongod-2.6.11) be-mean-pokemons> var query1 = {heigth: {$lte: 0.5}}
mau(mongod-2.6.11) be-mean-pokemons> var query2 = {type: "grass"}
mau(mongod-2.6.11) be-mean-pokemons> db.pokemons.find({$and: [query1, query2]})
Fetched 0 record(s) in 0ms
```

## Listando pokemon com o nome pikachu OU com heigth

```
mau(mongod-2.6.11) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {heigth: {$lte: 0.5}}]}
mau(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565336551a2f9458cc48f475"),
  "name": "Chimchar",
  "description": "Macaco de fogo",
  "type": "fogo",
  "attack": 45,
  "heigth": 0.5,
  "defense": 47
}
{
  "_id": ObjectId("565336551a2f9458cc48f476"),
  "name": "Shinx",
  "description": "Ele brilha quando está em dificuldades.",
  "type": "electric",
  "attack": 40,
  "heigth": 0.5,
  "defense": 41
}
{
  "_id": ObjectId("565336551a2f9458cc48f477"),
  "name": "Eevee",
  "description": "Eevee tem uma composição genética instável que de repente se transforma devido ao ambiente em que vive.",
  "type": "normal",
  "attack": 33,
  "heigth": 0.3,
  "defense": 39
}
{
  "_id": ObjectId("565336551a2f9458cc48f479"),
  "name": "Cubone",
  "description": "Vendo a semelhança de sua mãe na lua cheia, ele chora.",
  "type": "ground",
  "attack": 43,
  "heigth": 0.4,
  "defense": 47
}
{
  "_id": ObjectId("565336551a2f9458cc48f47d"),
  "name": "Meowth",
  "description": "este Pokémon ama moedas brilhantes que brilham com a luz.",
  "type": "normal",
  "attack": 43,
  "heigth": 0.4,
  "defense": 41
}
{
  "_id": ObjectId("565336551a2f9458cc48f47e"),
  "name": "Mankey",
  "description": "é impossível para qualquer um de fugir a sua ira.",
  "type": "fighting",
  "attack": 48,
  "heigth": 0.5,
  "defense": 45
}
Fetched 6 record(s) in 5ms
```

## Listando pokemons com attack >= 48 E heigth <= 0.5

```
mau(mongod-2.6.11) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {heigth: {$lte: 0.5}}]}
mau(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565336551a2f9458cc48f47e"),
  "name": "Mankey",
  "description": "é impossível para qualquer um de fugir a sua ira.",
  "type": "fighting",
  "attack": 48,
  "heigth": 0.5,
  "defense": 45
}
Fetched 1 record(s) in 1ms
```
