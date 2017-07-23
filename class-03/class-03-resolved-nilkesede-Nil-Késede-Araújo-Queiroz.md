# MongoDB - Aula 03 - Exercício
> Autor: Nil Késede

## Pokemons com a altura menor que `0.5`

```
> db.pokemons.find({height:{$lt: 0.5}})
{
  "_id": ObjectId("5645b279b34d118a7fc6670f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5645b292b34d118a7fc66710"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 2 record(s) in 1ms
```

## Pokemons com altura maior ou igual `0.5`
```
> db.pokemons.find({height:{$gte: 0.5}})
{
  "_id": ObjectId("5645b2afb34d118a7fc66711"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5645b34350416b74f9dc0050"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 1ms

```

## Pokemons com altura menor ou igual a `0.5` do tipo `grama`
```
> db.pokemons.find({$and:[ {height:{$lte: 0.5}}, {type:'grama'}]})
{
  "_id": ObjectId("5645b292b34d118a7fc66710"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 1ms

```

## Pokemons com o nome `Pikachu` ou com ataque menor ou igual que `0.5` 
```
> db.pokemons.find({$or:[{name:'Pikachu'}, {attack:{$lte: 0.5}}]})
{
  "_id": ObjectId("5645b279b34d118a7fc6670f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
```

## Pokemons com o ataque maior ou igual que `48` e com altura menor ou igual que `0.5`
```
> db.pokemons.find({$and:[{attack:{$gte: 48}},{height:{$lte: 0.5}}]})
{
  "_id": ObjectId("5645b279b34d118a7fc6670f"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5645b292b34d118a7fc66710"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5645b34350416b74f9dc0050"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 1ms

```
