# MongoDB - Aula 02 - Exercício
autor: LUAN RAFAEL CASTOR PINHEIRO


## 1. Crie uma database chamada be-mean-pokemons;

    ```
	ubuntu-luan(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
	switched to db be-mean-pokemons
	ubuntu-luan(mongod-3.0.7) be-mean-pokemons> 

    ```

## 2. Liste quais databases você possui nesse servidor;
	```
	ubuntu-luan(mongod-3.0.7) be-mean-pokemons> show dbs
	local             → 0.078GB
	be-mean           → 0.078GB
	be-mean-instagram → 0.078GB

	
	```

## 3. Liste quais coleções você possui nessa database;

	```
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> show collections
		pokemons       → 0.002MB / 0.008MB
		system.indexes → 0.000MB / 0.008MB

	```
## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

	```
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> var pokes = [
		... { 
		... name: "Raichu",
		... description: "Rato fodástico!",
		... type: "electric",
		... attack: 90,
		... defense: 55,
		... height: 0.8,
		... },
		... { 
		... name: "Charizard",
		... description: "Dragão voador do caralho!",
		... type: ["Fire","flying"],
		... attack: 84,
		... defense: 78,
		... height: 1.7,
		... },
		... { 
		... name: "Pidgeot",
		... description: "Passáro de topete!",
		... type: ["normal","flying"],
		... attack: 80,
		... defense: 75,
		... height: 1.5,
		... },
		... { 
		... name: "Blastoise",
		... description: "Bombeiro nas horas vagas",
		... type: "water",
		... attack: 83,
		... defense: 100,
		... height: 1.6,
		... },
		... { 
		... name: "Venusaur",
		... description: "Super bulbasaur",
		... type: ["poison","grass"],
		... attack: 82,
		... defense: 83,
		... height: 2.0,
		... },
		... { 
		... name: "Rapidash",
		... description: "Mais veloz que o Flash",
		... type: "fire",
		... attack: 100,
		... defense: 70,
		... height: 1.7,
		... },
		... { 
		... name: "Scyther",
		... description: "Corta tudo que vê pela frente!",
		... type: ["flying","bug"],
		... attack: 110,
		... defense: 80,
		... height: 1.5,
		... },
		... ];

		db.pokemons.insert(pokes)
		Inserted 1 record(s) in 772ms
		BulkWriteResult({
		  "writeErrors": [ ],
		  "writeConcernErrors": [ ],
		  "nInserted": 7,
		  "nUpserted": 0,
		  "nMatched": 0,
		  "nModified": 0,
		  "nRemoved": 0,
		  "upserted": [ ]
		})



	```
## 5. Liste os pokemons existentes na sua coleção;

	```
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
		{
		  "_id": ObjectId("564760ee4aee3194281111ec"),
		  "name": "Raichu",
		  "description": "Rato fodástico!",
		  "type": "electric",
		  "attack": 90,
		  "defense": 55,
		  "height": 0.8
		}
		{
		  "_id": ObjectId("564760ee4aee3194281111ed"),
		  "name": "Charizard",
		  "description": "Dragão voador do caralho!",
		  "type": [
		    "Fire",
		    "flying"
		  ],
		  "attack": 84,
		  "defense": 78,
		  "height": 1.7
		}
		{
		  "_id": ObjectId("564760ee4aee3194281111ee"),
		  "name": "Pidgeot",
		  "description": "Passáro de topete!",
		  "type": [
		    "normal",
		    "flying"
		  ],
		  "attack": 80,
		  "defense": 75,
		  "height": 1.5
		}
		{
		  "_id": ObjectId("564760ee4aee3194281111ef"),
		  "name": "Blastoise",
		  "description": "Bombeiro nas horas vagas",
		  "type": "water",
		  "attack": 83,
		  "defense": 100,
		  "height": 1.6
		}
		{
		  "_id": ObjectId("564760ee4aee3194281111f0"),
		  "name": "Venusaur",
		  "description": "Super bulbasaur",
		  "type": [
		    "poison",
		    "grass"
		  ],
		  "attack": 82,
		  "defense": 83,
		  "height": 2
		}
		{
		  "_id": ObjectId("564760ee4aee3194281111f1"),
		  "name": "Rapidash",
		  "description": "Mais veloz que o Flash",
		  "type": "fire",
		  "attack": 100,
		  "defense": 70,
		  "height": 1.7
		}
		{
		  "_id": ObjectId("564760ee4aee3194281111f2"),
		  "name": "Scyther",
		  "description": "Corta tudo que vê pela frente!",
		  "type": [
		    "flying",
		    "bug"
		  ],
		  "attack": 110,
		  "defense": 80,
		  "height": 1.5
		}
		Fetched 7 record(s) in 6ms


	```
## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

	```
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Charizard'}
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> poke
		{
		  "_id": ObjectId("564760ee4aee3194281111ed"),
		  "name": "Charizard",
		  "description": "Dragão voador do caralho!",
		  "type": [
		    "Fire",
		    "flying"
		  ],
		  "attack": 84,
		  "defense": 78,
		  "height": 1.7
		}


	```
## 7. Modifique sua `description` e salvê-o

	```
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> poke
		{
		  "_id": ObjectId("564760ee4aee3194281111ed"),
		  "name": "Charizard",
		  "description": "Dragão voador do caralho!",
		  "type": [
		    "Fire",
		    "flying"
		  ],
		  "attack": 84,
		  "defense": 78,
		  "height": 1.7
		}
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> poke.description = "Dragao voador que cospe fogo em todo mundo! "
		Dragao voador que cospe fogo em todo mundo! 
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> poke
		{
		  "_id": ObjectId("564760ee4aee3194281111ed"),
		  "name": "Charizard",
		  "description": "Dragao voador que cospe fogo em todo mundo! ",
		  "type": [
		    "Fire",
		    "flying"
		  ],
		  "attack": 84,
		  "defense": 78,
		  "height": 1.7
		}
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
		Updated 1 existing record(s) in 5ms
		WriteResult({
		  "nMatched": 1,
		  "nUpserted": 0,
		  "nModified": 1
		})
		ubuntu-luan(mongod-3.0.7) be-mean-pokemons> poke
		{
		  "_id": ObjectId("564760ee4aee3194281111ed"),
		  "name": "Charizard",
		  "description": "Dragao voador que cospe fogo em todo mundo! ",
		  "type": [
		    "Fire",
		    "flying"
		  ],
		  "attack": 84,
		  "defense": 78,
		  "height": 1.7
		}

	```