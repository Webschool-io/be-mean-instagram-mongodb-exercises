# MongoDB - Aula 02 - Exercício
autor: EDVALDO ELIAS FERREIRA

## 1. Crie uma database chamada be-mean-pokemons

```
$ mongo be-mean-pokemons
MongoDB shell version: 3.2.1
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.12
```

## 2. Liste quais databases você possui nesse servidor

```
show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
local             → 0.000GB
teste             → 0.000GB
```
	
## 3. Liste quais coleções você possui nessa database

```
show collections
```
	
## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

```
var pokemons = [{'name': 'Miltank', 'description': 'Miltank dá mais de cinco litros de leite diariamente', 'attack': 80, 'defense': 105, 'height': 12},
{'name': 'Charizard', 'description': 'Charizard voa em torno do céu em busca de adversários poderosos', 'attack': 84, 'defense': 78, 'height': 17},
{'name': 'Psyduck', 'description': 'Psyduck usa um poder misterioso', 'attack': 52, 'defense': 48, 'height': 8},
{'name': 'Mewtwo', 'description': 'Mewtwo é um Pokémon que foi criado por manipulação genética', 'attack': 110, 'defense': 90, 'height': 2},
{'name': 'Togepi', 'description': 'Como sua energia, Togepi usa as emoções positivas', 'attack': 20, 'defense': 65, 'height': 3}]
```

```
pokemons
[
  {
	"name": "Miltank",
	"description": "Miltank dá mais de cinco litros de leite diariamente",
	"attack": 80,
	"defense": 105,
	"height": 12
  },
  {
	"name": "Charizard",
	"description": "Charizard voa em torno do céu em busca de adversários poderosos",
	"attack": 84,
	"defense": 78,
	"height": 17
  },
  {
	"name": "Psyduck",
	"description": "Psyduck usa um poder misterioso",
	"attack": 52,
	"defense": 48,
	"height": 8
  },
  {
	"name": "Mewtwo",
	"description": "Mewtwo é um Pokémon que foi criado por manipulação genética",
	"attack": 110,
	"defense": 90,
	"height": 2
  },
  {
	"name": "Togepi",
	"description": "Como sua energia, Togepi usa as emoções positivas",
	"attack": 20,
	"defense": 65,
	"height": 3
  }
]
```

```
db.pokemons.insert(pokemons)
Inserted 1 record(s) in 141ms
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

## 5. Liste os pokemons existentes na sua coleção

```
db.pokemons.find()
{
  "_id": ObjectId("56cd205b342b39890a530167"),
  "name": "Miltank",
  "description": "Miltank dá mais de cinco litros de leite diariamente",
  "attack": 80,
  "defense": 105,
  "height": 12
}
{
  "_id": ObjectId("56cd205b342b39890a530168"),
  "name": "Charizard",
  "description": "Charizard voa em torno do céu em busca de adversários poderosos",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("56cd205b342b39890a530169"),
  "name": "Psyduck",
  "description": "Psyduck usa um poder misterioso",
  "attack": 52,
  "defense": 48,
  "height": 8
}
{
  "_id": ObjectId("56cd205b342b39890a53016a"),
  "name": "Mewtwo",
  "description": "Mewtwo é um Pokémon que foi criado por manipulação genética",
  "attack": 110,
  "defense": 90,
  "height": 2
}
{
  "_id": ObjectId("56cd205b342b39890a53016b"),
  "name": "Togepi",
  "description": "Como sua energia, Togepi usa as emoções positivas",
  "attack": 20,
  "defense": 65,
  "height": 3
}
Fetched 5 record(s) in 2ms
```

## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`

```
var query = {"name": "Mewtwo"}
query
{
  "name": "Mewtwo"
}
```

```
var poke = db.pokemons.findOne(query)
poke
{
  "_id": ObjectId("56cd205b342b39890a53016a"),
  "name": "Mewtwo",
  "description": "Mewtwo é um Pokémon que foi criado por manipulação genética",
  "attack": 110,
  "defense": 90,
  "height": 2
}
```

## 7. Modifique sua `description` e salvê-o
```
poke.description = "É o mais fodão"
É o mais fodão
```

```
db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

```
db.pokemons.find(query)
{
  "_id": ObjectId("56cd205b342b39890a53016a"),
  "name": "Mewtwo",
  "description": "É o mais fodão",
  "attack": 110,
  "defense": 90,
  "height": 2
}
Fetched 1 record(s) in 1ms
```
