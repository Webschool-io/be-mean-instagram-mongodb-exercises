# MongoDb - Aula 02 - Exercício
Autor: Patrick Adelino

## Criar database chamada be-mean-pokemons
  
  ```
  > use be-mean-pokemons
    switched to db be-mean-pokemons
  ```

## Listagem de todas dbs
  
  ```
  > show dbs
      local             → 0.078GB
      be-mean           → 0.078GB
      be-mean-pokemons  → 0.078GB
      be-mean-instagram → 0.078GB
  ```

## Listagem de todas as collections
  
  ```
  > show collections
  ```
## Criar cinco pokemons
    
  ```
  db.pokemons.insert({name:"Bulbasaur", description: "Bulbasaur é um pokemon pokemon do tipo planta.", attack: 100, defense:200, height:0.7})
  Inserted 1 record(s) in 1529ms
  WriteResult({
    "nInserted": 1
  })

  db.pokemons.insert({name:"Gengar", description: "Gengar é um pokemon boladão do tipo Ghost.", attack: 300, defense:300, height: 4.5})
  Inserted 1 record(s) in 2ms
  WriteResult({
    "nInserted": 1
  })

  db.pokemons.insert({name:"Steelix", description: "Evolução do Onix, versão pica e do tipo Steel.", attack: 460, defense:600, height:30.2})
  Inserted 1 record(s) in 2ms
  WriteResult({
    "nInserted": 1
  })

  db.pokemons.insert({name:"Hypno", description: "Tem um turbante na cabeça e é amarelinho.", attack: 400, defense:100, height:3.9})
  Inserted 1 record(s) in 6ms
  WriteResult({
    "nInserted": 1
  })

  db.pokemons.insert({name:"Fearow", description: "Um ave bem louca, evolução da spearow.", attack: 300, defense:300, height:7.8})
  Inserted 1 record(s) in 1ms
  WriteResult({
    "nInserted": 1
  })
  ```

## Listar todos os pokemons

  ```
  db.pokemons.find()
  { 
    "_id" : ObjectId("577945268d975db0829780bc"),
    "name" : "Bulbasaur",
    "description" : "Bulbasaur é um pokemon pokemon do tipo planta.",
    "attack" : 100,
    "defense" : 200,
    "height" : 0.7 
  }
  {
    "_id" : ObjectId("5779454d8d975db0829780bd"),
    "name" : "Gengar", 
    "description" : "Gengar é um pokemon boladão do tipo Ghost.", 
    "attack" : 300, 
    "defense" : 300, 
    "height" : 4.5 
  }
  {
   "_id" : ObjectId("577945718d975db0829780bf"), 
   "name" : "Steelix", 
   "description" : "Evolução do Onix, versão pica e do tipo Steel.", 
   "attack" : 460, 
   "defense" : 600, 
   "height" : 30.2 
  }
  { "_id" : ObjectId("577945828d975db0829780c0"), 
    "name" : "Hypno", 
    "description" : "Tem um turbante na cabeça e é amarelinho.", 
    "attack" : 400, 
    "defense" : 100, 
    "height" : 3.9 
  }
  { "_id" : ObjectId("577945948d975db0829780c1"), 
    "name" : "Fearow", 
    "description" : "Um ave bem louca, evolução da spearow.", 
    "attack" : 300, 
    "defense" : 300, 
    "height" : 7.8 
  }

  Fetched 5 record(s) in 2ms
  ```
## Buscar um pokemon

  ```
  > var query = {name: "Steelix"}
  > var poke = db.pokemons.findOne(query)
    {
     "_id" : ObjectId("577945718d975db0829780bf"), 
     "name" : "Steelix", 
     "description" : "Evolução do Onix, versão pica e do tipo Steel.", 
     "attack" : 460, 
     "defense" : 600, 
     "height" : 30.2 
    }
  ```
## Editar a description do pokemon escolhido
  
  ```
  > poke.description = "Pensa num bicho forte"
    Pensa num bicho forte

    db.pokemons.save(poke);
    Updated 1 existing record(s) in 3ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })
  ```
