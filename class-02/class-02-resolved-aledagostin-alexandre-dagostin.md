# MongoDB - Aula 02 - Exercício
autor: Alexandre D'Agostin

## 1. Criar uma database chamada be-mean-pokemons

```
aledagostin(mongod-3.0.7) test> use be-mean-pokemons
switched to db be-mean-pokemons

```

## 2. Liste quais databases você possui nesse servidor

```
aledagostin(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB

```

## 3. Liste quais coleções você possui nessa database

```
aledagostin(mongod-3.0.7) be-mean-pokemons> use be-mean-instagram
switched to db be-mean-instagram
aledagostin(mongod-3.0.7) be-mean-instagram> show collections
pokemons       → 0.001MB / 0.008MB
system.indexes → 0.000MB / 0.008MB
teste          → 0.000MB / 0.008MB

```

## 4. Insira pelo menos 5 pokemons

```
aledagostin(mongod-3.0.7) be-mean-pokemons> var pokemons = [{'name':'Sandshrew','description':'This Pokémon curls up to protect itself from its enemies','type': 'Ground','attack': 40,'defense': 40,'height': 2.0},{'name':'Nidorino','description':'Has a horn that is harder than a diamond','type': 'Poison','attack': 40,'defense': 30,'height': 2.11},{'name':'Zubat','description':'Remains quietly unmoving in a dark spot during the bright daylight hours','type': 'Flying','attack': 20,'defense': 20,'height': 2.07},{'name':'Mankey','description':'When Mankey starts shaking and its nasal breathing turns rough, it is a sure sign that it is becoming angry','type': 'Fighting','attack': 40,'defense': 20,'height': 1.08},{'name':'Growlithe','description':'Growlithe has a superb sense of smell','type': 'Fire','attack': 45,'defense': 20,'height': 2.04}]
aledagostin(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons)

```

## 5. Liste os pokemons existentes na sua coleção

```
aledagostin(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564aa9beaaa1c02ba435c3c6"),
  "name": "Sandshrew",
  "description": "This Pokémon curls up to protect itself from its enemies",
  "type": "Ground",
  "attack": 40,
  "defense": 40,
  "height": 2
}
{
  "_id": ObjectId("564aa9beaaa1c02ba435c3c7"),
  "name": "Nidorino",
  "description": "Has a horn that is harder than a diamond",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 2.11
}
{
  "_id": ObjectId("564aa9beaaa1c02ba435c3c8"),
  "name": "Zubat",
  "description": "Remains quietly unmoving in a dark spot during the bright daylight hours",
  "type": "Flying",
  "attack": 20,
  "defense": 20,
  "height": 2.07
}
{
  "_id": ObjectId("564aa9beaaa1c02ba435c3c9"),
  "name": "Mankey",
  "description": "When Mankey starts shaking and its nasal breathing turns rough, it is a sure sign that it is becoming angry",
  "type": "Fighting",
  "attack": 40,
  "defense": 20,
  "height": 1.08
}
{
  "_id": ObjectId("564aa9beaaa1c02ba435c3ca"),
  "name": "Growlithe",
  "description": "Growlithe has a superb sense of smell",
  "type": "Fire",
  "attack": 45,
  "defense": 20,
  "height": 2.04
}
Fetched 5 record(s) in 10ms

```

## 6. Busque um pokemon e armazene-o em uma variável chamada "poke"

```
aledagostin(mongod-3.0.7) be-mean-pokemons> var query = {name: 'Mankey'}
aledagostin(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)

```

## 7. Modifique sua "description" e salve-o

```
aledagostin(mongod-3.0.7) be-mean-pokemons> poke.description = "Macaco lutador"
Macaco lutador
aledagostin(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 8ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
aledagostin(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564aa9beaaa1c02ba435c3c9"),
  "name": "Mankey",
  "description": "Macaco lutador",
  "type": "Fighting",
  "attack": 40,
  "defense": 20,
  "height": 1.08
}

```
