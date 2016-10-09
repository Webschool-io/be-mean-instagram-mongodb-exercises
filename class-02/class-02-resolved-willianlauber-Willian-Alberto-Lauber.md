MongoDb - Aula 02 - Exercício

**Autor** : Willian Lauber
**Date** : s

# Cria database be-mean-pokemons (ex1)

```js
$ mongo be-mean-pokemons
MongoDB shell version: 2.6.10
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.14
lubuntu(mongod-2.6.10) be-mean-pokemons>
```

# Listagem das databases(ex 2)

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> show dbs
admin             → (empty)
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
class1            → 0.078GB
local             → 0.078GB
```

# Listagem de coleções (ex 3)

```Mongo-Hacker
lubuntu(mongod-2.6.10) be-mean-pokemons> show collections
```

# Inserindo pelo menos 5 pokemons na base (ex 4)

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var pokemon = {name : "Lagarto", description : "gosta de ovo e foje de cachoro", attack : 2, defence : 1, height : 0.6}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon)
lubuntu(mongod-2.6.10) be-mean-pokemons> var pokemon2 = {name : "Cobra", description : "gosta de rato e é venenosa", attack : 42, defence : 1, height : 1.6}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon2)
lubuntu(mongod-2.6.10) be-mean-pokemons> var pokemon3 = {name : "Cachoro", description : "gosta de osso e carnea", attack : 22, defence : 5, height : 0.6}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon3)
lubuntu(mongod-2.6.10) be-mean-pokemons> var pokemon4 = {name : "Gato", description : "gosta de osso e carne", attack : 10, defence : 2, height : 0.3}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon4)
lubuntu(mongod-2.6.10) be-mean-pokemons> var pokemon5 = {name : "ornitorinco", description : "gosta de osso e sabe nadar", attack : 0, defence : 312, height : 0.5}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.insert(pokemon5)
```


# Listar os pokemons existentes(passo 5)

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57fa74940dd8b7f6a1513792"),
  "name": "Lagarto",
  "description": "gosta de ovo e foje de cachoro",
  "attack": 2,
  "defence": 1,
  "height": 0.6
}
{
  "_id": ObjectId("57fa74b70dd8b7f6a1513793"),
  "name": "Cachoro",
  "description": "gosta de osso e carnea",
  "attack": 22,
  "defence": 5,
  "height": 0.6
}
{
  "_id": ObjectId("57fa74d80dd8b7f6a1513794"),
  "name": "Gato",
  "description": "gosta de osso e carne",
  "attack": 10,
  "defence": 2,
  "height": 0.3
}
{
  "_id": ObjectId("57fa74f00dd8b7f6a1513795"),
  "name": "Cachoro",
  "description": "gosta de osso e carnea",
  "attack": 22,
  "defence": 5,
  "height": 0.6
}
{
  "_id": ObjectId("57fa74f30dd8b7f6a1513796"),
  "name": "ornitorinco",
  "description": "gosta de osso e sabe nadar",
  "attack": 0,
  "defence": 312,
  "height": 0.5
}
{
  "_id": ObjectId("57fa750f0dd8b7f6a1513797"),
  "name": "ornitorinca",
  "description": "gosta de osso e sabe nadar e é femea",
  "attack": 1,
  "defence": 31,
  "height": 0.5
}
{
  "_id": ObjectId("57fa75f1e5e3195f7d8851dd"),
  "name": "Lagarto",
  "description": "gosta de ovo e foje de cachoro",
  "attack": 2,
  "defence": 1,
  "height": 0.6
}
{
  "_id": ObjectId("57fa7660e5e3195f7d8851de"),
  "name": "Cobra",
  "description": "gosta de rato e é venenosa",
  "attack": 42,
  "defence": 1,
  "height": 1.6
}
{
  "_id": ObjectId("57fa7693e5e3195f7d8851df"),
  "name": "Cachoro",
  "description": "gosta de osso e carnea",
"attack": 22,
"defence": 5,
"height": 0.6
}
{
"_id": ObjectId("57fa76b2e5e3195f7d8851e0"),
"name": "Gato",
"description": "gosta de osso e carne",
"attack": 10,
"defence": 2,
"height": 0.3
}
{
"_id": ObjectId("57fa76cce5e3195f7d8851e1"),
"name": "ornitorinco",
"description": "gosta de osso e sabe nadar",
"attack": 0,
"defence": 312,
"height": 0.5
}
Fetched 11 record(s) in 10ms
lubuntu(mongod-2.6.10) be-mean-pokemons>

  ```
# Busque pokemons pelo nome e armazene em uma variável(ex 5)

```js

lubuntu(mongod-2.6.10) be-mean-pokemons> var qyery = {"name":"ornitorinco"}
lubuntu(mongod-2.6.10) be-mean-pokemons> p
lubuntu(mongod-2.6.10) be-mean-pokemons> var p = db.pokemons.find(qyery)
{
  "_id": ObjectId("57fa74f30dd8b7f6a1513796"),
  "name": "ornitorinco",
  "description": "gosta de osso e sabe nadar",
  "attack": 0,
  "defence": 312,
  "height": 0.5
}
{
  "_id": ObjectId("57fa76cce5e3195f7d8851e1"),
  "name": "ornitorinco",
  "description": "gosta de osso e sabe nadar",
  "attack": 0,
  "defence": 312,
  "height": 0.5
}
Fetched 2 record(s) in 3ms
```

#Armazene em uma variavel e faça a alteração da descrição do Pokemon(ex 6 e 7)
```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var p = db.pokemons.findOne(qyery)
lubuntu(mongod-2.6.10) be-mean-pokemons> p
lubuntu(mongod-2.6.10) be-mean-pokemons> p.name = "ornitorinca"
ornitorinca
lubuntu(mongod-2.6.10) be-mean-pokemons> p.description = "femea estranha"
femea estranha
```
