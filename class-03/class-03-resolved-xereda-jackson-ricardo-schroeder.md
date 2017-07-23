# MongoDB - Aula 03 - Exercício
User: [xereda](http://www.github.com/xereda)

Autor: Jackson Ricardo Schroeder

## Pokémons com altura menor que 0.5

```
  macminixereda(mongod-3.2.0) be-mean-teste> var query = { height: { $lt: 0.5 } };
  macminixereda(mongod-3.2.0) be-mean-teste> query
  {
    "height": {
      "$lt": 0.5
    }
  }
  macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
  {
    "_id": ObjectId("573a8a5324450f724f323f15"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4
  }
  {
    "_id": ObjectId("573a8bbd24450f724f323f16"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  }
  {
    "_id": ObjectId("573a8d6e24450f724f323f19"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35
  }
  Fetched 3 record(s) in 2ms
```

## Pokémons com altura maior ou igual a 0.5

```
  macminixereda(mongod-3.2.0) be-mean-teste> var query = { height: { $gte: 0.5 } };
  macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
  {
    "_id": ObjectId("573a8c0524450f724f323f17"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6
  }
  {
    "_id": ObjectId("573a8c6524450f724f323f18"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5
  }
  Fetched 2 record(s) in 2ms
```

## Pokémons com altura menor ou igual a 0.5 e do tipo grama

```
  macminixereda(mongod-3.2.0) be-mean-teste> var query = { $and: [ { type: "grama" }, { height: { $lte: 0.5 } } ] };
  macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
  {
    "_id": ObjectId("573a8bbd24450f724f323f16"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  }
  Fetched 1 record(s) in 1ms
```

## Pokémons com nome 'Pikachu' ou com attack menor ou igual a 0.5

```
  macminixereda(mongod-3.2.0) be-mean-teste> var query = { $or: [ { name: "Pikachu" }, { height: { $lte: 0.5 } } ] };
  macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
  {
    "_id": ObjectId("573a8a5324450f724f323f15"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4
  }
  {
    "_id": ObjectId("573a8bbd24450f724f323f16"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  }
  {
    "_id": ObjectId("573a8c6524450f724f323f18"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5
  }
  {
    "_id": ObjectId("573a8d6e24450f724f323f19"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35
  }
  Fetched 4 record(s) in 2ms
```

## Pokémons com attack maior ou igual a 48 e altura menor ou igual a 0.5

```
  macminixereda(mongod-3.2.0) be-mean-teste> var query = { $and: [ { attack: { $gte: 48 } }, { height: { $lte: 0.5 } } ] };
  macminixereda(mongod-3.2.0) be-mean-teste> db.pokemons.find(query);
  {
    "_id": ObjectId("573a8a5324450f724f323f15"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4
  }
  {
    "_id": ObjectId("573a8bbd24450f724f323f16"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
  }
  {
    "_id": ObjectId("573a8c6524450f724f323f18"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5
  }
  Fetched 3 record(s) in 1ms
```
