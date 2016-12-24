# MongoDB - Aula 02 - Exercício
autor: Antonio Carlos da silva 

## Criando database chamada be-mean-pokemons;

```
use be-mean-pokemons
switched to db be-mean-pokemons

```
## Listando databases contida no servidor;

```
show dbs
admin             → 0.078GB
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB

```
## Listando as coleções contida na database;

```
show collections

```
## Inserir pelo menos 5 pokemons;

```
var pokemons = [{
'name':'bulbasaur',
'description':'Ṕode ser visto dormindo na luz solar. Por absorver os raios do sol.',
'attack':30,
'defense':20,
'height':70
},
{
'name':'Ivysaur',
'description':'Se ele começa a passar mais tempo deitado ao sol, é um sinal de que  vai florescer uma grande flor em breve.',
'attack':30,
'defense':30,
'height':100
},
{
'name': 'Venusaur',
'description':'Há uma grande flor na parte traseira. A flor é dito para ter  cores vivas. O aroma da flor acalma as emoções das pessoas.',
'attack':40,
'defense':40,
'height':200
},
{
'name':'Charmander',
'description':'A chama que arde na ponta da cauda é uma indicação das suas emoções. Se o Pokémon fica furioso, a chama queima ferozmente.',
'attack':30,
'defense':20,
'height':60
},
{
'name':'Charizard',
'description':'voa em torno do céu em busca de adversários poderosos.',
'attack':40,
'defense':30,
'height':170
},
{
'name':'Caterpie',
'description':' tem um apetite voraz. Ele pode devorar as folhas maiores do que o seu corpo. Este Pokémon libera um odor terrivelmente forte.',
'attack':20,
'defense':20,
'height':30
},
{
'name': 'Beedrill',
'description':'Extremamente territorial. Ninguém deve aproximar seu ninho para sua própria segurança.',
'attack':50,
'defense':20,
'height':100
},
{
'name': 'Pikachu',
'description':'Sempre que se depara com algo novo, ele dispara  um choque de elétrico',
'attack':30,
'defense':20,
'height':40
}]
avell-linux(mongod-3.2.10) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 128ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 8,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

```
## Listar os pokemons existente na coleção;

```
db.pokemons.find()
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff3"),
  "name": "bulbasaur",
  "description": "Ṕode ser visto dormindo na luz solar. Por absorver os raios do sol.",
  "attack": 30,
  "defense": 20,
  "height": 70
}
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff4"),
  "name": "Ivysaur",
  "description": "Se ele começa a passar mais tempo deitado ao sol, é um sinal de que  vai florescer uma grande flor em breve.",
  "attack": 30,
  "defense": 30,
  "height": 100
}
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff5"),
  "name": "Venusaur",
  "description": "Há uma grande flor na parte traseira. A flor é dito para ter  cores vivas. O aroma da flor acalma as emoções das pessoas.",
  "attack": 40,
  "defense": 40,
  "height": 200
}
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff6"),
  "name": "Charmander",
  "description": "A chama que arde na ponta da cauda é uma indicação das suas emoções. Se o Pokémon fica furioso, a chama queima ferozmente.",
  "attack": 30,
  "defense": 20,
  "height": 60
}
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff7"),
  "name": "Charizard",
  "description": "voa em torno do céu em busca de adversários poderosos.",
  "attack": 40,
  "defense": 30,
  "height": 170
}
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff8"),
  "name": "Caterpie",
  "description": " tem um apetite voraz. Ele pode devorar as folhas maiores do que o seu corpo. Este Pokémon libera um odor terrivelmente forte.",
  "attack": 20,
  "defense": 20,
  "height": 30
}
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff9"),
  "name": "Beedrill",
  "description": "Extremamente territorial. Ninguém deve aproximar seu ninho para sua própria segurança.",
  "attack": 50,
  "defense": 20,
  "height": 100
}
{
  "_id": ObjectId("57f30ce7cefe345b07a0bffa"),
  "name": "Pikachu",
  "description": "Sempre que se depara com algo novo, ele dispara  um choque de elétrico",
  "attack": 30,
  "defense": 20,
  "height": 40
}
Fetched 8 record(s) in 5ms

```

## Busquar um pokemon e armazenar em uma variavel poke;

```
var query = {name:'Caterpie'}
var poke = db.pokemons.find(query)
poke
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff8"),
  "name": "Caterpie",
  "description": " tem um apetite voraz. Ele pode devorar as folhas maiores do que o seu corpo. Este Pokémon libera um odor terrivelmente forte.",
  "attack": 20,
  "defense": 20,
  "height": 30
}
Fetched 1 record(s) in 1ms
```
## Modificar sua 'description' e salvar.

```
var query = {name:'Caterpie'}
var poke = db.pokemons.findOne(query)
poke.description = 'Apetite voraz e odor forte.'
Apetite voraz e odor forte.
avell-linux(mongod-3.2.10) be-mean-pokemons> poke
{
  "_id": ObjectId("57f30ce7cefe345b07a0bff8"),
  "name": "Caterpie",
  "description": "Apetite voraz e odor forte.",
  "attack": 20,
  "defense": 20,
  "height": 30
}
db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})


```
