# MongoDB - Aula 03 - Exercício
autor: Leandro Ferreira


### Etapa 1

```

leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> var query = {height: {$lt: 0.5}}
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564548fa16fb3c6e9444512f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("564549c216fb3c6e94445130"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56454d0d952268591ca3cace"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 1ms

```

## Etapa 2

```
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> var query = {height: {$lt: 0.5}}
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564548fa16fb3c6e9444512f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("564549c216fb3c6e94445130"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56454d0d952268591ca3cace"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 1ms
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> var query = {height: {$gte: 0.5}}
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56454a0616fb3c6e94445131"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56454a3d16fb3c6e94445132"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms


```


## Etapa 3


```

leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> var query = {$and : [{height:{$lte:0.5}},{type:'grama'}]}
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> query
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
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564549c216fb3c6e94445130"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms


```


### Etapa 4



```

leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> var query = {$or : [{name:'Pikachu'},{height:{$lte:0.5}}]}
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564548fa16fb3c6e9444512f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("564549c216fb3c6e94445130"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56454a3d16fb3c6e94445132"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("56454d0d952268591ca3cace"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 4 record(s) in 2ms


```



# Etapa 5


```

leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> var query = {$and : [{height:{$lte:0.5}},{attack:{$gte:48}}]}
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "attack": {
        "$gte": 48
      }
    }
  ]
}
leandro-IE-G31TM7(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564548fa16fb3c6e9444512f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("564549c216fb3c6e94445130"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56454a3d16fb3c6e94445132"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms


```
