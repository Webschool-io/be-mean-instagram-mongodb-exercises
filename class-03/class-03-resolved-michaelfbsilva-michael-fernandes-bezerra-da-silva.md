# MongoDB - Aula 03 - Exercício
autor: Michael Fernandes

## Liste todos Pokemons com a altura **menor que** 0.5;
```
    var query = {height: {$lt: 0.5}}
    query
    {
      "height": {
          "$lt": 0.5
      }
    }
    db.pokemons.find(query)
    {
      "_id": ObjectId("5648044446704952eb6850a2"),
      "name": "Pikachu",
      "description": "Tato elétrico bem fofinho",
      "type": "electic",
      "attack": 55,
      "height": 0.4
    }
    {
      "_id": ObjectId("5648044446704952eb6850a3"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4
    }
    {
      "_id": ObjectId("5648044446704952eb6850a6"),
      "name": "Caterpie",
      "description": "Larva lindinha",
      "type": "inseto",
      "attack": 30,
      "height": 0.3
    }
    Fetched 3 record(s) in 1ms

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
    var query = {height: {$gte: 0.5}}
    query
    {
        "height": {
            "$gte": 0.5
        }
    }
    db.pokemons.find(query)
    {
        "_id": ObjectId("5648044446704952eb6850a4"),
        "name": "Charmander",
        "description": "Esse é o cçao chupando manga de fofinho",
        "type": "fogo",
        "attack": 52,
        "height": 0.6
    }
    {
        "_id": ObjectId("5648044446704952eb6850a5"),
        "name": "Squirtle",
        "description": "Ejeta água que passarinho não bebe",
        "type": "água",
        "attack": 48,
        "height": 0.5
    }
    {
        "_id": ObjectId("5648044446704952eb6850a7"),
        "name": "Magby",
        "description": "Um pato que cospe fogo",
        "type": "fogo",
        "attack": 35,
        "height": 0.7
    }
    {
        "_id": ObjectId("5648044446704952eb6850a8"),
        "name": "Treecko",
        "description": "Largarto marento estiloso",
        "type": "grama",
        "attack": 30,
        "height": 0.5
    }
    {
        "_id": ObjectId("5648044446704952eb6850a9"),
        "name": "Elgyem",
        "description": "Largarta marenta cheia de estilo",
        "type": "psiquica",
        "attack": 35,
        "height": 0.5
    }
    Fetched 5 record(s) in 3ms

```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
    var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
    query
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

    db.pokemons.find(query)
    {
        "_id": ObjectId("5648044446704952eb6850a3"),
        "name": "Bulbassauro",
        "description": "Chicote de trepadeira",
        "type": "grama",
        "attack": 49,
        "height": 0.4
    }
    {
        "_id": ObjectId("5648044446704952eb6850a8"),
        "name": "Treecko",
        "description": "Largarto marento estiloso",
        "type": "grama",
        "attack": 30,
        "height": 0.5
    }
    Fetched 2 record(s) in 49ms



```


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
    var query = {$or:[{name:'Pikachu'},{attack:{$lte:0.5}}]}
    query
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

    db.pokemons.find(query)
    {
        "_id": ObjectId("5648044446704952eb6850a2"),
        "name": "Pikachu",
        "description": "Tato elétrico bem fofinho",
        "type": "electic",
        "attack": 55,
        "height": 0.4
    }
    Fetched 1 record(s) in 31ms

```


## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
    var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
    query
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

    db.pokemons.find(query)
    {
        "_id": ObjectId("5648044446704952eb6850a2"),
        "name": "Pikachu",
        "description": "Tato elétrico bem fofinho",
        "type": "electic",
        "attack": 55,
        "height": 0.4
    }
    {
        "_id": ObjectId("5648044446704952eb6850a3"),
        "name": "Bulbassauro",
        "description": "Chicote de trepadeira",
        "type": "grama",
        "attack": 49,
        "height": 0.4
    }
    {
        "_id": ObjectId("5648044446704952eb6850a5"),
        "name": "Squirtle",
        "description": "Ejeta água que passarinho não bebe",
        "type": "água",
        "attack": 48,
        "height": 0.5
    }
    Fetched 3 record(s) in 1ms

```
