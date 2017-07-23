# MongoDb - Aula 03 - Exercício

1. Liste todos Pokemons com a altura **menor que** 0.5;
2. Liste todos Pokemons com a altura **maior ou igual que** 0.5;
3. Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5;
5. Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5;

## Estrutura

```md
# MongoDB - Aula 03 - Exercício
autor: Fabio Gouw

## Liste todos Pokemons com a altura **menor que** 0.5;

```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> var query = {height: {$lt: 0.5}}
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("565f920d31ad5ca12bfd63f9"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("565f92c231ad5ca12bfd63fa"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("565f93be31ad5ca12bfd63fd"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "insect",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 21ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> var query = {height: {$gte: 0.5}}
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("565f92ee31ad5ca12bfd63fb"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fire",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("565f932031ad5ca12bfd63fc"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 13ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> var query1 = { height: { $lte: 0.5 } }
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> var query2 = { type: 'grass' }
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> db.pokemons.find({ $and: [query1, query2] })
{
  "_id": ObjectId("565f92c231ad5ca12bfd63fa"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 9ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> var query1 = { name: 'Pikachu' }
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> var query2 = { attack: { $lte: 0.5 } }
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> db.pokemons.find({ $or: [query1, query2] })
{
  "_id": ObjectId("565f920d31ad5ca12bfd63f9"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
Fetched 1 record(s) in 7ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> var query1 = { attack: { $gte: 48 } }
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> var query2 = { height: { $lte: 0.5 } }
Vanaheim(C:\Program Files\MongoDB\Server\3.0\bin\mongod.exe-3.0.6) be-mean-instagram> db.pokemons.find({ $and: [query1, query2] })
{
  "_id": ObjectId("565f920d31ad5ca12bfd63f9"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("565f92c231ad5ca12bfd63fa"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grass",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("565f932031ad5ca12bfd63fc"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "water",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 18ms
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
