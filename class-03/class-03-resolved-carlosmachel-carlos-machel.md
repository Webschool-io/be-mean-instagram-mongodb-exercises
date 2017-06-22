# MongoDB - Aula 03 - Exercício

autor: Carlos Machel

## Liste todos Pokemons com a altura **menor que** 0.5;

```
be-mean-pokemons> var query = {height: {$lt: 0.5}}

be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56514009b130c501af4eafab"),
  "name": "Cubone",
  "description": "Chora pela mãe que nunca mais vai ver =( ",
  "type": "Ground",
  "attack": 30,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("565148b5b130c501af4eafae"),
  "name": "Pikachu",
  "description": "Rato elétrico.",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("565148b5b130c501af4eafaf"),
  "name": "Geodude",
  "description": "Pedra redonda e rabugente.",
  "type": "Rock",
  "attack": 48,
  "defense": 40,
  "height": 0.4
}
Fetched 3 record(s) in 1ms
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
be-mean-pokemons> var query = {height: {$gte: 0.5}}

be-mean-pokemons> query
{
 "height": {
   "$gte": 0.5
 }
}

be-mean-pokemons> be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56514009b130c501af4eafa7"),
  "name": "Golbat",
  "description": "Morceguinho que adora sugar sangue.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 1.6
}
{
  "_id": ObjectId("56514009b130c501af4eafa8"),
  "name": "Zubat",
  "description": "Morceguinho que se queima no sol.",
  "type": "Poison",
  "attack": 20,
  "defense": 20,
  "height": 0.8
}
{
  "_id": ObjectId("56514009b130c501af4eafa9"),
  "name": "Psyduck",
  "description": "Pato muito doido que usa um poder misterioso",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.8
}
{
  "_id": ObjectId("56514009b130c501af4eafaa"),
  "name": "Mankey",
  "description": "Macaquinho que quando fica nervoso sai da reta.",
  "type": "Fighting",
  "attack": 40,
  "defense": 20,
  "height": 0.5
}
{
  "_id": ObjectId("56514009b130c501af4eafac"),
  "name": "Heracross",
  "description": "Besouro sinistro de forte. Derruba até uma árvore.",
  "type": "Bug",
  "attack": 60,
  "defense": 30,
  "height": 1.5
}
{
  "_id": ObjectId("565148b5b130c501af4eafad"),
  "name": "Oddish",
  "description": "Batata que se enfia no solo pra pegar nutrientes.",
  "type": "Grass",
  "attack": 30,
  "defense": 30,
  "height": 0.5
}
Fetched 6 record(s) in 1ms
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
be-mean-pokemons> var query = {$and: [{height: { $lte: 0.5 }  }, { type: /grass/i} ] }

be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": /grass/i
    }
  ]
}

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565148b5b130c501af4eafad"),
  "name": "Oddish",
  "description": "Batata que se enfia no solo pra pegar nutrientes.",
  "type": "Grass",
  "attack": 30,
  "defense": 30,
  "height": 0.5
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
be-mean-pokemons> var query = {$or: [ { name: /pikachu/i }, {attack: { $lte: 0.5 }}] }

be-mean-pokemons> query
{
  "$or": [
    {
      "name": /pikachu/i
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565148b5b130c501af4eafae"),
  "name": "Pikachu",
  "description": "Rato elétrico.",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
be-mean-pokemons> var query = {$and: [ {attack: { $gte: 48  }}, {height: {$lte: 0.5  }} ]}

be-mean-pokemons> query
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

be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565148b5b130c501af4eafaf"),
  "name": "Geodude",
  "description": "Pedra redonda e rabugente.",
  "type": "Rock",
  "attack": 48,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```
