# MongoDB - Aula 02 - Exercício
autor: Allysson dos Santoss

## Criação da database ‘be-mean-pokemons’

```
Allysson(mongod-3.2.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Liste quais databases você possui nesse servidor

```
Allysson(mongod-3.2.7) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
local             → 0.000GB
```

## Liste quais coleções você possui nessa database

```
Allysson(mongod-3.2.7) be-mean-pokemons> show collections
```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense, height

```
Allysson(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({'name': 'Metapod', 'description': 'Parece uma pedra', attack: 10, defense: 30, height: 9.9 })
Inserted 1 record(s) in 634ms
WriteResult({
  "nInserted": 1
})

Allysson(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({'name': 'Kakuna', 'description': 'Parece uma pedra amarela', attack: 10, defense: 20, height: 109 })
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Allysson(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({'name': 'Jigglypuff', 'description': 'Fofinho demais', attack: 20, defense: 10, height: 5.5 })
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Allysson(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({'name': 'Poliwrath', 'description': 'Esse é da agua', attack: 50, defense: 40, height: 54 })
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Allysson(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert({'name': 'Rattata', 'description': 'Rattata é bixo solto, fica ligeiro faz parte do jogo', attack: 30, defense: 20, height: 3.5 })
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

## Liste os pokemons existentes na sua coleção

```
Allysson(mongod-3.2.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("578ec17b994360514cf9ab65"),
  "name": "Metapod",
  "description": "Parece uma pedra",
  "attack": 10,
  "defense": 30,
  "height": 9.9
}
{
  "_id": ObjectId("578ec1d9994360514cf9ab66"),
  "name": "Kakuna",
  "description": "Parece uma pedra amarela",
  "attack": 10,
  "defense": 20,
  "height": 109
}
{
  "_id": ObjectId("578ec242994360514cf9ab67"),
  "name": "Jigglypuff",
  "description": "Fofinho demais",
  "attack": 20,
  "defense": 10,
  "height": 5.5
}
{
  "_id": ObjectId("578ec294994360514cf9ab68"),
  "name": "Poliwrath",
  "description": "Esse é da agua",
  "attack": 50,
  "defense": 40,
  "height": 54
}
{
  "_id": ObjectId("578ec2dd994360514cf9ab69"),
  "name": "Rattata",
  "description": "Rattata é bixo solto, fica ligeiro faz parte do jogo",
  "attack": 30,
  "defense": 20,
  "height": 3.5
}
Fetched 5 record(s) in 2ms
```

## Busque `o pokemon a sua escolha pelo nome` e armazene-o em uma variável chamada `poke`

```
Allysson(mongod-3.2.7) be-mean-pokemons> var query = {'name': 'Rattata'}
Allysson(mongod-3.2.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)
Allysson(mongod-3.2.7) be-mean-pokemons> poke
{
  "_id": ObjectId("578ec2dd994360514cf9ab69"),
  "name": "Rattata",
  "description": "Rattata é bixo solto, fica ligeiro faz parte do jogo",
  "attack": 30,
  "defense": 20,
  "height": 3.5
}
```

## Modifique sua `description` e salve-o

```
Allysson(mongod-3.2.7) be-mean-pokemons> poke.description = "Rattata é BICHO solto, salve sabotage"
Rattata é BICHO solto, salve sabotage
Allysson(mongod-3.2.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
