# MongoDB - Aula 04 - Exercício
autor: Baltazar Parra

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
    var query = {$or: [{name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassaur/i}, {name: /charmander/i}]};
    var mod = {$pushAll: {moves: ['dash','roll']}};
    var options = {multi: true};

    db.pokemons.update(query, mod, options);
    Updated 4 existing record(s) in 60ms
    WriteResult({
        "nMatched": 4,
        "nUpserted": 0,
        "nModified": 4
    })

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
    var query = {};
    var mod = { $push: { moves: "desvio"}}
    var opts = { multi: true }

    db.pokemons.update(query, mod, opts)
    Updated 15 existing record(s) in 4ms
    WriteResult({
        "nMatched": 15,
        "nUpserted": 0,
        "nModified": 15
    })

```


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
    var query = { name: /AindaNaoExisteMon/i };
    var mod = { $setOnInsert: {
        name: "AindaNaoExisteMon"
      , attack: null
      , height: null
      , defense: null
      , moves: []
      , description: "Sem maiores informações"
    }};

    var opts = { upsert: true };
    db.pokemons.update(query, mod, opts);
    Updated 1 new record(s) in 17ms
    WriteResult({
        "nMatched": 0,
        "nUpserted": 1,
        "nModified": 0,
        "_id": ObjectId("564ca7ca14c65cfb0574ee0b")
    })

```


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
    var query = { moves: { $in: ['investida', /dash/i] }};
    db.pokemons.find(query);
    {
        "_id": ObjectId("564c9d9865346d0d1552a36b"),
        "name": "Pikachu",
        "description": "Rato elétrico bem fofinho",
        "type": "eletric",
        "attack": 55,
        "height": 0.4,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d6"),
        "name": "Pikachu",
        "description": "Rato elétrico bem fofinho",
        "type": "eletric",
        "attack": 55,
        "height": 0.4,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d7"),
        "name": "Squirtle",
        "description": "tartoruguers das agua aquatica",
        "type": "agua",
        "attack": 48,
        "height": 0.5,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d9"),
        "name": "Charmander",
        "description": "dinassouro afeminado",
        "type": "fogo",
        "attack": 52,
        "height": 0.6,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    Fetched 4 record(s) in 6ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
    var query = {'moves': { $all: ['dash','roll']}};
    db.pokemons.find(query)
    {
        "_id": ObjectId("564c9d9865346d0d1552a36b"),
        "name": "Pikachu",
        "description": "Rato elétrico bem fofinho",
        "type": "eletric",
        "attack": 55,
        "height": 0.4,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d6"),
        "name": "Pikachu",
        "description": "Rato elétrico bem fofinho",
        "type": "eletric",
        "attack": 55,
        "height": 0.4,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d7"),
        "name": "Squirtle",
        "description": "tartoruguers das agua aquatica",
        "type": "agua",
        "attack": 48,
        "height": 0.5,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d9"),
        "name": "Charmander",
        "description": "dinassouro afeminado",
        "type": "fogo",
        "attack": 52,
        "height": 0.6,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    Fetched 4 record(s) in 6ms

```

## Pesquisar **todos** os pokemons que não são do tipo `eletric`.##

```
    var query = {type : {$ne: 'eletric'}};
    db.pokemons.find(query)
    {
        "_id": ObjectId("564c9d9865346d0d1552a366"),
        "name": "Fumichu",
        "description": "Rato de ervas diferenciadas",
        "type": "natural",
        "attack": 420,
        "height": 10,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564c9d9865346d0d1552a367"),
        "name": "Dechavassauro",
        "description": "Dinossauro triturados de ervas diferenciadas",
        "type": "triturador",
        "attack": 666,
        "height": 1.6,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564c9d9865346d0d1552a368"),
        "name": "Isqueirozard",
        "description": "Dragão tocador de fogo nas ervinhas diferenciadas",
        "type": "dragão",
        "attack": 9999,
        "height": 99.9,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564c9d9865346d0d1552a369"),
        "name": "Cedinhapi",
        "description": "Folhinha abraçadora de ervinhas diferenciadas",
        "type": "leda",
        "attack": 1,
        "height": 0.1,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564c9d9865346d0d1552a36a"),
        "name": "FumadorTwo",
        "description": "Alienogeno pegador das coisa pra transformar em baseados",
        "type": "fumero",
        "attack": 420,
        "height": 70.1,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d1"),
        "name": "Fumichu",
        "description": "Rato de ervas diferenciadas",
        "type": "natural",
        "attack": 420,
        "height": 10,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d2"),
        "name": "Dechavassauro",
        "description": "Dinossauro triturados de ervas diferenciadas",
        "type": "triturador",
        "attack": 666,
        "height": 1.6,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d3"),
        "name": "Isqueirozard",
        "description": "Dragão tocador de fogo nas ervinhas diferenciadas",
        "type": "dragão",
        "attack": 9999,
        "height": 99.9,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d4"),
        "name": "Cedinhapi",
        "description": "Folhinha abraçadora de ervinhas diferenciadas",
        "type": "leda",
        "attack": 1,
        "height": 0.1,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d5"),
        "name": "FumadorTwo",
        "description": "Alienogeno pegador das coisa pra transformar em baseados",
        "type": "fumero",
        "attack": 420,
        "height": 70.1,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d7"),
        "name": "Squirtle",
        "description": "tartoruguers das agua aquatica",
        "type": "agua",
        "attack": 48,
        "height": 0.5,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d8"),
        "name": "Bulbasaur",
        "description": "sapão maluco",
        "type": "grama",
        "attack": 49,
        "height": 0.7,
        "moves": [
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca3399c554da35f5cd5d9"),
        "name": "Charmander",
        "description": "dinassouro afeminado",
        "type": "fogo",
        "attack": 52,
        "height": 0.6,
        "moves": [
            "dash",
            "roll",
            "desvio"
        ]
    }
    {
        "_id": ObjectId("564ca7ca14c65cfb0574ee0b"),
        "name": "AindaNaoExisteMon",
        "attack": null,
        "height": null,
        "defense": null,
        "moves": [ ],
        "description": "Sem maiores informações"
    }
    Fetched 14 record(s) in 7ms

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
    var query ={$and: [{type: "água"}, {attack: {$lt: 50 }}]};

    db.pokemons.remove(query);
    Removed 1 record(s) in 10ms
    WriteResult({
      "nRemoved": 1
    })
```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.

```
    $ne: Seleciona os documentos onde o valor do campo não é igual ao valor especificado.
    
    $not: Seleciona os documentos que não correspondem ao operador.
```