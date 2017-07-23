# MongoDb - Aula 03 - Exercício
Autor: Paulo Roberto da Silva

## Listagem pokemons height < 0.5
```js
paulo(mongod-3.2.1) be-mean-pokemons> var query = {height : {$lt:0.5}}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 1ms
```


## Listagem pokemons height >= 0.5
```js
paulo(mongod-3.2.1) be-mean-pokemons> var query = {height : {$gte:0.5}}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query);
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
"description": "descricao alterada",
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
Fetched 5 record(s) in 5ms
```
## Listagem pokemons height <= 0.5 e type "grama"
```js
paulo(mongod-3.2.1) be-mean-pokemons> var query = {$and: [{height:{$lte:0.5}},{type:'grama'}]}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listagem pokemons name "Pikachu" ou attack <= 0.5
```
paulo(mongod-3.2.1) be-mean-pokemons> var query = {$or : [{name:'Pikachu'}, {attack: {$lte: 0.5}}]}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Listagem pokemons attack >= 48 e height <= 0.5
```js
paulo(mongod-3.2.1) be-mean-pokemons> var query = {$or : [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
paulo(mongod-3.2.1) be-mean-pokemons> db.pokemons.find(query)
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
"description": "descricao alterada",
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
Fetched 4 record(s) in 4ms
```
