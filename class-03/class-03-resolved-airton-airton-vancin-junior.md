# MongoDB - Aula 03 - Exercício
autor: Airton Vancin Junior


## Liste todos Pokemons com a altura **menor que** 0.5;

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {"height": {$lt: 0.5}}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fd05cba869323ecad2a6"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("5643fd57cba869323ecad2a7"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
Fetched 2 record(s) in 2ms

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {"height": {$gte: 0.5}}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fbcdcba869323ecad2a4"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
{
  "_id": ObjectId("5643fc5bcba869323ecad2a5"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("5643fdaccba869323ecad2a8"),
  "name": "Blastoise",
  "description": "Blastoise tem bicas de água que se projetam de sua concha. Os bicos de água são muito precisos. Eles podem disparar balas de água com precisão suficiente para atacar latas vazias de uma distância de mais de 160 pés.",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
Fetched 3 record(s) in 4ms

```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {$and: [{"height":{$lte: 0.5} }, {"type": "Grama"} ]}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
linux(mongod-2.6.10) be-mean-pokemons> var query = {$and: [{"height":{$lte: 0.5} },{"type": "Normal"} ]}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fd05cba869323ecad2a6"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {$or: [{"name": "Pikachu"}, {"attack": {$lte:0.5} }]}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
linux(mongod-2.6.10) be-mean-pokemons> var query = {$or: [{"name": "Pikachu"}, {"attack": {$lte:65} }]}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5643fbcdcba869323ecad2a4"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
{
  "_id": ObjectId("5643fc5bcba869323ecad2a5"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("5643fd05cba869323ecad2a6"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("5643fd57cba869323ecad2a7"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
Fetched 4 record(s) in 2ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
linux(mongod-2.6.10) be-mean-pokemons> var query = {$and: [{"attack":{$gte: 48} },{"height": {$lte: 0.5} } ]}
linux(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```