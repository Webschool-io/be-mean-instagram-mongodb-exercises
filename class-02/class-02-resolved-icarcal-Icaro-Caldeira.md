# MongoDB - Aula 02 - Exercício
autor: Icaro Caldeira (https://github.com/icarcal)

## Criando o database

```js
> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando databases no meu servidor

```js
> show dbs
be-mean           0.078GB
be-mean-pokemons  0.078GB
local             0.078GB
test              0.078GB
```

## Listando coleções da database be-mean-pokemons

```
> show collections
pokemons
system.indexes
```

## Inserindo pokemons

```js
> db.pokemons.insert({name: "Charmander", description: "The flame at the tip of its tail makes a sound as it burns. You can only hear it in quiet places.", attack: 52, defense: 43, height: 6})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({name: "Charmeleon", description: "When it swings its burning tail, it elevates the temperature to unbearably high levels.", attack: 64, defense: 58, height: 11})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({name: "Charizard", description: "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.", attack: 84, defense: 78, height: 17})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({name: "Pikachu", description: "It raises its tail to check its sur roundings. The tail is sometimes struck by lightning in this pose.", attack: 55, defense: 40, height: 4})
WriteResult({ "nInserted" : 1 })
> db.pokemons.insert({nome: "Raichu", description: "If the electric pouches in its cheeks become fully charged, both ears will stand straight up.", attack: 90, defense: 55, height: 8})
WriteResult({ "nInserted" : 1 })
```

## Listando pokemons

```js
> db.pokemons.find()
{ "_id" : ObjectId("5647d5d3ae7ee0ffc22ce47a"), "name" : "Charmander", "description" : "The flame at the tip of its tail makes a sound as it burns. You can only hear it in quiet places.", "attack" : 52, "defense" : 43, "height" : 6 }
{ "_id" : ObjectId("5647d5d3ae7ee0ffc22ce47b"), "name" : "Charmeleon", "description" : "When it swings its burning tail, it elevates the temperature to unbearably high levels.", "attack" : 64, "defense" : 58, "height" : 11 }
{ "_id" : ObjectId("5647d5d3ae7ee0ffc22ce47c"), "name" : "Charizard", "description" : "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.", "attack" : 84, "defense" : 78, "height" : 17 }
{ "_id" : ObjectId("5647d5d3ae7ee0ffc22ce47d"), "name" : "Pikachu", "description" : "It raises its tail to check its sur roundings. The tail is sometimes struck by lightning in this pose.", "attack" : 55, "defense" : 40, "height" : 4 }
{ "_id" : ObjectId("5647d5d3ae7ee0ffc22ce47e"), "name" : "Raichu", "description" : "If the electric pouches in its cheeks become fully charged, both ears will stand straight up.", "attack" : 90, "defense" : 55, "height" : 8 }
```

## Buscando pokemon

```js
> var query = {name: "Charizard"}
> var poke = db.pokemons.find(query)
> poke
{
    "_id" : ObjectId("5647d5d3ae7ee0ffc22ce47c"),
    "name" : "Charizard",
    "description" : "Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.",
    "attack" : 84,
    "defense" : 78,
    "height" : 17
}
```

## Alterando Pokemon
```js
> var query = {name: "Charizard"}
> var poke = db.pokemons.findOne(query)
> poke.description
Spits fire that is hot enough to melt boulders. Known to cause forest fires unintentionally.
> poke.description = "Charizard is fucking awesome"
Charizard is fucking awesome
> db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
> var poke = db.pokemons.findOne(query)
> poke
{
    "_id" : ObjectId("5647d5d3ae7ee0ffc22ce47c"),
    "name" : "Charizard",
    "description" : "Charizard is fucking awesome",
    "attack" : 84,
    "defense" : 78,
    "height" : 17
}
```