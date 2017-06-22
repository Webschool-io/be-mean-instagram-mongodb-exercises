# MongoDB Aula 03 - Exercício
autor: Jefferson Luiz de Lima

#### 1. Liste todos Pokemons com a altura menor que 0.5;

> var query = {height:{$lt:0.5}}

> db.pokemons.find(query)

{ "_id" : ObjectId("564b4c5187fe27a407f36392"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }

{ "_id" : ObjectId("564b4c8a87fe27a407f36393"), "name" : "Bulbassauro", "description" : "chicote trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }

{ "_id" : ObjectId("564b4e81cbb45b3cc807c1d3"), "name" : "Caterpie", "description" : "larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35 }

#### 2. Liste todos Pokemons com a altura maior ou igual que 0.5;

> var query = {height:{$gte:0.5}}

> db.pokemons.find(query)

{ "_id" : ObjectId("564b4ccc87fe27a407f36394"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }

{ "_id" : ObjectId("564b4d0287fe27a407f36395"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }

##### 3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

> var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]}

> db.pokemons.find(query)

{ "_id" : ObjectId("564b4c8a87fe27a407f36393"), "name" : "Bulbassauro", "description" : "chicote trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }

#### 4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}

> db.pokemons.find(query)

{ "_id" : ObjectId("564b4c5187fe27a407f36392"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }

#### 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}

> db.pokemons.find(query)

{ "_id" : ObjectId("564b4c5187fe27a407f36392"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }

{ "_id" : ObjectId("564b4c8a87fe27a407f36393"), "name" : "Bulbassauro", "description" : "chicote trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }

{ "_id" : ObjectId("564b4d0287fe27a407f36395"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
