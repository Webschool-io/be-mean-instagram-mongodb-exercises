
# MongoDB - Aula 03 - Exercício
autor: André Machado

## Liste todos Pokemons com a altura menor que 0.5;

>AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}

>AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

>{
  "_id": ObjectId("5643d253c8e7c6976cee0168"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}

>{
  "_id": ObjectId("5643d3acc8e7c6976cee0169"),
  "name": "Pikachu",
  "description": "Ratinho eletrico fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 40
}

>{
  "_id": ObjectId("5643d479c8e7c6976cee016a"),
  "name": "Tangela",
  "description": "Cabelo de medusa muito louco",
  "type": "grama",
  "attack": 55,
  "height": 0.3,
  "defense": 115
}

>{
  "_id": ObjectId("5643d4eec8e7c6976cee016b"),
  "name": "Nidoran",
  "description": "Um ratinho venenoso do fofinho",
  "type": "veneno",
  "attack": 47,
  "height": 0.4,
  "defense": 52
}
Fetched 4 record(s) in 2ms

## Liste todos Pokemons com a altura maior ou igual que 0.5;

>AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {height: {$gte: 0.5}};

>AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

>{
  "_id": ObjectId("5643d548c8e7c6976cee016c"),
  "name": "Mr. Mime",
  "description": "Um palhaco muito do estranho",
  "type": "psiquico/fada",
  "attack": 45,
  "height": 1.3,
  "defense": 65
}
Fetched 1 record(s) in 0ms

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

>AndrePC(mongod-3.0.7) be-mean-pokemons> var height = {height: {$lte: 0.5}};

>AndrePC(mongod-3.0.7) be-mean-pokemons> var type = {type: "grama"};

>AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {$and: [height, type]};

>AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

>{
  "_id": ObjectId("5643d479c8e7c6976cee016a"),
  "name": "Tangela",
  "description": "Cabelo de medusa muito louco",
  "type": "grama",
  "attack": 55,
  "height": 0.3,
  "defense": 115
}
Fetched 1 record(s) in 1ms

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

>AndrePC(mongod-3.0.7) be-mean-pokemons> var name = {name: "Pikachu"};

>AndrePC(mongod-3.0.7) be-mean-pokemons> var attack = {attack: {$lte: 45}};

>AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {$or: [name, attack]};

>AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

>{
  "_id": ObjectId("5643d253c8e7c6976cee0168"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}

>{
  "_id": ObjectId("5643d3acc8e7c6976cee0169"),
  "name": "Pikachu",
  "description": "Ratinho eletrico fofinho",
  "type": "eletrico",
  "attack": 55,
  "height": 0.4,
  "defense": 40
}

>{
  "_id": ObjectId("5643d548c8e7c6976cee016c"),
  "name": "Mr. Mime",
  "description": "Um palhaco muito do estranho",
  "type": "psiquico/fada",
  "attack": 45,
  "height": 1.3,
  "defense": 65
}
Fetched 3 record(s) in 0ms

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

>AndrePC(mongod-3.0.7) be-mean-pokemons> var attack = {attack: {$gte: 48}};

>AndrePC(mongod-3.0.7) be-mean-pokemons> var height = {heigth: {$lte: 0.5}};

>AndrePC(mongod-3.0.7) be-mean-pokemons> var query = {$and: [attack, height]};

>AndrePC(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);

>Fetched 0 record(s) in 0ms
