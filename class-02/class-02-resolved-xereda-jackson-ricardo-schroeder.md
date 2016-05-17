# MongoDb - Aula 02 - Exercício
Autor: Jackson Ricardo Schroeder

## Criar database chamada be-mean-pokemons

    ```
    macminixereda(mongod-3.2.0) local> use be-mean-pokemons
    switched to db be-mean-pokemons

    ```

## Listagem de todas dbs

  ```
  macminixereda(mongod-3.2.0) be-mean-pokemons> show dbs
  be-mean           → 0.004GB
  be-mean-instagram → 0.000GB
  local             → 0.000GB
  test              → 0.000GB
  ```

## Listagem de todas as collections

    ```
    macminixereda(mongod-3.2.0) be-mean-pokemons> show collections
    macminixereda(mongod-3.2.0) be-mean-pokemons>
    ```

## Criar cinco pokemons

    ```
    macminixereda(mongod-3.2.0) be-mean-pokemons> var pokemon = { name: "Raichu", description: "Raichu era um cara bem legal", type: "Eletric", height: 0.79, attack: 235, defense: 321  };
    macminixereda(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon);
    Inserted 1 record(s) in 527ms
    WriteResult({
      "nInserted": 1
    })

    macminixereda(mongod-3.2.0) be-mean-pokemons> var pokemon = { name: "Magnemite", description: "Magnemite is an Electric/Steel type Pokémon introduced in Generation 1. It is known as the Magnet Pokémon.", type: "Eletric", height: 0.3, attack: 35, defense: 70 };
    macminixereda(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon);
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })

    macminixereda(mongod-3.2.0) be-mean-pokemons> var pokemon = { name: "Magneton", description: "Magneton is an Electric/Steel type Pokémon introduced in Generation 1. It is known as the Magnet Pokémon.", type: "Eletric", height: 0.99, attack: 60, defense: 95 };
    macminixereda(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon);
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })

    macminixereda(mongod-3.2.0) be-mean-pokemons> var pokemon = { name: "Voltorb", description: "Voltorb is an Electric type Pokémon introduced in Generation 1. It is known as the Ball Pokémon.", type: "Eletric", height: 0.51, attack: 30, defense: 50 };
    macminixereda(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon);
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })

    macminixereda(mongod-3.2.0) be-mean-pokemons> var pokemon = { name: "Electrode", description: "Electrode is an Electric type Pokémon introduced in Generation 1. It is known as the Ball Pokémon.", type: "Eletric", height: 1.19, attack: 50, defense: 70 };
    macminixereda(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(pokemon);
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })
    ```

## Listar todos os pokemons

    ```
    macminixereda(mongod-3.2.0) be-mean-pokemons> db.pokemons.find();
    {
      "_id": ObjectId("573aa08f24450f724f323f1a"),
      "name": "Raichu",
      "description": "Raichu era um cara bem legal",
      "type": "Eletric",
      "height": 0.79,
      "attack": 235,
      "defense": 321
    }
    {
      "_id": ObjectId("573aa15124450f724f323f1b"),
      "name": "Magnemite",
      "description": "Magnemite is an Electric/Steel type Pokémon introduced in Generation 1. It is known as the Magnet Pokémon.",
      "type": "Eletric",
      "height": 0.3,
      "attack": 35,
      "defense": 70
    }
    {
      "_id": ObjectId("573aa1b724450f724f323f1c"),
      "name": "Magneton",
      "description": "Magneton is an Electric/Steel type Pokémon introduced in Generation 1. It is known as the Magnet Pokémon.",
      "type": "Eletric",
      "height": 0.99,
      "attack": 60,
      "defense": 95
    }
    {
      "_id": ObjectId("573aa20b24450f724f323f1d"),
      "name": "Voltorb",
      "description": "Voltorb is an Electric type Pokémon introduced in Generation 1. It is known as the Ball Pokémon.",
      "type": "Eletric",
      "height": 0.51,
      "attack": 30,
      "defense": 50
    }
    {
      "_id": ObjectId("573aa49124450f724f323f20"),
      "name": "Electrode",
      "description": "Electrode is an Electric type Pokémon introduced in Generation 1. It is known as the Ball Pokémon.",
      "type": "Eletric",
      "height": 1.19,
      "attack": 50,
      "defense": 70
    }
    Fetched 5 record(s) in 2ms
    ```

## Buscar um pokemon

    ```
    macminixereda(mongod-3.2.0) be-mean-pokemons> var query = {name: "Electrode"};
    macminixereda(mongod-3.2.0) be-mean-pokemons> var poke = db.pokemons.findOne(query);
    macminixereda(mongod-3.2.0) be-mean-pokemons> poke
    {
      "_id": ObjectId("573aa49124450f724f323f20"),
      "name": "Electrode",
      "description": "Electrode is an Electric type Pokémon introduced in Generation 1. It is known as the Ball Pokémon.",
      "type": "Eletric",
      "height": 1.19,
      "attack": 50,
      "defense": 70
    }
    ```

## Editar a description do pokemon escolhido

    ```
    macminixereda(mongod-3.2.0) be-mean-pokemons> var poke = db.pokemons.findOne(query);
    macminixereda(mongod-3.2.0) be-mean-pokemons> poke
    {
      "_id": ObjectId("573aa49124450f724f323f20"),
      "name": "Electrode",
      "description": "Electrode is an Electric type Pokémon introduced in Generation 1. It is known as the Ball Pokémon.",
      "type": "Eletric",
      "height": 1.19,
      "attack": 50,
      "defense": 70
    }
    macminixereda(mongod-3.2.0) be-mean-pokemons> poke.description = "Alterando a descrição do pokemon";
    Alterando a descrição do pokemon
    macminixereda(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(poke);
    Updated 1 existing record(s) in 47ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
    macminixereda(mongod-3.2.0) be-mean-pokemons> db.pokemons.find({ name: "Electrode"  });
    {
      "_id": ObjectId("573aa49124450f724f323f20"),
      "name": "Electrode",
      "description": "Alterando a descrição do pokemon",
      "type": "Eletric",
      "height": 1.19,
      "attack": 50,
      "defense": 70
    }
    Fetched 1 record(s) in 0ms
    ````
