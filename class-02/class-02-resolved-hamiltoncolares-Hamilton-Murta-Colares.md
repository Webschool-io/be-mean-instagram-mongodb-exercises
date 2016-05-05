# MongoDB - Aula 02 - Exerício
autor: Hamilton Murta Colares

## Criando o DB

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando DBs

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> show dbs
be-mean-instagram → 0.004GB
local             → 0.000GB
```

## Listando coleções

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> show collections
pokemons     →  0.001MB / 0.035MB
restaurantes → 10.138MB / 3.910MB
```

## Inserindo 5 pokemons

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var pokemon = {'name':'Charizard','description':'Dinossauro que voa','type': 'fogo', attack: 84, height: 1.7}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var pokemon = {'name':'Wartortle','description':'Tartaruga azul','type': 'água', attack: 49, height: 1.0}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var pokemon = {'name':'Blastoise','description':'Tartaruga cascuda','type': 'água', attack: 83, height: 1.6}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var pokemon = {'name':'Pidgeotto','description':'Pássaro topete','type': 'normal', attack: 60, height: 1.1}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var pokemon = {'name':'Nidorina','description':'Coala olrelhudo','type': 'venenoso', attack: 62, height: 0.8}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```

## Listando pokemons existentes

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.find()
{
  "_id": ObjectId("566efc41330b9efc28aedac4"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("566efca9330b9efc28aedac5"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("566efcc2330b9efc28aedac6"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("566efd99330b9efc28aedac7"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("566efdf5330b9efc28aedac8"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}
{
  "_id": ObjectId("566f0a3a330b9efc28aedac9"),
  "name": "Charizard",
  "description": "Dinossauro que voa",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}
{
  "_id": ObjectId("566f0a48330b9efc28aedaca"),
  "name": "Wartortle",
  "description": "Tartaruga azul",
  "type": "água",
  "attack": 49,
  "height": 1
}
{
  "_id": ObjectId("566f0a57330b9efc28aedacb"),
  "name": "Blastoise",
  "description": "Tartaruga cascuda",
  "type": "água",
  "attack": 83,
  "height": 1.6
}
{
  "_id": ObjectId("566f0a60330b9efc28aedacc"),
  "name": "Pidgeotto",
  "description": "Pássaro topete",
  "type": "normal",
  "attack": 60,
  "height": 1.1
}
{
  "_id": ObjectId("566f0a68330b9efc28aedacd"),
  "name": "Nidorina",
  "description": "Coala olrelhudo",
  "type": "venenoso",
  "attack": 62,
  "height": 0.8
}
Fetched 10 record(s) in 4ms
```

## Buscando pokemon

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var query = {name: 'Charizard'}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> var poke = db.pokemons.findOne(query)
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.findOne(query)
{
  "_id": ObjectId("566f0a3a330b9efc28aedac9"),
  "name": "Charizard",
  "description": "Dinossauro que voa",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}
```

## Modificando description

```
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> poke.description = 'Dinossauro voador gigante'
Dinossauro voador gigante
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.save(poke)
Updated 1 existing record(s) in 5ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> query = {name: 'Charizard'}
{
  "name": "Charizard"
}
MacBook-Pro-de-Hamilton(mongod-3.2.0) be-mean-instagram> db.pokemons.findOne(query)
{
  "_id": ObjectId("566f0a3a330b9efc28aedac9"),
  "name": "Charizard",
  "description": "Dinossauro voador gigante",
  "type": "fogo",
  "attack": 84,
  "height": 1.7
}
