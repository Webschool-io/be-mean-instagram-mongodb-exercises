# MongoDB - Aula 02 - Exercício
autor: Rodrigo Alviani

## Crie uma database chamada be-mean-pokemons;
```
WMD00096(mongod-3.0.7) be-mean> use be-mean-pokemons;
switched to db be-mean-pokemons
```

## Liste quais databases você possui nesse servidor;
```
WMD00096(mongod-3.0.7) be-mean-pokemons> show databases;
be-mean     0.078GB
local       0.078GB
test        0.078GB
```

## Liste quais coleções você possui nessa database;
```
WMD00096(mongod-3.0.7) be-mean-pokemons> show collections;
WMD00096(mongod-3.0.7) be-mean-pokemons>
```

## Insira pelo menos 5 pokemons **A SUA ESCOLHA** utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height;
```
WMD00096(mongod-3.0.7) be-mean-pokemons> var pokemons = [
{name: "Bulbasaur", description: "The seed on its back is filled with nutrients. The seed grows steadily larger as its body grows.", attack: 49, defense: 49, height: 0.7, type: "Grass"},
{name: "Charmander", description: "Obviously prefers hot places. When it rains, steam is said to spout from the tip of its tail.", attack: 52, defense: 43, height: 0.6, type: "Fire"},
{name: "Squirtle", description: "After birth, its back swells and hardens into a shell. Powerfully sprays foam from its mouth.", attack: 48, defense: 65, height: 0.5, type: "Water"},
{name: "Caterpie", description: "For protection, it releases a horrible stench from the antennae on its head to drive away enemies.", attack: 30, defense: 35, height: 0.3, type: "Bug"},
{name: "Pikachu", description: "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose.", attack: 55, defense: 40, height: 0.4, type: "Eletric"}
];

WMD00096(mongod-3.0.7) be-mean-pokemons> db.pokemons.insert(pokemons);
Inserted 1 record(s) in 1823ms
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

## Liste os pokemons existentes na sua coleção;
```
WMD00096(mongod-3.0.7) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("564a330af3878aca0716bc9f"),
  "name": "Bulbasaur",
  "description": "The seed on its back is filled with nutrients. The seed grows steadily larger as its body grows.",
  "attack": 49,
  "defense": 49,
  "height": 0.7,
  "type": "Grass"
}
{
  "_id": ObjectId("564a330af3878aca0716bca0"),
  "name": "Charmander",
  "description": "Obviously prefers hot places. When it rains, steam is said to spout from the tip of its tail.",
  "attack": 52,
  "defense": 43,
  "height": 0.6,
  "type": "Fire"
}
{
  "_id": ObjectId("564a330af3878aca0716bca1"),
  "name": "Squirtle",
  "description": "After birth, its back swells and hardens into a shell. Powerfully sprays foam from its mouth.",
  "attack": 48,
  "defense": 65,
  "height": 0.5,
  "type": "Water"
}
{
  "_id": ObjectId("564a330af3878aca0716bca2"),
  "name": "Caterpie",
  "description": "For protection, it releases a horrible stench from the antennae on its head to drive away enemies.",
  "attack": 30,
  "defense": 35,
  "height": 0.3,
  "type": "Bug"
}
{
  "_id": ObjectId("564a330af3878aca0716bca3"),
  "name": "Pikachu",
  "description": "It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose. (Version 2)",
  "attack": 55,
  "defense": 40,
  "height": 0.4,
  "type": "Eletric"
}
Fetched 5 record(s) in 66ms
```

## Busque um pokemon a sua escolha, que acabou de ser inserido, e armazene-o em uma variável chamada `poke`;
```
WMD00096(mongod-3.0.7) be-mean-pokemons> var poke = db.pokemons.findOne({name: 'Pikachu'});
```

## Modifique sua `description` e salvê-o
```
WMD00096(mongod-3.0.7) be-mean-pokemons> poke.description = 'It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose. (Version 2)';
It raises its tail to check its sur roundings. The tail is sometimes struck by light ning in this pose. (Version 2)
WMD00096(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke);
Updated 1 existing record(s) in 60ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```
