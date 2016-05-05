###MongoDB - Aula 02 - Exercício
Autor: Thiago de Carvalho

##Criando database
```
megazord(mongod-3.2.3) test> use be-mean-pokemon
switched to db be-mean-pokemon
```

##Listando databases
```
megazord(mongod-3.2.3) be-mean-pokemon> show dbs
BancoDeTestes     → 0.000GB
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
local             → 0.000GB
```

##Listando collections
```
megazord(mongod-3.2.3) be-mean-pokemon> show collections
```

##Cadastro de pokemons
```
megazord(mongod-3.2.3) be-mean-pokemon> var pokemons = [{'name':'Pikachu','description':'Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.',attack: 100, defense: 60, height: 0.4},{'name':'Rattata','description':'Rattata is cautious in the extreme. Even while it is asleep, it constantly listens by moving its ears around. It is not picky about where it lives—it will make its nest anywhere.',attack: 90, defense: 70, height: 0.3},{'name':'Gloom','description':'Gloom releases a foul fragrance from the pistil of its flower. When faced with danger, the stench worsens. If this Pokémon is feeling calm and secure, it does not release its usual stinky aroma.',attack: 80, defense: 80, height: 0.8},{'name':'Mewtwo','description':'Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémons body, they failed to endow Mewtwo with a compassionate heart.',attack: 70, defense: 90, height: 2.0},{'name':'Gyrados','description':'When Magikarp evolves into Gyarados, its brain cells undergo a structural transformation. It is said that this transformation is to blame for this Pokémons wildly violent nature.',attack: 60, defense: 100, height: 6.5}]
megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.insert(pokemons)
Inserted 1 record(s) in 29ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

##Lista dos pokemons
```
megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.find()
{
  "_id": ObjectId("56d5dc488904f06b371889c1"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 100,
  "defense": 60,
  "height": 0.4
}
{
  "_id": ObjectId("56d5dc488904f06b371889c2"),
  "name": "Rattata",
  "description": "Rattata is cautious in the extreme. Even while it is asleep, it constantly listens by moving its ears around. It is not picky about where it lives—it will make its nest anywhere.",
  "attack": 90,
  "defense": 70,
  "height": 0.3
}
{
  "_id": ObjectId("56d5dc488904f06b371889c3"),
  "name": "Gloom",
  "description": "Gloom releases a foul fragrance from the pistil of its flower. When faced with danger, the stench worsens. If this Pokémon is feeling calm and secure, it does not release its usual stinky aroma.",
  "attack": 80,
  "defense": 80,
  "height": 0.8
}
{
  "_id": ObjectId("56d5dc488904f06b371889c4"),
  "name": "Mewtwo",
  "description": "Mewtwo is a Pokémon that was created by genetic manipulation. However, even though the scientific power of humans created this Pokémons body, they failed to endow Mewtwo with a compassionate heart.",
  "attack": 70,
  "defense": 90,
  "height": 2
}
{
  "_id": ObjectId("56d5dc488904f06b371889c5"),
  "name": "Gyrados",
  "description": "When Magikarp evolves into Gyarados, its brain cells undergo a structural transformation. It is said that this transformation is to blame for this Pokémons wildly violent nature.",
  "attack": 60,
  "defense": 100,
  "height": 6.5
}
Fetched 5 record(s) in 8ms
```

##Buscar pokemon e armazenar em uma variavel
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {name:'Pikachu'};
megazord(mongod-3.2.3) be-mean-pokemon> var poke = db.pokemons.findOne(query);
megazord(mongod-3.2.3) be-mean-pokemon> poke
{
  "_id": ObjectId("56d5dc488904f06b371889c1"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its evidence that this Pokémon mistook the intensity of its charge.",
  "attack": 100,
  "defense": 60,
  "height": 0.4
}
Fetched 1 record(s) in 10ms
```

##Atualização do Pokemon
```
megazord(mongod-3.2.3) be-mean-pokemon> var query = {name:'Pikachu'};
megazord(mongod-3.2.3) be-mean-pokemon> var poke = db.pokemons.findOne(query);
megazord(mongod-3.2.3) be-mean-pokemon> poke.description = "Rato que dá choque em geral";
Rato que dá choque em geral
megazord(mongod-3.2.3) be-mean-pokemon> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
