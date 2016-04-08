# MongoDb - Aula 02 - Exercício
autor João Paulo Effting

## Importando os restaurantes

```
>use be-mean-pokemons
switched to db be-mean-pokemons

```
## Listagem das databases(passo 2)

```
joaopaulo(mongod-2.6.3) be-mean-pokemons> show dbs
admin             → (empty)
be-mean-instagram → 0.078GB
local             → 0.078GB
test              → 0.078GB
```
## Listagem das coleções (passo 3)
```
joaopaulo(mongod-2.6.3) be-mean-pokemons> show collections
joaopaulo(mongod-2.6.3) be-mean-pokemons> 

```
## Cadastro dos pokemons(passo 4)

```
joaopaulo(mongod-2.6.3) be-mean-pokemons> var pokemon = {
... name: 'Pikachu',
... description: 'Ratinho fofinho',
... attack: 50,
... defense: 25,
... height: 20
... }
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 68ms
WriteResult({
  "nInserted": 1
})

joaopaulo(mongod-2.6.3) be-mean-pokemons> var pokemon = {
... name: 'Raichu',
... description: 'Evolução feia do pikachu',
... attack: 70,
... defense: 35,
... height: 30
... }
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

joaopaulo(mongod-2.6.3) be-mean-pokemons> var pokemon = {
... name: 'Squartle',
... description: 'Tartaruga Badass',
... attack: 50,
... defense: 25,
... height: 28
... }
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 5ms
WriteResult({
  "nInserted": 1
})

joaopaulo(mongod-2.6.3) be-mean-pokemons> var pokemon = {
... name: 'Chicorita',
... description: 'Pokémon homossexual',
... attack: 10,
... defense: 15,
... height: 18
... }
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

joaopaulo(mongod-2.6.3) be-mean-pokemons> var pokemon = {
... name: 'Ditto',
... description: 'Chang Sung dos pokémons',
... attack: 100,
... defense: 115,
... height: 118
... }
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.insert(pokemon)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})


```

## Listagem dos pokemons(passo 5)

```
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("5706fa736255d7b0b728448e"),
  "name": "Pikachu",
  "description": "Ratinho fofinho",
  "attack": 50,
  "defense": 25,
  "height": 20
}
{
  "_id": ObjectId("5706facb6255d7b0b728448f"),
  "name": "Raichu",
  "description": "Evolução feia do pikachu",
  "attack": 70,
  "defense": 35,
  "height": 30
}
{
  "_id": ObjectId("5706faf06255d7b0b7284490"),
  "name": "Squartle",
  "description": "Tartaruga Badass",
  "attack": 50,
  "defense": 25,
  "height": 28
}
{
  "_id": ObjectId("5706fb196255d7b0b7284491"),
  "name": "Chicorita",
  "description": "Pokémon homossexual",
  "attack": 10,
  "defense": 15,
  "height": 18
}
{
  "_id": ObjectId("5706fb446255d7b0b7284492"),
  "name": "Ditto",
  "description": "Chang Sung dos pokémons",
  "attack": 100,
  "defense": 115,
  "height": 118
}
Fetched 5 record(s) in 5ms


```

## pokemons(passo 6)

```

joaopaulo(mongod-2.6.3) be-mean-pokemons> var query = {name: 'Chicorita'}
joaopaulo(mongod-2.6.3) be-mean-pokemons> var poke = db.pokemons.findOne(query)
joaopaulo(mongod-2.6.3) be-mean-pokemons> poke
{
  "_id": ObjectId("5706fb196255d7b0b7284491"),
  "name": "Chicorita",
  "description": "Pokémon homossexual",
  "attack": 10,
  "defense": 15,
  "height": 18
}

```

## Atualização de Pokemon (passo 7)

```
joaopaulo(mongod-2.6.3) be-mean-pokemons> poke.description = 'Pokémon que gosta do mesmo sexo'
Pokémon que gosta do mesmo sexo
joaopaulo(mongod-2.6.3) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
joaopaulo(mongod-2.6.3) be-mean-pokemons> var poke = db.pokemons.findOne(query)
joaopaulo(mongod-2.6.3) be-mean-pokemons> poke
{
  "_id": ObjectId("5706fb196255d7b0b7284491"),
  "name": "Chicorita",
  "description": "Pokémon que gosta do mesmo sexo",
  "attack": 10,
  "defense": 15,
  "height": 18
}

```

