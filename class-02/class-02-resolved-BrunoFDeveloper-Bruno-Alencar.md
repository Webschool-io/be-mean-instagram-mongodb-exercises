# MongoDb - Aula 02 - Exercício
Autor: Bruno Alencar

## Criar database chamada be-mean-pokemons

    ```
    use be-mean-pokemons
    switched to db be-mean-pokemons
    ```

## Listagem de todas dbs

  ```
  show dbs
  be-mean           → 0.004GB
  be-mean-instagram → 0.004GB
  local             → 0.000GB
  mean-dev          → 0.000GB
  test              → 0.000GB
  ```

## Listagem de todas as collections

    ```
    show collections
    pokemon      →  0.001MB / 0.035MB
    pokemons     →  0.002MB / 0.035MB
    restaurantes → 10.138MB / 3.914MB
    test         →  0.000MB / 0.031MB
    ```

## Criar cinco pokemons

    ```
    db.pokemons.insert({name:"Bulbasaur", description: "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", attack: 300, defense:200, height:0.7})
    Inserted 1 record(s) in 1549ms
    WriteResult({
      "nInserted": 1
    })

    db.pokemons.insert({name:"Charmander", description: "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.", attack: 300, defense:200, height:0.6})
    Inserted 1 record(s) in 2ms
    WriteResult({
      "nInserted": 1
    })

    db.pokemons.insert({name:"Squirtle", description: "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.", attack: 300, defense:300, height:0.5})
    Inserted 1 record(s) in 2ms
    WriteResult({
      "nInserted": 1
    })

    db.pokemons.insert({name:"Caterpie", description: "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.", attack: 200, defense:200, height:0.3})
    Inserted 1 record(s) in 2ms
    WriteResult({
      "nInserted": 1
    })

    db.pokemons.insert({name:"Abra", description: "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.", attack: 100, defense:100, height:0.9})
    Inserted 1 record(s) in 6ms
    WriteResult({
      "nInserted": 1
    })

    db.pokemons.insert({name:"Farfetch'd", description: "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.", attack: 300, defense:300, height:0.8})
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })
    ```

## Listar todos os pokemons

    ```
    db.pokemons.find()
    {
      "_id": ObjectId("56d4411ecb9fc33af447ab7b"),
      "name": "Charmander",
      "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
      "attack": 300,
      "defense": 200,
      "height": 0.6
    }
    {
      "_id": ObjectId("56d44146cb9fc33af447ab7c"),
      "name": "Bulbasaur",
      "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
      "attack": 300,
      "defense": 200,
      "height": 0.7
    }
    {
      "_id": ObjectId("56d4414dcb9fc33af447ab7d"),
      "name": "Squirtle",
      "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
      "attack": 300,
      "defense": 300,
      "height": 0.5
    }
    {
      "_id": ObjectId("56d44154cb9fc33af447ab7e"),
      "name": "Caterpie",
      "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
      "attack": 200,
      "defense": 200,
      "height": 0.3
    }
    {
      "_id": ObjectId("56d44164cb9fc33af447ab7f"),
      "name": "Abra",
      "description": "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
      "attack": 100,
      "defense": 100,
      "height": 0.9
    }
    {
      "_id": ObjectId("56d44169cb9fc33af447ab80"),
      "name": "Farfetch'd",
      "description": "Farfetch'd is always seen with a stalk from a plant of some sort. Apparently, there are good stalks and bad stalks. This Pokémon has been known to fight with others over stalks.",
      "attack": 300,
      "defense": 300,
      "height": 0.8
    }
    ```

## Buscar um pokemon

    ```
    MacBook-Pro-de-bruno(mongod-3.2.0) be-mean-pokemons> var query = {name: 'Caterpie'}
    MacBook-Pro-de-bruno(mongod-3.2.0) be-mean-pokemons> var p = db.pokemons.findOne(query)
    MacBook-Pro-de-bruno(mongod-3.2.0) be-mean-pokemons> p
    {
      "_id": ObjectId("56d44154cb9fc33af447ab7e"),
      "name": "Caterpie",
      "description": "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.",
      "attack": 200,
      "defense": 200,
      "height": 0.3
    }
    ```

## Editar a description do pokemon escolhido

    ```
    poke.description = "Change here"

    db.pokemons.save(poke);
    Updated 1 existing record(s) in 3ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    ````