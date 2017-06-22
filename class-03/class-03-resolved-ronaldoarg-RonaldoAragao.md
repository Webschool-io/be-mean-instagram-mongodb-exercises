# MongoDB - Aula 03 - Exercício
autor: Ronaldo Aragão

##Liste todos Pokemons com a altura menor que 0.5
```
be-mean-instagram> var query = { height: { $lt: 0.5 } };
be-mean-instagram> db.pokemons.find(query)
{
  "_id": ObjectId("564523478dfbf85d4ae2dedf"),
  "name": "pikachu",
  "description": "Rato Amarelo",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("5645267c8dfbf85d4ae2dee0"),
  "name": "bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564528ad8dfbf85d4ae2dee3"),
  "name": "cartepie",
  "description": "Larvinha",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 6ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5
```
  be-mean-pokemons> var query = { height: { $gte: 0.5 } };
  be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("564526cd8dfbf85d4ae2dee1"),
  "name": "charmander",
  "description": "O que tem o rado de fogo",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("564527078dfbf85d4ae2dee2"),
  "name": "squirtle",
  "description": "O azulzinho de água",
  "type": "água",
  "attack": 48,
  "height": 0.5
}

```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
```
be-mean-pokemons> var query = { $and: [ { height: { $lte: 0.5 } }, { type: 'grama' } ] };
  be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5645267c8dfbf85d4ae2dee0"),
  "name": "bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}

```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5
```
 be-mean-pokemons> var query = { $or: [ { name: 'pikachu' }, { attack: { $lte: 0.5 } } ] };
be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("564523478dfbf85d4ae2dedf"),
  "name": "pikachu",
  "description": "Rato Amarelo",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}

```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5
```
 be-mean-pokemons> var query = { $and: [ { attack: { $gte: 48 } }, { height: { $lte: 0.5 } } ] };
be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("564523478dfbf85d4ae2dedf"),
  "name": "pikachu",
  "description": "Rato Amarelo",
  "type": "eletric",
  "attack": 100,
  "height": 0.4
}
{
  "_id": ObjectId("5645267c8dfbf85d4ae2dee0"),
  "name": "bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("564527078dfbf85d4ae2dee2"),
  "name": "squirtle",
  "description": "O azulzinho de água",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 3 record(s) in 7ms

```
