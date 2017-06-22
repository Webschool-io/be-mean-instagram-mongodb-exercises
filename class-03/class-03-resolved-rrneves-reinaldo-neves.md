# MongoDB - Aula 03 - Exercício
autor: Reinaldo Neves

## Liste todos Pokemons com a altura **menor que** 0.5;
```
query = {height:{$lte: 0.5}}
{
    "height": {
        "$lte": 0.5
    }
}

db.pokemons.find(query)
{
    "_id": ObjectId("564b8f4981fe473183744e08"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0a"),
    "name": "Durant",
    "description": "Formiga de aço",
    "type": "inseto",
    "attack": 48,
    "height": 0.3
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0b"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0d"),
    "name": "Squirtle",
    "description": "Ejeta água",
    "type": "água",
    "attack": 48,
    "height": 0.5
}
{
    "_id": ObjectId("564b8f5d81fe473183744e11"),
    "name": "Rattata ",
    "description": "Muito cauteloso",
    "type": "normal",
    "attack": 56,
    "height": 0.3
}
Fetched 5 record(s) in 285ms                                                                                                
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
query = {height:{$gte: 0.5}}
{
    "height": {
        "$gte": 0.5
    }
}
db.pokemons.find(query)
{
    "_id": ObjectId("564b8f5d81fe473183744e0c"),
    "name": "Charmander",
    "description": "Dragão",
    "type": "fogo",
    "attack": 52,
    "height": 0.6
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0d"),
    "name": "Squirtle",
    "description": "Ejeta água",
    "type": "água",
    "attack": 48,
    "height": 0.5
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0e"),
    "name": "Raikou",
    "description": "Velocidade do raio e ondas de choque",
    "type": "elétrico",
    "attack": 85,
    "height": 1.9
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0f"),
    "name": "Charizard",
    "description": "Respira fogo de grande calor",
    "type": "fogo",
    "attack": 84,
    "height": 1.7
}
{
    "_id": ObjectId("564b8f5d81fe473183744e10"),
    "name": "Beedrill",
    "description": "Extremamente territorial, ataca em enxame",
    "type": "inseto",
    "attack": 80,
    "height": 1
}
Fetched 5 record(s) in 155ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
query = {$and: [{height:{$lte: 0.5}},{type: 'grama'}]}
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
    "_id": ObjectId("564b8f5d81fe473183744e0b"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
}
Fetched 1 record(s) in 41ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
query = {$or: [{attack:{$lte: 0.5}},{name: /pikachu/i}]}
{
    "$or": [
        {
            "attack": {
                "$lte": 0.5
            }
        },
        {
            "name": /pikachu/i
        }
    ]
}
db.pokemons.find(query)
{
    "_id": ObjectId("564b8f4981fe473183744e08"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
}
Fetched 1 record(s) in 23ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
query = {$and: [{attack:{$gte: 48}},{height:{$lte: 0.5}}]}
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
    "_id": ObjectId("564b8f4981fe473183744e08"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "electric",
    "attack": 55,
    "height": 0.4
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0a"),
    "name": "Durant",
    "description": "Formiga de aço",
    "type": "inseto",
    "attack": 48,
    "height": 0.3
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0b"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4
}
{
    "_id": ObjectId("564b8f5d81fe473183744e0d"),
    "name": "Squirtle",
    "description": "Ejeta água",
    "type": "água",
    "attack": 48,
    "height": 0.5
}
{
    "_id": ObjectId("564b8f5d81fe473183744e11"),
    "name": "Rattata ",
    "description": "Muito cauteloso",
    "type": "normal",
    "attack": 56,
    "height": 0.3
}
Fetched 5 record(s) in 229ms
```

