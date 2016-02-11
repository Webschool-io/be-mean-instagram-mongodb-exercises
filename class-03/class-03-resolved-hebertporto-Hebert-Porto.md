# MongoDB- Aula 03 - Exercício Resolvido
Autor: Hebert Porto

## Passo 1

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({'height':{$lt:0.5}})
{
  "_id": ObjectId("56bb39d084277bd0550d32c3"),
  "name": "Vaporeon",
  "description": "Nova Description",
  "type": "rock",
  "attack": 356,
  "defense": 250,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Passo 2

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({'height':{$gte:0.5}})
{
  "_id": ObjectId("56bb392384277bd0550d32bf"),
  "name": "Charizard",
  "description": "Sinistros de dia e de noite",
  "type": "ghost",
  "attack": 132,
  "defense": 2121,
  "height": 2
}
{
  "_id": ObjectId("56bb394184277bd0550d32c0"),
  "name": "Mew",
  "description": "Sinistros de dia e de noite",
  "type": "fighter",
  "attack": 99,
  "defense": 890,
  "height": 56.6
}
{
  "_id": ObjectId("56bb395784277bd0550d32c1"),
  "name": "Dragonite",
  "description": "Sinistros de dia e de noite",
  "type": "fire",
  "attack": 55,
  "defense": 21,
  "height": 4
}
{
  "_id": ObjectId("56bb39c384277bd0550d32c2"),
  "name": "Eevee",
  "description": "Sinistros de dia e de noite",
  "type": "water",
  "attack": 12,
  "defense": 222,
  "height": 21
}
Fetched 4 record(s) in 6ms
```

## Passo 3

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find( {$and:[{height:{$lte: '0.5'}}, {type: 'grass'}]} )
Fetched 0 record(s) in 1ms
```

## Passo 4

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({$or:[{name: 'Pikachu'},{attack:{$lte: '0.5'}}]})
Fetched 0 record(s) in 1ms
```

## Paao 5

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find({$and:[{attack: {$gte: 48}}, {height:{$lte: '0.5' }}] })
Fetched 0 record(s) in 1ms
```            