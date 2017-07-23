# MongoDB - Aula 03 - Exercício
autor: Diego Costa

## Liste todos Pokemons com a altura **menor que** 0.5;
```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ height: { $lt: 0.5 } })
{
  "_id": ObjectId("5643ea5074d288f816215409"),
  "name": "Pikachu",
  "description": "Pikachu is an Eletric-type Pokémon.",
  "attack": "55",
  "defense": "30",
  "height": 0.4
}
{
  "_id": ObjectId("5643ea5074d288f81621540a"),
  "name": "Meowth",
  "description": "Meowth is a Normal-type Pokémon and he speaks",
  "attack": "45",
  "defense": "35",
  "height": 0.4
}
Fetched 2 record(s) in 5ms
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons>
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ height : { $gte: 0.5 } })
{
  "_id": ObjectId("5643ea5074d288f816215406"),
  "name": "Bulbasaur",
  "description": "Bulbasaur is a dual-type Grass/Poison Pokémon.",
  "attack": 49,
  "defense": 49,
  "height": 0.7
}
{
  "_id": ObjectId("5643ea5074d288f816215407"),
  "name": "Charmander",
  "description": "Charmander is a Fire-type Pokémon.",
  "attack": 52,
  "defense": 43,
  "height": 0.6
}
{
  "_id": ObjectId("5643ea5074d288f816215408"),
  "name": "Squirtle",
  "description": "Squirtle is a Water-type Pokémon.",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
Fetched 3 record(s) in 8ms
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons>
```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ $and : [{ height: { $lte: 0.5 } }, { type: "grama" }] })
Fetched 0 record(s) in 1ms
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons>
```

Não houve cadastro de tipos.

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ $or : [{ name: "Pikachu" }, { attack: { $lte : 0.5 } }] })
{
  "_id": ObjectId("5643ea5074d288f816215409"),
  "name": "Pikachu",
  "description": "Pikachu is an Eletric-type Pokémon.",
  "attack": 55,
  "defense": 30,
  "height": 0.4
}
Fetched 1 record(s) in 3ms
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons>
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons> db.pokemons.find({ $and : [{ attack: { $gte : 48 } }, { height: { $lte : 0.5 } }] })
{
  "_id": ObjectId("5643ea5074d288f816215408"),
  "name": "Squirtle",
  "description": "Squirtle is a Water-type Pokémon.",
  "attack": 48,
  "defense": 65,
  "height": 0.5
}
{
  "_id": ObjectId("5643ea5074d288f816215409"),
  "name": "Pikachu",
  "description": "Pikachu is an Eletric-type Pokémon.",
  "attack": 55,
  "defense": 30,
  "height": 0.4
}
Fetched 2 record(s) in 9ms
DIEGO-LAPTOP(mongod-3.0.7) be-mean-pokemons>
```