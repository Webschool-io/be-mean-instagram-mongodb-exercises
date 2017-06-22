# MongoDB - Aula 03 - Exercício
autor: André Rocha

## Listando todos os Pokemons com altura menor que 0.5

```
be_mean_pokemons> var query = {height: {$lt: 0.5}}

db.be_mean_pokemons.findOne(query)
{
  "_id": ObjectId("56453ff950f757b5fdb43fa5"),
  "name": "Pikachu",
  "description": "Rato mudo, elétrico e fofo",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}

```

## Listando todos os Pokemons com altura maior ou igual que 0.5

```
be_mean_pokemons> var query = {height: {$gte: 0.5}}

{
  "_id": ObjectId("56453ed050f757b5fdb43fa0"),
  "name": "Charmeleon",
  "description": "Destrói tudo saporra",
  "type": "fire",
  "attack": 40,
  "defense": 40,
  "height": 1.1
}

```

## Listando todos os Pokemons com altura menor ou igual que 0.5 E do tipo grama

```
be_mean_pokemons> var query = {$and: [{height:{$lte: 0.5} }, {type:'grama'} ]}

be_mean_pokemons> db.be_mean_pokemons.findOne(query)
{
  "_id": ObjectId("5645567c3deed03ff449f06a"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}

```


## Listando todos os Pokemons com nome igual a Pikachu OU ataque menor ou igual a 0.5

```
be_mean_pokemons> var query = {$or: [{attack:{$lte: 0.5} }, {name:'Pikachu'} ]}

be_mean_pokemons> db.be_mean_pokemons.findOne(query)
{
  "_id": ObjectId("56453ff950f757b5fdb43fa5"),
  "name": "Pikachu",
  "description": "Rato mudo, elétrico e fofo",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}

```

## Listando todos os Pokemons com ataque maior ou igual que 48 E com height menor ou igual que 0.5

```
be_mean_pokemons> var query = {$and: [{attack:{$gte: 48} }, {height: {$lte: 0.5}} ]}

be_mean_pokemons> db.be_mean_pokemons.findOne(query)
{
  "_id": ObjectId("56453ff950f757b5fdb43fa5"),
  "name": "Pikachu",
  "description": "Rato mudo, elétrico e fofo",
  "type": "eletric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}

```