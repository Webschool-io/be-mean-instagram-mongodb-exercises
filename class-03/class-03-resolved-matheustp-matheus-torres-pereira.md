# MongoDB - Aula 03 - Exercício
autor: Matheus Torres Pereira

## 1. Liste todos os Pokemons com a altura menor que 0.5

```
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find({height: {$lt:0.5}})
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68c"),
  "name": "Pidgey",
  "description": "Pokemon pomba",
  "attack": 45,
  "defense": 40,
  "height": 0.3
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68d"),
  "name": "Pikachu",
  "description": "Pokemon rato amarelo que solta raio pela bochecha",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
Fetched 2 record(s) in 2ms
```

## 2. Liste todos os Pokemons com a altura maior ou igual que 0.5

```
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find({height: {$gte:0.5}})
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a689"),
  "name": "Bulbasaur",
  "description": "Pokemon com uma planta nas costas",
  "attack": 49,
  "defense": 49,
  "height": 0.71
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68a"),
  "name": "Charmander",
  "description": "Pokemon com fogo no rabo",
  "attack": 52,
  "defense": 43,
  "height": 0.61
}
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68b"),
  "name": "Squirtle",
  "description": "Tartaruga cuspidora de água",
  "attack": 48,
  "defense": 65,
  "height": 0.51
}
Fetched 3 record(s) in 3ms
```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 e do tipo grama
Obs:Antes de realizar esta etapa eu atualizei todos os pokemons, pois eles não possuiam o atributo 'type'

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}},{type:'grama'}]}

ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms

```

## 4. Liste todos Pokemons com o name 'Pikachu' ou com attack menor ou igual que 0.5

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}},{name:'Pikachu'}]}
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68d"),
  "name": "Pikachu",
  "description": "Pokemon rato amarelo que solta raio pela bochecha",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "type": "raio"
}
Fetched 1 record(s) in 2ms
```

## 5. Liste todos Pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5

```
ubuntu(mongod-3.2.12) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}},{height: {$lte:0.5}}]}
ubuntu(mongod-3.2.12) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("58af1bee57d2d3ebfdb8a68d"),
  "name": "Pikachu",
  "description": "Pokemon rato amarelo que solta raio pela bochecha",
  "attack": 55,
  "defense": 40,
  "height": 0.41,
  "type": "raio"
}
Fetched 1 record(s) in 2ms
```

