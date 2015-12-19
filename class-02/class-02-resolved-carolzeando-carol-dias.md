# MongoDB - Aula 02 - Exercício
autor: Carol Dias

## Crie a database be-mean-pokemons

```
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons

```

## Listagem das databases (passo 2)

```
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB

```

## Listagem das coleções (passo 3)

```
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> show collections

```

## Cadastro dos pokemons (passo 4)

```
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({name: 'Eevee', description:'Raposa coelho', attack:55, defense:0, height:1.0})
Inserted 1 record(s) in 129ms
WriteResult({
  "nInserted": 1
})

vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({name: 'Vaporeon', description:'Raposa coelho da água', attack:65, defense:60, height:3.03})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({name: 'Jolteon', description:'Raposa coelho elétrica', attack:65, height:2.07})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({name: 'Flareon', description:'Raposa coelho de fogo', attack:130, defense: 60, height:2.11})
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({name: 'Umbreon', description:'Raposa coelho trevosa', attack:65, defense:110, height:3.03})
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

```

## Lista dos pokemons (passo 5)

```
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564a758879bb040edf39e99a"),
  "name": "Eevee",
  "description": "Raposa coelho",
  "attack": 55,
  "defense": 0,
  "height": 1
}
{
  "_id": ObjectId("564a759679bb040edf39e99b"),
  "name": "Vaporeon",
  "description": "Raposa coelho da água",
  "attack": 65,
  "defense": 60,
  "height": 3.03
}
{
  "_id": ObjectId("564a75a579bb040edf39e99c"),
  "name": "Jolteon",
  "description": "Raposa coelho elétrica",
  "attack": 65,
  "height": 2.07
}
{
  "_id": ObjectId("564a75b379bb040edf39e99d"),
  "name": "Flareon",
  "description": "Raposa coelho de fogo",
  "attack": 130,
  "defense": 60,
  "height": 2.11
}
{
  "_id": ObjectId("564a75c579bb040edf39e99e"),
  "name": "Umbreon",
  "description": "Raposa coelho trevosa",
  "attack": 65,
  "defense": 110,
  "height": 3.03
}
Fetched 5 record(s) in 2ms

```

## Eevee (passo 6)

```
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne({name:'Eevee'})

```

## Atualização do Eevee (passo 6)

```
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> poke.description = 'Raposa coelho indefesa'
Raposa coelho indefesa
vagrant-ubuntu-trusty-64(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```