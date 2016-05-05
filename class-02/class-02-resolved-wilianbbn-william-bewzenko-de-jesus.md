###MongoDB - Aula 02 - Exercício
Autor: William Bewzenko de Jesus

##Criando database
```
> use be-mean-pokemons
switched to db be-mean-pokemons
```

##Listando databases
```
> show dbs
be-mean           → 0.004GB
be-mean-instagram → 0.000GB
local             → 0.000GB
```

##Listando collections
```
> show collections
```

##Cadastro dos pokemons
```
> var pokes = 
[
  {
    "name": "Hoopa",
    "description": "In its true form, it possesses a huge amount of power. Legends of its avarice tell how it once carried off an entire castle to gain the treasure hidden within.",
    "type": "ghost",
    "attack": 60,
    "height": 0.5,
    "defense": 30
  },
  {
    "name": "Diancie",
    "description": "A sudden transformation of Carbink, its pink, glimmering body is said to be the loveliest sight in the whole world.",
    "type": "fairy",
    "attack": 50,
    "height": 0.7,
    "defense": 60
  },
  {
    "name": "Zygarde",
    "description": "When the Kalos region's ecosystem falls into disarray, it appears and reveals its secret power.",
    "type": "ground",
    "attack": 50,
    "height": 5,
    "defense": 50
  },
  {
    "name": "Yveltal",
    "description": "When this legendary Pokémon's wings and tail feathers spread wide and glow red, it absorbs the life force of living creatures.",
    "type": "flying",
    "attack": 70,
    "height": 5.8,
    "defense": 40
  },
  {
    "name": "Xerneas",
    "description": "Legends say it can share eternal life. It slept for a thousand years in the form of a tree before its revival.",
    "type": "fairy",
    "attack": 70,
    "height": 3,
    "defense": 40
  },
  {
    "name": "Noivern",
    "description": "They fly around on moonless nights and attack careless prey. Nothing can beat them in a battle in the dark.",
    "type": "flying",
    "attack": 40,
    "height": 1.5,
    "defense": 40
  },
  {
    "name": "Avalugg",
    "description": "Its ice-covered body is as hard as steel. Its cumbersome frame crushes anything that stands in its way.",
    "type": "ice",
    "attack": 60,
    "height": 2,
    "defense": 80
  }
]
> db.pokemons.save(pokes)
Inserted 1 record(s) in 228ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 7,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
```

##Lista de todos os pokemons
```
> db.pokemons.find()
{
  "_id": ObjectId("568b0578e5c2ef5322619bb2"),
  "name": "Hoopa",
  "description": "In its true form, it possesses a huge amount of power. Legends of its avarice tell how it once carried off an entire castle to gain the treasure hidden within.",
  "type": "ghost",
  "attack": 60,
  "height": 0.5,
  "defense": 30
}
{
  "_id": ObjectId("568b0578e5c2ef5322619bb3"),
  "name": "Diancie",
  "description": "A sudden transformation of Carbink, its pink, glimmering body is said to be the loveliest sight in the whole world.",
  "type": "fairy",
  "attack": 50,
  "height": 0.7,
  "defense": 60
}
{
  "_id": ObjectId("568b0578e5c2ef5322619bb4"),
  "name": "Zygarde",
  "description": "When the Kalos region's ecosystem falls into disarray, it appears and reveals its secret power.",
  "type": "ground",
  "attack": 50,
  "height": 5,
  "defense": 50
}
{
  "_id": ObjectId("568b0578e5c2ef5322619bb5"),
  "name": "Yveltal",
  "description": "When this legendary Pokémon's wings and tail feathers spread wide and glow red, it absorbs the life force of living creatures.",
  "type": "flying",
  "attack": 70,
  "height": 5.8,
  "defense": 40
}
{
  "_id": ObjectId("568b0578e5c2ef5322619bb6"),
  "name": "Xerneas",
  "description": "Legends say it can share eternal life. It slept for a thousand years in the form of a tree before its revival.",
  "type": "fairy",
  "attack": 70,
  "height": 3,
  "defense": 40
}
{
  "_id": ObjectId("568b0578e5c2ef5322619bb7"),
  "name": "Noivern",
  "description": "They fly around on moonless nights and attack careless prey. Nothing can beat them in a battle in the dark.",
  "type": "flying",
  "attack": 40,
  "height": 1.5,
  "defense": 40
}
{
  "_id": ObjectId("568b0578e5c2ef5322619bb8"),
  "name": "Avalugg",
  "description": "Its ice-covered body is as hard as steel. Its cumbersome frame crushes anything that stands in its way.",
  "type": "ice",
  "attack": 60,
  "height": 2,
  "defense": 80
}
Fetched 7 record(s) in 4ms
```

##Query para buscar o pokemon
```
> var query = {name: 'Xerneas'}
> var poke = db.pokemons.findOne(query)
> poke
{
  "_id": ObjectId("568b0578e5c2ef5322619bb6"),
  "name": "Xerneas",
  "description": "Legends say it can share eternal life. It slept for a thousand years in the form of a tree before its revival.",
  "type": "fairy",
  "attack": 70,
  "height": 3,
  "defense": 40
}
```

##Atualizando a descrição do Pokemon
```
> var query = {name: 'Xerneas'}
> var poke = db.pokemons.findOne(query)
> poke
{
  "_id": ObjectId("568b0578e5c2ef5322619bb6"),
  "name": "Xerneas",
  "description": "Legends say it can share eternal life. It slept for a thousand years in the form of a tree before its revival.",
  "type": "fairy",
  "attack": 70,
  "height": 3,
  "defense": 40
}
> poke.description = "When the horns on its head shine in seven colors, it is said to be sharing everlasting life."
When the horns on its head shine in seven colors, it is said to be sharing everlasting life.
> db.pokemons.save(poke)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
