# MongoDB - Aula 03 - Exercício
> Autor: Nil Késede

## Pokemons com a altura menor que `5`
```js
> var query = { height: { $lt: 5 } }
> db.pokemons.find(query)
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f70"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 4
}
Fetched 1 record(s) in 1ms
```

## Pokemons com altura maior ou igual `5`
```js
> var query = { height: { $gte: 5 } }
> db.pokemons.find(query)
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f6d"),
  "name": "Bulbasaur",
  "description": "Pokemon fofinho que solta umas folha envenenada",
  "type": "Grama",
  "atack": 49,
  "defense": 49,
  "height": 7
}
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f6e"),
  "name": "Charizard",
  "description": "Dragão boladão",
  "type": "Fogo",
  "attack": 84,
  "defense": 78,
  "height": 17
}
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f6f"),
  "name": "Blastoise",
  "description": "Tem uns canhão de água nas costas foda pra carai",
  "type": "Água",
  "attack": 83,
  "defense": 100,
  "height": 16
}
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f71"),
  "name": "Snorlax",
  "description": "Pokemon dorminhoco",
  "type": "Normal",
  "attack": 110,
  "defense": 65,
  "height": 21
}
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f72"),
  "name": "Psyduck",
  "description": "Pato loko de droga",
  "type": "Água",
  "attack": 52,
  "defense": 48,
  "height": 8
}
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f73"),
  "name": "Onix",
  "description": "Cobra de pedra gigante",
  "type": "Água",
  "attack": 45,
  "defense": 160,
  "height": 88
}
Fetched 6 record(s) in 4ms
```

## Pokemons com altura menor ou igual a `50` do tipo `Grama`
```js
> var query = {
  $and:[
    { height:{ $lte: 50 } },
    { type: /grama/i }
  ]
}
> db.pokemons.find(query)
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f6d"),
  "name": "Bulbasaur",
  "description": "Pokemon fofinho que solta umas folha envenenada",
  "type": "Grama",
  "atack": 49,
  "defense": 49,
  "height": 7
}
Fetched 1 record(s) in 1ms
```

## Pokemons com o nome `Pikachu` ou com ataque menor ou igual que `5`
```js
> var query = {
  $or:[
      { name: /pikachu/i },
      { attack:{ $lte: 5 } }
    ]
}
> db.pokemons.find(query)
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f70"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 4
}
Fetched 1 record(s) in 1ms
```

## Pokemons com o ataque maior ou igual que `48` e com altura menor ou igual que `5`
```js
> var query = {
  $and:[
      { attack:{ $gte: 48 } },
      { height:{ $lte: 5 } }
    ]
}
> db.pokemons.find(query)
{
  "_id": ObjectId("56d7453a3482d57fcc5c1f70"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 4
}
Fetched 1 record(s) in 1ms
```
