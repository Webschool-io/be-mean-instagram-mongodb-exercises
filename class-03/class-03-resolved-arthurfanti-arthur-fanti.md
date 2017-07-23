# MongoDB - Aula 03 - Exercício
autor: SEU NOME

## Liste todos Pokemons com a altura **menor que** 0.5;
```zsh
be-mean-pokemons> var query = {height: {$lt: 0.5}}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644a4a112150f4ff7f6186a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5644a57012150f4ff7f6186b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5644a7c912150f4ff7f6186e"),
  "name": "Caterpie",
  "description": "Larva lutadora zica do pantano, manja nada dos paranaue",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 20
}
Fetched 3 record(s) in 10ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```zsh
be-mean-pokemons> var query = {height: {$gte: 0.5}}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644a5be12150f4ff7f6186c"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5644a61012150f4ff7f6186d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 12ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```zsh
be-mean-pokemons> var query = {$and: [{height:{$lte: 0.5}}, {type:"grama"}]}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644a57012150f4ff7f6186b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```zsh
be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {attack: {$lte: 48}}]}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644a4a112150f4ff7f6186a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5644a61012150f4ff7f6186d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5644a7c912150f4ff7f6186e"),
  "name": "Caterpie",
  "description": "Larva lutadora zica do pantano, manja nada dos paranaue",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 20
}
Fetched 3 record(s) in 10ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```zsh
be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5644a4a112150f4ff7f6186a"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5644a57012150f4ff7f6186b"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5644a61012150f4ff7f6186d"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 2ms
```
