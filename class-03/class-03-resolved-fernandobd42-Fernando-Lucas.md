## MongoDb - Aula 03
autor: Fernando Lucas

Na aula 3 continuaremos a desenvolver nosso CRUD no `Terminal` usando o cliente, `mongo`, para isso.

Para isso aprenderemos como buscar os registros do nosso banco.

* [find](./mongodb/find-findOne.md)
* [findOne](./mongodb/find-findOne.md)


### Listar Pokemons com a altura  MENOR QUE 0.5 (Passo 1)
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {height: {$lt: 0.5}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d7672dcb3b48d2bc977b8"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3
}
{
  "_id": ObjectId("572d76c7dcb3b48d2bc977b9"),
  "name": "Pikachu",
  "description": "Rato Eletrico",
  "type": "Eletric",
  "attack": 55,
  "height": 0.4
}
```


### Listar Pokemons com a altura MAIOR OU IGUAL QUE 0.5 (Passo 2)
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {height: {$gte: 0.5}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572b61faa1e3052ea6fd023a"),
  "name": "CunhaCu",
  "description": "Pokemon Ladrao/Safado",
  "type": "Ladrao",
  "attack": 9999,
  "defense": 9999,
  "height": 1.8
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023b"),
  "name": "AecioPo",
  "description": "Aspirador de Po",
  "type": "Cherador",
  "attack": 9999,
  "defense": 9999,
  "height": 1.82
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023c"),
  "name": "Fernando Collor",
  "description": "Aspirador Philco 2000",
  "type": "Cherador Nato",
  "attack": 8000,
  "defense": 8000,
  "height": 1.9
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023d"),
  "name": "Bolsonada",
  "description": "Militar Conservador",
  "type": "Careta",
  "attack": 5000,
  "defense": 5000,
  "height": 1.9
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023e"),
  "name": "Luladrao",
  "description": "Rouba de pobre",
  "type": "Cara Dura",
  "attack": 1000,
  "defense": 1000,
  "height": 1.8
}
{
  "_id": ObjectId("572d7702dcb3b48d2bc977ba"),
  "name": "Charmander",
  "description": "O Cão chupando manga",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("572d772adcb3b48d2bc977bb"),
  "name": "Squirtle",
  "description": "Ejeta água destilada",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
```

### Listar Pokemons com a altura MENOR OU IGUAL QUE 0.5 E do tipo grama (Passo 3)
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}}, {type:'grama'}]}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d7a5a7f16df60b250723e"),
  "name": "Bulbassauro",
  "description": "Chicote de bater em careta",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
```

### Listar Pokemons com o name 'Pikachu' OU com attack MENOR OU IGUAL QUE 0.5 (Passo 4)
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d76c7dcb3b48d2bc977b9"),
  "name": "Pikachu",
  "description": "Rato Eletrico",
  "type": "Eletric",
  "attack": 55,
  "height": 0.4
}
```

### Listar Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height MENOR OU IGUAL 0.5
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d76c7dcb3b48d2bc977b9"),
  "name": "Pikachu",
  "description": "Rato Eletrico",
  "type": "Eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("572d772adcb3b48d2bc977bb"),
  "name": "Squirtle",
  "description": "Ejeta água destilada",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("572d7a5a7f16df60b250723e"),
  "name": "Bulbassauro",
  "description": "Chicote de bater em careta",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
```