# MongoDB - Aula 03 - Exercício
autor: Ronaldo Feitosa

## Liste todos Pokemons com a altura menor que 0.5;
```
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> var query = {height: {$lt: 0.5}}

ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e74e19334563dc5915b2f2"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56e74e2e334563dc5915b2f3"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
```


##Liste todos Pokemons com a altura maior ou igual que 0.5
```
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> var query = {height: {$gte: 0.5}}

ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e5bef71ed08ada9f1ebe74"),
  "name": "Kadabra",
  "description": "Mestre das colheres tortas",
  "type": "psíquico",
  "height": 4.3,
  "attack": 35,
  "defense": 30
}
{
  "_id": ObjectId("56e5bfe41ed08ada9f1ebe75"),
  "name": "Cubone",
  "description": "Pokemon cabeça de Osso",
  "type": "terra",
  "height": 1.4,
  "attack": 50,
  "defense": 95
}
{
  "_id": ObjectId("56e5c0c61ed08ada9f1ebe76"),
  "name": "Vaporeon",
  "description": "Pokemon aquático evoluído do Eevee",
  "type": "água",
  "height": 3.3,
  "attack": 65,
  "defense": 60
}
{
  "_id": ObjectId("56e5c0ff1ed08ada9f1ebe77"),
  "name": "Butterfree",
  "description": "Pokemon voador",
  "type": "vento",
  "height": 3.7,
  "attack": 45,
  "defense": 50
}
{
  "_id": ObjectId("56e5c1931ed08ada9f1ebe78"),
  "name": "Golbat",
  "description": "Morcego sanguinário",
  "type": "vento e veneno",
  "height": 5.3,
  "attack": 80,
  "defense": 70
}
{
  "_id": ObjectId("56e74e4b334563dc5915b2f4"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56e74e6a334563dc5915b2f5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> var query = {$and: [{height: {$lte:0.5}}, {type:'grama'}]}

ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e74e2e334563dc5915b2f3"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> var query = {$or: [{attack: {$lte:0.5}}, {name:'Pikachu'}]}

ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e74e19334563dc5915b2f2"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> var query = {$and: [{attack: {$gte:48}}, {height:{$lte: 0.5}}]}

ronaldo-ubuntu(mongod-3.0.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56e74e19334563dc5915b2f2"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("56e74e2e334563dc5915b2f3"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56e74e6a334563dc5915b2f5"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
```


