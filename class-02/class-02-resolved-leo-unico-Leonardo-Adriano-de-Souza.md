# MongoDB - Aula 02 - Exercício
autor: Leonardo Adriano de Souza

## Cria a database (passo 1)
```
wall-e(mongod-3.2.0) local> use be-mean-pokemons
switched to db be-mean-pokemons
```
## Listagem das databases (passo 2)
```
wall-e(mongod-3.2.0) be-mean-pokemons> show dbs
be-mean          → 0.004GB
be-mean-pokemons → 0.000GB
local            → 0.000GB
```

## Listagem das coleções (passo 3)
```
wall-e(mongod-3.2.0) be-mean-pokemons> show collections
pokemons → 0.000MB / 0.004MB
```

## Cadastro dos pokemons (passo 4)
```
wall-e(mongod-3.2.0) be-mean-pokemons> var pokemons = [
  {name:"Porygon",description:"Porygon is capable of reverting itself entirely back to program data and entering cyberspace. This Pokémon is copy protected so it cannot be duplicated by copying",attack: 60,defense:   70,height: 8},
  {name:"Jigglypuff",description: "Jigglypuff's vocal cords can freely adjust the wavelength of its voice. This Pokémon uses this ability to sing at precisely the right wavelength to make its foes most drowsy",attack: 2,defense: 1,height: 0.5},
  {name:"Pikachu",description:"Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge",attack:55,defense: 30,height:4},
  {name:"Serperior",description: "It only gives its all against strong opponents who are not fazed by the glare from Serperior's noble eyes",attack: 40,defense: 40,heigth: 3.30},
  {name:"Metapod",description: "The shell covering this Pokémon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell",attack: 20, defense: 55 ,height : 0.7},
  {name:"Lickitung",description: "Whenever Lickitung comes across something new, it will unfailingly give it a lick. It does so because it memorizes things by texture and by taste. It is somewhat put off by sour things",attack: 30,defense: 30,height: 1.2}
 ]
wall-e(mongod-3.2.0) be-mean-pokemons> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 4ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 6,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})

```

## Lista dos pokemons (passo 5)
```
wall-e(mongod-3.2.0) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("569329fd59bb339b1dc7f0e0"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("56932dc359bb339b1dc7f0e1"),
  "name": "Porygon",
  "description": "Porygon is capable of reverting itself entirely back to program data and entering cyberspace. This Pokémon is copy protected so it cannot be duplicated by copying",
  "attack": 60,
  "defense": 70,
  "height": 8
}
{
  "_id": ObjectId("56932dc359bb339b1dc7f0e2"),
  "name": "Jigglypuff",
  "description": "Jigglypuff's vocal cords can freely adjust the wavelength of its voice. This Pokémon uses this ability to sing at precisely the right wavelength to make its foes most drowsy",
  "attack": 2,
  "defense": 1,
  "height": 0.5
}
{
  "_id": ObjectId("56932dc359bb339b1dc7f0e3"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge",
  "attack": 55,
  "defense": 30,
  "height": 4
}
{
  "_id": ObjectId("56932dc359bb339b1dc7f0e4"),
  "name": "Serperior",
  "description": "It only gives its all against strong opponents who are not fazed by the glare from Serperior's noble eyes",
  "attack": 40,
  "defense": 40,
  "heigth": 3.3
}
{
  "_id": ObjectId("56932dc359bb339b1dc7f0e5"),
  "name": "Metapod",
  "description": "The shell covering this Pokémon's body is as hard as an iron slab. Metapod does not move very much. It stays still because it is preparing its soft innards for evolution inside the hard shell",
  "attack": 20,
  "defense": 55,
  "height": 0.7
}
{
  "_id": ObjectId("56932dc359bb339b1dc7f0e6"),
  "name": "Lickitung",
  "description": "Whenever Lickitung comes across something new, it will unfailingly give it a lick. It does so because it memorizes things by texture and by taste. It is somewhat put off by sour things",
  "attack": 30,
  "defense": 30,
  "height": 1.2
}
Fetched 7 record(s) in 190ms
```

## Porygon (passo 6)
```
wall-e(mongod-3.2.0) be-mean-pokemons> var query = {name:'Porygon'}
wall-e(mongod-3.2.0) be-mean-pokemons> var poke = db.pokemons.findOne(query)
wall-e(mongod-3.2.0) be-mean-pokemons> poke
{
  "_id": ObjectId("56932dc359bb339b1dc7f0e1"),
  "name": "Porygon",
  "description": "Porygon is capable of reverting itself entirely back to program data and entering cyberspace. This Pokémon is copy protected so it cannot be duplicated by copying",
  "attack": 60,
  "defense": 70,
  "height": 8
}
```

## Atualização do Porygon (passo 6)
```
wall-e(mongod-3.2.0) be-mean-pokemons> poke.attack = 100
100
wall-e(mongod-3.2.0) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 239ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
wall-e(mongod-3.2.0) be-mean-pokemons> var poke = db.pokemons.findOne(query)
wall-e(mongod-3.2.0) be-mean-pokemons> poke
{
  "_id": ObjectId("56932dc359bb339b1dc7f0e1"),
  "name": "Porygon",
  "description": "Porygon is capable of reverting itself entirely back to program data and entering cyberspace. This Pokémon is copy protected so it cannot be duplicated by copying",
  "attack": 100,
  "defense": 70,
  "height": 8
}
```
