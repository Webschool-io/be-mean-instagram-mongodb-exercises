
1. Listar todos os Pokemons com a altura menor que 0.5
marcelo-note(mongod-2.6.10) be-mean-instagram> var query = {height:{$lt: 0.5}}
marcelo-note(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564746b08c0ae1f6d4440d9a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms


2. Listar todos os Pokemons com a altura maior ou igual que 0.5
marcelo-note(mongod-2.6.10) be-mean-instagram> var query = {height:{$gte: 0.5}}
marcelo-note(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564747578c0ae1f6d4440d9b"),
  "name": "Bulbassauro",
  "description": "chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.6
}
{
  "_id": ObjectId("564747948c0ae1f6d4440d9c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564747d28c0ae1f6d4440d9d"),
  "name": "Squirtie",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564748a98c0ae1f6d4440d9e"),
  "name": "Squirtie",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 4 record(s) in 1ms



3. Listar todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama.
marcelo-note(mongod-2.6.10) be-mean-instagram> var query = {$and: [{ height:{ $lte:0.5 } } , { type: "grama" } ]}
marcelo-note(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 1ms



4. Listar todos os Pokemons com aname 'Pikachu' OU com attack menor ou igual que 0.5
marcelo-note(mongod-2.6.10) be-mean-instagram> var query = {$or: [{name:"Pikachu"}, { attack:{$lte:0.5}}]}
marcelo-note(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564746b08c0ae1f6d4440d9a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms



5. Listar todos os Pokemons com attack MAIOR OU IGUAL QUE 48 E com height MENOR OU IGUAL que 0.5
marcelo-note(mongod-2.6.10) be-mean-instagram> var query = {$and: [{attack:{gte:48}},{height:{$lte:0.5}}]}
marcelo-note(mongod-2.6.10) be-mean-instagram> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
