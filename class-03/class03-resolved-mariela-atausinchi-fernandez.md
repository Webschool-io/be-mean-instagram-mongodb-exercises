# MongoDB - Aula 03 - Exercício
autor: Mariela Atausinchi

## Listando todos os pokemons com altura menor que 0.5

```
cem-008046106(mongod-3.4.2) test> var query = {height:{$lt:0.5}}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68bd8cf14125a4c53faf4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("58c68ca6cf14125a4c53faf5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 1ms


```

## Listando todos os pokemons com altura maior ou igual que 0.5

```
cem-008046106(mongod-3.4.2) test> var query = {height:{$gte:0.5}}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68cbacf14125a4c53faf6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("58c68cd3cf14125a4c53faf7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 0ms


```

## Listando todos os pokemons com altura menor ou igual que 0.5

```
cem-008046106(mongod-3.4.2) test> var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68ca6cf14125a4c53faf5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 0ms


```

## Listando todos os pokemons com nome 'Pikachu' ou com attack menor ou igual que 0.5

```
cem-008046106(mongod-3.4.2) test> var query = {$or:[{name:'Pikachu'},{attack:{$lte:0.5}}]}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68bd8cf14125a4c53faf4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 0ms


```

## Listando todos os pokemons attack maior ou igual que 48 e com height menor ou igual que 0.5

```
cem-008046106(mongod-3.4.2) test> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
cem-008046106(mongod-3.4.2) test> db.pokemons.find(query)
{
  "_id": ObjectId("58c68bd8cf14125a4c53faf4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("58c68ca6cf14125a4c53faf5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("58c68cd3cf14125a4c53faf7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms


```
