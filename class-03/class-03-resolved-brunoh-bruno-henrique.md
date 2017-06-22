# MongoDB - Aula 03 - Exercício
autor: Bruno Henrique C. da Silva

## Liste todos Pokemons com a altura **menor que** 0.5;
    ```
    var query = {height:{$lt:0.5}}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("567c1e847f749918b6358c64"),
      "name": "Caterpie",
      "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
      "attack": 200,
      "defense": 200,
      "height": 0.3
    }
    Fetched 1 record(s) in 1ms
    ```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

    ```
    var query = {height:{$gte:0.5}}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("567c1da87f749918b6358c61"),
      "name": "Bulbasaur",
      "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
      "attack": 300,
      "defense": 200,
      "height": 0.7
    }
    {
      "_id": ObjectId("567c1e0b7f749918b6358c62"),
      "name": "Charmander",
      "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
      "attack": 300,
      "defense": 200,
      "height": 0.6
    }
    {
      "_id": ObjectId("567c1e5a7f749918b6358c63"),
      "name": "Squirtle",
      "description": "Squirtle's shell is not merely used for protection",
      "attack": 300,
      "defense": 300,
      "height": 0.5
    }
    {
      "_id": ObjectId("567c1eb17f749918b6358c65"),
      "name": "Butterfree",
      "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.",
      "attack": 200,
      "defense": 200,
      "height": 1.1
    }
    {
      "_id": ObjectId("567c1eec7f749918b6358c66"),
      "name": "Abra",
      "description": "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
      "attack": 100,
      "defense": 100,
      "height": 0.9
    }
    {
      "_id": ObjectId("567c1f167f749918b6358c67"),
      "name": "Farfetch'd",
      "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
      "attack": 300,
      "defense": 300,
      "height": 0.8
    }
    Fetched 6 record(s) in 8ms
    ``

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
    ps: nao tinha tipo no meu db, entao fiz uma consulta entre a altura dos pokemons

    ```
    var query = {$and: [{height:{$gte:0.3}}, {height:{$lt:1.1}}]}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("567c1da87f749918b6358c61"),
      "name": "Bulbasaur",
      "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
      "attack": 300,
      "defense": 200,
      "height": 0.7
    }
    {
      "_id": ObjectId("567c1e0b7f749918b6358c62"),
      "name": "Charmander",
      "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
      "attack": 300,
      "defense": 200,
      "height": 0.6
    }
    {
      "_id": ObjectId("567c1e5a7f749918b6358c63"),
      "name": "Squirtle",
      "description": "Squirtle's shell is not merely used for protection",
      "attack": 300,
      "defense": 300,
      "height": 0.5
    }
    {
      "_id": ObjectId("567c1e847f749918b6358c64"),
      "name": "Caterpie",
      "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
      "attack": 200,
      "defense": 200,
      "height": 0.3
    }
    {
      "_id": ObjectId("567c1eec7f749918b6358c66"),
      "name": "Abra",
      "description": "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
      "attack": 100,
      "defense": 100,
      "height": 0.9
    }
    {
      "_id": ObjectId("567c1f167f749918b6358c67"),
      "name": "Farfetch'd",
      "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
      "attack": 300,
      "defense": 300,
      "height": 0.8
    }
    Fetched 6 record(s) in 9ms
    ```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

    ```
    var query = {$or:[{name:"Pikachu"}, {attack:{$lte:0.5}}]}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("567c5b7f7727e498f0898db4"),
      "name": "Pikachu",
      "description": "Cachorro do ashe",
      "attack": 350,
      "defense": 300,
      "height": 0.7
    }
    Fetched 1 record(s) in 3ms
    ```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

    ```
    var query = {$and:[{attack:{$gte:48}}, {height:{$lte:0.5}}]}
    brunoh(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
    {
      "_id": ObjectId("567c1e5a7f749918b6358c63"),
      "name": "Squirtle",
      "description": "Squirtle's shell is not merely used for protection",
      "attack": 300,
      "defense": 300,
      "height": 0.5
    }
    {
      "_id": ObjectId("567c1e847f749918b6358c64"),
      "name": "Caterpie",
      "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
      "attack": 200,
      "defense": 200,
      "height": 0.3
    }
    Fetched 2 record(s) in 1ms
    ```