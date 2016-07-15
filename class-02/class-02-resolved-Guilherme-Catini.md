# MongoDB - Aula 02 - Exercício
autor: Wallace Carvalho

## Crie uma database chamada be-mean-pokemons

    ```
    > use be-mean-pokemons
    switched to db be-mean-pokemons

    ```

## Liste quais databases você possui nesse servidor

    ```
    > show dbs
    admin  (empty)
    dbsol  0.078GB
    local  0.078GB
    teste  0.078GB

    ```
## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

    ```
    > db.pokemons.save({ 'name':'Caterpie', 'description':'Larva Lutadora', 'type':'inseto', 'attack':30, 'height':0.3, 'defense':35 })
    WriteResult({ "nInserted" : 1 })
    > db.pokemons.save({ 'name':'Snorlax', 'description':'Pokemon barra pesada', 'type':'animal', 'attack':30, 'height':0.9, 'defense':35 })
    WriteResult({ "nInserted" : 1 })
    > db.pokemons.save({ 'name':'Smooking', 'description':'Curte uma erva', 'type':'desconhecido', 'attack':30, 'height':0.3, 'defense':35 })
    WriteResult({ "nInserted" : 1 })
    > db.pokemons.save({ 'name':'Pikachu', 'description':'Pokemon que está sempre em choque', 'type':'rato', 'attack':30, 'height':0.3, 'defense':35 })
    WriteResult({ "nInserted" : 1 })
    > db.pokemons.save({ 'name':'Bulbasauro', 'description':'Javalizinho do mato', 'type':'animal', 'attack':30, 'height':0.3, 'defense':35 })
    WriteResult({ "nInserted" : 1 })

    ```    
## Liste os pokemons existentes na sua coleção

    ```
      > db.pokemons.find()
      { "_id" : ObjectId("57890bb4cbc982f056cdc90c"), "name" : "Caterpie", "description" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }
      { "_id" : ObjectId("57890bbbcbc982f056cdc90d"), "name" : "Snorlax", "description" : "Pokemon barra pesada", "type" : "animal", "attack" : 30, "height" : 0.9, "defense" : 35 }
      { "_id" : ObjectId("57890bc1cbc982f056cdc90e"), "name" : "Smooking", "description" : "Curte uma erva", "type" : "desconhecido", "attack" : 30, "height" : 0.3, "defense" : 35 }
      { "_id" : ObjectId("57890bc9cbc982f056cdc90f"), "name" : "Pikachu", "description" : "Pokemon que está sempre em choque", "type" : "rato", "attack" : 30, "height" : 0.3, "defense" : 35 }
      { "_id" : ObjectId("57890bd0cbc982f056cdc910"), "name" : "Bulbasauro", "description" : "Javalizinho do mato", "type" : "animal", "attack" : 30, "height" : 0.3, "defense" : 35 }

    ```   
## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`

    ```
      >var poke = db.pokemons.findOne({name:'Snorlax'})

    ```    
## Modifique sua `description` e salvê-o

    ```
    >poke.description = 'Pega esse gordão entãoo mlkkkkkk'
    Pega esse gordão entãoo mlkkkkkk
    > db.pokemons.save(poke)
    WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

    ```