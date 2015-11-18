# MongoDB - Aula 04 - Exercício
autor: Alexandre Reiff Janini

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

### Definindo e testando a query

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbasaur/i}, {name: /charmander/i}]}
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
  "_id": ObjectId("564c6f3a5cdce9685ea95fe7"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe8"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6
}
Fetched 4 record(s) in 8ms
```

### Definindo objeto com ataques a serem adicionados

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['dash', 'punch']}}
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> mod
{
  "$pushAll": {
    "moves": [
      "dash",
      "punch"
    ]
  }
}
```

### Definindo opções

Porque vou atualizar vários registros de uma vez, é necessário definir a opção `multi` como `true`.

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var opts = { multi: true }
```

### Executando o update

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 4 existing record(s) in 5ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

### Resultado

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "dash",
    "punch"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe7"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "dash",
    "punch"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe8"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "dash",
    "punch"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "dash",
    "punch"
  ]
}
Fetched 4 record(s) in 5ms
```

## 2. **Adicionar** 1 movimento em todos os pokemons: desvio.

Como está tudo em inglês, vou usar "dodge" ao invés de "desvio".

### Define a query

Vazia, porque queremos todos os pokemons.

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = {}
```

### Define o objeto de modificação

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'dodge'}}
```

### Usamos o mesmo objeto de opções anterior, com `multi` igual a `true`

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> opts
{
  "multi": true
}
```

### Executa o update

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 13 existing record(s) in 1ms
WriteResult({
  "nMatched": 13,
  "nUpserted": 0,
  "nModified": 13
})
```

### Verifica o resultado

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8da"),
  "name": "Shuckle",
  "description": "Shuckle quietly hides itself under rocks, keeping its body concealed inside its hard shell while eating berries it has stored away. The berries mix with its body fluids to become a juice.",
  "type": "bug",
  "attack": 10,
  "defense": 230,
  "height": 0.6,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8db"),
  "name": "Dewott",
  "description": "Strict training is how it learns its flowing double-scalchop technique.",
  "type": "water",
  "attack": 75,
  "defense": 60,
  "height": 0.8,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8de"),
  "name": "Jolteon",
  "description": "Jolteon's cells generate a low level of electricity. This power is amplified by the static electricity of its fur, enabling the Pokémon to drop thunderbolts. The bristling fur is made of electrically charged needles.",
  "type": "electric",
  "attack": 65,
  "defense": 60,
  "height": 0.8,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e0"),
  "name": "Claydol",
  "description": "Claydol are said to be dolls of mud made by primitive humans and brought to life by exposure to a mysterious ray. This Pokémon moves about while levitating.",
  "type": "psychic",
  "attack": 70,
  "defense": 105,
  "height": 15,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e1"),
  "name": "Zigzagoon",
  "description": "Zigzagoon restlessly wanders everywhere at all times. This Pokémon does so because it is very curious. It becomes interested in anything that it happens to see.",
  "type": "normal",
  "attack": 30,
  "defense": 41,
  "height": 0.4,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e2"),
  "name": "Herdier",
  "description": "This very loyal Pokémon helps Trainers, and it also takes care of other Pokémon.",
  "type": "normal",
  "attack": 80,
  "defense": 65,
  "height": 0.9,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe7"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe8"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8d9"),
  "name": "Zekrom",
  "description": "This legendary Pokémon can scorch the world with lightning. It assists those who want to build an ideal world.",
  "type": "electric",
  "attack": 150,
  "defense": 120,
  "height": 2.9,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dd"),
  "name": "Serperior",
  "description": "It only gives its all against strong opponents who are not fazed by the glare from Serperior's noble eyes.",
  "type": "grass",
  "attack": 75,
  "defense": 95,
  "height": 3.3,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8df"),
  "name": "Pumpkaboo",
  "description": "The pumpkin body is inhabited by a spirit trapped in this world. As the sun sets, it becomes restless and active.",
  "type": "grass",
  "attack": 66,
  "defense": 70,
  "height": 0.4,
  "moves": [
    "dodge"
  ]
}
Fetched 13 record(s) in 6ms
```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

Vou usar a sintaxe de `update` com `upsert` e `setOnInsert` para praticar.

### Definindo a query

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = {name: 'AindaNaoExisteMon'}
```

