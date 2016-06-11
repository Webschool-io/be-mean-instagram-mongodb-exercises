# MongoDB - Aula 02 - Exercício
autor: Mário Mello

## Criando database be-mean-pokemons
```
➜  ~ mongo be-mean-pokemons
MongoDB shell version: 3.2.6
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.13
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons>
```

## Listando as databases
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
local             → 0.000GB
test              → 0.000GB
```
PS: Não aparece ainda o be-mean-pokemons por não ter dados

## Listando as coleções
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> show collections
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons>
```
PS: Não tenho coleções ainda no database

## Inserindo os pokemons
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var pokemons = [
	{
      "name":"Bulbassauro",
      "description":"Chicote de trepadeira",
      "type":"grama",
      "attack":49,
      "defense":25,
      "height":0.4
   },
   {
      "name":"Charmander",
      "description":"Esse é o cão chupando manga de fofinho",
      "type":"fogo",
      "attack":52,
      "defense":35,
      "height":0.6
   },
   {
      "name":"charizard",
      "description":"Bota foto em tudo",
      "type":"Fogo",
      "attack":100,
      "defense":60,
      "height":2
   },
   {
      "name":"caterpie",
      "description":"Chicote de trepadeira",
      "type":"grama",
      "attack":20,
      "defense":25,
      "height":0.4
   },
   {
      "name":"metapod",
      "description":"Parece uma vagem",
      "type":"grama",
      "attack":10,
      "defense":50,
      "height":0.6
   }
]

macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.insert(pokemons)
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

## Listando os pokemons
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find()
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
  "description": "Parece uma vagem",
  "type": "grama",
  "attack": 10,
  "defense": 50,
  "height": 0.6
}
Fetched 5 record(s) in 3ms
```

## Buscando o 'metapod' para a variável poke
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var poke = db.pokemons.findOne({name: "metapod"})
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> poke
{
  "_id": ObjectId("5749e477a2ff0875f7e1684a"),
  "name": "metapod",
  "description": "Parece uma vagem",
  "type": "grama",
  "attack": 10,
  "defense": 50,
  "height": 0.6
}
```

## Modificando a description e salvando
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> poke.description = "É sério, parece uma vagem"
É sério, parece uma vagem
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```