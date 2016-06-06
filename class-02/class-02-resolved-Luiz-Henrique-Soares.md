# MongoDb - Aula 02 - Exercício
Autor: Luiz Henrique Soares

## Criar database chamada be-mean-pokemons

    ```
   MongoDB shell version: 3.2.6
	connecting to: test
	use be-mean-pokemons
	switched to db be-mean-pokemons
    ```

## Listagem de todas dbs

  ```
  show dbs
  be-mean    0.005GB
  curso_son  0.000GB
  local      0.000GB
  ```

## Listagem de todas as collections

    ```
    show collections
    pokemon      →  0.001MB / 0.035MB
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

    ```

## Listar todos os pokemons

    ```
    { "_id" : ObjectId("5755e6c091e61aa6dbc5c10b"), "name" : "Bulbasaur", "description" : "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.", "attack" : 300, "defense" : 200, "height" : 0.7 }
   
	{ "_id" : ObjectId("5755e7cb2f92092e978764f7"), "name" : "Abra", "description" : "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.", "attack" : 100, "defense" : 100, "height" : 0.9 }

	{ "_id" : ObjectId("5755e7e62f92092e978764f8"), "name" : "Charmander", "description" : "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.", "attack" : 300, "defense" : 200, "height" : 0.6 }

	{ "_id" : ObjectId("5755e8022f92092e978764f9"), "name" : "Squirtle", "description" : "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.", "attack" : 300, "defense" : 300, "height" : 0.5 }

	{ "_id" : ObjectId("5755e80f2f92092e978764fa"), "name" : "Caterpie", "description" : "Caterpie has a voracious appetite. It can devour leaves bigger than its body right before your eyes. From its antenna, this Pokémon releases a terrifically strong odor.", "attack" : 200, "defense" : 200, "height" : 0.3 }
    ```

## Buscar um pokemon

    ```
   db.pokemons.findOne({"name":"Abra"})
{
        "_id" : ObjectId("5755e7cb2f92092e978764f7"),
        "name" : "Abra",
        "description" : "Abra sleeps for eighteen hours a day. However, it can sense the presence of foes even while it is sleeping. In such a situation, this Pokémon immediately teleports to safety.",
        "attack" : 100,
        "defense" : 100,
        "height" : 0.9
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
