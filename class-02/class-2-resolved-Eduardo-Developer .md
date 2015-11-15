MongoDB - Aula 02 - Exercício

autor: Eduardo Developer
1. Crie uma database chamada be-mean-pokemons;

```
eduardodeveloper(mongod-3.0.7) be-man-pokemons>use be-man-pokemons
switched to db be-man-pokemons

```
2. Liste quais databases você possui nesse servidor;

```
eduardodeveloper(mongod-3.0.7) be-man-pokemons>show dbs
local             → 0.078GB
be-mean-instagran → 0.078GB

```
3. Liste quais coleções você possui nessa database;

```
eduardodeveloper(mongod-3.0.7) be-man-pokemons>show collections
eduardodeveloper(mongod-3.0.7) be-man-pokemons>

```
4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos
utilizado: name, description, attack, defense e height;

```
eduardodeveloper(mongod-3.0.7) be-man-pokemons> var pokemons = [{'name':'chlorophyll','description':'cara louco','attack':49,'defense':49, height:0.9},{'name':'Monster','description':'cara de maluco','attack':24,'defense':65, height:0.3}
... ,{'name':'Grass','description':'cara de bicho','attack':09,'defense':60, height:0.5}
... ,{'name':'Growl','description':'cara de cachorro','attack':67,'defense':98, height:0.2}
... ,{'name':'Bulbasaur','description':'cara de banana','attack':23,'defense':45, height:0.7}
... ,{'name':'Poison','description':'cara de mané','attack':09,'defense':34, height:0.4}]
eduardodeveloper(mongod-3.0.7) be-man-pokemons> pokemons
[
  {
    "name": "chlorophyll",
    "description": "cara louco",
    "attack": 49,
    "defense": 49,
    "height": 0.9
  },
  {
    "name": "Monster",
    "description": "cara de maluco",
    "attack": 24,
    "defense": 65,
    "height": 0.3
  },
  {
    "name": "Grass",
    "description": "cara de bicho",
    "attack": 9,
    "defense": 60,
    "height": 0.5
  },
  {
    "name": "Growl",
    "description": "cara de cachorro",
    "attack": 67,
    "defense": 98,
    "height": 0.2
  },
  {
    "name": "Bulbasaur",
    "description": "cara de banana",
    "attack": 23,
    "defense": 45,
    "height": 0.7
  },
  {
    "name": "Poison",
    "description": "cara de mané",
    "attack": 9,
    "defense": 34,
    "height": 0.4
  }
]
eduardodeveloper(mongod-3.0.7) be-man-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 11474ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

```
5. Liste os pokemons existentes na sua coleção;

```
eduardodeveloper(mongod-3.0.7) be-man-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2764"),
  "name": "chlorophyll",
  "description": "cara louco",
  "attack": 49,
  "defense": 49,
  "height": 0.9
}
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2765"),
  "name": "Monster",
  "description": "cara de maluco",
  "attack": 24,
  "defense": 65,
  "height": 0.3
}
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2766"),
  "name": "Grass",
  "description": "cara de bicho",
  "attack": 9,
  "defense": 60,
  "height": 0.5
}
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2767"),
  "name": "Growl",
  "description": "cara de cachorro",
  "attack": 67,
  "defense": 98,
  "height": 0.2
}
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2768"),
  "name": "Bulbasaur",
  "description": "cara de banana",
  "attack": 23,
  "defense": 45,
  "height": 0.7
}
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2769"),
  "name": "Poison",
  "description": "cara de mané",
  "attack": 9,
  "defense": 34,
  "height": 0.4
}
Fetched 6 record(s) in 45ms

```
6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada poke;

```
eduardodeveloper(mongod-3.0.7) be-man-pokemons> var query = {"name": "Poison"}
eduardodeveloper(mongod-3.0.7) be-man-pokemons> var poke = db.pokemons.findOne(query)
eduardodeveloper(mongod-3.0.7) be-man-pokemons> poke
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2769"),
  "name": "Poison",
  "description": "cara de mané",
  "attack": 9,
  "defense": 34,
  "height": 0.4
}

```
7. Modifique sua description e salvê-o

```
eduardodeveloper(mongod-3.0.7) be-man-pokemons> var query = {"name": "Poison"}
eduardodeveloper(mongod-3.0.7) be-man-pokemons> var poke = db.pokemons.findOne(query)
eduardodeveloper(mongod-3.0.7) be-man-pokemons> poke
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2769"),
  "name": "Poison",
  "description": "cara de mané",
  "attack": 9,
  "defense": 34,
  "height": 0.4
}
eduardodeveloper(mongod-3.0.7) be-man-pokemons> poke.description
cara de mané
eduardodeveloper(mongod-3.0.7) be-man-pokemons> poke.description = "Pokemon Bonde do Safadão"
Pokemon Bonde do Safadão
eduardodeveloper(mongod-3.0.7) be-man-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 27ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
eduardodeveloper(mongod-3.0.7) be-man-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("5643f0ca0c5e16c4051d2769"),
  "name": "Poison",
  "description": "Pokemon Bonde do Safadão",
  "attack": 9,
  "defense": 34,
  "height": 0.4
}

```
