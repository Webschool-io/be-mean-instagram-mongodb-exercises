# MongoDB - Aula 02 - Exercício
autor: Alexandre Luis Teixeira

1. Liste todos Pokemons com a altura menor que 0.5;
2. Liste todos Pokemons com a altura maior ou igual que 0.5;
3. Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;
4. Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;
5. Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

## Liste todos Pokemons com a altura menor que 0.5

```
be-mean-pokemons> var query = {height: {$lt: 0.5}}
be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
alexandre-debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648c94d001565661f1fc506"),
  "name": "Caterpie",
  "description": "Bixinho/Larva verde feinho",
  "type": "Fogo",
  "attack": 30,
  "defense": 35,
  "height": 0.3
}
{
  "_id": ObjectId("5648c94d001565661f1fc507"),
  "name": "Pikachu",
  "description": "Pestinha Amarela",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
{
  "_id": ObjectId("5648c94d001565661f1fc50d"),
  "name": "Litwick",
  "description": "Vla monstro!!!",
  "type": "Fantasma/fogo",
  "attack": 30,
  "defense": 55,
  "height": 0.3
}
Fetched 3 record(s) in 2ms


```

## Liste todos Pokemons com a altura maior ou igual que 0.5

```
be-mean-pokemons> var query = {height: {$gte: 0.5}}
be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
alexandre-debian(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648c94d001565661f1fc504"),
  "name": "Charizard",
  "description": "Dragão Voador guspidor de fogo",
  "type": "Fogo",
  "attack": 84,
  "defense": 78,
  "height": 1.7
}
{
  "_id": ObjectId("5648c94d001565661f1fc505"),
  "name": "Squirtle",
  "description": "Tartaruga Azul",
  "type": "Água",
  "attack": 48,
  "defense": 65,
  "height": 0.51
}
{
  "_id": ObjectId("5648c94d001565661f1fc508"),
  "name": "Lugia",
  "description": "Chavier dos Pokemons",
  "type": "Telepático/Voador",
  "attack": 90,
  "defense": 130,
  "height": 5.21
}
{
  "_id": ObjectId("5648c94d001565661f1fc509"),
  "name": "Kyurem",
  "description": "Dragão de Gelo imune a fogo",
  "type": "Dragão/Gelo",
  "attack": 130,
  "defense": 90,
  "height": 3
}
{
  "_id": ObjectId("5648c94d001565661f1fc50a"),
  "name": "Dialga",
  "description": "Dragão de Aço que viaja no tempo",
  "type": "Aço/Dragão",
  "attack": 120,
  "defense": 120,
  "height": 5.41
}
{
  "_id": ObjectId("5648c94d001565661f1fc50b"),
  "name": "Bulbasaur",
  "description": "Bichinho verde",
  "type": "Grama",
  "attack": 49,
  "defense": 49,
  "height": 0.71
}
{
  "_id": ObjectId("5648c94d001565661f1fc50c"),
  "name": "Victreebel",
  "description": "Mato..rs",
  "type": "Grama",
  "attack": 105,
  "defense": 65,
  "height": 1.7
}
Fetched 7 record(s) in 2ms

```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}},{type:"Grama"}]}
be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "Grama"
    }
  ]
}
be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms

```

## Liste todos Pokemons com o name `Pikachu` OU com attack menor ou igual que 0.5;

```
be-mean-pokemons> query
{
  "$or": [
    {
      "name": "Pikachu"
    },
    {
      "attack": {
        "$lte": 0.5
      }
    }
  ]
}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648c94d001565661f1fc507"),
  "name": "Pikachu",
  "description": "Pestinha Amarela",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
Fetched 1 record(s) in 2ms
```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com  height menor ou igual que 0.5;

```
be-mean-pokemons> query
{
  "$and": [
    {
      "attack": {
        "$gte": 48
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}
be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648c94d001565661f1fc507"),
  "name": "Pikachu",
  "description": "Pestinha Amarela",
  "type": "Elétrico",
  "attack": 55,
  "defense": 40,
  "height": 0.41
}
Fetched 1 record(s) in 0ms

```