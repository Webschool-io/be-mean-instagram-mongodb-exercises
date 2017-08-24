# MongoDB - Aula 03 - Exercício
autor: Carlos Henrique Ribeiro

## 1. Liste todos Pokemons com a altura menor que 0.5

	```
	> var query ={height: {$lt:0.5}}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type"
	: "eletric", "attack" : 55, "height" : 0.4 }
	{ "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type"
	: "grama", "attack" : 49, "height" : 0.4 }
	{ "_id" : ObjectId("57d41cbcc953b335c0afd7bc"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto"
	, "attack" : 30, "height" : 0.3, "defense" : 35 }
	>
	```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;


	```
	> var query ={height: {$gte:0.5}}
	>
	```

## 3. Liste todos os Pokemons com a altura menor ou igual que 0.5 AND do tipo grama;

	```
	> var query = {$and: [{height: {$lte:0.5}},{type:'grama'}]}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4 }
	>
	```

## 4. Liste todos Pokemons com o name 'Pikachu' OR com attack menor ou igual que 0.5;

	```
	> var query = {$nor:[{name:'Pikachu'},{attack:{$lte:0.5}}]}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4 }
	>
	```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5;

	```
	> var query = {$and:[{attack:{$gte:48}},{height:{$lte:0.5}}]}
	> db.pokemons.find(query)
	{ "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4 }
	{ "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4 }
	{ "_id" : ObjectId("57d419bcc953b335c0afd7bb"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5 }
	>
	```
