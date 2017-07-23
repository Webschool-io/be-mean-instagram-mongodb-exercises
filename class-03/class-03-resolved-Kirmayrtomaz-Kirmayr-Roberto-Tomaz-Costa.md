class-03-resolved-Kirmayrtomaz-Kirmayr-Roberto-Tomaz-Costa.md
# MongoDB - Aula 03 - Exercício
autor: Kirmayr Tomaz

##Liste todos Pokemons com a altura menor que 0.5
```
whey(mongod-2.6.11) be-mean-pokemons> var query = { height:{ $lt : 0.5}}
whey(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56441dbaa2038c3622aa0f32"),
  "name": "Ditto",
  "description": "Mais conhecido como Latino",
  "type": "grama",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 0ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5
```
whey(mongod-2.6.11) be-mean-pokemons> var query = { height:{ $lte : 0.5}}
whey(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56441dbaa2038c3622aa0f31"),
  "name": "Pidgey",
  "description": "Pokemon que mais parece na grama do gameboy",
  "type": "voador",
  "attack": 20,
  "defense": 20,
  "height": 0.5
}
{
  "_id": ObjectId("56441dbaa2038c3622aa0f32"),
  "name": "Ditto",
  "description": "Mais conhecido como Latino",
  "type": "grama",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 2 record(s) in 2ms

```
## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
whey(mongod-2.6.11) be-mean-pokemons> var query = { $and :[{ "height": {$lte: 0.5 }  }, { "type":"grama"}] }
whey(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56441dbaa2038c3622aa0f32"),
  "name": "Ditto",
  "description": "Mais conhecido como Latino",
  "type": "grama",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
Fetched 1 record(s) in 1ms


```
## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```

whey(mongod-2.6.11) be-mean-pokemons> var query = { $or :[{"name":"Pikachu"}, { "attack": {$gte: 0.5 }  }] }
whey(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56441dbaa2038c3622aa0f31"),
  "name": "Pidgey",
  "description": "Pokemon que mais parece na grama do gameboy",
  "type": "voador",
  "attack": 20,
  "defense": 20,
  "height": 0.5
}
{
  "_id": ObjectId("56441dbaa2038c3622aa0f32"),
  "name": "Ditto",
  "description": "Mais conhecido como Latino",
  "type": "grama",
  "attack": 30,
  "defense": 20,
  "height": 0.4
}
{
  "_id": ObjectId("56441dbaa2038c3622aa0f33"),
  "name": "Meowth",
  "description": "Gato leproso que vive com a Equipe rocket",
  "type": "normal",
  "attack": 0.5,
  "defense": 20,
  "height": 4.2
}
{
  "_id": ObjectId("56441dbaa2038c3622aa0f34"),
  "name": "Squirtle",
  "description": "Tartaruga que lança agua",
  "type": "agua",
  "attack": 30,
  "defense": 30,
  "height": 9
}
{
  "_id": ObjectId("56441dbaa2038c3622aa0f35"),
  "name": "charizard",
  "description": "Voa ao redor do céu",
  "type": "fogo",
  "attack": 40,
  "defense": 30,
  "height": 90
}
Fetched 5 record(s) in 3ms

```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```

whey(mongod-2.6.11) be-mean-pokemons> var query = { $and :[ { "attack": {$gte: 48 }  },{ "height" :{ $lte :  0.5  }  } ] }
whey(mongod-2.6.11) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
```
