 # MongoDB - Aula 03 - Exercício
autor: Diogo Pires Caires Silva (conta: Taise Feijo)

## 1- lista todos pokemons com altura menor que 0.5;
	> var query= {height:{$lt:0.5}}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("56452dd5cefd7b8237bd2cc4"), "name" : "Pikachu", "description" : "Pokemon fofo e tosco", "type" : "electric", "atack" : 100, "height" : 0.4 }
	



## 2- lista todos pokemons com altura maior ou igual a 0.5;
    var query= {height:{$gte:0.5}}
    > db.pokemons.find(query)
    { "_id" : ObjectId("564530ab915f674d9a28a687"), "name" : "Gengar", "description" : "Fantasma das trevas", "type" : "ghost", "atack" : 130, "height" : 1 }
    { "_id" : ObjectId("56453114915f674d9a28a688"), "name" : "Dragonite", "description" : "dragao", "type" : "dragon", "atack" : 180, "height" : 2.2 }
    { "_id" : ObjectId("5645312d915f674d9a28a689"), "name" : "venusaur", "description" : "weedmaster", "type" : "plant", "atack" : 130, "height" : 2.2 }

    

## 3- lista todos pokemons com altura menor ou igual a 0.5 e do tipo grama;
    diogo-pc(mongod-3.0.7) be-mean-pokemon> var query= {$and:[{height:{$lte:0.5}},{type:'grama'}]}
    diogo-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
    {
      "_id": ObjectId("56453cdb576ab7534715c996"),
      "name": "Odish",
      "description": "maconha mine",
      "type": "grama",
      "atack": 10,
      "height": 0.5
    }
    Fetched 1 record(s) in 1ms
    
 
## 4- lista todos pokemons com o nome pikachu ou com atack menor ou igual a 0.5
    diogo-pc(mongod-3.0.7) be-mean-pokemon> var query= {$or:[{name:'Pikachu'},{atack:{$lte:0.5}}]}
    diogo-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
    {
      "_id": ObjectId("56452dd5cefd7b8237bd2cc4"),
      "name": "Pikachu",
      "description": "Pokemon fofo e tosco",
      "type": "electric",
      "atack": 100,
      "height": 0.4
    }
    Fetched 1 record(s) in 1ms
    
## 5- lista todos pokemons com o atack maior ou igual que 48 e com height menor ou igual que 0.5
    diogo-pc(mongod-3.0.7) be-mean-pokemon> var query= {$and:[{atack:{$gte:48}},{height:{$lte:0.5}}]}
    diogo-pc(mongod-3.0.7) be-mean-pokemon> db.pokemons.find(query)
    {
      "_id": ObjectId("56452dd5cefd7b8237bd2cc4"),
      "name": "Pikachu",
      "description": "Pokemon fofo e tosco",
      "type": "electric",
      "atack": 100,
      "height": 0.4
    }
    Fetched 1 record(s) in 1ms


    


