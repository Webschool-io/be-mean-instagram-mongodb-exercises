# MongoDB - Aula 02 - Exercício
autor: Felipe Sousa

## Crie uma database chamada be-mean-pokemons;

```
felipesousa(mongod-2.6.11) test> use be-mean-pokemons
switched to db be-mean-pokemons
felipesousa(mongod-2.6.11) be-mean-pokemons>
```


## 2. Liste quais databases você possui nesse servidor;

```
felipesousa(mongod-2.6.11) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
local             → 0.078GB
admin             → (empty)
```


## 3. Liste quais coleções você possui nessa database;

Obs.: Criando a coleção antes pra ficar mais show.

```
felipesousa(mongod-2.6.11) be-mean-pokemons> db.createCollection('pokemons')
{
  "ok": 1
}
felipesousa(mongod-2.6.11) be-mean-pokemons> show collections
pokemons       → 0.000MB / 0.008MB
system.indexes → 0.000MB / 0.008MB

```


## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA


```
{
var pokemons = { name:'Pikachu', description:"Rato elétrico bem fofinho", type: 'eletric', atack:55, height:0.4 }

var pokemons = { name:'Squirtle', description:'Ejeta água que passarinho não bebe', type: 'agua', atack:48, height:0.5}

var pokemons = { name:'Bulbassauro', description:'Chicote de trepadeira', type: 'grama', atack:49, height:0.4 }

var pokemons = { name:'Charmander', description:'Esse é o cão chupando manga de fofinho', type: 'fogo', atack:52, height:0.6 }

var pokemons = { name:'Nidorino', description:'Bem resistente!', type: 'poison-pin', atack:40, height:0.9 }
}
felipesousa(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemons);
Inserted 1 record(s) in 5ms
WriteResult({
  "nInserted": 1
})
```


## 5. Liste os pokemons existentes na sua coleção;
```
felipesousa(mongod-2.6.11) be-mean-pokemons> db.pokemons.find({})
{
  "_id": ObjectId("564d014f4321085bf20fd55c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("564d03f9b033d44a966ad181"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564d03f9b033d44a966ad182"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564d03f9b033d44a966ad183"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564d03f9b033d44a966ad184"),
  "name": "Nidorino",
  "description": "Bem resistente!",
  "type": "poison-pin",
  "attack": 40,
  "height": 0.9
}

Fetched 5 record(s) in 5ms
```


## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;
```
felipesousa(mongod-2.6.11) be-mean-pokemons> var query = {'name': 'Charmander'}

felipesousa(mongod-2.6.11) be-mean-pokemons> var poke = db.pokemons.findOne(query)
felipesousa(mongod-2.6.11) be-mean-pokemons> poke
{
  "_id": ObjectId("564d03f9b033d44a966ad183"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}

```


## 7. Modifique sua `description` e salvê-o

```
felipesousa(mongod-2.6.11) be-mean-instagram> poke.description = 'faz espiral e descança.'
faz espiral e descança.
felipesousa(mongod-2.6.11) be-mean-instagram> poke
{
  "_id": ObjectId("564d03f9b033d44a966ad183"),
  "name": "Charmander",
  "description": "faz espiral e descança.",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}

felipesousa(mongod-2.6.11 be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
