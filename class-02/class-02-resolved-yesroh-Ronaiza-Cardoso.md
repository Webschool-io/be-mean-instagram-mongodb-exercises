# MongoDb - Aula 02 - Exercício
autor: Ronaiza Cardoso

## Exercicio Pokemons

```
>use be-mean-pokemons
switched to db be-mean-pokemons
```
## Listagem das databases(passo 2)

```
> show dbs
be-mean           → 0.000GB
be-mean-instagram → 0.000GB
be-mean-teste     → 0.000GB
local             → 0.000GB
```
## Listagem coleções na database (passo 3)
```
>show collections 
startup_log → 0.007MB / 0.035MB

```

## Cadastro dos pokemons(passo 4)

```

> var pokemon ={'name':'Charizar','description':'Charizard flies around the sky in search of powerful opponents.','type':'Fogo', attack:70, height:1.7}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

>  var pokemon ={'name':'Mariza','description':'Lacradora contenporanea.','type':'Fogo', attack:100, height:1.7}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon ={'name':'Silvio Santos','description':'A reprentatividade da meritocracia que funciona tal qual a roleta russa','type':'Aviões de Dinheiro', attack:300, height:2.8}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

> var pokemon ={'name':'Dikklma','description':'Presidenta que não teve jogo de cintura em relação a corja de bandidos que a cercavão, ensava poder vencer apenas com a honestidade','type':'Politica', attack:76, defense: 0, height:1.9}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

>var pokemon ={'name':'Bolsonaro','description':'Deputado direitista','type':'Metralhadora de merda', attack:180, defense: 500, height:1.5}
> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

```

## Listagem dos pokemons(passo 5)

```

> var lista = db.pokemons.find()

Ronaiza_Card(C:\Program Files\MongoDB\Server\3.2\bin\mongod.exe-3.2.7) be-mean-pokemons> lista

{
  "_id": ObjectId("577ba38306c3c41e402f538c"),
  "name": "Charizar",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "type": "Fogo",
  "attack": 70,
  "height": 1.7
}
{
  "_id": ObjectId("577ba3d906c3c41e402f538d"),
  "name": "Mariza",
  "description": "Lacradora contenporanea.",
  "type": "Fogo",
  "attack": 100,
  "height": 1.7
}
{
  "_id": ObjectId("577ba42406c3c41e402f538e"),
  "name": "Silvio Santos",
  "description": "A reprentatividade da meritocracia que funciona tal qual a roleta russa",
  "type": "Aviões de Dinheiro",
  "attack": 300,
  "height": 2.8
}
{
  "_id": ObjectId("577ba4ce06c3c41e402f538f"),
  "name": "Dikklma",
  "description": "Presidenta que não teve jogo de cintura em relação a corja de bandidos que a cercavão, ensava poder vencer apenas com a honestidade",
  "type": "Politica",
  "attack": 76,
  "defense": 0,
  "height": 1.9
}
{
  "_id": ObjectId("577ba51f06c3c41e402f5390"),
  "name": "Bolsonaro",
  "description": "Deputado direitista",
  "type": "Metralhadora de merda",
  "attack": 180,
  "defense": 500,
  "height": 1.5
}
Fetched 5 record(s) in 211ms

```

## pokemons(passo 6)

```
> var up = {name: 'Bolsonaro'}
> var poke = db.pokemons.findOne(up)
> poke
{
  "_id": ObjectId("577ba51f06c3c41e402f5390"),
  "name": "Bolsonaro",
  "description": "Deputado direitista",
  "type": "Metralhadora de merda",
  "attack": 180,
  "defense": 500,
  "height": 1.5
}


```

## Atualização de Pokemon (passo 7)

```

> poke.description = "Deputado direitista sustentado além de ser pelo povo da igreja o meu, o seu, o nosso fucking dinheiro"
Deputado direitista sustentado além de ser pelo povo da igreja o meu, o seu, o nosso fucking dinheiro

> poke.description = "Deputado direitista sustentado além de ser pelo povo da igreja o meu, o seu, o nosso fucking dinheiro"
Deputado direitista sustentado além de ser pelo povo da igreja o meu, o seu, o nosso fucking dinheiro

> db.pokemon.save(poke) Updated 1 new record(s) in 209ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("577ba51f06c3c41e402f5390")
})

> var lista = db.pokemons.find()
> lista
{
  "_id": ObjectId("577ba38306c3c41e402f538c"),
  "name": "Charizar",
  "description": "Charizard flies around the sky in search of powerful opponents.",
  "type": "Fogo",
  "attack": 70,
  "height": 1.7
}
{
  "_id": ObjectId("577ba3d906c3c41e402f538d"),
  "name": "Mariza",
  "description": "Lacradora contenporanea.",
  "type": "Fogo",
  "attack": 100,
  "height": 1.7
}
{
  "_id": ObjectId("577ba42406c3c41e402f538e"),
  "name": "Silvio Santos",
  "description": "A reprentatividade da meritocracia que funciona tal qual a roleta russa",
  "type": "Aviões de Dinheiro",
  "attack": 300,
  "height": 2.8
}
{
  "_id": ObjectId("577ba4ce06c3c41e402f538f"),
  "name": "Dikklma",
  "description": "Presidenta que não teve jogo de cintura em relação a corja de bandidos que a cercavão, ensava poder vencer apenas com a honestidade",
  "type": "Politica",
  "attack": 76,
  "defense": 0,
  "height": 1.9
}
{
  "_id": ObjectId("577ba51f06c3c41e402f5390"),
  "name": "Bolsonaro",
  "description": "Deputado direitista",
  "type": "Metralhadora de merda",
  "attack": 180,
  "defense": 500,
  "height": 1.5
}
Fetched 5 record(s) in 48ms

```

