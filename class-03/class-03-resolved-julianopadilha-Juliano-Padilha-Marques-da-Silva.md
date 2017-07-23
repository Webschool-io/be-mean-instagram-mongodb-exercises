# MongoDB - Aula 03 - Exercício
Autor: Juliano Padilha

## Liste todos os Pokemons com a altura menor que 0.5

```
var query = {height: {$lt: 0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("5778a83ea1daa07096d6b642"),
  "name": "Gitus",
  "description": "Faz push e faz pull",
  "attack": 70,
  "defense": 50,
  "height": 0.2,
  "type": "Terra"
}
Fetched 1 record(s) in 1ms
```

## Liste todos os Pokemons com a altura maior ou igual que 0.5

```
var query = {height: {$gte: 0.5}}
db.pokemons.find(query)
{
  "_id": ObjectId("5778a6e0a1daa07096d6b63e"),
  "name": "Bugossauro",
  "description": "Buga seu código sem você perceber",
  "attack": 60,
  "defense": 45,
  "height": 0.9,
  "type": "Grama"
}
{
  "_id": ObjectId("5778a76ba1daa07096d6b63f"),
  "name": "Javascripto",
  "description": "Seu melhor companheiro de aventura",
  "attack": 80,
  "defense": 60,
  "height": 0.5,
  "type": "Fogo"
}
{
  "_id": ObjectId("5778a7b3a1daa07096d6b640"),
  "name": "Maczin",
  "description": "Ataque de Maça",
  "attack": 50,
  "defense": 30,
  "height": 0.6,
  "type": "Ar"
}
{
  "_id": ObjectId("5778a805a1daa07096d6b641"),
  "name": "Freelagem",
  "description": "Faz tudo para sobreviver",
  "attack": 45,
  "defense": 70,
  "height": 0.8,
  "type": "Pobre"
}
Fetched 4 record(s) in 3ms
```

## Liste todos os Pokemons com a altura menor ou igual que 0.5(0.9) e do tipo grama

```
var query = {$and: [{height: {$lte: 0.9}}, {type: "Grama"}]}
db.pokemons.find(query)
{
  "_id": ObjectId("5778a6e0a1daa07096d6b63e"),
  "name": "Bugossauro",
  "description": "Buga seu código sem você perceber",
  "attack": 60,
  "defense": 45,
  "height": 0.9,
  "type": "Grama"
}
Fetched 1 record(s) in 1ms
```

## Liste todos os Pokemons com o nome 'Pikachu'('Freelagem') ou com attack menor ou igual que 0.5

```
var query = {$or: [{name: 'Freelagem'}, {attack: {$lte: 0.5}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("5778a805a1daa07096d6b641"),
  "name": "Freelagem",
  "description": "Faz tudo para sobreviver",
  "attack": 45,
  "defense": 70,
  "height": 0.8,
  "type": "Pobre"
}
Fetched 1 record(s) in 1ms
```

## Liste todos os Pokemons com attack maior ou igual que 48 e com height menor ou igual que 0.5

```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("5778a76ba1daa07096d6b63f"),
  "name": "Javascripto",
  "description": "Seu melhor companheiro de aventura",
  "attack": 80,
  "defense": 60,
  "height": 0.5,
  "type": "Fogo"
}
{
  "_id": ObjectId("5778a83ea1daa07096d6b642"),
  "name": "Gitus",
  "description": "Faz push e faz pull",
  "attack": 70,
  "defense": 50,
  "height": 0.2,
  "type": "Terra"
}
Fetched 2 record(s) in 2ms
```