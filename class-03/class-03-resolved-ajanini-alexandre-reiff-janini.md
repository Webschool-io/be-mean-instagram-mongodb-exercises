# MongoDB - Aula 03 - Exercício
autor: Alexandre Reiff Janini

## 1. Liste todos Pokemons com a altura menor que 0.5;

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = { height: { $lt: 0.5 } }
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8df"),
  "name": "Pumpkaboo",
  "description": "The pumpkin body is inhabited by a spirit trapped in this world. As the sun sets, it becomes restless and active.",
  "type": "grass",
  "attack": 66,
  "defense": 70,
  "height": 0.4
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e1"),
  "name": "Zigzagoon",
  "description": "Zigzagoon restlessly wanders everywhere at all times. This Pokémon does so because it is very curious. It becomes interested in anything that it happens to see.",
  "type": "normal",
  "attack": 30,
  "defense": 41,
  "height": 0.4
}
Fetched 3 record(s) in 3ms
```

## 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = { height: { $gte: 0.5 } }
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8d9"),
  "name": "Zekrom",
  "description": "This legendary Pokémon can scorch the world with lightning. It assists those who want to build an ideal world.",
  "type": "electric",
  "attack": 150,
  "defense": 120,
  "height": 2.9
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8da"),
  "name": "Shuckle",
  "description": "Shuckle quietly hides itself under rocks, keeping its body concealed inside its hard shell while eating berries it has stored away. The berries mix with its body fluids to become a juice.",
  "type": "bug",
  "attack": 10,
  "defense": 230,
  "height": 0.6
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8db"),
  "name": "Dewott",
  "description": "Strict training is how it learns its flowing double-scalchop technique.",
  "type": "water",
  "attack": 75,
  "defense": 60,
  "height": 0.8
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dd"),
  "name": "Serperior",
  "description": "It only gives its all against strong opponents who are not fazed by the glare from Serperior's noble eyes.",
  "type": "grass",
  "attack": 75,
  "defense": 95,
  "height": 3.3
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8de"),
  "name": "Jolteon",
  "description": "Jolteon's cells generate a low level of electricity. This power is amplified by the static electricity of its fur, enabling the Pokémon to drop thunderbolts. The bristling fur is made of electrically charged needles.",
  "type": "electric",
  "attack": 65,
  "defense": 60,
  "height": 0.8
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e0"),
  "name": "Claydol",
  "description": "Claydol are said to be dolls of mud made by primitive humans and brought to life by exposure to a mysterious ray. This Pokémon moves about while levitating.",
  "type": "psychic",
  "attack": 70,
  "defense": 105,
  "height": 15
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e2"),
  "name": "Herdier",
  "description": "This very loyal Pokémon helps Trainers, and it also takes care of other Pokémon.",
  "type": "normal",
  "attack": 80,
  "defense": 65,
  "height": 0.9
}
Fetched 7 record(s) in 4ms
```

## 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ {height: { $lte: 0.5 }}, { type: 'grass' } ] }
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8df"),
  "name": "Pumpkaboo",
  "description": "The pumpkin body is inhabited by a spirit trapped in this world. As the sun sets, it becomes restless and active.",
  "type": "grass",
  "attack": 66,
  "defense": 70,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = { $or: [ { name: "Pikachu"}, { attack: { $lte: 0.5 } } ] }
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

Não há qualquer pokemon com attack menor ou igual a 0.5. O menor valor é 10.

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { attack: { $gte: 48 } }, { height: { $lte: 0.5 } } ] }
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8df"),
  "name": "Pumpkaboo",
  "description": "The pumpkin body is inhabited by a spirit trapped in this world. As the sun sets, it becomes restless and active.",
  "type": "grass",
  "attack": 66,
  "defense": 70,
  "height": 0.4
}
Fetched 2 record(s) in 1ms
```
