ALTURA MENOR QUE 0.5

victor-notebook(mongod-3.0.7) be-mean-instagram> db.pokemons.find({height: {$lt: 0.5}}) { "_id": ObjectId("564cd10365495312d4d53b2b"), "name": "Pikachu", "description": "Rato elétrico bem fofinho", "type": "eletric", "attack": 55, "height": 0.4 } { "_id": ObjectId("564cd26565495312d4d53b2c"), "name": "Bulbassauro", "description": "Chicote de trepadeira", "type": "grama", "attack": 49, "height": 0.4 } { "_id": ObjectId("564ce10599f90d5badf595f1"), "name": "Cartepie", "description": "Larva lutadora", "type": "inseto", "attack": 30, "height": 0.3 } Fetched 3 record(s) in 0ms

ALTURA MAIOR OU IGUAL

victor-notebook(mongod-3.0.7) be-mean-instagram> var query = {height: {$gte: 0.5}} victor-notebook(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query) { "_id": ObjectId("564cd2f065495312d4d53b2d"), "name": "Charmander", "description": "Esse é o cão chupando manga de fofinho", "type": "fogo", "attack": 52, "height": 0.6 } { "_id": ObjectId("564cd36965495312d4d53b2e"), "name": "Squirtle", "description": "Ejeta água que passarinho não bebe", "type": "água", "attack": 48, "height": 0.5 } Fetched 2 record(s) in 1ms

ALTURA MENOR OU IGUAL QUE 0.5 E TIPO GRAMA

victor-notebook(mongod-3.0.7) be-mean-instagram> var query = { $and: [{height: {$lte: 0.5}}, {type: "grama"}]} victor-notebook(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query) { "_id": ObjectId("564cd26565495312d4d53b2c"), "name": "Bulbassauro", "description": "Chicote de trepadeira", "type": "grama", "attack": 49, "height": 0.4 } Fetched 1 record(s) in 0ms

TODOS POKEMONS COM NOME PIKACHU OU COM ATTACK MENOR OU IGUAL QUE 0.5

r: [{name:"Pikachu"},{attack: {$lte: 0.5}}]} victor-notebook(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query) { "_id": ObjectId("564cd10365495312d4d53b2b"), "name": "Pikachu", "description": "Rato elétrico bem fofinho", "type": "eletric", "attack": 55, "height": 0.4 } Fetched 1 record(s) in 1ms

Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5

victor-notebook(mongod-3.0.7) be-mean-instagram> var query = {$and: [{attack: {$gte: 48 }}, {height: {$lte:0.5}}]} victor-notebook(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query) { "_id": ObjectId("564cd10365495312d4d53b2b"), "name": "Pikachu", "description": "Rato elétrico bem fofinho", "type": "eletric", "attack": 55, "height": 0.4 } { "_id": ObjectId("564cd26565495312d4d53b2c"), "name": "Bulbassauro", "description": "Chicote de trepadeira", "type": "grama", "attack": 49, "height": 0.4 } { "_id": ObjectId("564cd36965495312d4d53b2e"), "name": "Squirtle", "description": "Ejeta água que passarinho não bebe", "type": "água", "attack": 48, "height": 0.5 } Fetched 3 record(s) in 0ms
