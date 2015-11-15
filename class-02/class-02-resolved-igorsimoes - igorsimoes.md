# MongoDB - Aula 02 - Exercício

autor: Igor Simões de Oliveira Lima

### 1 Criar database be-mean-pokemons
    ```
	ubuntu-igor(mongod-3.0.7) test> use be-mean-pokemons
	switched to db be-mean-pokemons
    ```

### 2 Listar as databases
    ```
	ubuntu-igor(mongod-3.0.7) test> show dbs
	be-mean-pokemons → 0.078GB
	local            → 0.078GB
	be-mean          → 0.078GB

    ```
### 3 Listar collections
    ```
	ubuntu-igor(mongod-3.0.7) be-mean-pokemons> show collections
	pokemons       → 0.000MB / 0.008MB
	system.indexes → 0.000MB / 0.008MB

    ```
### 4 Inserir 5 pokemons
    ```
	var mewtwo = {name:"Mewtwo", description:"zica psiquico",attack:110,defense:90,height:20}
	var diglett = {name:"Diglett", description:"Cava buraco",attack:55,defense:25,height:2}
	var dodrio = {name:"Dodrio", description:"Ave zica",attack:110,defense:70,height:18}
	var muk = {name:"Muk", description:"Zica do pântano",attack:105,defense:75,height:12}
	var sandshrew = {name:"Sandshrew", description:"Rato da terra",attack:75,defense:85,height:6}

	var pokemons = [mewtwo, diglett, dodrio, muk, sandshrew]

	ubuntu-igor(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
	Inserted 1 record(s) in 9ms
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
### 5 Listar os pokemons inseridos
    ```
	ubuntu-igor(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
	{
	  "_id": ObjectId("5645eb0af5c1f5d1e52aec29"),
	  "name": "Mewtwo",
	  "description": "zica psiquico",
	  "attack": 110,
	  "defense": 90,
	  "height": 20
	}
	{
	  "_id": ObjectId("5645eb0af5c1f5d1e52aec2a"),
	  "name": "Diglett",
	  "description": "Cava buraco",
	  "attack": 55,
	  "defense": 25,
	  "height": 2
	}
	{
	  "_id": ObjectId("5645eb0af5c1f5d1e52aec2b"),
	  "name": "Dodrio",
	  "description": "Ave zica",
	  "attack": 110,
	  "defense": 70,
	  "height": 18
	}
	{
	  "_id": ObjectId("5645eb0af5c1f5d1e52aec2c"),
	  "name": "Muk",
	  "description": "Zica do pântano",
	  "attack": 105,
	  "defense": 75,
	  "height": 12
	}
	{
	  "_id": ObjectId("5645eb0af5c1f5d1e52aec2d"),
	  "name": "Sandshrew",
	  "description": "Rato da terra",
	  "attack": 75,
	  "defense": 85,
	  "height": 6
	}
	Fetched 5 record(s) in 29ms

    ```

### 6 Buscar um pokemon em uma variavel 'poke'
    ```
	var poke = db.pokemons.findOne({name:"Mewtwo"})
	ubuntu-igor(mongod-3.0.7) be-mean-pokemons> poke
	{
	  "_id": ObjectId("5645eb0af5c1f5d1e52aec29"),
	  "name": "Mewtwo",
	  "description": "zica psiquico",
	  "attack": 110,
	  "defense": 90,
	  "height": 20
	}

    ```

### 7 Editar campo 'description' do pokemon escolhido
    ```
	ubuntu-igor(mongod-3.0.7) be-mean-pokemons> poke.description = "Zica modafoca psiquico"
	ubuntu-igor(mongod-3.0.7) be-mean-pokemons> poke
	{
	  "_id": ObjectId("5645eb0af5c1f5d1e52aec29"),
	  "name": "Mewtwo",
	  "description": "Zica modafoca psiquico",
	  "attack": 110,
	  "defense": 90,
	  "height": 20
	}
	ubuntu-igor(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
	Updated 1 existing record(s) in 3ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
    ```
