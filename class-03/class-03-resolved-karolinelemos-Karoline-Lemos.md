# MongoDB - Aula 03 - Exercício
autor: Karoline Lemos

## Pokemons altura menor que 0.5

```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("578028389af54197ee22cd15"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57802b62c9f294b0d14c8d65"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57802dc6c9f294b0d14c8d68"),
  "nome": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}

```

## Altura maior ou igual a 0.5

```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("57802bb8c9f294b0d14c8d66"),
  "name": "Charmander",
  "descriprion": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("57802bffc9f294b0d14c8d67"),
  "name": "Squirtle",
  "description": "Ejata água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5780c0eee217205feb8b00fa"),
  "name": "Poliwag",
  "description": "Bolinha hipnotizante",
  "type": "água",
  "attack": 30,
  "height": 0.6
}
{
  "_id": ObjectId("5780c180e217205feb8b00fb"),
  "name": "Clefairy",
  "description": "Fofurinha rosa",
  "type": "fada",
  "attack": 20,
  "height": 0.6
}
{
  "_id": ObjectId("5780c1d7e217205feb8b00fc"),
  "name": "Jigglypuff",
  "description": "Bolinha rosa hiper fofa",
  "type": "fada",
  "attack": 20,
  "height": 0.5
}
{
  "_id": ObjectId("5780c236e217205feb8b00fd"),
  "name": "Vileplume",
  "description": "Flor loka",
  "type": "grama",
  "attack": 40,
  "height": 1.2
}
{
  "_id": ObjectId("5780c2b0e217205feb8b00fe"),
  "name": "Psyduck",
  "description": "Patinho legal",
  "type": "água",
  "attack": 30,
  "height": 0.8
}

```

## Altura menor ou igual a 0.5 E do tipo grama

```
var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}
db.pokemons.find(query)
{
  "_id": ObjectId("57802b62c9f294b0d14c8d65"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}

```

## Nome Pikachu OU attack menor ou igual a 0.5

```
var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("578028389af54197ee22cd15"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}

```

## Attack maior ou igual a 48 E altura menor ou igual a 0.5

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("578028389af54197ee22cd15"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57802b62c9f294b0d14c8d65"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57802bffc9f294b0d14c8d67"),
  "name": "Squirtle",
  "description": "Ejata água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}

```