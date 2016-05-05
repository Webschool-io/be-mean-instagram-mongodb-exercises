# MongoDB - Aula 02 - Exercício
autor: Ederson Devaldo da Silva

## Criando Database

```
codevops(mongod-3.0.6) test> use be-mean-pokemons
switched to db be-mean-pokemons

```
## Listagem das databases (passo 2)

```
codevops(mongod-3.0.6) be-mean-pokemons> show dbs
be-mean-instagram → 0.078GB
be-mean           → 0.078GB
local             → 0.078GB
```

## Listagem das coleções (passo 3)

```
codevops(mongod-3.0.6) be-mean-pokemons> show collections
```

## Cadastro dos pokemons (passo 4)

```
codevops(mongod-3.0.6) be-mean-pokemons> var metapod = {'name':'Metapod','description':'The shell covering this Pokémons body is as hard as an iron slab.Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.','type':'Bug','attack':10,'defense':30,'height':0.7}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.insert(metapod)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})
```

```
codevops(mongod-3.0.6) be-mean-pokemons> var nidorino = {'name':'Nidorino','description':'Nidorino has a horn that is harder than a diamond. If it senses a hostile presence, all the barbs on its back bristle up at once, and it challenges the foe with all its might.','type':'Poison','attack':40,'defense': 30,'height':0.9}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.insert(nidorino)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
```

```
codevops(mongod-3.0.6) be-mean-pokemons> var golduck = {'name':'Golduck','description':'The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. This Pokémon is definitely much faster than even the most athletic swimmer.','type':'Water','attack':40,'defense': 30,'height':1.7}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.insert(golduck)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

```
codevops(mongod-3.0.6) be-mean-pokemons> var primeape = {'name':'Primeape','description':'When Primeape becomes furious, its blood circulation is boosted. In turn, its muscles are made even stronger. However, it also becomes much less intelligent at the same time.','type':'Fighting','attack':50,'defense':30,'height':1.0}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.insert(primeape)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```

```
codevops(mongod-3.0.6) be-mean-pokemons> var arcanine = {'name':'Arcanine','description':'Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. The fire that blazes wildly within this Pokémons body is its source of power.','type':'Fire','attack':60,'defense':40,'height':1.9}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.insert(arcanine)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})
```

```
codevops(mongod-3.0.6) be-mean-pokemons> var pikachu = {'name':'Pikachu','description':'Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.','type':'Eletric','attack':30,'defense':20,'height':0.4}
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.insert(pikachu)
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})
```
## Lista dos pokemons (passo 5)

```
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("566219f4f3045dd41d6869d2"),
  "name": "Metapod",
  "description": "The shell covering this Pokémons body is as hard as an iron slab.Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell.",
  "type": "Bug",
  "attack": 10,
  "defense": 30,
  "height": 0.7
}
{
  "_id": ObjectId("56621a69f3045dd41d6869d3"),
  "name": "Nidorino",
  "description": "Nidorino has a horn that is harder than a diamond. If it senses a hostile presence, all the barbs on its back bristle up at once, and it challenges the foe with all its might.",
  "type": "Poison",
  "attack": 40,
  "defense": 30,
  "height": 0.9
}
{
  "_id": ObjectId("56621b2cf3045dd41d6869d4"),
  "name": "Golduck",
  "description": "The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. This Pokémon is definitely much faster than even the most athletic swimmer.",
  "type": "Water",
  "attack": 40,
  "defense": 30,
  "height": 1.7
}
{
  "_id": ObjectId("56621bd9f3045dd41d6869d5"),
  "name": "Primeape",
  "description": "When Primeape becomes furious, its blood circulation is boosted. In turn, its muscles are made even stronger. However, it also becomes much less intelligent at the same time.",
  "type": "Fighting",
  "attack": 50,
  "defense": 30,
  "height": 1
}
{
  "_id": ObjectId("56621cbcf3045dd41d6869d6"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. The fire that blazes wildly within this Pokémons body is its source of power.",
  "type": "Fire",
  "attack": 60,
  "defense": 40,
  "height": 1.9
}

  "_id": ObjectId("56623dd5f3045dd41d6869d7"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 6 record(s) in 5ms
```

## Pikachu (passo 6)

```
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.find({name:'Pikachu'})
{
  "_id": ObjectId("56623dd5f3045dd41d6869d7"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "type": "Eletric",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
codevops(mongod-3.0.6) be-mean-pokemons> var poke = db.pokemons.find({name:'Pikachu'})
``

## Atualização do Pikachu (passo 6)
```
codevops(mongod-3.0.6) be-mean-pokemons> poke.description = 'Bicho muito loko'
Bicho muito loko
codevops(mongod-3.0.6) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

