# MongoDB - Aula 02 - Exercício
autor: Alexandre Reiff Janini

## 1. Criar database chamada be-mean-pokemons

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons
```

## 2. Listar databases no servidor

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
```

## 3. Listar coleções da database selecionada

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> show collections
```

Não há coleções na database be-mean-pokemons, ainda.

## 4. Inserir pokemons

Inserindo 10 pokemons **quase** aleatórios. Dados obtidos de http://www.pokemon.com/br/pokedex/ e http://pokeapi.co/

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var pokemons = [ { 'name': 'Zekrom', 'description': 'This legendary Pokémon can scorch the world with lightning. It assists those who want to build an ideal world.', 'type': 'electric', 'attack': 150, 'defense': 120, 'height': 2.9, }, { 'name': 'Shuckle', 'description': 'Shuckle quietly hides itself under rocks, keeping its body concealed inside its hard shell while eating berries it has stored away. The berries mix with its body fluids to become a juice.', 'type': 'bug', 'attack': 10, 'defense': 230, 'height': 0.6, }, { 'name': 'Dewott', 'description': 'Strict training is how it learns its flowing double-scalchop technique.', 'type': 'water', 'attack': 75, 'defense': 60, 'height': 0.8, }, { 'name': 'Pikachu', 'description': 'Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it\'s evidence that this Pokémon mistook the intensity of its charge.', 'type': 'electric', 'attack': 55, 'defense': 40, 'height': 0.4, }, { 'name': 'Serperior', 'description': 'It only gives its all against strong opponents who are not fazed by the glare from Serperior\'s noble eyes.', 'type': 'grass', 'attack': 75, 'defense': 95, 'height': 3.3, }, { 'name': 'Jolteon', 'description': 'Jolteon\'s cells generate a low level of electricity. This power is amplified by the static electricity of its fur, enabling the Pokémon to drop thunderbolts. The bristling fur is made of electrically charged needles.', 'type': 'electric', 'attack': 65, 'defense': 60, 'height': 0.8, }, { 'name': 'Pumpkaboo', 'description': 'The pumpkin body is inhabited by a spirit trapped in this world. As the sun sets, it becomes restless and active.', 'type': 'grass', 'attack': 66, 'defense': 70, 'height': 0.4, }, { 'name': 'Claydol', 'description': 'Claydol are said to be dolls of mud made by primitive humans and brought to life by exposure to a mysterious ray. This Pokémon moves about while levitating.', 'type': 'psychic', 'attack': 70, 'defense': 105, 'height': 15, }, { 'name': 'Zigzagoon', 'description': 'Zigzagoon restlessly wanders everywhere at all times. This Pokémon does so because it is very curious. It becomes interested in anything that it happens to see.', 'type': 'normal', 'attack': 30, 'defense': 41, 'height': 0.4, }, { 'name': 'Herdier', 'description': 'This very loyal Pokémon helps Trainers, and it also takes care of other Pokémon.', 'type': 'normal', 'attack': 80, 'defense': 65, 'height': 0.9, }, ]
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 238ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 10,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

Como esperado, foram inseridos 10 pokemons.

## 5. Listar os pokemons existentes na coleção

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({})
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
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
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
  "_id": ObjectId("5649c4a775dda0a3d275f8df"),
  "name": "Pumpkaboo",
  "description": "The pumpkin body is inhabited by a spirit trapped in this world. As the sun sets, it becomes restless and active.",
  "type": "grass",
  "attack": 66,
  "defense": 70,
  "height": 0.4
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
  "_id": ObjectId("5649c4a775dda0a3d275f8e1"),
  "name": "Zigzagoon",
  "description": "Zigzagoon restlessly wanders everywhere at all times. This Pokémon does so because it is very curious. It becomes interested in anything that it happens to see.",
  "type": "normal",
  "attack": 30,
  "defense": 41,
  "height": 0.4
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
Fetched 10 record(s) in 6ms
```

## 6. Buscar um pokemon pelo nome e armazena-lo na variável poke

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne({name: "Pikachu"})
```

Confirmando que foi encontrado:
```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
```

## 7. Modificar sua descrição e salvar

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> poke.description += " It is the world's most famouse and cute pokemon."
Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.
```

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

Confirmando que foi salvo:
```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne({name: "Pikachu"})
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4
}
```