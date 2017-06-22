# MongoDB - Aula 03 - Exercício
autor: Gabriel Tomé

## Liste todos Pokemons com a altura **menor que** 0.5;


```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {height: {$lt: 0.5}}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56551778c6086b7b42449019"),
  "name": "Togepi",
  "description": "O mais bonitinho",
  "type": "Fairy",
  "attack": 10,
  "defense": 30,
  "height": 0.3
}
{
  "_id": ObjectId("56551778c6086b7b4244901c"),
  "name": "Mew",
  "description": "Só tem cara de bonzinho, mas bota o terror!",
  "type": "psicoloco",
  "attack": 88,
  "defense": 99,
  "height": 0.4
}
```

## Liste todos Pokemons com a altura **maior ou igual que** 0.5

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {height: {$gte: 0.5}}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56551778c6086b7b42449018"),
  "name": "Magikarp",
  "description": "Pokemon doidão",
  "type": "Água",
  "attack": 10,
  "defense": 10,
  "height": 0.5
}
{
  "_id": ObjectId("56551778c6086b7b4244901a"),
  "name": "Butterfree",
  "description": "Brabuleta endiabrada",
  "type": "inseto/fly",
  "attack": 20,
  "defense": 20,
  "height": 1.1
}
{
  "_id": ObjectId("56551778c6086b7b4244901b"),
  "name": "Mewtwo",
  "description": "Esse é fodão!",
  "type": "psicoloco",
  "attack": 100,
  "defense": 99,
  "height": 2.1
}
```


## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {$and : [{height: {$lte:0.5}},{type: "grama"}]}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": "grama"
    }
  ]
}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 71ms
```

## Liste todos Pokemons com o name `Pikachu` **OU** com attack **menor ou igual que** 0.5

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {$or : [{name : "Pikachu"},{attack: {$lte:0.5}}]}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> query
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
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 98ms
```

## Liste todos Pokemons com o attack **MAIOR OU IGUAL QUE** 48 **E** com  height **menor ou igual que** 0.5

```
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> var query = {$and : [{attack: {$gte :48}},{height : {$lte: 0.5}}]}
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> query
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
MacBook-Pro-de-Gabriel-Tome(mongod-2.6.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56551778c6086b7b4244901c"),
  "name": "Mew",
  "description": "Só tem cara de bonzinho, mas bota o terror!",
  "type": "psicoloco",
  "attack": 88,
  "defense": 99,
  "height": 0.4
}
Fetched 1 record(s) in 2ms
```