# MongoDB - Aula 03 - Exercício
autor: Alex Sandro Souza


## Liste todos Pokemons com a altura **menor que** 0.5;

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {height:{$lt:0.5}}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f904c4241d4eb872e7e216"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("59f906a1241d4eb872e7e217"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("59f90898b754920f4ff31def"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 3ms

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {height:{$gte:0.5}}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f906b6241d4eb872e7e218"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("59f906be241d4eb872e7e219"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 18,
  "height": 0.5
}
Fetched 2 record(s) in 3ms


```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f906a1241d4eb872e7e217"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {$or:[{name:'Pikachu'},{attack:{$lte:0.5}}]}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f904c4241d4eb872e7e216"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
gigantus(mongod-3.2.17) be-mean-instagram> var query = {$and:[{attack:{$gte:48}} , {height : {$lte : 0.5}} ]}
gigantus(mongod-3.2.17) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("59f904c4241d4eb872e7e216"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("59f906a1241d4eb872e7e217"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}


```
