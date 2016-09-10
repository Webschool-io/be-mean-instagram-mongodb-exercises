# MongoDB - Aula 02 - Exercício
autor: Thiago R. M. Bitencourt

## Criar database be-mean-pokemons (passo 1)

```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Databases existentes (passo 2)

```
> show dbs
be-mean   0.203GB
local     0.078GB
test      0.203GB
xy-inc    0.203GB
```

## Listagem das coleções (passo 3)
```
show collections
```

## Inserir pokemons (passo 4)

```
> var Charizard = {name: 'Charizard', description: 'Pokemon massa de fogo', type: 'fogo', attack: 77, height:1.7 }
> var Pidgeot = {name: 'Pidgeot', description: 'Voador dos bons', type: 'voador', attack: 69, height: 1.5}
> var Persian = {name: 'Persian', description: 'Gatinho bonitinho', type: 'Fancy cat', attack: 94, height: 1.1}
> var Vulpix = {name: 'Vulpix', description: 'Fofo porém mortal', type: 'fogo', attack: 41, height: 0.6}
> var Zubat = {name: 'Zubat', description: 'Parente distante do batman', type: 'Batman', attack: 38, height: 0.8}

> db.pokemons.insert(Charizard)
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert(Pidgeot)
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert(Persian)
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert(Vulpix)
WriteResult({ "nInserted" : 1 })

> db.pokemons.insert(Zubat)
WriteResult({ "nInserted" : 1 })
```

## Liste os pokemons (passo 5)

```
> db.pokemons.find().pretty()
{
	"_id" : ObjectId("5779c63eebea693787997603"),
	"name" : "Charizard",
	"description" : "Pokemon massa de fogo",
	"type" : "fogo",
	"attack" : 77,
	"height" : 1.7
}
{
	"_id" : ObjectId("5779c64bebea693787997604"),
	"name" : "Pidgeot",
	"description" : "Voador dos bons",
	"type" : "voador",
	"attack" : 69,
	"height" : 1.5
}
{
	"_id" : ObjectId("5779c650ebea693787997605"),
	"name" : "Persian",
	"description" : "Gatinho bonitinho",
	"type" : "Fancy cat",
	"attack" : 94,
	"height" : 1.1
}
{
	"_id" : ObjectId("5779c658ebea693787997606"),
	"name" : "Vulpix",
	"description" : "Fofo porém mortal",
	"type" : "fogo",
	"attack" : 41,
	"height" : 0.6
}
{
	"_id" : ObjectId("5779c65debea693787997607"),
	"name" : "Zubat",
	"description" : "Parente distante do batman",
	"type" : "Batman",
	"attack" : 38,
	"height" : 0.8
}
```

## Buscar Pokemon (passo 6)

```
> var query = {name: 'Persian'}
> var poke = db.pokemons.findOne(query)
> poke
{
	"_id" : ObjectId("5779c650ebea693787997605"),
	"name" : "Persian",
	"description" : "Gatinho bonitinho",
	"type" : "Fancy cat",
	"attack" : 94,
	"height" : 1.1
}
```

## Modificar e salvar (passo 7)

```
> poke.description
Gatinho bonitinho
> poke.description = "Gatinho mortal"
Gatinho mortal
> db.pokemons.save(poke)
WriteResult({
  "nMatched" : 1,
  "nUpserted" : 0,
  "nModified": 1 })
> db.pokemons.findOne(query)
{
	"_id" : ObjectId("5779c650ebea693787997605"),
	"name" : "Persian",
	"description" : "Gatinho mortal",
	"type" : "Fancy cat",
	"attack" : 94,
	"height" : 1.1
}
```
