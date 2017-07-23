# MongoDB - Aula 03 - Exercício
**Autor**: Maurício José da Silva Júnior

### Todos Pokemons menores que 0.5
```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {height:{$lt:0.5}}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56426ebca4e4c4604c3cd103"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56426f5aa4e4c4604c3cd104"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56427048a4e4c4604c3cd107"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 4ms
mjunior(mongod-3.0.7) be-mean-instagram> 
 
```

### Todos os com altura **MAIOR OU IGUAL a 0.5**
```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {height:{$gte:0.5}}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56426f6ba4e4c4604c3cd105"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564d312bf1e03798b5454ff7"),
  "name": "Maurisson",
  "description": "faz nada",
  "type": "estudante",
  "attack": 9000,
  "height": 179,
  "defensee": 100
}
{
  "_id": ObjectId("564d3152f1e03798b5454ff8"),
  "name": "Pokezinho",
  "description": "nem sei o que faz nem existe",
  "type": "inexistente",
  "attack": 500,
  "height": 179,
  "defensee": 100
}
Fetched 3 record(s) in 1ms
mjunior(mongod-3.0.7) be-mean-instagram> 

```

### Todos os pokemons com algura menor ou igual 0.5 e do tipo grama
```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {$and:[{height:{$lte:0.5}},{type:'grama'}]}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56426f5aa4e4c4604c3cd104"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
mjunior(mongod-3.0.7) be-mean-instagram>
```


### Todos com nome PIKACHU ou attack MENOR ou IGUAL a 0.5
```
mjunior(mongod-3.0.7) be-mean-instagram> var query = { $or:[{name:'Pikachu'},{attack:{$lte:0.5}}]  }
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56426ebca4e4c4604c3cd103"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
mjunior(mongod-3.0.7) be-mean-instagram> 

```
## Todos com attack maior ou igual a 48 com altura menor ou igual a 0.5
```
mjunior(mongod-3.0.7) be-mean-instagram> var query = {$and: [ {attack:{$gte:48}} , {height:{$lte:0.5}} ]}
mjunior(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("56426ebca4e4c4604c3cd103"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56426f5aa4e4c4604c3cd104"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 1ms
mjunior(mongod-3.0.7) be-mean-instagram> 

```
