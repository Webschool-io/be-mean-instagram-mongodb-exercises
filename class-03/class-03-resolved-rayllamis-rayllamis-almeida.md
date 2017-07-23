# MongoDB - Aula 03 - Exercício
autor: Rayllamis Almeida

## Liste todos Pokemons com a altura **menor que** 0.5;

    > var query = {height: {$lt: 0.5}}
    > db.pokemons.find(query)
    {
      "_id": ObjectId("56490decba1b3df2a830019d"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "eletric",
      "attack": 55,
      "height": 0.4
    }
    {
      "_id": ObjectId("56490dfaba1b3df2a830019e"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4
    }
    {
      "_id": ObjectId("56490f1bba1b3df2a83001a1"),
      "name": "Caterpie",
      "description": "Larva lutadora",
      "type": "inseto",
      "attack": 30,
      "height": 0.3,
      "defense": 35
    }
    Fetched 3 record(s) in 2ms

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

    > var query = {height: {$gte: 0.5}}
    > db.pokemons.find(query)
    {
      "_id": ObjectId("56490e10ba1b3df2a830019f"),
      "name": "Charmander",
      "description": "Esse é o cão chpando manga de fofinho",
      "type": "fogo",
      "attack": 52,
      "height": 0.6
    }
    {
      "_id": ObjectId("56490e1aba1b3df2a83001a0"),
      "name": "Squirtle",
      "description": "Ejeta água que passarinho não bebe",
      "type": "água",
      "attack": 48,
      "height": 0.5
    }
    Fetched 2 record(s) in 5ms

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

    > var query = {$and: [{height:{$lte: 0.5} }, {type:'grama'} ]}
    > db.pokemons.find(query)
    {
      "_id": ObjectId("56490dfaba1b3df2a830019e"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4
    }
    Fetched 1 record(s) in 3ms

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

    > var query = {$or: [{name:'Pikachu'}, {attack:{$lte: 0.5}}]}
    > db.pokemons.find(query)
    {
      "_id": ObjectId("56490decba1b3df2a830019d"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "eletric",
      "attack": 55,
      "height": 0.4
    }
    Fetched 1 record(s) in 1ms

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

    > var query = {$and: [{attack:{$gte: 48}}, {height: {$lte: 0.5}}]}
    > db.pokemons.find(query)
    {
      "_id": ObjectId("56490decba1b3df2a830019d"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "eletric",
      "attack": 55,
      "height": 0.4
    }
    {
      "_id": ObjectId("56490dfaba1b3df2a830019e"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4
    }
    {
      "_id": ObjectId("56490e1aba1b3df2a83001a0"),
      "name": "Squirtle",
      "description": "Ejeta água que passarinho não bebe",
      "type": "água",
      "attack": 48,
      "height": 0.5
    }
    Fetched 3 record(s) in 2ms

