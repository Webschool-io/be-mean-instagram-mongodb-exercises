MongoDB - Aula 03 - Exercício
Autor: Nicolas de Paulo Rosa

Listando todos pokemons com altura menor que 0.5(passo 1)

```
MEAN(mongod-3.0.7) be-mean-instagram> var query = {height: {$lt:0.5}}
MEAN(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56466dace3d371685183aeb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56466dd1e3d371685183aeb1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56468586e3d371685183aeb5"),
  "name": "Caterpie",
  "description": "Larva Lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
```

Listando todos pokemons com altura maior ou igual que 0.5(passo 2)

```
MEAN(mongod-3.0.7) be-mean-instagram> var query = {height: {$gte:0.5}}
MEAN(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56466df8e3d371685183aeb2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 53,
  "height": 0.6
}
{
  "_id": ObjectId("56466e0fe3d371685183aeb3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
```

Listando todos pokemons com altura menor ou igual que 0.5 e do tipo grama(passo 3)

```
MEAN(mongod-3.0.7) be-mean-instagram> var query = {$and: [{type: 'grama'},{height: {$lte: 0.5}}]}
MEAN(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56466dd1e3d371685183aeb1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
```

Listando todos pokemons com o nome Pikachu OU com attack menor ou igual que 0.5(passo 4)

```
MEAN(mongod-3.0.7) be-mean-instagram> var query = {$or: [{name: 'Pikachu'},{attack: {$lt: 0.5}}]}
MEAN(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56466dace3d371685183aeb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
```

Listando todos pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5(passo 5)

```
MEAN(mongod-3.0.7) be-mean-instagram> var query = {$and: [{height: {$lte: 0.5}},{attack: {$gte: 48}}]}
MEAN(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56466dace3d371685183aeb0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56466dd1e3d371685183aeb1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56466e0fe3d371685183aeb3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
```
