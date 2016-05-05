# MongoDB - Aula 02 - Exercício
autor: Diego Bittencourt Silva

## 1. Criar uma database chamada be-mean-pokemons

```
diego@DESKTOP-B86UP9T MINGW64 ~
  $ mongo
  MongoDB shell version: 3.0.7
  connecting to: test
  use be-mean-pokemons
  switched to db be-mean-pokemons

```

## 2. Liste quais databases você possui nesse servidor

```
show dbs
  be-mean            0.078GB
  be-mean-instagram  0.078GB
  local              0.078GB
```

## 3. Liste quais coleções você possui nessa database

```
show collections

```

## 4. Insira pelo menos 5 pokemons

```
var pokemons = [{'name':'ninetales','description':'Pokemon raposa de olhos vermelhos','type': 'fogo','attack': 40,'defense': 60,'height': 4.0},{'name':'oddish','description':'Pokemon rabanete azul','type': 'veneno','attack': 30,'defense': 40,'height': 3.00},{'name':'persian','description':'Evolução do gato da equipe rocket','type': 'normal','attack': 40,'defense': 50,'height': 4.80},{'name':'arcanine','description':'Evolução do Growlithe, cachorro loko de fogo','type': 'fogo','attack': 50,'defense': 30,'height': 5.30},{'name':'kadabra','description':'Pokemon com doença mental','type': 'psíquico','attack': 50,'defense': 30,'height': 5.70}]
```

## 5. Liste os pokemons existentes na sua coleção

```
db.pokemons.find()
{ "_id" : ObjectId("564e01e2a6c083fcd8802ffb"), "name" : "ninetales", "description" : "Pokemon raposa de olhos vermelhos", "type" : "fogo", "attack" : 40, "defense" : 60, "height" : 4 }
{ "_id" : ObjectId("564e01e2a6c083fcd8802ffc"), "name" : "oddish", "description" : "Pokemon rabanete azul", "type" : "veneno", "attack" : 30, "defense" : 40, "height" : 3 }
{ "_id" : ObjectId("564e01e2a6c083fcd8802ffd"), "name" : "persian", "description" : "Evolução do gato da equipe rocket", "type" : "normal", "attack" : 40, "defense" : 50, "height" : 4.8 }
{ "_id" : ObjectId("564e01e2a6c083fcd8802ffe"), "name" : "arcanine", "description" : "Evolução do Growlithe, cachorro loko de fogo", "type" : "fogo", "attack" : 50, "defense" : 30, "height" : 5.3 }
{ "_id" : ObjectId("564e01e2a6c083fcd8802fff"), "name" : "kadabra", "description" : "Pokemon com doença mental", "type" : "psíquico", "attack" : 50, "defense" : 30, "height" : 5.7 }
```

## 6. Busque um pokemon e armazene-o em uma variável chamada "poke"

```
var query = {"name" : "kadabra"}
query
"name" : "kadabra" }
db.pokemons.find(query)
"_id" : ObjectId("564e04e94b54c023375aff2a"), "name" : "kadabra", "description" : "Pokemon com doença mental", "type"
"psíquico", "attack" : 50, "defense" : 30, "height" : 5.7 }
var poke = db.pokemons.findOne(query)
	poke
	{
     	 "_id" : ObjectId("564e04e94b54c023375aff2a"),
     	 "name" : "kadabra",
     	 "description" : "Pokemon com doença mental",
     	 "type" : "psíquico",
     	 "attack" : 50,
    	  "defense" : 30,
    	  "height" : 5.7
	}

```

## 7. Modifique sua "description" e salve-o

```
> poke.description
Pokemon com doença mental
> poke.description = "Pokemon com sérios problemas mentais"
Pokemon com sérios problemas mentais
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> db.pokemons.findOne(query)
{
        "_id" : ObjectId("564e04e94b54c023375aff2a"),
        "name" : "kadabra",
        "description" : "Pokemon com sérios problemas mentais",
        "type" : "psíquico",
        "attack" : 50,
        "defense" : 30,
        "height" : 5.7
}

```
