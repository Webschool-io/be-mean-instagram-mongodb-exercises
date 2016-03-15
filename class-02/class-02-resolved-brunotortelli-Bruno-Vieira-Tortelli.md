## MongoDb - Aula 02
Autor: Bruno Vieira Tortelli

### Crie uma database chamada be-mean-pokemons

    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-instagram> use be-mean-pokemons
    switched to db be-mean-pokemons
    
### Liste quais databases voce possui nesse servidor
    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> show dbs
    be-mean-instagram → 0.078GB
    bemean            → 0.078GB
    local             → 0.078GB

### Liste quais coleções voce possui nessa database
    (mongod-3.2.3) be-mean-pokemons> show collections

### Insira pelo menos 5 pokemons a sua escolha utilizando o mesmo padrao de campos utilizados: name, description, attack, defense, height
    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> db.pokemons.save({nome:'Zubat', description:'Morcego azul', attack:34, defense:28, height:0.8})
    Inserted 1 record(s) in 1ms
    WriteResult({
        "nInserted": 1
    })
    
    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> db.pokemons.save({name:'Metapod', description: 'Casulo impenetravel', attack: 10, defense:67, height:0.7})
    Inserted 1 record(s) in 1ms
    WriteResult({
        "nInserted": 1
    })
    
    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> db.pokemons.save({name:'Bergmite', description: 'Pedra pontuda brilhante', attack: 63, defense:65, height:1.1})
    Inserted 1 record(s) in 2ms
    WriteResult({
        "nInserted": 1
    })

    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> db.pokemons.save({name:'Avalugg', description: 'Iceberg sobre 4 patas', attack: 67, defense:87, height:2.0})
    Inserted 1 record(s) in 1ms
    WriteResult({
        "nInserted": 1
    })
    
    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> db.pokemons.save({name:'Noibat', description:'Morcego roxo com orelhas de chinchila', attack: 21, defense:23, height:0.5})
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })

    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> db.pokemons.save({name:'Porigon', description:'Pato poligonal', attack: 31, defense:29, height:0.8})
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })
    
### Liste os pokemons existentes na sua coleção

    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> db.pokemons.find()
    {
      "_id": ObjectId("56e0df35450a54a244425785"),
      "nome": "Zubat",
      "description": "Morcego azul",
      "attack": 34,
      "defense": 28,
      "height": 0.8
    }
    {
      "_id": ObjectId("56e0e025450a54a244425786"),
      "name": "Metapod",
      "description": "Casulo impenetravel",
      "attack": 10,
      "defense": 67,
      "height": 0.7
    }
    {
      "_id": ObjectId("56e0e804450a54a244425787"),
      "name": "Bergmite",
      "description": "Pedra pontuda brilhante",
      "attack": 63,
      "defense": 65,
      "height": 1.1
    }
    {
      "_id": ObjectId("56e0e901450a54a244425788"),
      "name": "Avalugg",
      "description": "Iceberg sobre 4 patas",
      "attack": 67,
      "defense": 87,
      "height": 2
    }
    {
      "_id": ObjectId("56e0e9e9450a54a244425789"),
      "name": "Noibat",
      "description": "Morcego roxo com orelhas de chinchila",
      "attack": 21,
      "defense": 23,
      "height": 0.5
    }
    {
      "_id": ObjectId("56e0ea88450a54a24442578a"),
      "name": "Porigon",
      "description": "Pato poligonal",
      "attack": 31,
      "defense": 29,
      "height": 0.8
    }
    Fetched 6 record(s) in 2ms

### Busque o pokemon a sua escolha pelo nome e o armazene em uma variavel chamada poke
    
    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> poke = db.pokemons.findOne({name:'Avalugg'})
    {
      "_id": ObjectId("56e0e901450a54a244425788"),
      "name": "Avalugg",
      "description": "Iceberg sobre 4 patas",
      "attack": 67,
      "defense": 87,
      "height": 2
    }


### modifique sua description e salve-o

    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> poke.description = 'Iceberg movel'
    Iceberg movel
    
    bruno-Q470C-500P4C(mongod-3.2.3) be-mean-pokemons> db.pokemons.save(poke)
    Updated 1 existing record(s) in 1ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })


    