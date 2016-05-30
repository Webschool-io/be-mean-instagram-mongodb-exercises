# MongoDb - Aula 02 - Exercício
autor: Felipe Rodrigues Alves

## Crie uma database chamada be-mean-pokemons;

```
Ubuntu16lts(mongod-3.2.6) test> use be-mean-pokemons
switched to db be-mean-pokemons

```
## Liste quais databases você possui nesse servidor;

```
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons> show dbs
be-mean → 0.078GB
local   → 0.078GB

```
## Liste quais coleções você possui nessa database;

```
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons> show collections
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons>

```

## Insira pelo menos 5 pokemons A SUA ESCOLHA;

```
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons> var pokemons = [
...     {
...         "name" : "Mareep",
...         "description" : "Mareep's fluffy coat of wool rubs together and builds a static charge. The more static electricity is charged, the more brightly the lightbulb at the tip of its tail glows.",
...         "attack" : "40",
...         "defense" : "40",
...         "height" : "6"
...     },
...     {
...         "name" : "Flaaffy",
...         "description" : "Flaaffy's wool quality changes so that it can generate a high amount of static electricity with a small amount of wool. The bare and slick parts of its hide are shielded against electricity.",
...         "attack" : "55",
...         "defense" : "55",
...         "height" : "8"
...     },
...     {
...         "name" : "Ampharos",
...         "description" : "Ampharos gives off so much light that it can be seen even from space. People in the old days used the light of this Pokémon to send signals back and forth with others far away.",
...         "attack" : "75",
...         "defense" : "85",
...         "height" : "14"
...     },
...     {
...         "name" : "Aipom",
...         "description" : "Aipom's tail ends in a hand-like appendage that can be cleverly manipulated. However, because the Pokémon uses its tail so much, its real hands have become rather clumsy.",
...         "attack" : "70",
...         "defense" : "55",
...         "height" : "8"
...     },
...     {
...         "name" : "Ambipom",
...         "description" : "They work in large colonies and make rings by linking their tails, apparently in friendship.",
...         "attack" : "100",
...         "defense" : "66",
...         "height" : "12"
...     }
... ]

db.pokedex.insert(pokemons)
Inserted 1 record(s) in 150ms
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

## Liste os pokemons existentes na sua coleção;

```
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons> db.pokedex.find()
{
  "_id": ObjectId("574c8eca2e1df3765012b15e"),
  "name": "Mareep",
  "description": "Ovelhinha azul do rabo laranja.",
  "attack": "40",
  "defense": "40",
  "height": "6"
}
{
  "_id": ObjectId("574c8eca2e1df3765012b15f"),
  "name": "Flaaffy",
  "description": "Ovelha rosa do rabo azul.",
  "attack": "55",
  "defense": "55",
  "height": "8"
}
{
  "_id": ObjectId("574c8eca2e1df3765012b160"),
  "name": "Ampharos",
  "description": "Ovelha pelada amarela do rabo vermelho.",
  "attack": "75",
  "defense": "85",
  "height": "14"
}
{
  "_id": ObjectId("574c8eca2e1df3765012b161"),
  "name": "Aipom",
  "description": "Macaquinho roxo sapeca.",
  "attack": "70",
  "defense": "55",
  "height": "8"
}
{
  "_id": ObjectId("574c8eca2e1df3765012b162"),
  "name": "Ambipom",
  "description": "Macaco roxo de dois rabos.",
  "attack": "100",
  "defense": "66",
  "height": "12"
}
Fetched 5 record(s) in 12ms
```

## Busque o pokemon da sua escolha, pelo nome, e armazene-o em uma variável chamada poke;

```
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons> var poke = db.pokedex.findOne(query)
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons> poke
{
  "_id": ObjectId("574c8eca2e1df3765012b161"),
  "name": "Aipom",
  "description": "Macaquinho roxo sapeca.",
  "attack": "70",
  "defense": "55",
  "height": "8"
}
```

## Modifique sua description e salvê-o;

```
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons> poke.description = 'Macaquinho roxo pilantra'
Macaquinho roxo pilantra
Ubuntu16lts(mongod-3.2.6) be-mean-pokemons> db.pokedex.save(poke)
Updated 1 existing record(s) in 9ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
