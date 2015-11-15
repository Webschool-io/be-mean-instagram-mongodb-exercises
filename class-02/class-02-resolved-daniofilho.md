# MongoDB - Aula 02 - Exercício
autor: Dânio Filho

## Listagem das databases (passo 2)

```
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> show dbs
be-mean            0.078GB
be-mean-instagram  0.078GB
local              0.078GB
```

## Listagem das coleções (passo 3)

```
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> use be-mean
switched to db be-mean

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> show collections
restaurantes
system.indexes

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> use be-mean-instagram
switched to db be-mean-instagram

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> show collections
pokemons
system.indexes
teste
```


## Cadastro dos pokemons (passo 4)

```
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> var pokemon = {'name':'Cacturne','description':'Lorem ipsum dolor sit amet', 'attack': 115, 'defense': 68, height: 13 }
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> var pokemon = {'name':'Chesnaught','description':'Maecenas non tincidunt sapien, in sodales augue.', 'attack': 107, 'defense': 49, height: 0 }
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> var pokemon = {'name':'Phanpy','description':'Fusce blandit leo tristique sem facilisis luctus.', 'attack': 60, 'defense': 24, height: 5 }
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> var pokemon = {'name':'Caterpie','description':'Suspendisse potenti. Nullam nec erat venenatis, cursus neque posuere.', 'attack': 30, 'defense': 35, height: 3 }
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> var pokemon = {'name':'Voltorb','description':'Sed fringilla purus justo', 'attack': 30,'defense': 50, height: 5 }
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> var pokemon = {'name':'Cherrim','description':'Quisque quis blandit eros.', 'attack': 60, 'defense': 70, height: 5 }
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })

MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> var pokemon = {'name':'Glameow','description':'Nullam ornare sed nibh id gravida. ', 'attack': 55, 'defense': 42, height: 5 }
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-instagram> db.pokemons.insert(pokemon)
WriteResult({ "nInserted" : 1 })
```

## Lista dos pokemons (passo 5)

```
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56427cfc03570fe3664c85ab"),
  "name": "Cacturne",
  "description": "Lorem ipsum dolor sit amet",
  "attack": 115,
  "defense": 68,
  "height": 13
}
{
  "_id": ObjectId("56427cfe03570fe3664c85ac"),
  "name": "Chesnaught",
  "description": "Maecenas non tincidunt sapien, in sodales augue.",
  "attack": 107,
  "defense": 49,
  "height": 0
}
{
  "_id": ObjectId("56427cfe03570fe3664c85ad"),
  "name": "Phanpy",
  "description": "Fusce blandit leo tristique sem facilisis luctus.",
  "attack": 60,
  "defense": 24,
  "height": 5
}
{
  "_id": ObjectId("56427cfe03570fe3664c85ae"),
  "name": "Caterpie",
  "description": "Suspendisse potenti. Nullam nec erat venenatis, cursus neque posuere.",
  "attack": 30,
  "defense": 35,
  "height": 3
}
{
  "_id": ObjectId("56427cfe03570fe3664c85af"),
  "name": "Voltorb",
  "description": "Descrição alterada",
  "attack": 30,
  "defense": 50,
  "height": 5
}
{
  "_id": ObjectId("56427cfe03570fe3664c85b0"),
  "name": "Cherrim",
  "description": "Quisque quis blandit eros.",
  "attack": 60,
  "defense": 70,
  "height": 5
}
{
  "_id": ObjectId("56427cfe03570fe3664c85b1"),
  "name": "Glameow",
  "description": "Nullam ornare sed nibh id gravida. ",
  "attack": 55,
  "defense": 42,
  "height": 5
}
Fetched 7 record(s) in 6ms
```

## Pikachu (passo 6)

```
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-pokemons> var query = {name: "Voltorb"}
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
```

## Atualização do Pikachu (passo 6)

```
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-pokemons> poke.description = "Descrição alterada"
Descrição alterada
MacBook-Pro-de-Danio(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 7ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
