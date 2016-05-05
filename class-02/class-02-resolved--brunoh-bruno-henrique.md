# MongoDb - Aula 02 - Exercício
Autor: Bruno Henrique C. da Silva

## Criar database chamada be-mean-pokemons

    ```
    use be-mean-pokemons
    switched to db be-mean-pokemons
    ```

## Listagem de todas dbs

    ```
    show dbs
    be-mean-instagram → 0.078GB
    local             → 0.078GB
    pokemons          → 0.078GB
    ```

## Listagem de todas as collections

    ```
    show collections
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

    db.pokemons.insert({name:"Butterfree", description: "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest.", attack: 200, defense:200, height:1.1})
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
      "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
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
    Fetched 7 record(s) in 4ms
    ```

## Buscar um pokemon

    ```
    var query = {name:"Squirtle"}
    brunoh(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
    brunoh(mongod-3.0.7) be-mean-pokemons> poke
    {
      "_id": ObjectId("567c1e5a7f749918b6358c63"),
      "name": "Squirtle",
      "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
      "attack": 300,
      "defense": 300,
      "height": 0.5
    }
    ```

## Editar a description do pokemon escolhido

    ```
    poke.description = "Squirtle's shell is not merely used for protection"
    "Squirtle's shell is not merely used for protection"

    db.pokemons.save(poke);
    Updated 1 existing record(s) in 3ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    ````