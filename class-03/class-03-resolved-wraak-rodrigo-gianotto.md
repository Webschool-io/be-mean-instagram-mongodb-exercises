# MongoDB - Aula 03 - Exercício
# Autor: Rodrigo de Medeiros Gianotto 

## Step 1: Liste todos os pokemons com altura menor que 0.5
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = { height: {$lt:0.5} }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb0e258133224d47381a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5648bb7f258133224d47381b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5648bc60258133224d47381e"),
  "name": "Caterpie",
  "description": "teste",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 1ms
```

## Step 2: Liste todos os pokemons com altura maior ou igual que 0.5
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = { height: { $gte:0.5 } } 
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb92258133224d47381c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5648bbb7258133224d47381d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms
```

## Step 3: Liste todos os pokemons com altura menor ou igual que 0.5 E do tipo grama
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = { $and: [{type:'grama'}, {height:{$lte:0.5}}] }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb7f258133224d47381b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Step 4: Liste todos os pokemons com o nome "Pikachu" OU com attack menor ou igual que 0.5
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = { $or: [ { name:'Pikachu' } , { attack: { $lte:0.5 } } ] }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb0e258133224d47381a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Step 5: Liste todos os pokemons com o attack maior ou igual a 48 E com height menor ou igual que 0.5
```
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> var query = { $and: [ { height: {$lte:0.5} } , { attack: {$gte:48} } ] }
Rodrigos-iMac(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5648bb0e258133224d47381a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5648bb7f258133224d47381b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5648bbb7258133224d47381d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms
```