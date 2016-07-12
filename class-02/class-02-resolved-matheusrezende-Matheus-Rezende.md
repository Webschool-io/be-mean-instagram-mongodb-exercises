### MongoDB - Aula 02 - Exercício

autor: Matheus Rezende Figueira

## 1. Crie uma database chamada be-mean-pokemons;
```
matheus@matheus:~$ mongo be-mean-pokemons
MongoDB shell version: 3.0.12
connecting to: be-mean-pokemons
Mongo-Hacker 0.0.13

```
## 2. Liste quais databases você possui nesse servidor;

```
matheus(mongod-3.0.12) be-mean-pokemons> show dbs
be-mean           → 0.078GB
be-mean-instagram → 0.078GB
local             → 0.078GB
```

## 3. Liste quais coleções você possui nessa database;

```
matheus(mongod-3.0.12) be-mean-pokemons> show collections
matheus(mongod-3.0.12) be-mean-pokemons>
```
## 4. Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;

```
matheus(mongod-3.0.12) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("573ca2a86bbeb49156967250"),
  "name": "Pidgey",
  "description": "Pokemon voador mó daora",
  "attack": 49,
  "defense": 49,
  "height": 1
}
{
  "_id": ObjectId("573ca41c6bbeb49156967251"),
  "name": "Psyduck",
  "description": "Só tem cara de troxa",
  "attack": 62,
  "defense": 68,
  "height": 2.07
}
{
  "_id": ObjectId("573ca4326bbeb49156967252"),
  "name": "Machamp",
  "description": "Senta a porrada",
  "attack": 82,
  "defense": 83,
  "height": 5.03
}
{
  "_id": ObjectId("573ca4476bbeb49156967253"),
  "name": "Gastly",
  "description": "Assusta os cabra macho",
  "attack": 82,
  "defense": "13",
  "height": 4.03
}
{
  "_id": ObjectId("573ca4726bbeb49156967254"),
  "name": "Charizard",
  "description": "Solta fogo pela fuça",
  "attack": "90",
  "defense": "90",
  "height": "5.07"
}
Fetched 5 record(s) in 3ms
```

## 5. Liste os pokemons existentes na sua coleção;

```
matheus(mongod-3.0.12) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("573ca2a86bbeb49156967250"),
  "name": "Pidgey",
  "description": "Pokemon voador mó daora",
  "attack": 49,
  "defense": 49,
  "height": 1
}
{
  "_id": ObjectId("573ca41c6bbeb49156967251"),
  "name": "Psyduck",
  "description": "Só tem cara de troxa",
  "attack": 62,
  "defense": 68,
  "height": 2.07
}
{
  "_id": ObjectId("573ca4326bbeb49156967252"),
  "name": "Machamp",
  "description": "Senta a porrada",
  "attack": 82,
  "defense": 83,
  "height": 5.03
}
{
  "_id": ObjectId("573ca4476bbeb49156967253"),
  "name": "Gastly",
  "description": "Assusta os cabra macho",
  "attack": 82,
  "defense": "13",
  "height": 4.03
}
{
  "_id": ObjectId("573ca4726bbeb49156967254"),
  "name": "Charizard",
  "description": "Solta fogo pela fuça",
  "attack": "90",
  "defense": "90",
  "height": "5.07"
}
Fetched 5 record(s) in 3ms

```

## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada 'poke';

```
matheus(mongod-3.0.12) be-mean-pokemons> var poke = db.pokemons.findOne({'name': 'Gastly'})
matheus(mongod-3.0.12) be-mean-pokemons> poke
{
  "_id": ObjectId("573ca4476bbeb49156967253"),
  "name": "Gastly",
  "description": "Assusta os cabra macho",
  "attack": 82,
  "defense": "13",
  "height": 4.03
```

## 7. Modifique sua 'description' e salvê-o

```
matheus(mongod-3.0.12) be-mean-pokemons> poke.description = "Pokemons fdp dos tempos de game boy"
Pokemons fdp dos tempos de game boy
matheus(mongod-3.0.12) be-mean-pokemons> poke
{
  "_id": ObjectId("573ca4476bbeb49156967253"),
  "name": "Gastly",
  "description": "Pokemons fdp dos tempos de game boy",
  "attack": 82,
  "defense": "13",
  "height": 4.03
}
```
