# MongoDb - Aula 02 - Exercício
Autor: Paulo Roberto da Silva

## Criar database chamada be-mean-pokemons

```
paulo(mongod-3.2.1) be-mean-teste> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listagem de todas dbs

```
paulo(mongod-3.2.1) be-mean-pokemons> show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
be-mean-teste     → 0.000GB
local             → 0.000GB
```

## Listagem de todas as collections

```
paulo(mongod-3.2.1) be-mean-teste> show collections
```

## Criar cinco pokemons

```js
var pokemons = [
{'name': 'Butterfree', 'description': 'Its wings, covered with poisonous powders, repel water.', 'type': 'inseto', 'attack': 45, 'defense': 50, 'height': 11},
{'name': 'Arbok', 'description': 'The frightening patterns on its belly have been studied. Six variations have been confirmed.', 'type': 'veneno', 'attack': 85, 'defense': 69, 'height': 35},
{'name': 'Ninetales', 'description': 'Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.', 'type': 'fogo', 'attack': 76, 'defense': 75, 'height': 11},
{'name': 'Grimer', 'description': 'Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.', 'type': 'veneno', 'attack': 80, 'defense': 50, 'height': 9},
{'name': 'Nidorina', 'description': 'When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.', 'type': 'veneno', attack: 62, 'defense': 67, 'height': 8}
];
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 220ms
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

## Listar todos os pokemons

```js
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find()
{
"_id": ObjectId("56b784d94a6ae70439c45bca"),
"name": "Butterfree",
"description": "Its wings, covered with poisonous powders, repel water.",
"type": "inseto",
"attack": 45,
"defense": 50,
"height": 11
}
{
"_id": ObjectId("56b784d94a6ae70439c45bcb"),
"name": "Arbok",
"description": "The frightening patterns on its belly have been studied. Six variations have been confirmed.",
"type": "veneno",
"attack": 85,
"defense": 69,
"height": 35
}
{
"_id": ObjectId("56b784d94a6ae70439c45bcc"),
"name": "Ninetales",
"description": "Its nine tails are said to be imbued with a mystic power. It can live for a thousand years.",
"type": "fogo",
"attack": 76,

"defense": 75,
"height": 11
}
{
"_id": ObjectId("56b784d94a6ae70439c45bcd"),
"name": "Grimer",
"description": "Appears in filthy areas. Thrives by sucking up polluted sludge that is pumped out of factories.",
"type": "veneno",
"attack": 80,
"defense": 50,
"height": 9
}
{
"_id": ObjectId("56b784d94a6ae70439c45bce"),
"name": "Nidorina",
"description": "When NIDORINA are with their friends or family, they keep their barbs tucked away to prevent hurting each other.",
"type": "veneno",
"attack": 62,

"defense": 67,
"height": 8
}
```

## Buscar um pokemon

```js
paulo(mongod-3.2.1) be-mean-pokemons> var query = ({'name': 'Grimer'})
paulo(mongod-3.2.1) be-mean-pokemons> var poke = db.pokemons.findOne(query)
paulo(mongod-3.2.1) be-mean-pokemons>poke
{

"_id": ObjectId("56b784d94a6ae70439c45bcd"),
"name": "Grimer",
"description": "descricao alterada",
"type": "veneno",
"attack": 80,
"defense": 50,
"height": 9
}
Fetched 1 record(s) in 2ms
```

## Editar a description do pokemon escolhido

```js
paulo(mongod-3.2.1) be-mean-pokemons> poke.description = 'descricao alterada'
descricao alterada
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
"nMatched": 1,
"nUpserted": 0,
"nModified": 0
})
