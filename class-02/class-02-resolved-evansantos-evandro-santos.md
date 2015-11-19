# MongoDB - Aula 02 - Exercício
autor: Evandro Santos


##Criar database

```

Evandros-Mini(mongod-3.0.7) be-mean-instagram> use be-mean-pokemons
switched to db be-mean-pokemons

```

##Listar databases

```

Evandros-Mini(mongod-3.0.7) be-mean-pokemons> show databases
be-mean-instagram  0.078GB
be-mean            0.078GB
local              0.078GB

```

##Listar coleções

```

Evandros-Mini(mongod-3.0.7) be-mean-pokemons> show collections
Evandros-Mini(mongod-3.0.7) be-mean-pokemons>

```

##Inserir pelo menos 5 pokemons

```
db.pokemons.insert({'name': 'Mr. Mime', 'description': 'If interrupted while it is miming, it will slap around the offender with its broad hands.', 'attack': 45, 'defense': 65, 'height': 4.3})
Inserted 1 record(s) in 1491ms
WriteResult({
  "nInserted": 1
})

Evandros-Mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name': 'Porygon','description': 'A POKéMON that consists entirely of programming code. Capable of moving freely in cyberspace.', 'attack': 60, defense: '70', 'height': 2.7})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Evandros-Mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name': 'Tangela','description': 'The whole body is swathed with wide vines that are similar to seaweed. Its vines shake as it walks.', 'attack': 55, 'defense': 115, 'height': 3.3})
Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

Evandros-Mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name': 'Mr. Mime', 'description': 'If interrupted while it is miming, it will slap around the offender with its broad hands.', 'attack': 45, 'defense': 65, 'height': 4.3})
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

Evandros-Mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert({'name': 'Ditto', 'description': 'Capable of copying an enemy\'s genetic code to instantly transform itself into a duplicate of the enemy.', 'attack': 48, 'defense': 48, 'height': 1})
Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

```

##Listar pokemons existentes

```
Evandros-Mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("564936377b6c3094d7d697ee"),
  "name": "Snorlax",
  "description": "Very lazy. Just eats and sleeps. As its rotund bulk builds, it becomes steadily more slothful.",
  "attack": 110,
  "defense": "65",
  "height": 6.11
}
{
  "_id": ObjectId("564936387b6c3094d7d697ef"),
  "name": "Porygon",
  "description": "A POKéMON that consists entirely of programming code. Capable of moving freely in cyberspace.",
  "attack": 60,
  "defense": "70",
  "height": 2.7
}
{
  "_id": ObjectId("564936387b6c3094d7d697f0"),
  "name": "Tangela",
  "description": "The whole body is swathed with wide vines that are similar to seaweed. Its vines shake as it walks.",
  "attack": 55,
  "defense": 115,
  "height": 3.3
}
{
  "_id": ObjectId("564936387b6c3094d7d697f1"),
  "name": "Mr. Mime",
  "description": "If interrupted while it is miming, it will slap around the offender with its broad hands.",
  "attack": 45,
  "defense": 65,
  "height": 4.3
}
{
  "_id": ObjectId("564936fe7b6c3094d7d697f2"),
  "name": "Ditto",
  "description": "Capable of copying an enemy's genetic code to instantly transform itself into a duplicate of the enemy.",
  "attack": 48,
  "defense": 48,
  "height": 1
}
Fetched 5 record(s) in 3ms
```
##Selecionar pokemon pelo nome e armazenar na variavel poke
```
Evandros-Mini(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne({name: 'Ditto'});
Evandros-Mini(mongod-3.0.7) be-mean-pokemons> poke
{
  "_id": ObjectId("564936fe7b6c3094d7d697f2"),
  "name": "Ditto",
  "description": "Capable of copying an enemy's genetic code to instantly transform itself into a duplicate of the enemy.",
  "attack": 48,
  "defense": 48,
  "height": 1
}

```
##Modificar o campo description e salvar
```
Evandros-Mini(mongod-3.0.7) be-mean-pokemons> poke.description = 'It can freely recombine its own cellular structure to transform into other life-forms.';
It can freely recombine its own cellular structure to transform into other life-forms.
Evandros-Mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
Evandros-Mini(mongod-3.0.7) be-mean-pokemons> db.pokemons.findOne({name: 'Ditto'});
{
  "_id": ObjectId("564936fe7b6c3094d7d697f2"),
  "name": "Ditto",
  "description": "It can freely recombine its own cellular structure to transform into other life-forms.",
  "attack": 48,
  "defense": 48,
  "height": 1
}
```
