# MongoDB - Aula 02 - Exercício

autor: Carlos Machel

## Criação da database (passo 1)

```
elementaryos(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem das databases (passo 2)

```
elementaryos(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
```


## Listagem das coleções (passo 3)

```
elementaryos(mongod-3.0.7) be-mean-pokemons> show collections
elementaryos(mongod-3.0.7) be-mean-pokemons>
```

## Cadastro dos pokemons (passo 4)

```
var pokemons = [{'name': 'Golbat', 'description': 'Morceguinho que adora sugar sangue.', 'type': 'Poison', 'attack': 40, 'defense': 30, 'height': 1.6},
                {'name': 'Zubat', 'description': 'Morceguinho que se queima no sol.', 'type':'Poison', 'attack': 20, 'defense': 20, 'height': 0.8},
                {'name': 'Psyduck', 'description': 'Pato muito doido que usa um poder misterioso', 'type':'Eletric', 'attack': 30, 'defense': 20, 'height': 0.8},
                {'name': 'Mankey', 'description': 'Macaquinho que quando fica nervoso sai da reta.', 'type': 'Fighting', 'attack': 40, 'defense': 20, 'height': 0.5},
                {'name': 'Cubone', 'description': 'Chora pela mãe que nunca mais vai ver =( ', 'type': 'Ground', 'attack': 30, 'defense': 40, 'height': 0.4},
                {'name': 'Heracross', 'description': 'Besouro sinistro de forte', 'type': 'Bug', 'attack': 60, 'defense': 30, 'height': 1.5}];

elementaryos(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 320ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

## Lista dos pokemons (passo 5)

```
elementaryos(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("56514009b130c501af4eafa7"),
  "name": "Golbat",
  "description": "Morceguinho que adora sugar sangue.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 1.6
}
{
  "_id": ObjectId("56514009b130c501af4eafa8"),
  "name": "Zubat",
  "description": "Morceguinho que se queima no sol.",
  "type": "Poison",
  "attack": 20,
  "defense": 20,
  "height": 0.8
}
{
  "_id": ObjectId("56514009b130c501af4eafa9"),
  "name": "Psyduck",
  "description": "Pato muito doido que usa um poder misterioso",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.8
}
{
  "_id": ObjectId("56514009b130c501af4eafaa"),
  "name": "Mankey",
  "description": "Macaquinho que quando fica nervoso sai da reta.",
  "type": "Fighting",
  "attack": 40,
  "defense": 20,
  "height": 0.5
}
{
  "_id": ObjectId("56514009b130c501af4eafab"),
  "name": "Cubone",
  "description": "Chora pela mãe que nunca mais vai ver =( ",
  "type": "Ground",
  "attack": 30,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56514009b130c501af4eafac"),
  "name": "Heracross",
  "description": "Besouro sinistro de forte",
  "type": "Bug",
  "attack": 60,
  "defense": 30,
  "height": 1.5
}
Fetched 6 record(s) in 1ms
```

## Pikachu (passo 6)

```
elementaryos(mongod-3.0.7) be-mean-pokemons> var query = {'name': 'Heracross'}
elementaryos(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
elementaryos(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("56514009b130c501af4eafac"),
  "name": "Heracross",
  "description": "Besouro sinistro de forte",
  "type": "Bug",
  "attack": 60,
  "defense": 30,
  "height": 1.5
}
```

## Atualização do Pikachu (passo 6)

```
elementaryos(mongod-3.0.7) be-mean-pokemons> poke.description = 'Besouro sinistro de forte. Derruba até uma árvore.'
Besouro sinistro de forte. Derruba até uma árvore.
elementaryos(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

elementaryos(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{{
  "_id": ObjectId("56514009b130c501af4eafac"),
  "name": "Heracross",
  "description": "Besouro sinistro de forte. Derruba até uma árvore.",
  "type": "Bug",
  "attack": 60,
  "defense": 30,
  "height": 1.5
}
Fetched 1 record(s) in 1ms
```
