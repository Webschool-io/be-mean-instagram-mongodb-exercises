# MongoDB - Aula 03 - Exercício
autor: Jean Scussel

## Liste todos Pokemons com a altura **menor que** 0.5;

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {height:{$lt: 0.5}}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56466a619f352f3891c8ccbc"),
  "name": "Treeglass",
  "description": "Ataca com folhas afiadas",
  "type": "grama",
  "attack": 35,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccc0"),
  "name": "Antmelt",
  "description": "Inseto poderoso tipo a formiga atômica",
  "type": "insect",
  "attack": 80,
  "defense": 100,
  "height": 0.3
}
Fetched 2 record(s) in 2ms

```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {height:{$lte: 0.5}}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56466a619f352f3891c8ccbc"),
  "name": "Treeglass",
  "description": "Ataca com folhas afiadas",
  "type": "grama",
  "attack": 35,
  "defense": 40,
  "height": 0.4
}
{
  "_id": ObjectId("56466aa09f352f3891c8ccbd"),
  "name": "Pikachu",
  "description": "Coelho amarelo que atira raios",
  "type": "electric",
  "attack": 65,
  "defense": 55,
  "height": 0.5
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccc0"),
  "name": "Antmelt",
  "description": "Inseto poderoso tipo a formiga atômica",
  "type": "insect",
  "attack": 80,
  "defense": 100,
  "height": 0.3
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccc1"),
  "name": "Raticate",
  "description": "Ratão do banhado",
  "type": "normal",
  "attack": 20,
  "defense": 25,
  "height": 0.5
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccc3"),
  "name": "Venomito",
  "description": "Bichinho muito feio",
  "type": "poison",
  "attack": 15,
  "defense": 10,
  "height": 0.5
}
Fetched 5 record(s) in 2ms

```

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{height: {$lte: 0.5}},{type: 'grama'}]}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56466a619f352f3891c8ccbc"),
  "name": "Treeglass",
  "description": "Ataca com folhas afiadas",
  "type": "grama",
  "attack": 35,
  "defense": 40,
  "height": 0.4
}
Fetched 1 record(s) in 0ms

```
## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {$or:[{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56466aa09f352f3891c8ccbd"),
  "name": "Pikachu",
  "description": "Coelho amarelo que atira raios",
  "type": "electric",
  "attack": 65,
  "defense": 55,
  "height": 0.5
}
Fetched 1 record(s) in 1ms

```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {$and:[{attack:{$gte: 48}},{height:{$lte: 0.5}}]}
jean-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56466aa09f352f3891c8ccbd"),
  "name": "Pikachu",
  "description": "Coelho amarelo que atira raios",
  "type": "electric",
  "attack": 65,
  "defense": 55,
  "height": 0.5
}
{
  "_id": ObjectId("56466c7d9f352f3891c8ccc0"),
  "name": "Antmelt",
  "description": "Inseto poderoso tipo a formiga atômica",
  "type": "insect",
  "attack": 80,
  "defense": 100,
  "height": 0.3
}
Fetched 2 record(s) in 1ms

```

