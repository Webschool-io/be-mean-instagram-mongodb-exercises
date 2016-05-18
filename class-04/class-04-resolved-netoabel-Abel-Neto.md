# MongoDB - Aula 04 - Exercício
User: [netoabel](http://www.github.com/netoabel)

Autor: Abel Neto

## Adicionando duas skills aos pokemóns `Pikachu`, `Squirtle`, `Bulbassaur` e `Charmander`

```
be-mean-pokemons> var query = { name: { $in: [/pikachu/i, /squirtle/i, /bulbassaur/i, /charmander/i] } }
be-mean-pokemons> var modifier = { $pushAll: { skills: ['chute', 'cascudo'] } }
be-mean-pokemons> var options = { multi: true }
be-mean-pokemons> db.pokemons.update(query, modifier, options)
Updated 4 existing record(s) in 32ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## Adicionando a skill `desvio` a todos os pokemóns

```
be-mean-pokemons> var query = {}
be-mean-pokemons> var modifier = { $push: { skills: 'desvio' } }
be-mean-pokemons> var options = { multi: true }
be-mean-pokemons> db.pokemons.update(query, modifier, options)
Updated 7 existing record(s) in 2ms
WriteResult({
  "nMatched": 7,
  "nUpserted": 0,
  "nModified": 7
})
```

## Adicionando o pokemón `Aindanaoexistemon`, caso ele não exista

```
be-mean-pokemons> var query = { name: /aindanaoexistemon/i }
be-mean-pokemons> var modifier = { $set: { description: "Sem maiores informações" }, $setOnInsert: { name: 'Aindanaoexistemon', attack: null, defense: null, heigh: null, type: null } }
be-mean-pokemons> var options = { upsert: true }
be-mean-pokemons> db.pokemons.update(query, modifier, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("572e9c06b31c114d305adf11")
})
```

## Listando todos os pokemóns que possuem as skills `investida` e `cascudo`

```
be-mean-pokemons> var query = { skills: { $all: [/investida/i, /cascudo/i] } }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d05603e77fb046dc9bcd0"),
  "name": "Bulbassaur",
  "description": "Um sapo com folhas",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grass",
  "skills": [
    "chute",
    "cascudo",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 35ms
```

## Listando todos os pokemóns que possuem as skills `chute` e `cascudo`

```
be-mean-pokemons> var query = { skills: { $all: [/chute/i, /cascudo/i] } }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d05603e77fb046dc9bcd0"),
  "name": "Bulbassaur",
  "description": "Um sapo com folhas",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grass",
  "skills": [
    "chute",
    "cascudo",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd3"),
  "name": "Charmander",
  "description": "Um filhote de dinossauro com o rabo pegando fogo",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire",
  "skills": [
    "chute",
    "cascudo",
    "desvio"
  ]
}
{
  "_id": ObjectId("572e96da33de04a6ed785f02"),
  "name": "Pikachu",
  "description": "Um rato elétrico",
  "attack": 60,
  "defense": 40,
  "height": 0.4,
  "type": "electric",
  "skills": [
    "chute",
    "cascudo",
    "desvio"
  ]
}
{
  "_id": ObjectId("572e972e33de04a6ed785f03"),
  "name": "Squirtle",
  "description": "Uma tartaruga que cospe água",
  "attack": 45,
  "defense": 35,
  "height": 0.6,
  "type": "water",
  "skills": [
    "chute",
    "cascudo",
    "desvio"
  ]
}
Fetched 4 record(s) in 4ms
```

## Listando todos os pokemóns que não são do tipo `elétrico`

```
be-mean-pokemons> var query = { type: { $ne: 'electric' } }
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d05603e77fb046dc9bcd0"),
  "name": "Bulbassaur",
  "description": "Um sapo com folhas",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grass",
  "skills": [
    "chute",
    "cascudo",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd1"),
  "name": "Ivysaur",
  "description": "Um sapo com uma bromélia",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "type": "grass",
  "skills": [
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd2"),
  "name": "Venusaur",
  "description": "Um sapo com um coqueiro",
  "attack": 40,
  "defense": 40,
  "height": 2,
  "type": "grass",
  "skills": [
    "desvio"
  ]
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd3"),
  "name": "Charmander",
  "description": "Um filhote de dinossauro com o rabo pegando fogo",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire",
  "skills": [
    "chute",
    "cascudo",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd4"),
  "name": "Charmeleon",
  "description": "Um pterodáctilo sem asas com o rabo pegando fogo",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "type": "fire",
  "skills": [
    "desvio"
  ]
}
{
  "_id": ObjectId("572e972e33de04a6ed785f03"),
  "name": "Squirtle",
  "description": "Uma tartaruga que cospe água",
  "attack": 45,
  "defense": 35,
  "height": 0.6,
  "type": "water",
  "skills": [
    "chute",
    "cascudo",
    "desvio"
  ]
}
{
  "_id": ObjectId("572e9c06b31c114d305adf11"),
  "description": "Sem maiores informações",
  "attack": null,
  "defense": null,
  "heigh": null,
  "type": null
}
Fetched 7 record(s) in 3ms
```

## Listando todos os pokemóns que possuam a skill `investida` e cuja defesa não seja menor ou igual a 49

```
be-mean-pokemons> var skillsQuery = { skills: { $in: [/investida/i] } }
be-mean-pokemons> var defenseQuery = { defense: { $not: { $lte: 49 } } }
be-mean-pokemons> var query = { $and: [ skillsQuery, defenseQuery ] }
be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("572d05603e77fb046dc9bcd0"),
  "name": "Bulbassaur",
  "description": "Um sapo com folhas",
  "attack": 30,
  "defense": 50,
  "height": 0.4,
  "type": "grass",
  "skills": [
    "chute",
    "cascudo",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 3ms
```

## Removendo todos os pokemóns do tipo `água` com ataque menor que 50

```
be-mean-pokemons> var query = { $and: [ { type: /water/i }, { attack: { $lt: 50 } } ] }
be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 18ms
WriteResult({
  "nRemoved": 1
})
```
