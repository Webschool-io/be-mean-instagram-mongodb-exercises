# MongoDB - Aula 03 - Exercício
autor: **Jonatas Leon**

## Liste todos Pokemons com a altura **menor que** 0.5;
```
lucy(mongod-3.0.12) be-mean-pokemons> var query = { height: { $lt: 0.5 } }
lucy(mongod-3.0.12) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
lucy(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef17"),
  "attack": 105,
  "defense": 90,
  "height": 0.4,
  "name": "Krabby",
  "type": "water",
  "description": "Caranguejo boladão"
}
{
  "_id": ObjectId("579e73be5e913e20d1a79d78"),
  "attack": 53,
  "defense": 70,
  "height": 0.3,
  "name": "Sewaddle",
  "type": "grass",
  "description": "Bichão do mato!!"
}
Fetched 2 record(s) in 2ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5;
```
lucy(mongod-3.0.12) be-mean-pokemons> var query = { height: { $gte: 0.5 } }
lucy(mongod-3.0.12) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
lucy(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef15"),
  "attack": 110,
  "defense": 70,
  "height": 1.8,
  "name": "Dodrio",
  "type": "flying",
  "description": "Bichão zica de 3 cabeças feio pra casseta"
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef16"),
  "attack": 52,
  "defense": 48,
  "height": 0.8,
  "name": "Psyduck",
  "type": "water",
  "description": "Patão chapado"
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef18"),
  "attack": 110,
  "defense": 90,
  "height": 2,
  "name": "Mewtwo",
  "type": "psychic",
  "description": "Vem monstro, vem monstro! Bichão criado em laboratório pra destruir todas essas árvores do Parque Ibirapuera"
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef19"),
  "attack": 120,
  "defense": 120,
  "height": 3.2,
  "name": "Arceus",
  "type": "normal",
  "description": "According to the legends of Sinnoh, this Pokémon emerged from an egg and shaped all there is in this world."
}
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef1a"),
  "attack": 150,
  "defense": 50,
  "height": 1.7,
  "name": "Deoxys",
  "type": "psychic",
  "description": "Pokemon pika, não Pikachu, mas pika das galaxia mesmo!"
}
Fetched 5 record(s) in 6ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;
```
lucy(mongod-3.0.12) be-mean-pokemons> var query = { $and: [ { height: { $lte: 0.5 } }, { type: 'grass' } ] }
lucy(mongod-3.0.12) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grass"
    }
  ]
}
lucy(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("579e73be5e913e20d1a79d78"),
  "attack": 53,
  "defense": 70,
  "height": 0.3,
  "name": "Sewaddle",
  "type": "grass",
  "description": "Bichão do mato!!"
}
Fetched 1 record(s) in 1ms

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;
```
lucy(mongod-3.0.12) be-mean-pokemons> var query = { $or: [ { name: 'Pikachu' }, { attack: { $lte: 0.5 } } ] }
lucy(mongod-3.0.12) be-mean-pokemons> query
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
lucy(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com height **menor ou igual que** 0.5;
```
lucy(mongod-3.0.12) be-mean-pokemons> var query = { $and: [ { attack: { $gte: 48 } }, { height: { $lte: 0.5 } } ] }
lucy(mongod-3.0.12) be-mean-pokemons> query
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
lucy(mongod-3.0.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("579d7fc3cf09c5720e50ef17"),
  "attack": 105,
  "defense": 90,
  "height": 0.4,
  "name": "Krabby",
  "type": "water",
  "description": "Caranguejo boladão"
}
{
  "_id": ObjectId("579e73be5e913e20d1a79d78"),
  "attack": 53,
  "defense": 70,
  "height": 0.3,
  "name": "Sewaddle",
  "type": "grass",
  "description": "Bichão do mato!!"
}
Fetched 2 record(s) in 1ms

```
