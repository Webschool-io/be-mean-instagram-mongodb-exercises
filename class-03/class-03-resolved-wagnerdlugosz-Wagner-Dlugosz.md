###MongoDB - Aula 03 - Exercício
Autor: Wagner Dlugosz Donato

##1. lista todos Pokemons com a altura menor que 0.5
```

donato-dell(mongod-3.2.4) be-mean-pokemons> var query = {height: {$lt: 0.5}}
donato-dell(mongod-3.2.4) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
donato-dell(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484a"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484b"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("570ea807f5ba6e1deb4e484f"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4852"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4853"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
Fetched 5 record(s) in 19ms


```

##2. liste todos pokemons com a altura maior ou igual que 0.5
```
donato-dell(mongod-3.2.4) be-mean-pokemons> var query = {height: {$gte: 0.5}}
donato-dell(mongod-3.2.4) be-mean-pokemons> query
{
  "height": {
    "$gte": 0.5
  }
}
donato-dell(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("570ea5d0f5ba6e1deb4e4849"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484c"),
  "name": "Raicu",
  "description": "não é nada disso",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("570ea670f5ba6e1deb4e484d"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
{
  "_id": ObjectId("570ea7d5f5ba6e1deb4e484e"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("570ea89bf5ba6e1deb4e4850"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4851"),
  "name": "Blastoise",
  "description": "Tem bicas de água que se projetam de sua concha",
  "type": "Water",
  "attack": 75,
  "height": 1.6
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4854"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4855"),
  "name": "Arbok",
  "description": "Este Pokémon é terrivelmente forte, a fim de contrair coisas com seu corpo",
  "type": "Poison",
  "attack": 65,
  "height": 3.5
}
Fetched 8 record(s) in 12ms

```

##3. lsite todos pokemons com aaltura menor ou igual que 0.5 E do tipo grama
##mudei para >=0.5 tipo eletrico
```
donato-dell(mongod-3.2.4) be-mean-pokemons> var query = {$and: [{height: {$gte: 0.5}}, {type: "Electric"}]}
donato-dell(mongod-3.2.4) be-mean-pokemons> query
{
  "$and": [
    {
      "height": {
        "$gte": 0.5
      }
    },
    {
      "type": "Electric"
    }
  ]
}
donato-dell(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484c"),
  "name": "Raicu",
  "description": "não é nada disso",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4854"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
Fetched 2 record(s) in 3ms

```

##4. liste todos pokemons com o name 'pikachu' OU com attack menor ou igual que 0.5
###mudei para <=55 e raicu
```
donato-dell(mongod-3.2.4) be-mean-pokemons> var query = {$or: [{attack: {$lte: 55}}, {name: /raicu/i}]}
donato-dell(mongod-3.2.4) be-mean-pokemons> query
{
  "$or": [
    {
      "attack": {
        "$lte": 55
      }
    },
    {
      "name": /raicu/i
    }
  ]
}
donato-dell(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484a"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484b"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484c"),
  "name": "Raicu",
  "description": "não é nada disso",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
{
  "_id": ObjectId("570ea807f5ba6e1deb4e484f"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4852"),
  "name": "Wurmple",
  "description": "Descasca a casca das árvores e se alimenta de seiva que escorre para fora",
  "type": "Bug",
  "attack": 35,
  "height": 0.3
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4853"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4854"),
  "name": "Raicu",
  "description": "Raichu plantas a cauda no chão e descargas",
  "type": "Electric",
  "attack": 55,
  "height": 0.8
}
Fetched 7 record(s) in 87ms



```

##5. liste todos pokemons com o attack Maior ou igual que 48 E com height menor ou igual que 0.5
##mudei para 44 de attack
```
donato-dell(mongod-3.2.4) be-mean-pokemons> var query = {$and: [{attack: {$gte: 44}}, {height: {$lte: 0.5}}]}
donato-dell(mongod-3.2.4) be-mean-pokemons> query
{
  "$and": [
    {
      "attack": {
        "$gte": 44
      }
    },
    {
      "height": {
        "$lte": 0.5
      }
    }
  ]
}
donato-dell(mongod-3.2.4) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("570ea667f5ba6e1deb4e484b"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
{
  "_id": ObjectId("570eaa27f5ba6e1deb4e4853"),
  "name": "Zigzagoon",
  "description": "Inquieto vagueia em todos os lugares em todos os momentos",
  "type": "Normal",
  "attack": 45,
  "height": 0.4
}
Fetched 2 record(s) in 4ms

```


