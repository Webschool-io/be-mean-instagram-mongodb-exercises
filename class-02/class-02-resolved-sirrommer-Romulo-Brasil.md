MongoDB - Aula 02 - Exercício
autor: sirrommer - Rômulo Brasil


## Criando database (passo 1)

```
> use be-mean-pokemons
switched to db be-mean-pokemons

```

## Listando databases (passo 2)

```
> show databases
be-mean            0.078GB
be-mean-instagram  0.078GB
be-mean-pokemons   0.078GB
local              0.078GB
```

## Listando collections da database be-mean-pokemons (passo 3)

```
> show collections
pokemons
system.indexes
```

## Cadastro dos pokemons (passo 4)

```
> var pokemon = [{"name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 100, "height" : 0.4},{"name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4},{"name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6},{"name" : "Caterpie", "description" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3},{"name" : "charizard", "description" : "Voa ao redor do céu", "type" : "fogo", "attack" : 40, "defense" : 30, "heigth" : 90}]

> db.pokemons.save(pokemon)
Inserted 1 record(s) in 129ms
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

## Lista de todos os pokemons da collections pokemons (passo 5)

```
> db.pokemons.find()
{ 
    "_id" : ObjectId("564a467a740cc428f1f83908"), 
    "name" : "Pikachu", 
    "description" : "Rato elétrico bem fofinho", 
    "type" : "electric", 
    "attack" : 100,
    "height" : 0.4 
}
{ 
    "_id" : ObjectId("564a467f740cc428f1f83909"), 
    "name" : "Bulbassauro", 
    "description" : "Chicote de trepadeira",
    "type" : "grama", 
    "attack" : 49,
    "height" : 0.4 
}
{ 
    "_id" : ObjectId("564a4685740cc428f1f8390a"), 
    "name" : "Charmander", 
    "description" : "Esse é o cão chupando manga de fofinho", 
    "type" : "fogo", 
    "attack" : 52, 
    "height" : 0.6 
}
{ 
    "_id" : ObjectId("564a4696740cc428f1f8390b"), 
    "name" : "Caterpie", 
    "description" : "Larva Lutadora", 
    "type" : "inseto", 
    "attack" : 30, 
    "height" : 0.3 
}
{ 
    "_id" : ObjectId("564a46d7740cc428f1f8390c"), 
    "name" : "charizard", 
    "description" : "Voa ao redor do céu", 
    "type" : "fogo", 
    "attack" : 40, 
    "defense" : 30,
    "heigth" : 90 
}

```

## Query para buscar um pokemon (passo 6)

```
> var query = {name:"charizard"}
> var poke = db.pokemons.findOne(query)
> poke
{
"_id" : ObjectId("564a46d7740cc428f1f8390c"),
"name" : "charizard",
"description" : "Voa ao redor do céu",
"type" : "fogo",
"attack" : 40,
"defense" : 30,
"heigth" : 90
}
```

## Atualização do Pokemon selecionado (passo 7)

```
> poke.description = "Charizard é um Pokémon tipo Fogo e Voador. Ele é a forma final da evolução de Charmander e Charmeleon quando chega no nível 36"
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> poke
{
"_id" : ObjectId("564a46d7740cc428f1f8390c"),
"name" : "charizard",
"description" : "Charizard é um Pokémon tipo Fogo e Voador. Ele é a forma final da evolução de Charmander e Charmeleon quando chega no nível 36",
"type" : "fogo",
"attack" : 40,
"defense" : 30,
"heigth" : 90
}

```
