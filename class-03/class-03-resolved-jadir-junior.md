# MongoDB - Aula 03 - Exercício
autor: Jadir Junior

## Liste todos Pokemons com a altura **menor que** 0.5;
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> query = {height: {$lt: 0.5}}
{
  "height": {
    "$lt": 0.5
  }
}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> query = {height: {$gte: 0.5}}
{
  "height": {
    "$gte": 0.5
  }
}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> query = {$and:[{height: {$lte: 0.5}}, {types: "grass"}]}
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "types": "grass"
    }
  ]
}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5 (adaptado o attack para 50)
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> query = {$or: [{name:/pikachu/i}, {attack: {$lte: 50}}]}
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "attack": {
        "$lte": 50
      }
    }
  ]
}
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
ubuntu(mongod-3.0.7) be-mean-pokemons-01> query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
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
ubuntu(mongod-3.0.7) be-mean-pokemons-01> db.pokemons.find(query)
```
