# MongoDB - Aula 03 - Exercício
autor: Matheus Joveliano

## Liste todos Pokemons com a altura menor que 0.5

...
> use be-mean-pokemons
switched to db be-mean-pokemons
> var query = { height:{$lt : 0.5}}
> db.pokemon.find(query)
	{ 
		"_id" : ObjectId("564789549a9dcf2bfbb59860"),
	 	"name" : "Charmander",
	  	"description" : "Pokemons 02",
	   	"attack" : 50,
	    "defense" : 50,
	    "height" : 0.4,
	    "type" : "fogo"
	}
	{ 
		"_id" : ObjectId("564789e09a9dcf2bfbb59862"),
	 	"name" : "Abra",
	  	"description" : "Pokemon 04 - Modificado",
	   	"attack" : 35,
	    "defense" : 30,
	    "height" : 0.4,
	    "type" : "fantasma"
	}
...

## Liste todos Pokemons com a altura maior ou igual que 0.5

...
> var query = { height:{$lte:0.5}}
> db.pokemon.find(query)
	{ 
		"_id" : ObjectId("564789109a9dcf2bfbb5985f"),
	 	"name" : "Bulbasaur",
	  	"description" : "Pokemons 01",
	   	"attack" : 49,
	    "defense" : 49,
	    "height" : 0.5,
	    "type" : "grama"
	}
	{
	 	"_id" : ObjectId("564789549a9dcf2bfbb59860"),
	 	"name" : "Charmander",
	   	"description" : "Pokemons 02",
	    "attack" : 50, 
	    "defense" : 50,
	    "height" : 0.4,
	    "type" : "fogo"
	}
	{
	 	"_id" : ObjectId("564789e09a9dcf2bfbb59862"), 
	 	"name" : "Abra", 
	 	"description" : "Pokemon 04 - Modificado", 
	 	"attack" : 35,
	 	"defense" : 30, 
	  	"height" : 0.4,
	  	"type" : "fantasma"
	}
...

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

...
> var query = { $and :[{ "height": {$lte: 0.5 }  }, { "type":"grama"}] }
> db.pokemon.find(query)
	{ 
		"_id" : ObjectId("564789109a9dcf2bfbb5985f"),
	    "name" : "Bulbasaur",
	    "description" : "Pokemons 01",
	    "attack" : 49,
	    "defense" : 49,
	    "height" : 0.5,
	    "type" : "grama"
	}
...

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5

...
> var query = { $or :[{"name":"Abra"}, {"attack": {$lte: 0.5}}]}
> db.pokemon.find(query)
	{ 
		"_id" : ObjectId("564789e09a9dcf2bfbb59862"),
		"name" : "Abra",
		"description" : "Pokemon 04 - Modificado",
		"attack" : 35,
		"defense" : 30,
		"height" : 0.4,
		"type" : "fantasma"
	}
...

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5

...
> var query = { $and :[{height:{$lte: 0.5}}, {attack:{$gte: 48}}]}
> db.pokemon.find(query)
	{ 
		"_id" : ObjectId("564789109a9dcf2bfbb5985f"),
		"name" : "Bulbasaur",
	  	"description" : "Pokemons 01",
	   	"attack" : 49,
	    "defense" : 49,
	    "height" : 0.5,
	     "type" : "grama"
	}
	{ 
		"_id" : ObjectId("564789549a9dcf2bfbb59860"),
	 	"name" : "Charmander",
	  	"description" : "Pokemons 02",
	   	"attack" : 50,
	    "defense" : 50,
	    "height" : 0.4, 
	    "type" : "fogo" 
	}
...
