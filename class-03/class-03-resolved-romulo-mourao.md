# MongoDB - Aula 03 - Exercício
autor: Romulo de Araújo Mourão

## 1. Liste todos Pokemons com a altura menor que 0.5;

    ```
    rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({height: {$lt:0.5}})
    {
      "_id": ObjectId("5644c90a2ea0618e48bdc921"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "electric",
      "attack": 55,
      "height": 0.4
    }
    {
      "_id": ObjectId("5644c90a2ea0618e48bdc922"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4
    }
    Fetched 2 record(s) in 7ms


    ```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

    ```
  rmourao(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte:0.5}}
  rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
  {
    "_id": ObjectId("56439264ec4acad482954438"),
    "name": "zapdos",
    "description": "Passaro elétrico",
    "atack": 60,
    "defense": 50,
    "height": 2.3
  }
  {
    "_id": ObjectId("56439264ec4acad482954439"),
    "name": "articuno",
    "description": "Pavão azul de gelo",
    "atack": 50,
    "defense": 50,
    "height": 1.5
  }
  {
    "_id": ObjectId("56439264ec4acad48295443a"),
    "name": "aerodactyl",
    "description": "dragão voador",
    "atack": 47,
    "defense": 49,
    "height": 7.3
  }
  {
    "_id": ObjectId("56439264ec4acad48295443b"),
    "name": "porygon",
    "description": "bicho estranho",
    "atack": 30,
    "defense": 35,
    "height": 1.3
  }
  {
    "_id": ObjectId("56439264ec4acad48295443c"),
    "name": "umbreon",
    "description": "raposa preta",
    "atack": 56,
    "defense": 40,
    "height": 2.4
  }
  {
    "_id": ObjectId("5644c90a2ea0618e48bdc923"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6
  }
  {
    "_id": ObjectId("5644c90a2ea0618e48bdc924"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5
  }
  Fetched 7 record(s) in 3ms


    ```


## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

    ```
    rmourao(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
    rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("5644c90a2ea0618e48bdc922"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4
    }
    Fetched 1 record(s) in 4ms

    ```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

    ```
    rmourao(mongod-3.0.7) be-mean-pokemons> var query = {$or:[{name:'pikachu'},{attack:{$lte:0.5}}]}
    rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    Fetched 0 record(s) in 1ms

    ```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

    ```
    rmourao(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
    rmourao(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("5644c90a2ea0618e48bdc921"),
      "name": "Pikachu",
      "description": "Rato elétrico bem fofinho",
      "type": "electric",
      "attack": 55,
      "height": 0.4
    }
    {
      "_id": ObjectId("5644c90a2ea0618e48bdc922"),
      "name": "Bulbassauro",
      "description": "Chicote de trepadeira",
      "type": "grama",
      "attack": 49,
      "height": 0.4
    }
    {
      "_id": ObjectId("5644c90a2ea0618e48bdc924"),
      "name": "Squirtle",
      "description": "Ejeta água que passarinho não bebe",
      "type": "água",
      "attack": 48,
      "height": 0.5
    }
    Fetched 3 record(s) in 2ms


    ```
