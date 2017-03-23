# MongoDB - Aula 02 - Exercício
autor: Matheus Torres Pereira

## 1. Crie uma database chamada be-mean-pokemons

```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## 2. Liste quais databases você possui nesse servidor

```
> show dbs
be-mean    0.005GB
local      0.000GB
mattpress  0.000GB
nodepress  0.001GB
```

## 3. Liste quais coleções você possui nessa database

```
> show collections
```

## 4. Insira pelo menos 5 pokémons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

```
> var pokemons = [{name:'Bulbasaur', description:'Pokemon com uma planta nas costas', attack: 49, defense: 49, height: 0.71}, {name:'Charmander', description:'Pokemon com fogo no rabo', attack: 52, defense:43, height:0.61}, {name:'Squirtle', description:'Tartaruga cuspidora de água', attack:48, defense: 65, height: 0.51}, {name: 'Pidgey', description:'Pokemon pomba', attack: 45, defense: 40, height: 0.30}, {name: 'Pikachu', description:'Rato de raio', attack:55, defense: 40, height: 0.41}]
> pokemons
[
	{
		"name" : "Bulbasaur",
		"description" : "Pokemon com uma planta nas costas",
		"attack" : 49,
		"defense" : 49,
		"height" : 0.71
	},
	{
		"name" : "Charmander",
		"description" : "Pokemon com fogo no rabo",
		"attack" : 52,
		"defense" : 43,
		"height" : 0.61
	},
	{
		"name" : "Squirtle",
		"description" : "Tartaruga cuspidora de água",
		"attack" : 48,
		"defense" : 65,
		"height" : 0.51
	},
	{
		"name" : "Pidgey",
		"description" : "Pokemon pomba",
		"attack" : 45,
		"defense" : 40,
		"height" : 0.3
	},
	{
		"name" : "Pikachu",
		"description" : "Rato de raio",
		"attack" : 55,
		"defense" : 40,
		"height" : 0.41
	}
]

> db.pokemons.insert(pokemons)
BulkWriteResult({
	"writeErrors" : [ ],
	"writeConcernErrors" : [ ],
	"nInserted" : 5,
	"nUpserted" : 0,
	"nMatched" : 0,
	"nModified" : 0,
	"nRemoved" : 0,
	"upserted" : [ ]

```

## 5. Liste os pokemons existentes na sua coleção

```
> db.pokemons.find()
{
	"_id" : ObjectId("58af1bee57d2d3ebfdb8a689"), 
	"name" : "Bulbasaur", 
	"description" : "Pokemon com uma planta nas costas", 
	"attack" : 49,
	"defense" : 49, 
	"height" : 0.71
}
{ 
	"_id" : ObjectId("58af1bee57d2d3ebfdb8a68a"), 
	"name" : "Charmander", 
	"description" : "Pokemon com fogo no rabo", 
	"attack" : 52, 
	"defense" : 43, 
	"height" : 0.61 
}
{ 
	"_id" : ObjectId("58af1bee57d2d3ebfdb8a68b"), 
	"name" : "Squirtle", 
	"description" : "Tartaruga cuspidora de água",
	"attack" : 48, 
	"defense" : 65, 
	"height" : 0.51 
}
{ 
	"_id" : ObjectId("58af1bee57d2d3ebfdb8a68c"), 
	"name" : "Pidgey", 
	"description" : "Pokemon pomba", 
	"attack" : 45, 
	"defense" : 40, 
	"height" : 0.3 
}
{ 
	"_id" : ObjectId("58af1bee57d2d3ebfdb8a68d"), 
	"name" : "Pikachu", 
	"description" : "Rato de raio", 
	"attack" : 55, 
	"defense" : 40, 
	"height" : 0.41 
}
```

## 6. Busque um pokemon a sua escolha, pelo nome, e armazene-o em uma variável chamada 'poke'

```
> var poke = db.pokemons.findOne({name:'Pikachu'})
> poke
{
	"_id" : ObjectId("58af1bee57d2d3ebfdb8a68d"),
	"name" : "Pikachu",
	"description" : "Rato de raio",
	"attack" : 55,
	"defense" : 40,
	"height" : 0.41
}
```

## 7. Modifique sua 'description' e salvê-o

```
> poke.description = 'Pokemon rato amarelo que solta raio pela bochecha'
Pokemon rato amarelo que solta raio pela bochecha

> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> db.pokemons.findOne({name:'Pikachu'})
{
	"_id" : ObjectId("58af1bee57d2d3ebfdb8a68d"),
	"name" : "Pikachu",
	"description" : "Pokemon rato amarelo que solta raio pela bochecha",
	"attack" : 55,
	"defense" : 40,
	"height" : 0.41
}

```