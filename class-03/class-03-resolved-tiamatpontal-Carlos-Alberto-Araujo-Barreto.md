### Listar todos os pokemons com a altura menor que 0.5 (Passo 1)
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {'height': {$lt: 0.5}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a2da728ccce8415450488"),
  "name": "pikachu",
  "description": "Rato de raio",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "elétrico"
}
Fetched 1 record(s) in 1ms

### Listar todos os pokemons com a altura maior ou igual que 0.5 (Passo 2)
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {'height': {$gte: 0.5}}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a2dc028ccce841545048c"),
  "name": "raichu",
  "description": "Ratazana elétrica boladona",
  "attack": 90,
  "defense": 55,
  "height": 0.8,
  "type": "elétrico"
}
{
  "_id": ObjectId("564a2dbd28ccce841545048b"),
  "name": "porygon",
  "description": "Lego",
  "attack": 60,
  "defense": 70,
  "height": 0.8,
  "type": "normal"
}
{
  "_id": ObjectId("564a2dbb28ccce841545048a"),
  "name": "blastoise",
  "description": "Tartaruga bolada",
  "attack": 83,
  "defense": 100,
  "height": 1.6,
  "type": "água"
}
{
  "_id": ObjectId("564a2db728ccce8415450489"),
  "name": "charizard",
  "description": "Lagarto de asas que cospe fogo",
  "attack": 84,
  "defense": 78,
  "height": 1.7,
  "type": "fogo"
}
{
  "_id": ObjectId("564b410341b4b3a29f92f505"),
  "name": "ivysaur",
  "description": "Pokemon com broto em suas costas",
  "attack": 62,
  "defense": 63,
  "height": 1,
  "type": "grama"
}
Fetched 5 record(s) in 10ms

### Listar todos os pokemons com a altura menor ou igual que 0.5 e do tipo grama (Passo 3)
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {'height': {$gte: 0.5}, 'type': "grama"}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564b410341b4b3a29f92f505"),
  "name": "ivysaur",
  "description": "Pokemon com broto em suas costas",
  "attack": 62,
  "defense": 63,
  "height": 1,
  "type": "grama"
}
Fetched 1 record(s) in 1ms

### Listar todos os pokemons com o name 'pikachu' ou com attack menor ou igual que 0.5 (Passo 4)
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {$or: [{'name': "pikachu"}, {'attack': {$lte: 0.5}}]}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a2da728ccce8415450488"),
  "name": "pikachu",
  "description": "Rato de raio",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "elétrico"
}
Fetched 1 record(s) in 1ms

### Listar todos os pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5 (Passo 5)
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> var query = {$and: [{'attack': {$gte: 48}}, {'height': {$lte: 0.5}}]}
carlos-VirtualBox(mongod-2.4.9) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a2da728ccce8415450488"),
  "name": "pikachu",
  "description": "Rato de raio",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "elétrico"
}
Fetched 1 record(s) in 3ms


