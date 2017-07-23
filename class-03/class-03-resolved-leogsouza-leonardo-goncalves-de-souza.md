# MongoDB - Aula 03 - Exercício
autor: Leonardo Gonçalves de Souza

## Liste todos Pokemons com a altura menor que 0.5
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var query = {
... height: {$lt: 0.5}
... }

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c1fca57eb136c4319ae3df"),
  "name": "Miguelmon",
  "description": "Pokemon estranho",
  "attack": 27,
  "defense": 25,
  "height": 0.2
}
{
  "_id": ObjectId("57c1fcc57eb136c4319ae3e0"),
  "name": "Fabianamon",
  "description": "Pokemon femea",
  "attack": 48,
  "defense": 32,
  "height": 0.4
}
Fetched 2 record(s) in 11ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var query = {
... height: { $gte: 0.5}
... }

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3d8"),
  "name": "Sandshrew",
  "description": "Parece um tatu",
  "attack": 75,
  "defense": 85,
  "height": 6
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3d9"),
  "name": "Nidorino",
  "description": "Tá com cara de bravo",
  "attack": 72,
  "defense": 57,
  "height": 9
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3da"),
  "name": "Charizard",
  "description": "Meu dragão favorito",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3db"),
  "name": "Pidgeot",
  "description": "Passarinho legalzinho",
  "attack": 56,
  "defense": 35,
  "height": 3
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3dc"),
  "name": "Clefairy",
  "description": "Que fofura",
  "attack": 45,
  "defense": 48,
  "height": 6
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3dd"),
  "name": "Zubat",
  "description": "O mais odiado em Pokemon Go",
  "attack": 45,
  "defense": 35,
  "height": 8
}
{
  "_id": ObjectId("57c1c9ee7eb136c4319ae3de"),
  "name": "Psyduck",
  "description": "Pato Maluco",
  "attack": 52,
  "defense": 48,
  "height": 8
}
Fetched 7 record(s) in 118ms
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var query = {
... $and: [
... {height: {$lte: 0.5}},
... {type:'grama'}
... ]}

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c1fca57eb136c4319ae3df"),
  "name": "Miguelmon",
  "description": "Pokemon estranho",
  "attack": 27,
  "defense": 25,
  "height": 0.2,
  "type": "grama"
}
{
  "_id": ObjectId("57c1fcc57eb136c4319ae3e0"),
  "name": "Fabianamon",
  "description": "Pokemon femea",
  "attack": 48,
  "defense": 32,
  "height": 0.4,
  "type": "grama"
}
Fetched 2 record(s) in 42ms
```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var query = {
... $and: [
... {name: 'Pikachu'},
... {attack: {$lte: 0.5}}
... ]}

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> var query = {
... $and: [
... {attack: {$gte: 48}},
... {height: {$lte: 0.5}}
... ]}

Leonardo-PC(d:\mongodb\bin\mongod.exe-3.0.5) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57c1fcc57eb136c4319ae3e0"),
  "name": "Fabianamon",
  "description": "Pokemon femea",
  "attack": 48,
  "defense": 32,
  "height": 0.4,
  "type": "grama"
}
Fetched 1 record(s) in 7ms
```
