## MongoDb - Aula 02 Exercício
Autor: Leonardo Larocca

## 1 - Conectando ao banco
```
	➜  ~  mongo
	MongoDB shell version: 3.0.7
	connecting to: test
	Mongo-Hacker 0.0.9
	Server has startup warnings: 
	2015-11-28T16:56:46.821-0200 I CONTROL  [initandlisten] ** WARNING: You are running this process as the root user, which is not recommended.
	2015-11-28T16:56:46.821-0200 I CONTROL  [initandlisten] 
	2015-11-28T16:56:46.822-0200 I CONTROL  [initandlisten] 
	2015-11-28T16:56:46.822-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/enabled is 'always'.
	2015-11-28T16:56:46.822-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
	2015-11-28T16:56:46.822-0200 I CONTROL  [initandlisten] 
	2015-11-28T16:56:46.822-0200 I CONTROL  [initandlisten] ** WARNING: /sys/kernel/mm/transparent_hugepage/defrag is 'always'.
	2015-11-28T16:56:46.822-0200 I CONTROL  [initandlisten] **        We suggest setting it to 'never'
	2015-11-28T16:56:46.822-0200 I CONTROL  [initandlisten] 

	asus(mongod-3.0.7) test> use be-mean-pokemons
	switched to db be-mean-pokemons
	asus(mongod-3.0.7) be-mean-pokemons> 
```

## 2 - Listando Database's
```
	asus(mongod-3.0.7) be-mean-pokemons> show dbs
	local             → 0.078GB
	be-mean           → 0.078GB
	be-mean-instagram → 0.078GB
	test              → 0.078GB
	asus(mongod-3.0.7) be-mean-pokemons> 
```

## 3 - Criando e Listando Collections
```
	asus(mongod-3.0.7) be-mean-pokemons> db.createCollection('pokemons')
	{
	  "ok": 1
	}

	asus(mongod-3.0.7) be-mean-pokemons> show collections
	pokemons       → 0.000MB / 0.008MB
	system.indexes → 0.000MB / 0.008MB

```
## 4 - Inserindo pokemons
```
	asus(mongod-3.0.7) be-mean-pokemons> var pokemon = [{'name': 'Pikachu','description': 'Rato elétrico',attack: 55,defense: 120,height: 0.44},{'name': 'Charizard','description': 'Dragão teimoso',attack: 120,defense: 50,height: 40},{'name': 'Squirtle','description': 'Tartaruga a jato',attack: 30,defense: 45,height: 9},{'name': 'Entei','description': 'Starfish Head Horse',attack: 85,defense: 70,height: 198},{'name': 'Pidgeot','description': 'Calopsita eletrica',attack: 150,defense: 120,height: 40}]

	asus(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemon)
	Inserted 1 record(s) in 13ms
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
## 5 - Listando Pokemons
```
	asus(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
	{
	  "_id": ObjectId("565a1a3275dfc16def1a8b62"),
	  "name": "Pikachu",
	  "description": "Rato elétrico",
	  "attack": 55,
	  "defense": 120,
	  "height": 0.44
	}
	{
	  "_id": ObjectId("565a1a3275dfc16def1a8b63"),
	  "name": "Charizard",
	  "description": "Dragão teimoso",
	  "attack": 120,
	  "defense": 50,
	  "height": 40
	}
	{
	  "_id": ObjectId("565a1a3275dfc16def1a8b64"),
	  "name": "Squirtle",
	  "description": "Tartaruga a jato",
	  "attack": 30,
	  "defense": 45,
	  "height": 9
	}
	{
	  "_id": ObjectId("565a1a3275dfc16def1a8b65"),
	  "name": "Entei",
	  "description": "Starfish Head Horse",
	  "attack": 85,
	  "defense": 70,
	  "height": 198
	}
	{
	  "_id": ObjectId("565a1a3275dfc16def1a8b66"),
	  "name": "Pidgeot",
	  "description": "Calopsita eletrica",
	  "attack": 150,
	  "defense": 120,
	  "height": 40
	}
	Fetched 5 record(s) in 9ms

```
## 6 - Buscando pokemon e armazenando na variável 'poke'
```
	asus(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Pikachu'}
	asus(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
	asus(mongod-3.0.7) be-mean-pokemons> poke
	{
	  "_id": ObjectId("565a1a3275dfc16def1a8b62"),
	  "name": "Pikachu",
	  "description": "Rato elétrico",
	  "attack": 55,
	  "defense": 120,
	  "height": 0.44
	}
```
## Modificando a description, salvando e mostrando.
```
	asus(mongod-3.0.7) be-mean-pokemons> poke.description = 'Rato eletrico fofinho'
	Rato eletrico fofinho
	asus(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	asus(mongod-3.0.7) be-mean-pokemons> poke
	{
	  "_id": ObjectId("565a1a3275dfc16def1a8b62"),
	  "name": "Pikachu",
	  "description": "Rato eletrico fofinho",
	  "attack": 55,
	  "defense": 120,
	  "height": 0.44
	}

```
