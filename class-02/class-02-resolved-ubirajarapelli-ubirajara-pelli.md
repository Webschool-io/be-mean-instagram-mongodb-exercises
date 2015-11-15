# MongoDB - Aula 02 - Exercício
autor: Ubirajara Pelli

## Criar o Banco Be MEAN Instgram Pokemons
```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)
```
> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
contatooh          0.078GB
local              0.078GB
```

## Listagem das coleções (passo 3)
```
> show collections
> 
```

## Cadastro dos pokemons (passo 4)
```
> var pokemon = { "name" : "Pikachu", "description" : "Rato elétrico", "type" : "eletric", "attack" : 55, "defense": 30, "height" : 0.4 }
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 

> var pokemon = { "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "defense": 45, "height" : 0.4 }
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 

> var pokemon = { "name" : "Charmander", "description" : "Dragão de fogo", "type" : "fogo", "attack" : 52,  "defense": 40, "height" : 0.6 }.
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 

> var pokemon = { "name" : "Squirtle", "description" : "Tartaruga que solta água", "type" : "água", "attack" : 48, "defense": 35, "height" : 0.5 }
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 

> var pokemon = { "name" : "Caterpie", "description": "Larva lutadora", "type": "inseto", "attack": 30, "defense": 20, height: 0.3}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
> 
```

## Lista dos pokemons (passo 5)
```
> db.pokemons.find()
{ "_id" : ObjectId("5644bd4c3c7fe93746e4b470"), "name" : "Pikachu", "description" : "Rato elétrico", "type" : "eletric", "attack" : 55, "defense" : 30, "height" : 0.4 }
{ "_id" : ObjectId("5644bdae3c7fe93746e4b471"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "defense" : 45, "height" : 0.4 }
{ "_id" : ObjectId("5644bdd73c7fe93746e4b472"), "name" : "Charmander", "description" : "Dragão de fogo", "type" : "fogo", "attack" : 52, "defense" : 40, "height" : 0.6 }
{ "_id" : ObjectId("5644be4b5af181c8ac5d122f"), "name" : "Squirtle", "description" : "Tartaruga que solta água", "type" : "água", "attack" : 48, "defense" : 35, "height" : 0.5 }
{ "_id" : ObjectId("5644be6d5af181c8ac5d1230"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "defense" : 20, "height" : 0.3 }
> 
```

## Pikachu (passo 6)
```
> var query = {name: 'Pikachu'}
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("5644bd4c3c7fe93746e4b470"),
	"name" : "Pikachu",
	"description" : "Rato elétrico",
	"type" : "eletric",
	"attack" : 55,
	"defense" : 30,
	"height" : 0.4
}
> 
```

## Atualização do Pikachu (passo 6)
```
> poke.description = "Eu prefiro cerveja"
Eu prefiro cerveja
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("5644bd4c3c7fe93746e4b470"),
	"name" : "Pikachu",
	"description" : "Eu prefiro cerveja",
	"type" : "eletric",
	"attack" : 55,
	"defense" : 30,
	"height" : 0.4
}
> 
```
