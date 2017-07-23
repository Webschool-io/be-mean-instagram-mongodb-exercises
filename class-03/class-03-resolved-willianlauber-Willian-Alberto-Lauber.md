# MongoDB - Aula 03 - Exercício
**autor** willianlauber

## Listando pokémons com altura menor que 0.5 (exercicio 1)
```sql
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {height : {$lt : 0.5}}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57fa74d80dd8b7f6a1513794"),
  "name": "Gato",
  "description": "gosta de osso e carne",
  "attack": 10,
  "defence": 2,
  "height": 0.3
}
{
  "_id": ObjectId("57fa76b2e5e3195f7d8851e0"),
  "name": "Gato",
  "description": "gosta de osso e carne",
  "attack": 10,
  "defence": 2,
  "height": 0.3
}
Fetched 2 record(s) in 1ms
lubuntu(mongod-2.6.10) be-mean-pokemons>
```

## Listando pokémons com altura maior ou igual a 0.5 (exercicio 2)
```sql
lc@lubuntu ~
$ mongo be-mean-pokemons
MongoDB shell version: 2.6.10
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.14
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = {height : {$gte : 0.5}}
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
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
 "_id": ObjectId("57fa76cce5e3195f7d8851e1"),
 "name": "ornitorinco",
 "description": "gosta de osso e sabe nadar",
 "attack": 0,
 "defence": 312,
 "height": 0.5
}
Fetched 9 record(s) in 5ms
lubuntu(mongod-2.6.10) be-mean-pokemons>
```

## Listando as pokémons com altura menor ou igual a 0.5 e do tipo grama (exercicio 3)
```sql
query = { $and: [{height: { $lte: 0.5 }}, { type: "grama" }] }
db.pokemons.find(query)
```

## Listando pokémons com o nome Pikachu ou com attack menor ou igual a 0.5 (exercicio 4)
```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = { $or: [{ name: "Pikachu" }, { attack: { $lte: 0.5 } }] }
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
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
Fetched 2 record(s) in 44ms
lubuntu(mongod-2.6.10) be-mean-pokemons>
```

## Listando os pokémons com attack maior ou igual a 48 e com height menor que 0.5 (exercicio 5)

```js
lubuntu(mongod-2.6.10) be-mean-pokemons> var query = { $and: [{ attack: { $gte: 48 } }, { height: { $lte: 0.5 } }] }
lubuntu(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
lubuntu(mongod-2.6.10) be-mean-pokemons>
```
