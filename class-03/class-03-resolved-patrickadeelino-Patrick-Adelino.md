# MongoDB - Aula 03 - Exercício

Autor: Patrick Adelino

## 1. Liste todos Pokemons com altura menor que 0.5 

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {height: {$lt: 0.5 }}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 124ms
```

## 2. Liste todos Pokemons com altura maior ou igual que 0.5 

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {height: {$gte: 0.5 }}

pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}

pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5784309e9fc95fecf503fec1"),
  "name": "Bulbasaur",
  "description": "Bulbasaur é um pokemon pokemon do tipo planta.",
  "attack": 100,
  "defense": 200,
  "height": 0.7
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec2"),
  "name": "Gengar",
  "description": "Gengar é um pokemon boladão do tipo Ghost.",
  "attack": 300,
  "defense": 300,
  "height": 4.5
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec3"),
  "name": "Steelix",
  "description": "Evolução do Onix, versão pica e do tipo Steel.",
  "attack": 460,
  "defense": 600,
  "height": 30.2
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec4"),
  "name": "Hypno",
  "description": "Tem um turbante na cabeça e é amarelinho.",
  "attack": 400,
  "defense": 100,
  "height": 3.9
}
{
  "_id": ObjectId("5784309f9fc95fecf503fec5"),
  "name": "Fearow",
  "description": "Um ave bem louca, evolução da spearow.",
  "attack": 300,
  "defense": 300,
  "height": 7.8
}
Fetched 5 record(s) in 4ms
```

## 3. Liste todos Pokemons com altura menor ou igual que 0.5 E do tipo grama 

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{ height: {$lte: 0.5}}, {type: "grama"} ]}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grama"
    }
  ]
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 93ms
```

## 4. Liste todos Pokemons com o name 'Pìkachu' OU com attack menor ou igual que 0.5

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 0.5}}]}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "$or": [
    {
      "name": "Pikachu"
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```

## 5. Liste todos Pokemons com attack maior ou igual que 48 E com altura menor ou igual que 0.5 

```
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{ attack: {$gte: 48} }, { height: {$lte: 0.5} }] }
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}
pontocom-Aspire-4252(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```
