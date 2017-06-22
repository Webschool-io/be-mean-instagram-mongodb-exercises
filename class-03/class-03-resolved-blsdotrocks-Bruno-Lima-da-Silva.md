# MongoDB - Aula 03 - Exercício

autor: Bruno Lima da Silva

## 1. Crie uma database chamada be-mean-pokemons;
```js
use be-mean-pokemons
```
## 2. Liste quais databases você possui nesse servidor;

```js
blsrocks(mongod-3.2.8) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
be-mean-test      → 0.000GB
local             → 0.000GB
```
## 3. Liste quais coleções você possui nessa database;

```js
blsrocks(mongod-3.2.8) be-mean-pokemons> show collections
pokemons → 0.001MB / 0.016MB

```
## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.insert(pokemon)
```
## 5. Liste os pokemons existentes na sua coleção;
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57af6f3292ac5d57da5217bb"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("57af6f4192ac5d57da5217bc"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("57af6f5092ac5d57da5217bd"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("57af6f6292ac5d57da5217be"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("57af6f7692ac5d57da5217bf"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}

```
## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> var query = {name: 'Squirtle'}
blsrocks(mongod-3.2.8) be-mean-pokemons> var poke = db.pokemons.findOne(query)
blsrocks(mongod-3.2.8) be-mean-pokemons> poke
{
  "_id": ObjectId("57af6f6292ac5d57da5217be"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}

```
## 7. Modifique sua `description` e salvê-o
```js
blsrocks(mongod-3.2.8) be-mean-pokemons> poke.description = 'Ejeta água zikada'
Ejeta água zikada
blsrocks(mongod-3.2.8) be-mean-pokemons> poke
{
  "_id": ObjectId("57af6f6292ac5d57da5217be"),
  "name": "Squirtle",
  "description": "Ejeta água zikada",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
blsrocks(mongod-3.2.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```