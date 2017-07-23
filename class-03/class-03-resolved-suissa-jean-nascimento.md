# MongoDb - Aula 03 - Exercício

1. Liste todos Pokemons com a altura **menor que** 0.5;
2. Liste todos Pokemons com a altura **maior ou igual que** 0.5;
3. Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;
5. Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5;

## Estrutura

```md
# MongoDB - Aula 03 - Exercício
autor: **Jean Nascimento**

## Liste todos Pokemons com a altura **menor que** 0.5

var query = {height: {$lt: 0.5}}

db.pokemons.find(query)
{
  "_id": ObjectId("564220f0613f89ac53a7b5d0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("56422345613f89ac53a7b5d1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56422705613f89ac53a7b5d4"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 2ms

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

var query = {height: {$gte: 0.5}}

db.pokemons.find(query)
{
  "_id": ObjectId("56422345613f89ac53a7b5d2"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56422345613f89ac53a7b5d3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("564350c8613f89ac53a7b5da"),
  "name": "Suissamon",
  "description": "Pokemon Hacker",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69
}
{
  "_id": ObjectId("564350c8613f89ac53a7b5db"),
  "name": "Dilmamon",
  "description": "Pokemon presidANTA",
  "type": "besta",
  "attack": 1,
  "defense": 1,
  "height": 1.6
}
{
  "_id": ObjectId("564350c8613f89ac53a7b5dc"),
  "name": "Cunhamon",
  "description": "Filho da puta",
  "type": "besta",
  "attack": 9990,
  "defense": 9999,
  "height": 1.8
}
{
  "_id": ObjectId("564350c8613f89ac53a7b5dd"),
  "name": "Calheirosmon",
  "description": "Irmão do filho da PUTA",
  "type": "besta",
  "attack": 8500,
  "defense": 9999,
  "height": 1.79
}
{
  "_id": ObjectId("564350c8613f89ac53a7b5de"),
  "name": "FeliciANUS",
  "description": "Pastor BAITOLA E FILHO DA PUTA",
  "type": "besta",
  "attack": 666,
  "defense": 666,
  "height": 1.7
}
Fetched 7 record(s) in 4ms


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": /grama/
    }
  ]
}

db.pokemons.find(query)
{
  "_id": ObjectId("56422345613f89ac53a7b5d1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}
query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": /pikachu/i
    }
  ]
}

db.pokemons.find(query)
{
  "_id": ObjectId("564220f0613f89ac53a7b5d0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]}

query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}

{
  "_id": ObjectId("564220f0613f89ac53a7b5d0"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("56422345613f89ac53a7b5d1"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("56422345613f89ac53a7b5d3"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms

```


## Envio

[Veja na nossa Wiki](https://github.com/Webschool-io/be-mean-instagram/wiki/Exerc%C3%ADcios)

1. Crie o repositório específico do módulo. Ex.: be-mean-instagram-mongodb
2. Crie a solução do exercício localmente nesse repositório, usando sempre o padrão `class-03-resolved-suissa-jean-nascimento.md`
3. Dê um `fork` no repositório oficial https://github.com/Webschool-io/be-mean-instagram-mongodb-excercises
4. Vá até a pasta do módulo desejado e **COLE** seu arquivo na pasta `class-03`
5. Crie um **Pull Request** enviando **APENAS** o seu arquivo sem modificar mais nada.
6. Na mensagem do commit/pull request favor seguir o padrão: Jean Nascimento - MongoDB - Exercicio 03 resolvido
7. Levante as mão para o céu e agradeça se acaso tiver ... #brinks
