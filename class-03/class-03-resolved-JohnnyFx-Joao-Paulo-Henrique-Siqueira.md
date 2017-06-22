# MongoDB - Aula 03 - Exercício
autor: João Siqueira

##Liste todos Pokemons com a altura menor que 0.5
```
	var query = {height: {$lte:0.5}}
	be-mean-pokemons> db.pokemons.find(query)
		{
		  "_id": ObjectId("56479cb080f0fae6f6c988b6"),
		  "name": "Ratata",
		  "description": "Rato com poder",
		  "type": "normal",
		  "attack": 30,
		  "defense": 35,
		  "height": 0.3
		}

``` 

## Liste todos Pokemons com a altura maior ou igual que 0.5
```
	var query = {height: {$gte:0.5}}
	be-mean-pokemons> db.pokemons.find(query)
		{
		  "_id": ObjectId("5645554a40e9fbb07dd1c3c4"),
		  "name": "Charizard",
		  "description": "Avoa e cospe fogo? C é o bixão memo hein",
		  "type": "fogo",
		  "attack": 84,
		  "defense": 78,
		  "height": 1.7
		}
		{
		  "_id": ObjectId("5645554a40e9fbb07dd1c3c5"),
		  "name": "Alakazam",
		  "description": "QI de 9000, mas nao fala 2 palavras",
		  "type": "Psychic",
		  "attack": 50,
		  "defense": 45,
		  "height": 1.5
		}
		{
		  "_id": ObjectId("5645554a40e9fbb07dd1c3c6"),
		  "name": "Rayquaza",
		  "description": "Lagartão que avua",
		  "type": "dragon/fly",
		  "attack": 150,
		  "defense": 90,
		  "height": 7.001
		}
		{
		  "_id": ObjectId("5645554a40e9fbb07dd1c3c7"),
		  "name": "Pidgeot",
		  "description": "Baita de uma ave, digassi de passagi",
		  "type": "normal/fly",
		  "attack": 80,
		  "defense": 75,
		  "height": 1.5
		}
		{
		  "_id": ObjectId("5645554a40e9fbb07dd1c3c8"),
		  "name": "Ninetales",
		  "description": "Cachorrão lindo",
		  "type": "fire",
		  "attack": 76,
		  "defense": 75,
		  "height": 1.09,
		  "power": 59
		}
Fetched 5 record(s) in 2ms

```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
``
	var query = {$and: [{height: {$lte:0.5}},{'type':"grass"}]}
	db.pokemons.find(query)
	

	{
	  "_id": ObjectId("5647a1b280f0fae6f6c988b7"),
	  "name": "Oddish",
	  "description": "Planta que dá barato",
	  "type": "grass",
	  "attack": 45,
	  "defense": 55,
	  "height": 0.5
	}
	Fetched 1 record(s) in 0ms

	```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 50
```
 	var query = {$or: [{'name':'Pikachu'},{attack: {$lte:50}}]}
	db.pokemons.find(query)
	{
	  "_id": ObjectId("5645554a40e9fbb07dd1c3c5"),
	  "name": "Alakazam",
	  "description": "QI de 9000, mas nao fala 2 palavras",
	  "type": "Psychic",
	  "attack": 50,
	  "defense": 45,
	  "height": 1.5
	}
	{
	  "_id": ObjectId("56479cb080f0fae6f6c988b6"),
	  "name": "Ratata",
	  "description": "Rato com poder",
	  "type": "normal",
	  "attack": 30,
	  "defense": 35,
	  "height": 0.3
	}
	{
	  "_id": ObjectId("5647a1b280f0fae6f6c988b7"),
	  "name": "Oddish",
	  "description": "Planta que dá barato",
	  "type": "grass",
	  "attack": 45,
	  "defense": 55,
	  "height": 0.5
	}
	Fetched 3 record(s) in 2ms

```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
	var query = {$and: [{attack : {$gte:48}},{height: {$lte:1.5}}]}
	db.pokemons.find(query)
		
		{
		  "_id": ObjectId("5645554a40e9fbb07dd1c3c5"),
		  "name": "Alakazam",
		  "description": "QI de 9000, mas nao fala 2 palavras",
		  "type": "Psychic",
		  "attack": 50,
		  "defense": 45,
		  "height": 1.5
		}
		{
		  "_id": ObjectId("5645554a40e9fbb07dd1c3c7"),
		  "name": "Pidgeot",
		  "description": "Baita de uma ave, digassi de passagi",
		  "type": "normal/fly",
		  "attack": 80,
		  "defense": 75,
		  "height": 1.5
		}
		{
		  "_id": ObjectId("5645554a40e9fbb07dd1c3c8"),
		  "name": "Ninetales",
		  "description": "Cachorrão lindo",
		  "type": "fire",
		  "attack": 76,
		  "defense": 75,
		  "height": 1.09,
		  "power": 59
		}
Fetched 3 record(s) in 2ms

  
```
