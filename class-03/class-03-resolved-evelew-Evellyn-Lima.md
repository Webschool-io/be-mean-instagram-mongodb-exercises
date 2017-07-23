


# MongoDB - Aula 03 - Exercício
autor: EVELLYN LIMA

## 1. Liste todos os Pokemons com a altura menor que 0.5
```
> var query = {height: {$lt: 0.5}}
> db.pokemons.find(query)
{
        "_id" : ObjectId("58436949841326e66ea9ebb5"),
        "name" : "Rattata",
        "description" : "Rato nervoso e tem em todo lugar",
        "type" : "normal",
        "attack" : 103,
        "height" : 0.3
}
{
        "_id" : ObjectId("584369a2841326e66ea9ebb6"),
        "name" : "Meowth",
        "description" : "Gato doido",
        "type" : "normal",
        "attack" : 92,
        "height" : 0.4
}
{
        "_id" : ObjectId("584c5db792b43802cf89585a"),
        "name" : "Pikachu",
        "description" : "Tato elétrico bem fofinho",
        "type" : "electic",
        "attack" : 55,
        "height" : 0.4
}
{
        "_id" : ObjectId("584c5db792b43802cf89585b"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4
}
{
        "_id" : ObjectId("584c5db792b43802cf89585e"),
        "name" : "Caterpie",
        "description" : "Larva lindinha",
        "type" : "inseto",
        "attack" : 30,
        "height" : 0.3
}
```

## 2. Liste todos os Pokemons com a altura maior ou igual a 0.5
```
> var query = {height: {$gte: 0.5}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("584368e4841326e66ea9ebb4"),
        "name" : "Charizard",
        "description" : "Dragão muito doido que cospe fogo",
        "type" : "fogo",
        "attack" : 223,
        "height" : 1.7
}
{
        "_id" : ObjectId("584369f0841326e66ea9ebb7"),
        "name" : "Psyduck",
        "description" : "Pato fofo doido da porra",
        "type" : "água",
        "attack" : 122,
        "height" : 0.8
}
{
        "_id" : ObjectId("58436a48841326e66ea9ebb8"),
        "name" : "Nidorina",
        "description" : "Muito fofo com cara de bravinho *-*",
        "type" : "mistico",
        "attack" : 117,
        "height" : 0.8
}
{
        "_id" : ObjectId("584c5db792b43802cf89585c"),
        "name" : "Charmander",
        "description" : "Esse é o cçao chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6
}
{
        "_id" : ObjectId("584c5db792b43802cf89585f"),
        "name" : "Magby",
        "description" : "Um pato que cospe fogo",
        "type" : "fogo",
        "attack" : 35,
        "height" : 0.7
}
{
        "_id" : ObjectId("584c5db792b43802cf895860"),
        "name" : "Treecko",
        "description" : "Largarto marento estiloso",
        "type" : "grama",
        "attack" : 30,
        "height" : 0.5
}
{
        "_id" : ObjectId("584c5db792b43802cf895861"),
        "name" : "Elgyem",
        "description" : "Lagarto marrentão",
        "type" : "psiquica",
        "attack" : 35,
        "height" : 0.5
}
```

## 3. Liste todos os Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
> var query = {$and: [ {height: {$lte: 0.5}}, {type: 'grama'} ]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("584c5db792b43802cf89585b"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4
}
{
        "_id" : ObjectId("584c5db792b43802cf895860"),
        "name" : "Treecko",
        "description" : "Largarto marento estiloso",
        "type" : "grama",
        "attack" : 30,
        "height" : 0.5
}
```

## 4. Liste todos os Pokemons com o nome `Pikachu` OU com attack menor ou igual que 0.5
```
> var query = {$or: [ {name: "Pikachu"}, {attack: { $lte:0.5 } } ]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("584c5db792b43802cf89585a"),
        "name" : "Pikachu",
        "description" : "Tato elétrico bem fofinho",
        "type" : "electic",
        "attack" : 55,
        "height" : 0.4
}
```

## 5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5
```
> var query = {$and: [ {attack: {$gte: 48}}, { height: {$lte: 0.5} } ]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("58436949841326e66ea9ebb5"),
        "name" : "Rattata",
        "description" : "Rato nervoso e tem em todo lugar",
        "type" : "normal",
        "attack" : 103,
        "height" : 0.3
}
{
        "_id" : ObjectId("584369a2841326e66ea9ebb6"),
        "name" : "Meowth",
        "description" : "Gato doido",
        "type" : "normal",
        "attack" : 92,
        "height" : 0.4
}
{
        "_id" : ObjectId("584c5db792b43802cf89585a"),
        "name" : "Pikachu",
        "description" : "Tato elétrico bem fofinho",
        "type" : "electic",
        "attack" : 55,
        "height" : 0.4
}
{
        "_id" : ObjectId("584c5db792b43802cf89585b"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4
}
```