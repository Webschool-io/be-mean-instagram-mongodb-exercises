# MongoDB - Aula 02 - Exercício
autor: Leonardo Gonçalves de Souza

## Crie uma database chamada be-mean-pokemons
```
(mongod-3.2.8) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Liste quais databases você possui nesse servidor
```
(mongod-3.2.8) be-mean-pokemons> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
be-mean-teste     → 0.078GB
local             → 0.078GB
```

## Liste quais coleções você possui nessa database
```
(mongod-3.2.8) be-mean-pokemons> show collections
```

## Cadastro de pokemons
```
(mongod-3.2.8) be-mean-pokemons> var pokemons = [
... {
... name: 'Sandshrew',
... description: 'Parece um tatu',
... attack: 75,
... defense: 85,
... height: 6
... },
... {
... name: 'Nidorino',
... description: 'Tá com cara de bravo',
... attack: 72,
... defense: 57,
... height: 9
... },
... {
... name: 'Charizard',
... description: 'Meu dragão favorito',
... attack: 84,
... defense: 78,
... height: 17
... },
... {
... name: 'Pidgeot',
... description: 'Passarinho legalzinho',
... attack: 56,
... defense: 35,
... height: 3
... },
... {
... name: 'Clefairy',
... description: 'Que fofura',
... attack: 45,
... defense: 48,
... height: 6
... },
... {
... name: 'Zubat',
... description: 'O mais odiado em Pokemon Go',
... attack: 45,
... defense: 35,
... height: 8
... },
... {
... name: 'Psyduck',
... description: 'Pato Maluco',
... attack: 52,
... defense: 48,
... height: 8
... }
... ];

(mongod-3.2.8) be-mean-pokemons> db.pokemons.insert(pokemons)

Inserted 1 record(s) in 922ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 7,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Liste os pokemons existentes na sua coleção
```
(mongod-3.2.8) be-mean-pokemons> db.pokemons.find({})
{
  "_id": ObjectId("57bf1c92f2738e9bac257114"),
  "name": "Sandshrew",
  "description": "Parece um tatu",
  "attack": 75,
  "defense": 85,
  "height": 6
}
{
  "_id": ObjectId("57bf1c92f2738e9bac257115"),
  "name": "Nidorino",
  "description": "Tá com cara de bravo",
  "attack": 72,
  "defense": 57,
  "height": 9
}
{
  "_id": ObjectId("57bf1c92f2738e9bac257116"),
  "name": "Charizard",
  "description": "Meu dragão favorito",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("57bf1c92f2738e9bac257117"),
  "name": "Pidgeot",
  "description": "Passarinho legalzinho",
  "attack": 56,
  "defense": 35,
  "height": 3
}
{
  "_id": ObjectId("57bf1c92f2738e9bac257118"),
  "name": "Clefairy",
  "description": "Que fofura",
  "attack": 45,
  "defense": 48,
  "height": 6
}
{
  "_id": ObjectId("57bf1c92f2738e9bac257119"),
  "name": "Zubat",
  "description": "O mais odiado em Pokemon Go",
  "attack": 45,
  "defense": 35,
  "height": 8
}
{
  "_id": ObjectId("57bf1c92f2738e9bac25711a"),
  "name": "Psyduck",
  "description": "Pato Maluco",
  "attack": 52,
  "defense": 48,
  "height": 8
}
Fetched 7 record(s) in 69ms
```

## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada 'poke'
```
(mongod-3.2.8) be-mean-pokemons> var query = {name: 'Nidorino'}

(mongod-3.2.8) be-mean-pokemons> query
{
  "name": "Nidorino"
}

(mongod-3.2.8) be-mean-pokemons> var poke = db.pokemons.findOne(query)

(mongod-3.2.8) be-mean-pokemons> poke
{
  "_id": ObjectId("57bf1c92f2738e9bac257115"),
  "name": "Nidorino",
  "description": "Tá com cara de bravo",
  "attack": 72,
  "defense": 57,
  "height": 9
}
```

## Modifique sua 'description' e salve-o
```
(mongod-3.2.8) be-mean-pokemons> poke.description = 'Cara de bravo mas é fofinho'
Cara de bravo mas é fofinho

(mongod-3.2.8) be-mean-pokemons> poke
{
  "_id": ObjectId("57bf1c92f2738e9bac257115"),
  "name": "Nidorino",
  "description": "Cara de bravo mas é fofinho",
  "attack": 72,
  "defense": 57,
  "height": 9
}

(mongod-3.2.8) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 25ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

(mongod-3.2.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57bf1c92f2738e9bac257115"),
  "name": "Nidorino",
  "description": "Cara de bravo mas é fofinho",
  "attack": 72,
  "defense": 57,
  "height": 9
}
Fetched 1 record(s) in 2ms
```
