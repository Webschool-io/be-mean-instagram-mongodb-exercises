# MongoDB - Aula 03 - Exercício
autor: Edison Magalhães Rocha


### 1. Liste todos os Pokemons com a altura menor que 0.5

```
njinga(mongod-3.2.6) be-mean-instagram> var query = {height: {$lt: 0.5}}
njinga(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5753aa598d1753881846ca8c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5753aaf78d1753881846ca8d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5753adc08d1753881846ca91"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 4ms
njinga(mongod-3.2.6) be-mean-instagram> 
```


### 2. Liste todos Pokemons com a altura maior ou igual que 0.5

```
njinga(mongod-3.2.6) be-mean-instagram> var query = {height: {$gte: 0.5}}
njinga(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5753ab358d1753881846ca8e"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5753ab658d1753881846ca8f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 4ms
njinga(mongod-3.2.6) be-mean-instagram> 
```


### 3. Liste todos Pokemons com a altura menor ou igual que 0.5 e do tipo grama

```
njinga(mongod-3.2.6) be-mean-instagram> var query = {$and: [{type: 'grama'}, {height: {$lte:0.5}}]}
njinga(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5753aaf78d1753881846ca8d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
njinga(mongod-3.2.6) be-mean-instagram>
```


### 4. Liste todos os Pokemons com o name 'Pikachu' ou com attack menor ou igual que 0.5

```
njinga(mongod-3.2.6) be-mean-instagram> var query = {$or: [{name: 'Pikachu'}, {attack: {$lte:0.5}}]}
njinga(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5753aa598d1753881846ca8c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 3ms
njinga(mongod-3.2.6) be-mean-instagram> 
 
```


### 5. Liste todos Pokemons com attack maior ou igual que 48 e com heigth menor ou igual que 0.5

```
njinga(mongod-3.2.6) be-mean-instagram> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte:0.5}}]}
njinga(mongod-3.2.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("5753aa598d1753881846ca8c"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5753aaf78d1753881846ca8d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5753ab658d1753881846ca8f"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5753ab758d1753881846ca90"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 4 record(s) in 4ms
njinga(mongod-3.2.6) be-mean-instagram> 
```