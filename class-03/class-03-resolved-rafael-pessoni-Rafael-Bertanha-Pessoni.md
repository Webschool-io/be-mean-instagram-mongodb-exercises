# MongoDB - Aula 03 - Exercício
  
  ```
  Autor: Rafael Pessoni

  ```

## Selecionando o banco be-mean-pokemons criado na aula 02 (passo 1)

  ```
  localhost(mongod-3.2.0) test> use be-mean-pokemon
  switched to db be-mean-pokemon

  ```

## Listagem de todos os Pokemons com a altura menor que 0.5 (passo 2)

  ```
  localhost(mongod-3.2.0) be-mean-pokemon> db.pokemons.find({height: {$lt: 0.5}})
  {
    "_id": ObjectId("5691590e046a0e39d3813d5b"),
    "name": "Caterpie",
    "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
    "attack": 200,
    "defense": 200,
    "height": 0.3
  }
  Fetched 1 record(s) in 1ms

  ```

## Listagem de todos os Pokemons com a altura maior ou igual que 0.5 (passo 3)

  ```
  localhost(mongod-3.2.0) be-mean-pokemon> db.pokemons.find({height: {$gte: 0.5}})
  {
    "_id": ObjectId("569158d4046a0e39d3813d58"),
    "name": "Farfetch'd",
    "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
    "attack": 300,
    "defense": 300,
    "height": 0.8
  }
  {
    "_id": ObjectId("56915901046a0e39d3813d59"),
    "name": "Abra",
    "description": "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
    "attack": 100,
    "defense": 100,
    "height": 0.9
  }
  {
    "_id": ObjectId("56915909046a0e39d3813d5a"),
    "name": "Butterfree",
    "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
    "attack": 200,
    "defense": 200,
    "height": 1.1
  }
  {
    "_id": ObjectId("56915914046a0e39d3813d5c"),
    "name": "Squirtle",
    "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
    "attack": 300,
    "defense": 300,
    "height": 0.5
  }
  {
    "_id": ObjectId("5691591b046a0e39d3813d5d"),
    "name": "Charmander",
    "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
    "attack": 300,
    "defense": 200,
    "height": 0.6
  }
  {
    "_id": ObjectId("56915924046a0e39d3813d5e"),
    "name": "Bulbasaur",
    "description": "Bulbasaur can be seen napping in bright sunlight.",
    "attack": 300,
    "defense": 200,
    "height": 0.7
  }
  Fetched 6 record(s) in 3ms

  ```

## Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 4)

  ```
	localhost(mongod-3.2.0) be-mean-pokemon> var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]}
  localhost(mongod-3.2.0) be-mean-pokemon> db.pokemons.find(query)
  Fetched 0 record(s) in 1ms

  ```

## Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5 (passo 5)

  ```
	localhost(mongod-3.2.0) be-mean-pokemon> var query = {$or: [{name: "pikachu"}, {attack: {$lte: 0.5}}]}
  localhost(mongod-3.2.0) be-mean-pokemon> db.pokemons.find(query)
  Fetched 0 record(s) in 1ms

  ```

## Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 6)

  ```
  localhost(mongod-3.2.0) be-mean-pokemon> var query = {$and: [{height: {lte: 0.5}}, {attack: {$gte: 48}}]}
  localhost(mongod-3.2.0) be-mean-pokemon> db.pokemons.find(query)
  Fetched 0 record(s) in 1ms

  ```
    