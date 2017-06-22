#MongoDB - Aula 03 - Exercício

autor: MARLON WANGER

##Selecionando o banco be-mean-pokemons criado na aula 02 (passo 1)
```
kakashicafe-PC(mongod-3.0.7) test> use be-mean-instagram
switched to db be-mean-instagram
```

##Listagem de todos os Pokemons com a altura menor que 0.5 (passo 2)
```
kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var query = {height:{$lt:0.5}}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e56eab54fcab69c7306ee"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564e5957b54fcab69c7306f2"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 37ms

```

##Listagem de todos os Pokemons com a altura maior ou igual que 0.5 (passo 3)
```
kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var query = {height:{$gte:0.5}}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564e54eab54fcab69c7306ed"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 4
}
{
  "_id": ObjectId("564e56eab54fcab69c7306ef"),
  "name": "Charmander",
  "description": "cao chupando maga de tao fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564e56eab54fcab69c7306f0"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 2ms

```

##Listagem de todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama (passo 4)
```
kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var query1 = {height:{$lte:0.5}}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var query2 = {type:"grama"}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var queryFinal = {$and:[query1,query2]}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> db.pokemons.find(queryFinal)
{
  "_id": ObjectId("564e56eab54fcab69c7306ee"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}

Fetched 1 record(s) in 3ms

```

##Listagem de todos os Pokemons com o nome Pikachu ou com attack menor ou igual que 0.5 (passo 5)
```
kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var query1 = {name:"Pikachu"}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var query2 = {attack:{$lte:0.5}}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var queryFinal = {$or:[query1,query2]}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> db.pokemons.find(queryFinal)
{
  "_id": ObjectId("564e54eab54fcab69c7306ed"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 4
}

Fetched 1 record(s) in 3ms

```

##Listagem de todos os Pokemons com o attack maior ou igual que 48 E com height menor ou igual que 0.5 (passo 6)
```
kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var query1 = {attack:{$gte:48}}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var query2 = {height:{$lte:0.5}}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> var queryFinal = {$and:[query1,query2]}

kakashicafe-PC(mongod-3.0.7) be-mean-instagram> db.pokemons.find(queryFinal)
{
  "_id": ObjectId("564e56eab54fcab69c7306ee"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564e56eab54fcab69c7306f0"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "agua",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 2ms

```
