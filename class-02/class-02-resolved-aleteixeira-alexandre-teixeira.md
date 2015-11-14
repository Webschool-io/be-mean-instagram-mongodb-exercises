# MongoDB - Aula 02 - Exercício
autor: Alexandre Luis Teixeira

1. Crie uma database chamada be-mean-pokemons;
2. Liste quais databases vocÊ possui neste servidor;
3. Liste quais coleções você possui nessa database;
4. Insira pelo menos 5 pokemons ==A SUA ESCOLHA== utilizando o mesmo padrão de
campos utilizado: name, description, attack, defense e height;
5. Liste os pokemons existentes na sua coleção;
6. Busque um pokemon a sua escolha, que acabou de ser inserido, e armazene-o
em uma variável chamada `poke`;
7. Modifique sua `description` e salvê-o


## Crie uma database chamada be-mean-pokemons (passo 1)

```
    use be-mean-pokemons
switched to db be-mean-pokemons

```

## Listagem das databases (passo 2)

```
    show dbs
    be-mean           0.078GB
    local             0.078GB

```

## Listagem das coleções (passo 3)

```
    show collections

```

## Cadastro dos pokemons (passo 4)

```
    var pokens = [
            {name: "Charizard", description: "Fire", attack: 84, defense: 78, heigth: 1.70},
            {name:'Gengar',description:'Fantasma bolado',atack:30,defense:55,height:0.5},
            {name: "Butterfree", description: "Flying", attack: 45, defense: 50, heigth: 1.09},
            {name:'Alakazam',description:'Macumbeiro',atack:40,defense:20,height:0.8},
            {name: "Pidgeot", description: "Flying", attack: 80, defense: 75, heigth: 1.50},
            {name:'Salamancer',description:'Dragao crazy',atack:300,defense:140,height:3.0},
            {name:'Infernape',description:'Macaco em chamas',atack:300,defense:130,height:1.0},
            {'name':'Onyx','description':'Pedra no formato fálico','type': 'preda', attack: 200, height: 50 },
            {name: "Rattatá", description: "Normal", attack: 56, defense: 35, heigth: 0.30},
            {'name':'Ratata','description':'The Better - PowerFull','type': 'terra', attack: 10000, height: 15 }
    ]

  db.pokemons.insert(pokens)
 Inserted 1 record(s) in 7ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 10,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})


```


## Lista dos pokemons (passo 5)

```
be-mean-pokemons> db.pokemons.find()

{
  "_id": ObjectId("564747b3962d90a43db33c61"),
  "name": "Charizard",
  "description": "Fire",
  "attack": 84,
  "defense": 78,
  "heigth": 1.7
}
{
  "_id": ObjectId("564747b3962d90a43db33c62"),
  "name": "Gengar",
  "description": "Fantasma bolado",
  "atack": 30,
  "defense": 55,
  "height": 0.5
}
{
  "_id": ObjectId("564747b3962d90a43db33c63"),
  "name": "Butterfree",
  "description": "Flying",
  "attack": 45,
  "defense": 50,
  "heigth": 1.09
}
{
  "_id": ObjectId("564747b3962d90a43db33c64"),
  "name": "Alakazam",
  "description": "Macumbeiro",
  "atack": 40,
  "defense": 20,
  "height": 0.8
}
{
  "_id": ObjectId("564747b3962d90a43db33c65"),
  "name": "Pidgeot",
  "description": "Flying",
  "attack": 80,
  "defense": 75,
  "heigth": 1.5
}
{
  "_id": ObjectId("564747b3962d90a43db33c66"),
  "name": "Salamancer",
  "description": "Dragao crazy",
  "atack": 300,
  "defense": 140,
  "height": 3
}
{
  "_id": ObjectId("564747b3962d90a43db33c67"),
  "name": "Infernape",
  "description": "Macaco em chamas",
  "atack": 300,
  "defense": 130,
  "height": 1
}
{
  "_id": ObjectId("564747b3962d90a43db33c68"),
  "name": "Onyx",
  "description": "Pedra no formato fálico",
  "type": "preda",
  "attack": 200,
  "height": 50
}
{
  "_id": ObjectId("564747b3962d90a43db33c69"),
  "name": "Rattatá",
  "description": "Normal",
  "attack": 56,
  "defense": 35,
  "heigth": 0.3
}
{
  "_id": ObjectId("564747b3962d90a43db33c6a"),
  "name": "Ratata",
  "description": "The Better - PowerFull",
  "type": "terra",
  "attack": 10000,
  "height": 15
}
Fetched 10 record(s) in 5ms

```

## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

```
    var query  = {"name":"Ratata"}

    var poke = db.pokemons.findOne(query)

    alexandre-System-Product-Name(mongod-3.0.7) be-mean-pokemons> poke
    {
      "_id": ObjectId("56474cccc94b7d95f36a6353"),
      "name": "Ratata",
      "description": "The Better - PowerFull",
      "type": "terra",
      "attack": 10000,
      "height": 15
    }
```

## Atualizar o Poke

```
alexandre-System-Product-Name(mongod-3.0.7) be-mean-pokemons> poke.description
The Better - PowerFull

alexandre-System-Product-Name(mongod-3.0.7) be-mean-pokemons> poke.description = "O melhor - Fodão"
O melhor - Fodão

alexandre-System-Product-Name(mongod-3.0.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 33ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```