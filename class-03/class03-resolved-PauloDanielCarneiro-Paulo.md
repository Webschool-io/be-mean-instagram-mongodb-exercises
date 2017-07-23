# MongoDB - Aula 03 - Exercício
Autor: Paulo Daniel Carneiroi

## Listando os pokemons com altura maior que 0.5
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {"height": {$lt: 0.5}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listando todos os pokemons com altura maior ou igual a 0.5
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {"height": {$gte: 0.5}}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57d0b65537e697e8ef7398c9"),
  "name": "bulbasaur",
  "description": "Pokemon planta",
  "type": "grass",
  "attack": 45,
  "defense": 30,
  "height": 7
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398ca"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da sua cauda é uma indicação das suas emoções",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "defense": 20
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cb"),
  "name": "Charizard",
  "description": "Bicho feio que voa e cospe fogo",
  "type": "fogo",
  "attack": 40,
  "height": 1.7,
  "defense": 30
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cc"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "plant",
  "attack": 4,
  "defense": 4,
  "height": 6.07
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cd"),
  "name": "Charmeleon",
  "description": "Charmeleon fights everywhere!",
  "type": "fire",
  "attack": 3,
  "defense": 3,
  "height": 3.07
}
Fetched 5 record(s) in 7ms
```

## Listando todos os pokemons com altura menor ou igual a 0.5 e do tipo grama
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {$and: [{"height": {$lte: 0.5}}, {"type" : "grass"}]}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listando todos os pokemons com name "pikachu" ou com ataque menos ou igual a 0.5
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {$or: [{"attack": {$lte: 0.5}}, {"name": "pikachu"}]}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Listando todos os pokemons com ataque maior ou igual a 48 e com altura menor ou igual a 0.5
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> var query = {$and: [{"attack": {$gte: 48}}, {"height": {$lte: 0.5}}]}
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Obs.: Dados que estão no banco:
```
Paulo-PC(mongod-3.0.12) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57d0b65537e697e8ef7398c9"),
  "name": "bulbasaur",
  "description": "Pokemon planta",
  "type": "grass",
  "attack": 45,
  "defense": 30,
  "height": 7
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398ca"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da sua cauda é uma indicação das suas emoções",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "defense": 20
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cb"),
  "name": "Charizard",
  "description": "Bicho feio que voa e cospe fogo",
  "type": "fogo",
  "attack": 40,
  "height": 1.7,
  "defense": 30
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cc"),
  "name": "Venusaur",
  "description": "There is a large flower on Venusaur's back",
  "type": "plant",
  "attack": 4,
  "defense": 4,
  "height": 6.07
}
{
  "_id": ObjectId("57d0b65537e697e8ef7398cd"),
  "name": "Charmeleon",
  "description": "Charmeleon fights everywhere!",
  "type": "fire",
  "attack": 3,
  "defense": 3,
  "height": 3.07
}
Fetched 5 record(s) in 1ms
```
