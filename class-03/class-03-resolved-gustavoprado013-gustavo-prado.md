## MongoDB - Aula 03 - Exercício
autor: Gustavo Prado

## 1 - Listando todos os Pokemons com a altura menor que 0.5
```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt:0.5}}
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649dfb0aafb2dd43c53f629"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("5649dfbfaafb2dd43c53f62a"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}

```

## 2 - Listando todos os Pokemons com a altura maior ou igual que 0.5

```
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte:0.5}}
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649df9caafb2dd43c53f628"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("5649dfccaafb2dd43c53f62b"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("5649dfdcaafb2dd43c53f62c"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}

```

## 3 - Listando todos os Pokemons com a altura maior ou igual que 0.5 E do tipo poison

```

gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$gte: 0.5}}, {type: 'Poison'}]}
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649dfdcaafb2dd43c53f62c"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}

```

## 4 - Listando todos os Pokemons com o nome Blastoise OU com attack menor ou igual que 50

```

gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: 'Blastoise'}, {attack: {$lte: 50}}]}
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649df9caafb2dd43c53f628"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("5649dfb0aafb2dd43c53f629"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("5649dfbfaafb2dd43c53f62a"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}

```

## 5 - Listando todos os Pokemons com attack maior ou igual que 48 E com height menor ou igual que 1.0

```

gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 1.0}}]}
gustavo-Inspiron-3442(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649dfccaafb2dd43c53f62b"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}

```