#MongoDB - Aula 06 - Exercícios
autor: Thiago R. M. Bitencourt

## 1. Fazer uma query para o campo `name` utilizando `explain` para ver o resultado da busca

```
> db.pokemons.find({"name" : /gogoat/i})
.explain('executionStats')
.executionStats.totalDocsExamined
610
> db.pokemons.find({"name" : /gogoat/i})\
.explain('executionStats')
.executionStats.executionTimeMillis
0
```

## 2. Criar index para o campo `name`

```
> db.pokemons.createIndex({name: 1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}
> db.pokemons.getIndexes()
[
	{
		"v" : 1,
		"key" : {
			"_id" : 1
		},
		"ns" : "be-mean.pokemons",
		"name" : "_id_"
	},
	{
		"v" : 1,
		"key" : {
			"name" : 1
		},
		"name" : "name_1",
		"ns" : "be-mean.pokemons"
	}
]
```

## 3. Refazer a query para o campo `name` utilizando `explain` para ver o resultado da busca

```
> db.pokemons.find({"name" : /gogoat/i})
.explain('executionStats')
.executionStats.totalDocsExamined
1
> db.pokemons.find({"name" : /gogoat/i})
.explain('executionStats')
.executionStats.executionTimeMillis
0
```

## 4. Fazer uma query para dois campos juntos utilizando `explain` para ver o resultado da busca

```
> db.pokemons.find({"name" : /gogoat/i, attack: 64})
.explain('executionStats')
.executionStats.totalDocsExamined
610
> db.pokemons.find({"name" : /gogoat/i, attack: 64})
.explain('executionStats')
.executionStats.executionTimeMillis
3
```

## 5. Criar um `index` para dois campos juntos

```
> db.pokemons.createIndex({name: 1, attack: 1})
{
	"createdCollectionAutomatically" : false,
	"numIndexesBefore" : 1,
	"numIndexesAfter" : 2,
	"ok" : 1
}
> db.pokemons.getIndexes()
[
	{
		"v" : 1,
		"key" : {
			"_id" : 1
		},
		"ns" : "be-mean.pokemons",
		"name" : "_id_"
	},
  {
		"v" : 1,
		"key" : {
			"name" : 1
		},
		"name" : "name_1",
		"ns" : "be-mean.pokemons"
	},
	{
		"v" : 1,
		"key" : {
			"name" : 1,
			"attack" : 1
		},
		"name" : "name_1_attack_1",
		"ns" : "be-mean.pokemons"
	}
]
```

## 6. Refazer a query para os dois campos juntos utilizando `explain` para ver o resultado da busca

```
> db.pokemons.find({"name" : /gogoat/i, attack: 64})
.explain('executionStats')
.executionStats.totalDocsExamined
1
> db.pokemons.find({"name" : /gogoat/i, attack: 64})
.explain('executionStats')
.executionStats.executionTimeMillis
0
```
