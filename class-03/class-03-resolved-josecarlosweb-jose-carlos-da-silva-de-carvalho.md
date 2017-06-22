# MongoDB - Aula 03 - Exercício
autor: José Carlos

## Listando todos os pokemons com altura menor que 0.5

```
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({height: {$lt: 0.5}})
{
  "_id": ObjectId("565fb522096fb0ddd2aaac9c"),
  "name": "Sandshrew",
  "description": "Rato grande azul e com orelhas gigantes",
  "attack": 30,
  "defence": 20,
  "height": 0.4
}
{
  "_id": ObjectId("565fb630096fb0ddd2aaac9e"),
  "name": "Exeggcute",
  "description": "Esse é muito estranho, parece um monte de ovos",
  "attack": 20,
  "defence": 40,
  "height": 0.4
}
{
  "_id": ObjectId("565fb664096fb0ddd2aaac9f"),
  "name": "Cubone",
  "description": "Bixinho de pelúcia com uma caveira na cabeça",
  "attack": 30,
  "defence": 40,
  "height": 0.4
}
Fetched 3 record(s) in 1ms```

## Listando todos os pokemons com altura maior ou igual que 0.5

```
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({height: {$gte: 0.5}})
{
  "_id": ObjectId("565fb437096fb0ddd2aaac99"),
  "name": "Hitmonlee",
  "description": "Lutador com chute potente",
  "attack": 120,
  "defence": 80,
  "height": 1.5
}
{
  "_id": ObjectId("565fb497096fb0ddd2aaac9a"),
  "name": "Raichu",
  "description": "Rato gigante, a evolução do pickachu",
  "attack": 90,
  "defence": 50,
  "height": 0.8
}
{
  "_id": ObjectId("565fb4d8096fb0ddd2aaac9b"),
  "name": "Magna",
  "description": "Uma nova descrição para o pokemon",
  "attack": 60,
  "defence": 80,
  "height": 0.6
}
{
  "_id": ObjectId("565fb585096fb0ddd2aaac9d"),
  "name": "Voltorb",
  "description": "Se parece com uma pokebola e pode explodir",
  "attack": 20,
  "defence": 20,
  "height": 0.5
}
Fetched 4 record(s) in 5ms

```

## Listando todos os pokemons com altura menor ou igual que 0.5

```

carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({height: {$lte: 0.5}})
{
  "_id": ObjectId("565fb522096fb0ddd2aaac9c"),
  "name": "Sandshrew",
  "description": "Rato grande azul e com orelhas gigantes",
  "attack": 30,
  "defence": 20,
  "height": 0.4
}
{
  "_id": ObjectId("565fb585096fb0ddd2aaac9d"),
  "name": "Voltorb",
  "description": "Se parece com uma pokebola e pode explodir",
  "attack": 20,
  "defence": 20,
  "height": 0.5
}
{
  "_id": ObjectId("565fb630096fb0ddd2aaac9e"),
  "name": "Exeggcute",
  "description": "Esse é muito estranho, parece um monte de ovos",
  "attack": 20,
  "defence": 40,
  "height": 0.4
}
{
  "_id": ObjectId("565fb664096fb0ddd2aaac9f"),
  "name": "Cubone",
  "description": "Bixinho de pelúcia com uma caveira na cabeça",
  "attack": 30,
  "defence": 40,
  "height": 0.4
}
Fetched 4 record(s) in 2ms

```

## Listando todos os pokemons com nome 'Pikachu' ou com attack menor ou igual que 0.5

```
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({$or: [{name: "Hitmonlee"}, {attack: {$lte: 0.5}}]})
{
  "_id": ObjectId("565fb437096fb0ddd2aaac99"),
  "name": "Hitmonlee",
  "description": "Lutador com chute potente",
  "attack": 120,
  "defence": 80,
  "height": 1.5
}
Fetched 1 record(s) in 25ms

```

## Listando todos os pokemons attack maior ou igual que 48 e com height menor ou igual que 0.5

```
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]})
Fetched 0 record(s) in 1ms
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({$and: [{attack: {$gte: 40}}, {height: {$lte: 0.5}}]})
Fetched 0 record(s) in 1ms
carlos-pc(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({$and: [{attack: {$gte: 40}}, {height: {$lte: 1.5}}]})
{
  "_id": ObjectId("565fb437096fb0ddd2aaac99"),
  "name": "Hitmonlee",
  "description": "Lutador com chute potente",
  "attack": 120,
  "defence": 80,
  "height": 1.5
}
{
  "_id": ObjectId("565fb497096fb0ddd2aaac9a"),
  "name": "Raichu",
  "description": "Rato gigante, a evolução do pickachu",
  "attack": 90,
  "defence": 50,
  "height": 0.8
}
{
  "_id": ObjectId("565fb4d8096fb0ddd2aaac9b"),
  "name": "Magna",
  "description": "Uma nova descrição para o pokemon",
  "attack": 60,
  "defence": 80,
  "height": 0.6
}
Fetched 3 record(s) in 2ms
```
