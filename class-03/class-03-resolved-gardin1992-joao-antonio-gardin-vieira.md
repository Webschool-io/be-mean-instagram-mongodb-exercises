# MongoDB - Aula 03 - Exercício
autor: **Joao Antonio Gardin Vieira"

## Liste todos os Pokemons com a altura **menor que** 0.5

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {height: {$lt: 0.5}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b96ff113858fed541cda5b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defese": 30
}
{
  "_id": ObjectId("56b972bb9c6d5acc1f92e9d9"),
  "name": "Caterpie",
  "description": "Larva lutadore",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defese": 35
}
{
  "_id": ObjectId("56b9702813858fed541cda5c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defese": 35
}
{
  "_id": ObjectId("56b97c7c4f203473d0d38d41"),
  "name": "Weedle",
  "description": "Este pokemon possui o poder de sexto sentido",
  "type": "bug",
  "attack": 35,
  "height": 0.3,
  "defese": 30
}
{
  "_id": ObjectId("56b97c834f203473d0d38d42"),
  "name": "pidgey",
  "description": "Pokemon voador com geolocalizador",
  "type": "flying",
  "attack": 45,
  "height": 0.3,
  "defese": 40
}
{
  "_id": ObjectId("56b97c914f203473d0d38d44"),
  "name": "Spearow",
  "description": "Spearow tem um grito muito alto que pode ser ouvido mais de meia milha de distância",
  "type": "flying",
  "attack": 60,
  "height": 0.3,
  "defese": 30
}
{
  "_id": ObjectId("56b97c8a4f203473d0d38d43"),
  "name": "Rattata",
  "description": "Pokemon comedor de queijo",
  "type": "normal",
  "attack": 56,
  "height": 0.3,
  "defese": 35
}
{
  "_id": ObjectId("56b97cac4f203473d0d38d48"),
  "name": "Meowth",
  "description": "este Pokémon ama moedas brilhantes que brilham com a luz.",
  "type": "normal",
  "attack": 45,
  "height": 0.4,
  "defese": 35
}
Fetched 8 record(s) in 3ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b9706c13858fed541cda5e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinhoo não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56b9704813858fed541cda5d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defese": 40
}
{
  "_id": ObjectId("56b97c974f203473d0d38d45"),
  "name": "Ekans",
  "description": "Ekans enrola-se em uma espiral enquanto descansa",
  "type": "snake",
  "attack": 60,
  "height": 2,
  "defese": 44
}
{
  "_id": ObjectId("56b97c9d4f203473d0d38d46"),
  "name": "vulpix",
  "description": "Na época de seu nascimento, Vulpix tem uma cauda branca.",
  "type": "fire",
  "attack": 40,
  "height": 0.6,
  "defese": 41
}
{
  "_id": ObjectId("56b97ca54f203473d0d38d47"),
  "name": "Venonat",
  "description": "Venonat é dito ter evoluído com um casaco de cabelo fino",
  "type": "poison",
  "attack": 55,
  "height": 1,
  "defese": 50
}
{
  "_id": ObjectId("56b97cb44f203473d0d38d49"),
  "name": "Mankey",
  "description": "Esse pokemon foi editado para sevir o exercicio",
  "type": "figthing",
  "attack": 80,
  "height": 0.5,
  "defese": 40
}
Fetched 6 record(s) in 5ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b9706c13858fed541cda5e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinhoo não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56b9704813858fed541cda5d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defese": 40
}
{
  "_id": ObjectId("56b97c974f203473d0d38d45"),
  "name": "Ekans",
  "description": "Ekans enrola-se em uma espiral enquanto descansa",
  "type": "snake",
  "attack": 60,
  "height": 2,
  "defese": 44
}
{
  "_id": ObjectId("56b97c9d4f203473d0d38d46"),
  "name": "vulpix",
  "description": "Na época de seu nascimento, Vulpix tem uma cauda branca.",
  "type": "fire",
  "attack": 40,
  "height": 0.6,
  "defese": 41
}
{
  "_id": ObjectId("56b97ca54f203473d0d38d47"),
  "name": "Venonat",
  "description": "Venonat é dito ter evoluído com um casaco de cabelo fino",
  "type": "poison",
  "attack": 55,
  "height": 1,
  "defese": 50
}
{
  "_id": ObjectId("56b97cb44f203473d0d38d49"),
  "name": "Mankey",
  "description": "Esse pokemon foi editado para sevir o exercicio",
  "type": "figthing",
  "attack": 80,
  "height": 0.5,
  "defese": 40
}
Fetched 6 record(s) in 6ms
Tto(mongod-3.2.1) be-mean-pokemons> 
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b9702813858fed541cda5c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defese": 35
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {height: {$gte: 0.5}}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b9706c13858fed541cda5e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinhoo não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56b9704813858fed541cda5d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "defese": 40
}
{
  "_id": ObjectId("56b97c974f203473d0d38d45"),
  "name": "Ekans",
  "description": "Ekans enrola-se em uma espiral enquanto descansa",
  "type": "snake",
  "attack": 60,
  "height": 2,
  "defese": 44
}
{
  "_id": ObjectId("56b97c9d4f203473d0d38d46"),
  "name": "vulpix",
  "description": "Na época de seu nascimento, Vulpix tem uma cauda branca.",
  "type": "fire",
  "attack": 40,
  "height": 0.6,
  "defese": 41
}
{
  "_id": ObjectId("56b97ca54f203473d0d38d47"),
  "name": "Venonat",
  "description": "Venonat é dito ter evoluído com um casaco de cabelo fino",
  "type": "poison",
  "attack": 55,
  "height": 1,
  "defese": 50
}
{
  "_id": ObjectId("56b97cb44f203473d0d38d49"),
  "name": "Mankey",
  "description": "Esse pokemon foi editado para sevir o exercicio",
  "type": "figthing",
  "attack": 80,
  "height": 0.5,
  "defese": 40
}
Fetched 6 record(s) in 6ms
Tto(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
Tto(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b9702813858fed541cda5c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defese": 35
}
Fetched 1 record(s) in 1ms
Tto(mongod-3.2.1) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b96ff113858fed541cda5b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defese": 30
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
Tto(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
Tto(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b96ff113858fed541cda5b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "defese": 30
}
{
  "_id": ObjectId("56b9706c13858fed541cda5e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinhoo não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56b9702813858fed541cda5c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "defese": 35
}
{
  "_id": ObjectId("56b97c914f203473d0d38d44"),
  "name": "Spearow",
  "description": "Spearow tem um grito muito alto que pode ser ouvido mais de meia milha de distância",
  "type": "flying",
  "attack": 60,
  "height": 0.3,
  "defese": 30
}
{
  "_id": ObjectId("56b97c8a4f203473d0d38d43"),
  "name": "Rattata",
  "description": "Pokemon comedor de queijo",
  "type": "normal",
  "attack": 56,
  "height": 0.3,
  "defese": 35
}
{
  "_id": ObjectId("56b97cb44f203473d0d38d49"),
  "name": "Mankey",
  "description": "Esse pokemon foi editado para sevir o exercicio",
  "type": "figthing",
  "attack": 80,
  "height": 0.5,
  "defese": 40
}
Fetched 6 record(s) in 5ms
```

