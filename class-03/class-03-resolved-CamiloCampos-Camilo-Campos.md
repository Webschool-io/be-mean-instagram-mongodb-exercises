# MongoDb - Aula 03 - Exercício

1. Liste todos Pokemons com a altura **menor que** 0.5;
2. Liste todos Pokemons com a altura **maior ou igual que** 0.5;
3. Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;
5. Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5;

## Estrutura

```md
# MongoDB - Aula 03 - Exercício
autor: Camilo Campos

## Liste todos Pokemons com a altura **menor que** 0.5;
var query = {height: {$lt: 0.5}}

camilo-Inspiron-N5110(mongod-2.6.11) be-mean-pokemon> db.pokemon.find(query)
Fetched 0 record(s) in 1ms


## Liste todos Pokemons com a altura **maior ou igual que** 0.5
camilo-Inspiron-N5110(mongod-2.6.11) be-mean-pokemon> db.pokemon.find(query)
{
  "_id": ObjectId("5643e3193b1fb9352ed6db1c"),
  "name": "gabumon",
  "type": "dinosaur",
  "height": 0.9
}
{
  "_id": ObjectId("5643e3193b1fb9352ed6db1d"),
  "name": "pinokomon",
  "type": "wood",
  "height": 1.5
}
{
  "_id": ObjectId("5643e3193b1fb9352ed6db1e"),
  "name": "devilmon",
  "type": "dark",
  "height": 3
}
Fetched 3 record(s) in 2ms

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
var query = {$and: [{height: {$lte: 1.5}, type: /wood/}]}

query
{
  "$and": [
    {
      "height": {
        "$lte": 1.5
      },
      "type": /wood/
    }
  ]
}

db.pokemon.find(query)

{
  "_id": ObjectId("5643e3193b1fb9352ed6db1d"),
  "name": "pinokomon",
  "type": "wood",
  "height": 1.5
}
Fetched 1 record(s) in 2ms


## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

var query = {$or: [{attack: {$lte: 0.5}, name: /pikachu/i}]}

query
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      },
      "name": /pikachu/i
    }
  ]
}

camilo-Inspiron-N5110(mongod-2.6.11) be-mean-pokemon> db.pokemon.find(query)
Fetched 0 record(s) in 26ms


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

camilo-Inspiron-N5110(mongod-2.6.11) be-mean-pokemon> db.pokemon.find(query)
Fetched 0 record(s) in 1ms


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
