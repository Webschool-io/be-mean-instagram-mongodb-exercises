# MongoDB - Aula 03 - Exercício
autor: Edno Fedulo

## Liste todos Pokemons com a altura **menor que** 0.5;
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {height : {$lt: .5}}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56436b31e560d128cc56ee65"),
  "name": "Diglett",
  "attack": 55,
  "defense": 25,
  "height": 0.2,
  "description": "Diglett are raised in most farms. The reason is simple— wherever this Pokémon burrows, the soil is left perfectly tilled for planting crops. This soil is made ideal for growing delicious vegetables."
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56436b31e560d128cc56ee66"),
  "name": "Machop",
  "attack": 80,
  "defense": 50,
  "height": 0.8,
  "description": "Machop's muscles are special—they never get sore no matter how much they are used in exercise. This Pokémon has sufficient power to hurl a hundred adult humans."
}
{
  "_id": ObjectId("56436b31e560d128cc56ee67"),
  "name": "Butterfree",
  "attack": 45,
  "defense": 50,
  "height": 1.1,
  "description": "Butterfree has a superior ability to search for delicious honey from flowers. It can even search out, extract, and carry honey from flowers that are blooming over six miles from its nest."
}
{
  "_id": ObjectId("56436b31e560d128cc56ee68"),
  "name": "Nidoran",
  "attack": 57,
  "defense": 40,
  "height": 0.5,
  "description": "alterando descricao"
}
{
  "_id": ObjectId("56436b31e560d128cc56ee69"),
  "name": "Bellsprout",
  "attack": 75,
  "defense": 35,
  "height": 0.7,
  "description": "Bellsprout's thin and flexible body lets it bend and sway to avoid any attack, however strong it may be. "
}
{
  "_id": ObjectId("56436b31e560d128cc56ee6a"),
  "name": "Kingler",
  "attack": 130,
  "defense": 115,
  "height": 1.3,
  "description": "Kingler has an enormous, oversized claw. It waves this huge claw in the air to communicate with others. However, because the claw is so heavy, the Pokémon quickly tires.",
  "descriptio": "descricao alterada"
}
Fetched 5 record(s) in 1ms
```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}},{type: 'grass'}]}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'},{attack: {$lte: 0.5}}]}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> query
{
  "$or": [
    {
      "name": "Pikachu"
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}
ubuntu-VirtualBox(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56436b31e560d128cc56ee65"),
  "name": "Diglett",
  "attack": 55,
  "defense": 25,
  "height": 0.2,
  "description": "Diglett are raised in most farms. The reason is simple— wherever this Pokémon burrows, the soil is left perfectly tilled for planting crops. This soil is made ideal for growing delicious vegetables."
}
{
  "_id": ObjectId("56436b31e560d128cc56ee68"),
  "name": "Nidoran",
  "attack": 57,
  "defense": 40,
  "height": 0.5,
  "description": "alterando descricao"
}
Fetched 2 record(s) in 2ms
```
