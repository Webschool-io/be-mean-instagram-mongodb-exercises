# MongoDB - Aula 02 - Exercício
autor: MARLON WANGER

## Criando database (passo 2)
```
	kakashicafe-PC(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
	switched to db be-mean-pokemons

```

## Listagem das databases (passo 2)
```
	kakashicafe-PC(mongod-3.0.7) be-mean-pokemons> show dbs
	be-mean-instagram → 0.078GB
	local             → 0.078GB
	be-mean           → 0.078GB
```


## Listagem das coleções (passo 3)
```
	kakashicafe-PC(mongod-3.0.7) be-mean-pokemons> show collections

```


## Cadastro dos pokemons (passo 4)
```
	pokemons = [
		{'name':'Pikachu','description':'Rato eletrico bolado','type':'eletrico',attack:55, height:0.4},
		{'name':'Charizard','description':'Charmander grande','type':'fogo',attack:90, height:90.5},
		{'name':'Blastoise','description':'Squirtle com 2 canhao','type':'agua',attack:90, height:85.5},
		{'name':'Butterfree','description':'Borboleta Style','type':'grama',attack:75, height:32.0},
		{'name':'Venusaur','description':'Gordo lento','type':'grama',attack:90, height:100.0},
		{'name':'Pidgeot','description':'Passaro boladao','type':'voador',attack:85, height:39.5},
	]

	kakashicafe-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemons)
	Inserted 1 record(s) in 460ms
	BulkWriteResult({
	  "writeErrors": [ ],
	  "writeConcernErrors": [ ],
	  "nInserted": 6,
	  "nUpserted": 0,
	  "nMatched": 0,
	  "nModified": 0,
	  "nRemoved": 0,
	  "upserted": [ ]
	})

```	

## Lista dos pokemons (passo 5)
```
	kakashicafe-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
	{
	  "_id": ObjectId("564e5fdfb54fcab69c7306f4"),
	  "name": "Pikachu",
	  "description": "Rato eletrico bolado",
	  "type": "eletrico",
	  "attack": 55,
	  "height": 0.4
	}
	{
	  "_id": ObjectId("564e5fdfb54fcab69c7306f5"),
	  "name": "Charizard",
	  "description": "Charmander grande",
	  "type": "fogo",
	  "attack": 90,
	  "height": 90.5
	}
	{
	  "_id": ObjectId("564e5fdfb54fcab69c7306f6"),
	  "name": "Blastoise",
	  "description": "Squirtle com 2 canhao",
	  "type": "agua",
	  "attack": 90,
	  "height": 85.5
	}
	{
	  "_id": ObjectId("564e5fdfb54fcab69c7306f7"),
	  "name": "Butterfree",
	  "description": "Borboleta Style",
	  "type": "grama",
	  "attack": 75,
	  "height": 32
	}
	{
	  "_id": ObjectId("564e5fdfb54fcab69c7306f8"),
	  "name": "Venusaur",
	  "description": "Gordo lento",
	  "type": "grama",
	  "attack": 90,
	  "height": 100
	}
	{
	  "_id": ObjectId("564e5fdfb54fcab69c7306f9"),
	  "name": "Pidgeot",
	  "description": "Passaro boladao",
	  "type": "voador",
	  "attack": 85,
	  "height": 39.5
	}
	Fetched 6 record(s) in 4ms

```

## Pikachu (passo 6)
```
	var poke = {name:'Pidgeot'}

	kakashicafe-PC(mongod-3.0.7) be-mean-pokemons> pokeOne = db.pokemons.findOne(poke)
	{
	  "_id": ObjectId("564e5fdfb54fcab69c7306f9"),
	  "name": "Pidgeot",
	  "description": "Passaro boladao",
	  "type": "voador",
	  "attack": 85,
	  "height": 39.5
	}

```

## Atualização do Pokemon (passo 7)
```	
	kakashicafe-PC(mongod-3.0.7) be-mean-pokemons> pokeOne.description = 'Alterando a descrição para passaro boladao voador'
	Alterando a descrição para passaro boladao voador
	kakashicafe-PC(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokeOne)
	Updated 1 existing record(s) in 3ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

```


