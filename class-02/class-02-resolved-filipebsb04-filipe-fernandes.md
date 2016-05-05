# MongoDB - Aula 02 - Exercício 
autor: Filipe Fernandes


## Criação da database chamada be-mean-pokemons;
	> use be-mean-pokemons
	switched to db be-mean-pokemons

## Listagem das databases (passo 2)
	> show dbs
	be-mean            0.078GB
	be-mean-instagram  0.078GB
	local              0.078GB

## Listagem das coleções (passo 3)
	> show collections
	>

## Cadastro dos pokemons (passo 4)
	> var pokemons = [
	...    {
	...   name: 'Geodude',
	...   description: 'O COISA quando era apenas uma bebê',
	...   type: 'rock',
	...   attack: 80,
	...   height: 4
	...    },
	...    {
	...   name: 'Graveler',
	...   description: 'O COISA adolescente',
	...   type: 'rock',
	...   attack: 95,
	...   height: 10
	...    },
	...    {
	...   name: 'Golem',
	...   description: 'O COISA aposentado e bem gordinho',
	...   type: 'rock',
	...   attack: 120,
	...   height: 14
	...    },
	...    {
	...   name: 'Charmander',
	...   description: 'Dradãozinho com fogo no rabo',
	...   type: 'fire',
	...   attack: 52,
	...   height: 6
	...    },
	...    {
	...   name: 'Charmeleon',
	...   description: 'Dradão chifrudo com fogo no rabo',
	...   type: 'fire',
	...   attack: 64,
	...   height: 11
	...    },
	...    {
	...   name: 'Butterfree',
	...   description: 'Borboleta Fofinha',
	...   type: 'flying',
	...   attack: 45,
	...   height: 11
	...    },
	...    {
	...   name: 'Beedrill',
	...   description: '',
	...   type: 'poison',
	...   attack: 90,
	...   height: 10
	...    }
	...    ]
	
	> db.pokemons.insert(pokemons)
	BulkWriteResult({
			"writeErrors" : [ ],
			"writeConcernErrors" : [ ],
			"nInserted" : 7,
			"nUpserted" : 0,
			"nMatched" : 0,
			"nModified" : 0,
			"nRemoved" : 0,
			"upserted" : [ ]
	})
	>
	

## Lista dos pokemons (passo 5)
	> db.pokemons.find()                                                                                                                                                    
	{ "_id" : ObjectId("564501949e4bc1df5f028898"), "name" : "Geodude", "description" : "O COISA quando era apenas uma bebê", "type" : "rock", "attack" : 80, "height" : 4 }
							
	{ "_id" : ObjectId("564501949e4bc1df5f028899"), "name" : "Graveler", "description" : "O COISA adolescente", "type" : "rock", "attack" : 95, "height" : 10 }             
	
	{ "_id" : ObjectId("564501949e4bc1df5f02889a"), "name" : "Golem", "description" : "O COISA aposentado e bem gordinho", "type" : "rock", "attack" : 120, "height" : 14 } 
	
	{ "_id" : ObjectId("564501949e4bc1df5f02889b"), "name" : "Charmander", "description" : "Dradãozinho com fogo no rabo", "type" : "fire", "attack" : 52, "height" : 6 }   
	
	{ "_id" : ObjectId("564501949e4bc1df5f02889c"), "name" : "Charmeleon", "description" : "Dradão chifrudo com fogo no rabo", "type" : "fire", "attack" : 64, "height" :11}  
	
	{ "_id" : ObjectId("564501949e4bc1df5f02889d"), "name" : "Butterfree", "description" : "Borboleta Fofinha", "type" : "flying", "attack" : 45, "height" : 11 }           
	
	{ "_id" : ObjectId("564501949e4bc1df5f02889e"), "name" : "Beedrill", "description" : "", "type" : "poison", "attack" : 90, "height" : 10}
	>
	
	
## pokemon escolhido (passo 6)
	> var poke = db.pokemons.findOne({name: 'Beedrill'});   
	> poke                                                  
	{                                                       
			"_id" : ObjectId("564501949e4bc1df5f02889e"),   
			"name" : "Beedrill",                            
			"description" : "",                             
			"type" : "poison",                              
			"attack" : 90,                                  
			"height" : 10                                   
	}                                                       
	>                                                       


## Atualização do pokemon escolhido (passo 7)
	> poke.description = 'Vilão do Homem Formiga'
	Vilão do Homem Formiga
	> poke
	{
			"_id" : ObjectId("564501949e4bc1df5f02889e"),
			"name" : "Beedrill",
			"description" : "Vilão do Homem Formiga",
			"type" : "poison",
			"attack" : 90,
			"height" : 10
	}
	>
	
	> db.pokemons.save(poke)
	WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
	> poke
	{
			"_id" : ObjectId("564501949e4bc1df5f02889e"),
			"name" : "Beedrill",
			"description" : "Vilão do Homem Formiga",
			"type" : "poison",
			"attack" : 90,
			"height" : 10
	}
	>


http://www.pokemon.com/us/pokedex/butterfree
http://pokeapi.co/