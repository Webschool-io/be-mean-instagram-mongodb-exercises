# MongoDB - Aula 02 - Exercício
autor: William Dias

## Listagem das databases (passo 2)
```
> show dbs
teste             → 0.078GB
test              → 0.078GB
db_test           → 0.078GB
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
be-mean-teste     → 0.078GB

```

## Listagem das coleções (passo 3)
```
> show collections
HP(mongod-3.0.7) be-mean-pokemons> 
```

## Cadastro dos pokemons (passo 4)
```
var pokemons = [{name: "Ivysaur",description: "pokemon rosa", attack: 62, defense: 63, height: 10 },
{name: "Poliwag",description: "pokemons com negocio hipnotico na barriga", attack: 50, defense: 40, height: 6 },
{name: "Girafarig",description: "Um pokemon estilo girafa", attack: 80, defense: 65, height: 15 },
{name: "Linoone",description: "Rato muito loco", attack: 70, defense: 61, height: 5 },
{name: "Bibarel",description: "nao consegui definir", attack: 85, defense: 60, height: 10 }]

HP(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(pokemons)

Inserted 1 record(s) in 698ms
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

## Lista dos pokemons (passo 5)
```
> db.pokemons.find({})
{
	"_id": ObjectId("56464151737c536ec253b426"),
	"name": "Ivysaur",
	"description": "pokemon rosa",
	"attack": 62,
	"defense": 63,
	"height": 10
}
{
	"_id": ObjectId("56464151737c536ec253b427"),
	"name": "Poliwag",
	"description": "pokemons com negocio hipnotico na barriga",
	"attack": 50,
	"defense": 40,
	"height": 6
}
{
	"_id": ObjectId("56464151737c536ec253b428"),
	"name": "Girafarig",
	"description": "Um pokemon estilo girafa",
	"attack": 80,
	"defense": 65,
	"height": 15
}
{
	"_id": ObjectId("56464151737c536ec253b429"),
	"name": "Linoone",
	"description": "Rato muito loco",
	"attack": 70,
	"defense": 61,
	"height": 5
}
{
	"_id": ObjectId("56464151737c536ec253b42a"),
	"name": "Bibarel",
	"description": "nao consegui definir",
	"attack": 85,
	"defense": 60,
	"height": 10
}
Fetched 5 record(s) in
```

## Passo 6

```
HP(mongod-3.0.7) be-mean-pokemons> var query = {"name":"Bibarel"}
HP(mongod-3.0.7) be-mean-pokemons> var poke =db.pokemons.findOne(query)

HP(mongod-3.0.7) be-mean-pokemons> poke
{
	"_id": ObjectId("56464151737c536ec253b42a"),
	"name": "Bibarel",
	"description": "nao consegui definir",
	"attack": 85,
	"defense": 60,
	"height": 10
}

```
## Passo 7


```
HP(mongod-3.0.7) be-mean-pokemons> var query = {"name":"Bibarel"}
HP(mongod-3.0.7) be-mean-pokemons> var poke =db.pokemons.findOne(query)

HP(mongod-3.0.7) be-mean-pokemons> poke
{
	"_id": ObjectId("56464151737c536ec253b42a"),
	"name": "Bibarel",
	"description": "nao consegui definir",
	"attack": 85,
	"defense": 60,
	"height": 10
}
HP(mongod-3.0.7) be-mean-pokemons> poke.description
nao consegui definir
HP(mongod-3.0.7) be-mean-pokemons> poke.description = "Ainda nao consegui Definir o q é esse pokemon"
Ainda nao consegui Definir o q é esse pokemon
HP(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 52ms
WriteResult({
"nMatched": 1,
"nUpserted": 0,
"nModified": 1
})
HP(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne(query)
{
	"_id": ObjectId("56464151737c536ec253b42a"),
	"name": "Bibarel",
	"description": "Ainda nao consegui Definir o q é esse pokemon",
	"attack": 85,
	"defense": 60,
	"height": 10
}

```
