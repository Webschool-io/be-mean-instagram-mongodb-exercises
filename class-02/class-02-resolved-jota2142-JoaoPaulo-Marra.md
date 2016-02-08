# MongoDB - Aula 02 - Exercício

Autor: João Paulo Costa Marra

## Criar base de dados be-mean-pokemons

``` shell
Jota-PC(mongod-3.2.1) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listar databases locais

``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean → 0.004GB
local   → 0.000GB
test    → 0.000GB
```

## Listar coleções na database atual

``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> show collections
```

## Inserir na database 5 pokemons

``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> var pokemonList = [
    {name: 'Pikachu', description: 'Ratinho elétrico', type: 'elétrico', attack: 55, defense: 40, height: 0.41},
    {name: 'Charmander', description: 'Lagartixa isqueiro', type: 'fogo', attack: 52, defense: 43, height: 0.61},
    {name: 'Squirtle', description: 'Tartaruga das bolhas', type: 'água', attack: 48, defense: 65, height: 0.51},
    {name: 'Pidgey', description: 'Passarinho nervoso', type: 'normal', attack: 45, defense: 40, height: 0.3},
    {name: 'Bulbasaur', description: 'Sapinho dos chicotes', type: 'grama', attack: 49, defense: 49, height: 0.4}
]
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemonList)
Inserted 1 record(s) in 17ms
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

## Listar todos os pokemons da collection criada

``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c0"),
  "name": "Pikachu",
  "description": "Ratinho elétrico",
  "type": "elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c1"),
  "name": "Charmander",
  "description": "Lagartixa isqueiro",
  "type": "fogo",
  "attack": 52,
  "defense": 43,
  "height": 0.61
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c2"),
  "name": "Squirtle",
  "description": "Tartaruga das bolhas",
  "type": "água",
  "attack": 48,
  "defense": 65,
  "height": 0.51
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c3"),
  "name": "Pidgey",
  "description": "Passarinho nervoso",
  "type": "normal",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}
{
  "_id": ObjectId("56b8df22a5f278ec2aa1a1c4"),
  "name": "Bulbasaur",
  "description": "Sapinho dos chicotes",
  "type": "grama",
  "attack": 49,
  "defense": 49,
  "height": 0.4
}
Fetched 5 record(s) in 5ms
```

## Buscar o 'Pikachu' e armazenar na variável poke

``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne({name: 'Pikachu'})
```

## Alterar o description da variável poke e salvar

``` shell
Jota-PC(mongod-3.2.1) be-mean-pokemons> poke.description = 'Rato que curte falar pika'
Rato que curte falar pika
Jota-PC(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```