### Objeto para o update

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var mod = { $set: {description: 'Sem maiores informações'}, $setOnInsert: { name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, moves: null, } }
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> mod
{
  "$set": {
    "description": "Sem maiores informações"
  },
  "$setOnInsert": {
    "name": "AindaNaoExisteMon",
    "type": null,
    "attack": null,
    "defense": null,
    "height": null,
    "moves": null
  }
}
```

### Opções com `upsert`

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var opts = {upsert: true}
```

### Executando o update/insert

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, opts)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564c76a36b22a6995f2b89d8")
})
```

### Verificando com a mesma query

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564c76a36b22a6995f2b89d8"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "moves": null
}
Fetched 1 record(s) in 1ms
```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

Novamente, vou usar "dash", mantendo o padrão em inglês.

### Monta a pesquisa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$all: ['dash', 'dodge']}}
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> query
{
  "moves": {
    "$all": [
      "dash",
      "dodge"
    ]
  }
}
```

### Executa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe7"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe8"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
Fetched 4 record(s) in 1ms
```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

### Monta a pesquisa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['dash', 'dodge', 'punch']}}
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> query
{
  "moves": {
    "$in": [
      "dash",
      "dodge",
      "punch"
    ]
  }
}
```

### Executa a pesquisa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8da"),
  "name": "Shuckle",
  "description": "Shuckle quietly hides itself under rocks, keeping its body concealed inside its hard shell while eating berries it has stored away. The berries mix with its body fluids to become a juice.",
  "type": "bug",
  "attack": 10,
  "defense": 230,
  "height": 0.6,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8db"),
  "name": "Dewott",
  "description": "Strict training is how it learns its flowing double-scalchop technique.",
  "type": "water",
  "attack": 75,
  "defense": 60,
  "height": 0.8,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dc"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. It is the world's most famouse and cute pokemon.",
  "type": "electric",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8de"),
  "name": "Jolteon",
  "description": "Jolteon's cells generate a low level of electricity. This power is amplified by the static electricity of its fur, enabling the Pokémon to drop thunderbolts. The bristling fur is made of electrically charged needles.",
  "type": "electric",
  "attack": 65,
  "defense": 60,
  "height": 0.8,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e0"),
  "name": "Claydol",
  "description": "Claydol are said to be dolls of mud made by primitive humans and brought to life by exposure to a mysterious ray. This Pokémon moves about while levitating.",
  "type": "psychic",
  "attack": 70,
  "defense": 105,
  "height": 15,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e1"),
  "name": "Zigzagoon",
  "description": "Zigzagoon restlessly wanders everywhere at all times. This Pokémon does so because it is very curious. It becomes interested in anything that it happens to see.",
  "type": "normal",
  "attack": 30,
  "defense": 41,
  "height": 0.4,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e2"),
  "name": "Herdier",
  "description": "This very loyal Pokémon helps Trainers, and it also takes care of other Pokémon.",
  "type": "normal",
  "attack": 80,
  "defense": 65,
  "height": 0.9,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe7"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe8"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8d9"),
  "name": "Zekrom",
  "description": "This legendary Pokémon can scorch the world with lightning. It assists those who want to build an ideal world.",
  "type": "electric",
  "attack": 150,
  "defense": 120,
  "height": 2.9,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dd"),
  "name": "Serperior",
  "description": "It only gives its all against strong opponents who are not fazed by the glare from Serperior's noble eyes.",
  "type": "grass",
  "attack": 75,
  "defense": 95,
  "height": 3.3,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8df"),
  "name": "Pumpkaboo",
  "description": "The pumpkin body is inhabited by a spirit trapped in this world. As the sun sets, it becomes restless and active.",
  "type": "grass",
  "attack": 66,
  "defense": 70,
  "height": 0.4,
  "moves": [
    "dodge"
  ]
}
Fetched 13 record(s) in 5ms
```

## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

### Monta a pesquisa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = {type: {$ne: 'electric'}}
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> query
{
  "type": {
    "$ne": "electric"
  }
}
```

### Executa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5649c4a775dda0a3d275f8da"),
  "name": "Shuckle",
  "description": "Shuckle quietly hides itself under rocks, keeping its body concealed inside its hard shell while eating berries it has stored away. The berries mix with its body fluids to become a juice.",
  "type": "bug",
  "attack": 10,
  "defense": 230,
  "height": 0.6,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8db"),
  "name": "Dewott",
  "description": "Strict training is how it learns its flowing double-scalchop technique.",
  "type": "water",
  "attack": 75,
  "defense": 60,
  "height": 0.8,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e0"),
  "name": "Claydol",
  "description": "Claydol are said to be dolls of mud made by primitive humans and brought to life by exposure to a mysterious ray. This Pokémon moves about while levitating.",
  "type": "psychic",
  "attack": 70,
  "defense": 105,
  "height": 15,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e1"),
  "name": "Zigzagoon",
  "description": "Zigzagoon restlessly wanders everywhere at all times. This Pokémon does so because it is very curious. It becomes interested in anything that it happens to see.",
  "type": "normal",
  "attack": 30,
  "defense": 41,
  "height": 0.4,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8e2"),
  "name": "Herdier",
  "description": "This very loyal Pokémon helps Trainers, and it also takes care of other Pokémon.",
  "type": "normal",
  "attack": 80,
  "defense": 65,
  "height": 0.9,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe7"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe8"),
  "name": "Bulbasaur",
  "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
  "type": "grass",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely.",
  "type": "fire",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8dd"),
  "name": "Serperior",
  "description": "It only gives its all against strong opponents who are not fazed by the glare from Serperior's noble eyes.",
  "type": "grass",
  "attack": 75,
  "defense": 95,
  "height": 3.3,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("5649c4a775dda0a3d275f8df"),
  "name": "Pumpkaboo",
  "description": "The pumpkin body is inhabited by a spirit trapped in this world. As the sun sets, it becomes restless and active.",
  "type": "grass",
  "attack": 66,
  "defense": 70,
  "height": 0.4,
  "moves": [
    "dodge"
  ]
}
{
  "_id": ObjectId("564c76a36b22a6995f2b89d8"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "moves": null
}
Fetched 11 record(s) in 5ms

```

## 7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

### Monta a pesquisa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { moves: { $in: [ 'dash' ] } }, { defense: { $not: { $lte: 49 } } } ] }
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> query
{
  "$and": [
    {
      "moves": {
        "$in": [
          "dash"
        ]
      }
    },
    {
      "defense": {
        "$not": {
          "$lte": 49
        }
      }
    }
  ]
}
```

### Executa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe7"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
Fetched 1 record(s) in 1ms
```

## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

### Monta a pesquisa

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ { type: 'water' }, { 'attack': { $lt: 50 } } ] }
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> query
{
  "$and": [
    {
      "type": "water"
    },
    {
      "attack": {
        "$lt": 50
      }
    }
  ]
}
```

### Pesquisa antes de apagar

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564c6f3a5cdce9685ea95fe7"),
  "name": "Squirtle",
  "description": "Squirtle's shell is not merely used for protection. The shell's rounded shape and the grooves on its surface help minimize resistance in water, enabling this Pokémon to swim at high speeds.",
  "type": "water",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "moves": [
    "dash",
    "punch",
    "dodge"
  ]
}
Fetched 1 record(s) in 1ms
```

### Adeus, Squirtle!

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```

### Verifica a exclusão

```
MacBook-Pro-de-Alexandre(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```