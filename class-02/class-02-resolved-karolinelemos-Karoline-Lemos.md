# MongoDB - Aula 02 - Exercício
autor: Karoline Lemos

## Criando a database

...

mongo be-mean-pokemons

...

## Listando Databases  

...

show dbs

be-mean           → 0.005GB

be-mean-instagram → 0.000GB

local             → 0.000GB

...

## Listando Collections  

...

show collections

...

## Cadastrando Pokemons  

...

var pokemon4 = {name: 'Psyduck', description: 'Patinho legal', type: 'água', attack: 30, height: 0.8}  

db.pokemons.insert(pokemon4)  

Inserted 1 record(s) in 1ms  

WriteResult({  

  "nInserted": 1  

})  

var pokemon = {name: 'Poliwag', description: 'Bolinha hipnotizante', type: 'água', attack: 30, height: 0.6}  

db.pokemons.insert(pokemon)  

Inserted 1 record(s) in 2ms 

WriteResult({  

  "nInserted": 1  

})  

var pokemon1 = {name: 'Clefairy', description: 'Fofurinha rosa', type: 'fada', attack: 20, height: 0.6}

db.pokemons.insert(pokemon1) 

Inserted 1 record(s) in 1ms  

WriteResult({  

  "nInserted": 1  

})

var pokemon2 = {name: 'Jigglypuff', description: 'Bolinha rosa hiper fofa', type: 'fada', attack: 20, height: 0.5}  

db.pokemons.insert(pokemon2) 

Inserted 1 record(s) in 1ms  

WriteResult({  

  "nInserted": 1  

})  

var pokemon3 = {name: 'Vileplume', description: 'Flor loka', type: 'grama', attack: 40, height: 1.2}  

db.pokemons.insert(pokemon3)  

Inserted 1 record(s) in 1ms 

WriteResult({  

  "nInserted": 1  

})  

...

## Listagem dos Pokemons  

...

db.pokemons.find()  

{  
  "_id": ObjectId("5780c372dede126c95d4da3e"),  

  "name": "Psyduck",  

  "description": "Patinho legal",  

  "type": "água",  

  "attack": 30,  

  "height": 0.8  
}  
{  
  "_id": ObjectId("5780c39ddede126c95d4da3f"), 

  "name": "Poliwag",  

  "description": "Bolinha hipnotizante",  

  "type": "água",  

  "attack": 30,  

  "height": 0.6  
}  
{  
  "_id": ObjectId("5780c449bd368739f35ad5d3"),  

  "name": "Clefairy",  

  "description": "Fofurinha rosa",  

  "type": "fada",  

  "attack": 20,  

  "height": 0.6  
}  
{  
  "_id": ObjectId("5780c453bd368739f35ad5d4"),  

  "name": "Jigglypuff",  

  "description": "Bolinha rosa hiper fofa",  

  "type": "fada",  

  "attack": 20,  

  "height": 0.5  
}  
{  
  "_id": ObjectId("5780c462bd368739f35ad5d5"), 

  "name": "Vileplume",  

  "description": "Flor loka", 

  "type": "grama",  

  "attack": 40,  

  "height": 1.2  
}  

... 

## Buscando Pokemon  

...

var busca = {name: 'Clefairy'}  

var poke = db.pokemons.findOne(busca)  

poke  

{  
  "_id": ObjectId("5780c449bd368739f35ad5d3"), 

  "name": "Clefairy",  

  "description": "Fofurinha rosa",  

  "type": "fada", 

  "attack": 20, 

  "height": 0.6  
}  

... 

## Atualizando a descrição  

...

poke.description = 'Fofuuuuuuurinha' 

Fofuuuuuuurinha  

db.pokemons.save(poke)  

Updated 1 existing record(s) in 2ms  

WriteResult({  
  "nMatched": 1,  

  "nUpserted": 0, 

  "nModified": 1  
})  

...

