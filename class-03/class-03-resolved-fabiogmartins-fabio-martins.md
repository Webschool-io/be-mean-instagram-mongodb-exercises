# MongoDB - Aula 03 - Exercício
autor: Fabio Martins

## Liste todos Pokemons com a altura **menor que** 0.5;
```
var query = {height:{$lt:0.5}}
db.pokemons.find(query)

{
  "_id": ObjectId("56577f606559eb84fe2dfb15"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb16"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb1d"),
  "name": "Rattata ",
  "description": "Muito cauteloso",
  "type": "normal",
  "attack": 56,
  "height": 0.3
}

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
var query = {height:{$gte:0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("56577f606559eb84fe2dfb17"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.7
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb18"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb19"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho nao bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb1a"),
  "name": "Raikou",
  "description": "Encarna a velocidade do raio",
  "type": "elétrico",
  "attack": 85,
  "height": 1.9
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb1b"),
  "name": "Charizard",
  "description": "Respira fogo de grande calor",
  "type": "fogo",
  "attack": 83,
  "height": 1.7
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb1c"),
  "name": "Beedrill",
  "description": "Extremamente territorial, ataca em enxame",
  "type": "inseto",
  "attack": 80,
  "height": 1
}


```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
var query = {$and:[{height:{$lte:0.5}},{"type":"grama"}]}
db.pokemons.find(query)

Fetched 0 record(s) in 1ms

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
var query = {$or:[{"name":"Pikachu"},{attack:{$lte:0.5}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56577f606559eb84fe2dfb16"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
var query = {$and:[{"attack":{$gte:48}},{height:{$lte:0.5}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("56577f606559eb84fe2dfb16"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb19"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho nao bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56577f606559eb84fe2dfb1d"),
  "name": "Rattata ",
  "description": "Muito cauteloso",
  "type": "normal",
  "attack": 56,
  "height": 0.3
}
Fetched 3 record(s) in 3ms

```
