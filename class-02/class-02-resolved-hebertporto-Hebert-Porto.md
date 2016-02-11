## MongoDB- Aula 02 - Exercício Resolvido
Autor: Hebert Porto

## Passo 1

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) use be-mean-pokemons
switched to db be-mean-pokemons
```
## Passo 2 

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> show dbs
be-mean → 0.203GB
local   → 0.078GB
test    → 0.203GB
```

## Passo 3

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.collections
be-mean-pokemons.collections
```

## Passo 4

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Charizard", description: "Sinistros de dia e de noite", type: "ghost", attack: 132 , defens
                                                         db.pokemons.insert({name: "Charizard", description: "Sinistros de dia e de noite", type: "ghost", attack: 132 , defens
e: 2121,height: 2 })
Inserted 1 record(s) in 82ms
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Mew", description: "Sinistros de dia e de noite", type: "fighter", attack: 99 , defense: 89
                                                         db.pokemons.insert({name: "Mew", description: "Sinistros de dia e de noite", type: "fighter", attack: 99 , defense: 89
0,height: 56.6})
Inserted 1 record(s) in 2ms
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Dragonite", description: "Sinistros de dia e de noite", type: "fire", attack: 55, defense:
                                                         db.pokemons.insert({name: "Dragonite", description: "Sinistros de dia e de noite", type: "fire", attack: 55, defense:
21,height: 4})
Inserted 1 record(s) in 4ms

vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Eevee", description: "Sinistros de dia e de noite", type: "water", attack: 12, defense: 222
                                                         db.pokemons.insert({name: "Eevee", description: "Sinistros de dia e de noite", type: "water", attack: 12, defense: 222
,height: 21 })
Inserted 1 record(s) in 1ms
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.insert({name: "Vaporeon", description: "Sinistros de dia e de noite", type: "rock", attack: 356, defense:
                                                         db.pokemons.insert({name: "Vaporeon", description: "Sinistros de dia e de noite", type: "rock", attack: 356, defense:
250,height: 21})
Inserted 1 record(s) in 1ms
```


## Passo 5

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.find()
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
{
  "_id": ObjectId("56bb39d084277bd0550d32c3"),
  "name": "Vaporeon",
  "description": "Sinistros de dia e de noite",
  "type": "rock",
  "attack": 356,
  "defense": 250,
  "height": 21
}
Fetched 5 record(s) in 12ms
```

## Passo 6

```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var query = {name: "Vaporeon"}
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> var poke = db.pokemons.findOne(query)
```

## Passo 7
```
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> poke.description = "Nova Description"
Nova Description
vagrant-ubuntu-trusty-64(mongod-2.4.9) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
```
