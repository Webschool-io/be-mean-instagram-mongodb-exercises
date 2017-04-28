# MongoDB - Aula 02 - Exercício
autor: Renan Roger Ferreira da silva

## Criando Database
  ```
  use be-mean-pokemons
  switched to db be-mean-pokemons
 ```

 ## Listando as bases de dados

  ``` 
  show dbs
   admin             → 0.000GB
   be-mean           → 0.005GB
   be-mean-instagram → 0.000GB
   local             → 0.000GB
   teste             → 0.005GB

            
  ```

  ## Listando as collections
    ```
           show collections
   renan-pc(mongod-3.4.3) be-mean-pokemons>
    ```

  ## Cadastro dos pokemons 
    ```
    renan-pc(mongod-3.4.3) be-mean-pokemon> var pokemons= [{"name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4 },{"name" : "charmander", "description" : "Raio cabuloso de fogo", "type": "fire", "attack" : 60, "height" : 0.5},{"name" : "charlizard", "description" : "Dragon modafoka", "type": "fire", "attack" : 99, "height" : 1.2},{"name" : "Blastoise", "description" : "Mega tartaruga bolada", "type": "water", "attack" : 99, "height" : 1.5},{"name" : "gree-ninja", "description" : "Ninjaao das sombras", "type": "ninja", "attack" : 85, "height" : 1.2}]
      
      renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.insert(pokemons)
      Inserted 1 record(s) in 252ms
      BulkWriteResult({
        "writeErrors": [ ],
        "writeConcernErrors": [ ],
        "nInserted": 5,
        "nUpserted": 0,
        "nMatched": 0,
        "nModified": 0,
        "nRemoved": 0,
        "upserted": [ ]
      })


    ```
  ## Listagem dos pokemons

   ```
  renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.find()

      {
  "_id": ObjectId("5903895dc663a59d8b11b95d"),
  "name": "Pikachu",
  "description": "Raio eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5903895dc663a59d8b11b95e"),
  "name": "charmander",
  "description": "Raio cabuloso de fogo",
  "type": "fire",
  "attack": 60,
  "height": 0.5
}
{
  "_id": ObjectId("5903895dc663a59d8b11b95f"),
  "name": "charlizard",
  "description": "Dragon modafoka",
  "type": "fire",
  "attack": 99,
  "height": 1.2
}
{
  "_id": ObjectId("5903895dc663a59d8b11b960"),
  "name": "Blastoise",
  "description": "Mega tartaruga bolada",
  "type": "water",
  "attack": 99,
  "height": 1.5
}
{
  "_id": ObjectId("5903895dc663a59d8b11b961"),
  "name": "gree-ninja",
  "description": "Ninjaao das sombras",
  "type": "ninja",
  "attack": 85,
  "height": 1.2
}

   ```

   ## Listar 1 pokemon apenas
   ```
      renan-pc(mongod-3.4.3) be-mean-pokemon>var poke= db.pokemons.findOne(query);
{
  "_id": ObjectId("5903895dc663a59d8b11b961"),
  "name": "gree-ninja",
  "description": "Ninjaao das sombras",
  "type": "ninja",
  "attack": 85,
  "height": 1.2
}
    
   ```
  ## Atualização do pokemon

   ```
      renan-pc(mongod-3.4.3) be-mean-pokemon> ninja.description
      Ninjaao das sombras
      renan-pc(mongod-3.4.3) be-mean-pokemon> ninja.description = "ninjao trevoso"
      renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.save(ninja)
	  Updated 1 existing record(s) in 30ms
      WriteResult({
  		"nMatched": 1,
  		"nUpserted": 0,
  		"nModified": 1
  	})
   
       
   ``` 

