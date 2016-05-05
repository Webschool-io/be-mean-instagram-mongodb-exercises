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
            {name: "Charizard", description: "Dragão Voador guspidor de fogo", type: "Fogo", attack: 84, defense: 78, height: 1.70},
            {name: "Squirtle", description: "Tartaruga Azul", type: "Água", attack: 48 , defense: 65 , height: 0.51},
            {name: "Caterpie", description: "Bixinho/Larva verde feinho", type: "Fogo", attack: 30, defense:  35, height: 0.30},
            {name: "Pikachu", description: "Pestinha Amarela", type: "Elétrico", attack: 55, defense: 40, height: 0.41},
            {name: "Lugia", description: "Chavier dos Pokemons", type: "Telepático/Voador", attack: 90, defense: 130, height: 5.21},
            {name: "Kyurem", description: "Dragão de Gelo imune a fogo", type: "Dragão/Gelo", attack: 130, defense: 90, height: 3.00},
            {name: "Dialga", description: "Dragão Temporal de Aço", type: "Aço/Dragão", attack: 120, defense: 120, height: 5.41},
            {name: "Bulbasaur", description: "Bichinho verde", type: "Grama", attack: 49, defense: 49, height: 0.71},
            {name: "Victreebel", description: "Mato..rs", type: "Grama", attack: 105, defense: 65, height: 1.7},
            {name: "Litwick", description: "Vla monstro!!!", type: "Fantasma/fogo", attack: 30, defense: 55, height: 0.3}
    ]

be-mean-pokemons> db.pokemons.insert(pokens)
Inserted 1 record(s) in 30ms
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
  "description": "Dragão Temporal de Aço",
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
{
  "_id": ObjectId("5648c94d001565661f1fc50d"),
  "name": "Litwick",
  "description": "Vla monstro!!!",
  "type": "Fantasma/fogo",
  "attack": 30,
  "defense": 55,
  "height": 0.3
}
Fetched 10 record(s) in 4ms


```

## 6. Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`;

```
be-mean-pokemons> var query  = {"name":"Dialga"}
be-mean-pokemons> var poke = db.pokemons.findOne(query)
be-mean-pokemons> poke
{
  "_id": ObjectId("5648c94d001565661f1fc50a"),
  "name": "Dialga",
  "description": "Dragão Temporal de Aço",
  "type": "Aço/Dragão",
  "attack": 120,
  "defense": 120,
  "height": 5.41
}

```

## Atualizar o Poke

```
be-mean-pokemons> poke.description
Dragão Temporal de Aço
be-mean-pokemons> poke.description = "Dragão de Aço que viaja no tempo"
Dragão de Aço que viaja no tempo
be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

```