# MongoDB - Aula 03 - Exercício
autor: Alex Farias

## 1 - Liste todos Pokemons com a altura **menor que** 0.5;
```
    var value = 0.5
    var query = {height : {$lt : value}}
    db.pokemons.find(query)
    {
      "_id": ObjectId("5643a0b7bdda6aabca5a7fd5"),
      "name": "Pidgey",
      "description": "Passarinho q grita e voa",
      "attack": 20,
      "defense": 20,
      "height": 0.3,
      "type": "Fly"
    }

```

## 2 - Liste todos Pokemons com a altura **maior ou igual que** 0.5
```
    var value = 0.5
    var query = {height : {$gte : value}}
    db.pokemons.find(query)
    {
      "_id": ObjectId("56439d6abdda6aabca5a7fd1"),
      "name": "Squirtle",
      "description": "Shell is not merely for protection",
      "attack": 48,
      "defense": 65,
      "height": 0.5,
      "type": "Water"
    }
    {
      "_id": ObjectId("56439f82bdda6aabca5a7fd2"),
      "name": "Butterfree",
      "description": "Inseto q avoa",
      "attack": 20,
      "defense": 30,
      "height": 1.1,
      "type": "Bug"
    }
    {
      "_id": ObjectId("5643a00ebdda6aabca5a7fd3"),
      "name": "Blastoise",
      "description": "Monxtrão que tem canhão de água",
      "attack": 40,
      "defense": 40,
      "height": 1.6,
      "type": "Water"
    }
    {
      "_id": ObjectId("5643a05ebdda6aabca5a7fd4"),
      "name": "Metapod",
      "description": "Inseto de casca dura",
      "attack": 10,
      "defense": 30,
      "height": 0.7,
      "type": "Bug"
    }
    {
      "_id": ObjectId("5643a11abdda6aabca5a7fd6"),
      "name": "Beedrill",
      "description": "Abelhão do mal, vixe",
      "attack": 50,
      "defense": 30,
      "height": 1,
      "type": "Bug"
    }
    {
      "_id": ObjectId("5643a157bdda6aabca5a7fd7"),
      "name": "Arbok",
      "description": "Cobra da Equipe Rocket",
      "attack": 40,
      "defense": 30,
      "height": 3.5,
      "type": "Poison"
    }
    {
      "_id": ObjectId("56463238a560e80191083d44"),
      "name": "Bulbasaur",
      "description": "Bicho verde que solta folha q corta",
      "attack": 49,
      "defense": 49,
      "height": 2.4,
      "type": "Grass"
    }
    {
      "_id": ObjectId("564632d2a560e80191083d45"),
      "name": "Chikorita",
      "description": "Verdinha massa com folha grande na cabeça",
      "attack": 49,
      "defense": 65,
      "height": 2.1,
      "type": "Grass"
    }

```

## 3 - Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama
```
    var value = 0.5
    var query1 = {height : {$lte : value}}
    var query2 = {type : "Grass"}
    db.pokemons.find({$and : [query1, query2]})
    Fetched 0 record(s) in 0ms


```

## 4 - Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5
```
    var query1 = {name : "Pikachu"}
    var query2 = {attack : {$lte : 0.5}}
    db.pokemons.find({$or : [query1, query2]})
    {
      "_id": ObjectId("564637533cb365fe72ce44cb"),
      "name": "Pikachu",
      "description": "Rato amarelo q solta raio",
      "attack": 55,
      "defense": 40,
      "height": 1.4,
      "type": "Electric"
    }

```

## 5 - Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5
```
    var query1 = {attack : {$gte : 48}}
    var query2 = {height : {$lte : 0.5}}
    db.pokemons.find({$and : [query1, query2]})
    {
      "_id": ObjectId("56439d6abdda6aabca5a7fd1"),
      "name": "Squirtle",
      "description": "Shell is not merely for protection",
      "attack": 48,
      "defense": 65,
      "height": 0.5,
      "type": "Water"
    }

```


