# MongoDB - Aula 03 - Exercício
autor: Renan Roger Ferreira da silva

## 1º Listando os pokemons menores que 0.5

  ```
  var query = {height:{$lt:0.5}}
  db.pokemons.find(query)

  "_id": ObjectId("5903895dc663a59d8b11b95d"),
  "name": "Pikachu",
  "description": "Raio eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "hei
  ```
## 2º Listando os pokemons com autura maior ou igual que 0.5
 ``` 
   renan-pc(mongod-3.4.3) be-mean-pokemon> var query = {height:{$gte:0.5}}
renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.find(query)
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
  "description": "ninjao trevoso",
  "type": "ninja",
  "attack": 85,
  "height": 1.2
}
  ``` 
  ## 3º Listando os pokemons com autura menor ou igual que 0.5 e do tipo fire

  ```
     renan-pc(mongod-3.4.3) be-mean-pokemon> var query = {$and:[{height:{$lte:0.5}},{type: "fire"}]}
     renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.find(query)
     {
       "_id": ObjectId("5903895dc663a59d8b11b95e"),
       "name": "charmander",
       "description": "Raio cabuloso de fogo",
       "type": "fire",
       "attack": 60,
       "height": 0.5
     }
     
  ```
 ## 4º Listando todos os pokemons com name pikachu ou com atack menor ou igual a 0.5
  ```
   renan-pc(mongod-3.4.3) be-mean-pokemon> var query = {$or:[{name:"pikachu"},{attack:{$lte:0.5}}]}
 -pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.find(query)
        Fetched 0 record(s) in 1ms

  ```

  ## 5º listando todos os pokemons com o atack maior ou igual que 48 e com height menor ou igual a 0.5
  ```
  renan-pc(mongod-3.4.3) be-mean-pokemon> var query = {$and:[{attack:{$gte:48}},{heigt:{$lte:0.5}}]}
  renan-pc(mongod-3.4.3) be-mean-pokemon> db.pokemons.find(query)
  Fetched 0 record(s) in 1ms
   
  ```