#MongoDb - Aula 02 - Exercício

  ```
  Autor: Rafael Pessoni

  ```

##Criar database chamada be-mean-pokemons

  ```
  localhost(mongod-3.2.0) be-mean> use be-mean-pokemons
  switched to db be-mean-pokemons

  ```

##Listagem de todas dbs

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> show dbs
  be-mean           → 0.004GB
  be-mean-instagram → 0.004GB
  local             → 0.000GB

  ```

##Listagem de todas as collections

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> show collections
  localhost(mongod-3.2.0) be-mean-pokemons> 

  ```

##Criar cinco pokemons

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert({name:"Bulbasaur", description: "Bulbasaur can be seen napping in bright sunlight.", attack: 300, defense:200, height:0.7})
  Inserted 1 record(s) in 270ms
  WriteResult({
    "nInserted": 1
  })

  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert({name:"Charmander", description: "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.", attack: 300, defense:200, height:0.6})
  Inserted 1 record(s) in 1ms
  WriteResult({
    "nInserted": 1
  })

  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert({name:"Squirtle", description: "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.", attack: 300, defense:300, height:0.5})
  Inserted 1 record(s) in 2ms
  WriteResult({
    "nInserted": 1
  })

  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert({name:"Caterpie", description: "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.", attack: 200, defense:200, height:0.3})
  Inserted 1 record(s) in 2ms
  WriteResult({
    "nInserted": 1
  })

  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert({name:"Butterfree", description: "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.", attack: 200, defense:200, height:1.1})
  Inserted 1 record(s) in 1ms
  WriteResult({
    "nInserted": 1
  })

  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert({name:"Abra", description: "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.", attack: 100, defense:100, height:0.9})
  Inserted 1 record(s) in 1ms
  WriteResult({
    "nInserted": 1
  })

  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert({name:"Farfetch'd", description: "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.", attack: 300, defense:300, height:0.8})
  Inserted 1 record(s) in 1ms
  WriteResult({
    "nInserted": 1
  })

  ```

##Listar todos os pokemons

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.find()
  {
    "_id": ObjectId("56896b541347fec60f58c5e1"),
    "name": "Bulbasaur",
    "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
    "attack": 300,
    "defense": 200,
    "height": 0.7
  }
  {
    "_id": ObjectId("56896bf91347fec60f58c5e2"),
    "name": "Charmander",
    "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
    "attack": 300,
    "defense": 200,
    "height": 0.6
  }
  {
    "_id": ObjectId("56896c041347fec60f58c5e3"),
    "name": "Squirtle",
    "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
    "attack": 300,
    "defense": 300,
    "height": 0.5
  }
  {
    "_id": ObjectId("56896c151347fec60f58c5e4"),
    "name": "Caterpie",
    "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
    "attack": 200,
    "defense": 200,
    "height": 0.3
  }
  {
    "_id": ObjectId("56896c1f1347fec60f58c5e5"),
    "name": "Butterfree",
    "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
    "attack": 200,
    "defense": 200,
    "height": 1.1
  }
  {
    "_id": ObjectId("56896c2a1347fec60f58c5e6"),
    "name": "Abra",
    "description": "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
    "attack": 100,
    "defense": 100,
    "height": 0.9
  }
  {
    "_id": ObjectId("56896c321347fec60f58c5e7"),
    "name": "Farfetch'd",
    "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
    "attack": 300,
    "defense": 300,
    "height": 0.8
  }
  Fetched 7 record(s) in 3ms

  ```

##Buscar um pokemon

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> var poke = db.pokemons.findOne({name:"Farfetch'd"})
  localhost(mongod-3.2.0) be-mean-pokemons> poke
  {
    "_id": ObjectId("56896c321347fec60f58c5e7"),
    "name": "Farfetch'd",
    "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
    "attack": 300,
    "defense": 300,
    "height
  }

  ```


##Editar a description do pokemon escolhido

  ```
  localhost(mongod-3.2.0) be-mean-pokemons> poke.description = "pokemon hacker"
  pokemon hacker
  localhost(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(poke)
  Updated 1 existing record(s) in 2ms
  WriteResult({
    "nMatched": 1,
    "nUpserted": 0,
    "nModified": 1
  })

  ```
