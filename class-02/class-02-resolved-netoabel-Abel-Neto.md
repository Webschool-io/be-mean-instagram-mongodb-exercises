# MongoDB - Aula 02 - Exercício
User: [netoabel](http://www.github.com/netoabel)

Autor: Abel Neto

## Criando uma database chamada be-mean-pokemons

```
be-mean> use be-mean-pokemons
switched to db be-mean-pokemons
```

## Listando as databases

```
be-mean-pokemons> show dbs
local            → 0.078GB
```

## Listando as collections

```
be-mean-pokemons> show collections
```

## Inserindo cinco pokémons

```
be-mean-pokemons> var pokemons = [
                                  { name: "Bulbassaur", description: "Um sapo com folhas", attack: 30, defense: 20, height: 0.4, type: 'grass' },
                                  { name: "Ivysaur", description: "Um sapo com uma flor", attack: 30, defense: 30, height: 1, type: 'grass' },
                                  { name: "Venusaur", description: "Um sapo com um coqueiro", attack: 40, defense: 40, height: 2, type: 'grass' },
                                  { name: "Charmander", description: "Um filhote de dinossauro com o rabo pegando fogo", attack: 30, defense: 20, height: 0.6, type: 'fire' },
                                  { name: "Charmeleon", description: "Um pterodáctilo sem asas com o rabo pegando fogo", attack: 30, defense: 30, height: 1, type: 'fire' }
                                ];
be-mean-pokemons> db.pokemons.save(pokemons)
Inserted 1 record(s) in 264ms
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

## Listando os pokémons

```
be-mean-pokemons>db.pokemons.find()
{
  "_id": ObjectId("572d05603e77fb046dc9bcd0"),
  "name": "Bulbassaur",
  "description": "Um sapo com folhas",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "grass"
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd1"),
  "name": "Ivysaur",
  "description": "Um sapo com uma flor",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "type": "grass"
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd2"),
  "name": "Venusaur",
  "description": "Um sapo com um coqueiro",
  "attack": 40,
  "defense": 40,
  "height": 2,
  "type": "grass"
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd3"),
  "name": "Charmander",
  "description": "Um filhote de dinossauro com o rabo pegando fogo",
  "attack": 30,
  "defense": 20,
  "height": 0.6,
  "type": "fire"
}
{
  "_id": ObjectId("572d05603e77fb046dc9bcd4"),
  "name": "Charmeleon",
  "description": "Um pterodáctilo sem asas com o rabo pegando fogo",
  "attack": 30,
  "defense": 30,
  "height": 1,
  "type": "fire"
}
Fetched 5 record(s) in 7ms
```

## Buscando um pokémon pelo nome e atualizando a descrição dele

```
be-mean-pokemons> var poke = db.pokemons.findOne({name:'Ivysaur'})
be-mean-pokemons> poke.description = 'Um sapo com uma bromélia'
Um sapo com uma bromélia
be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 17ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
