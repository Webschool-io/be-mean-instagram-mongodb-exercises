###MongoDB - Aula 03 - Exercício
Autor: Mário Mello

##1. lista todos Pokemons com a altura menor que 0.5
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {height: {$lt: 0.5}}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5749e477a2ff0875f7e16846"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "defense": 25,
  "height": 0.4
}
{
  "_id": ObjectId("5749e477a2ff0875f7e16849"),
  "name": "caterpie",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 20,
  "defense": 25,
  "height": 0.4
}
Fetched 2 record(s) in 1ms
```

##2. liste todos pokemons com a altura maior ou igual que 0.5
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {height: {$gte: 0.5}}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5749e477a2ff0875f7e16847"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "defense": 35,
  "height": 0.6
}
{
  "_id": ObjectId("5749e477a2ff0875f7e16848"),
  "name": "charizard",
  "description": "Bota foto em tudo",
  "type": "Fogo",
  "attack": 100,
  "defense": 60,
  "height": 2
}
{
  "_id": ObjectId("5749e477a2ff0875f7e1684a"),
  "name": "metapod",
  "description": "É sério, parece uma vagem",
  "type": "grama",
  "attack": 10,
  "defense": 50,
  "height": 0.6
}
Fetched 3 record(s) in 8ms
```

##3. lsite todos pokemons com aaltura menor ou igual que 0.5 E do tipo grama
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{height: {$gte: 0.5}}, {type: /grama/i}]}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$gte": 0.5
      }
    },
    {
      "type": /grama/i
    }
  ]
}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5749e477a2ff0875f7e1684a"),
  "name": "metapod",
  "description": "É sério, parece uma vagem",
  "type": "grama",
  "attack": 10,
  "defense": 50,
  "height": 0.6
}
Fetched 1 record(s) in 1ms
```

##4. liste todos pokemons com o name 'metapod' OU com attack menor ou igual que 55
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {$or: [{attack: {$lte: 55}}, {name: /Metapod/i}]}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> query
{
  "$or": [
    {
      "attack": {
        "$lte": 55
      }
    },
    {
      "name": /Metapod/i
    }
  ]
}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5749e477a2ff0875f7e16846"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "defense": 25,
  "height": 0.4
}
{
  "_id": ObjectId("5749e477a2ff0875f7e16847"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "defense": 35,
  "height": 0.6
}
{
  "_id": ObjectId("5749e477a2ff0875f7e16849"),
  "name": "caterpie",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 20,
  "defense": 25,
  "height": 0.4
}
{
  "_id": ObjectId("5749e477a2ff0875f7e1684a"),
  "name": "metapod",
  "description": "É sério, parece uma vagem",
  "type": "grama",
  "attack": 10,
  "defense": 50,
  "height": 0.6
}
Fetched 4 record(s) in 5ms
```

##5. liste todos pokemons com o attack Maior ou igual que 48 E com height menor ou igual que 55
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 55}}]}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 55
      }
    }
  ]
}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5749e477a2ff0875f7e16846"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "defense": 25,
  "height": 0.4
}
{
  "_id": ObjectId("5749e477a2ff0875f7e16847"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "defense": 35,
  "height": 0.6
}
{
  "_id": ObjectId("5749e477a2ff0875f7e16848"),
  "name": "charizard",
  "description": "Bota foto em tudo",
  "type": "Fogo",
  "attack": 100,
  "defense": 60,
  "height": 2
}
Fetched 3 record(s) in 2ms
```


