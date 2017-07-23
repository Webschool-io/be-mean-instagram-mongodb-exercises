# MongoDB - Aula 03 - Exercício
autor: Baltazar Parra

## Liste todos Pokemons com a altura menor que 0.5;

```
    $ mongo be-mean-pokemons
    MongoDB shell version: 3.0.7
    connecting to: be-mean-pokemons
    Mongo-Hacker 0.0.4
    var query = {height: {$lt: 0.5}}
    db.pokemons.find(query)
    {
        "_id": ObjectId("5642871c332e1197e9ae246d"),
        "name": "Cedinhapi",
        "description": "Folhinha abraçadora de ervinhas diferenciadas",
        "type": "leda",
        "attack": 1,
        "height": 0.1
    }
    {
        "_id": ObjectId("56428890332e1197e9ae246f"),
        "name": "Pikachu",
        "description": "Ratão do matagal, tocador de raio nus oto",
        "type": "eletric",
        "attack": 55,
        "height": 0.4
    }
    {
        "_id": ObjectId("56428b1e6fd8dd5b36bf5ac5"),
        "name": "Cedinhapi",
        "description": "Folhinha abraçadora de ervinhas diferenciadas",
        "type": "leda",
        "attack": 1,
        "height": 0.1
    }
    {
        "_id": ObjectId("56428b1e6fd8dd5b36bf5ac7"),
        "name": "Pikachu",
        "description": "Rato elétrico bem fofinho",
        "type": "eletric",
        "attack": 55,
        "height": 0.4
    }
    Fetched 4 record(s) in 3ms
```

## Liste todos Pokemons com a altura maior ou igual que 0.5;
```
        $ mongo be-mean-pokemons
    MongoDB shell version: 3.0.7
    connecting to: be-mean-pokemons
    Mongo-Hacker 0.0.4
    var query = {height: {$gte: 0.5}}
    db.pokemons.find(query)
    {
        "_id": ObjectId("564285d5332e1197e9ae246a"),
        "name": "Fumichu",
        "description": "Rato de ervas diferenciadas",
        "type": "natural",
        "attack": 420,
        "height": 10
    }
    {
        "_id": ObjectId("5642869a332e1197e9ae246b"),
        "name": "Dechavassauro",
        "description": "Dinossauro triturados de ervas diferenciadas",
        "type": "triturador",
        "attack": 666,
        "height": 1.6
    }
    {
        "_id": ObjectId("564286df332e1197e9ae246c"),
        "name": "Isqueirozard",
        "description": "Dragão tocador de fogo nas ervinhas diferenciadas",
        "type": "dragão",
        "attack": 9999,
        "height": 99.9
    }
    {
        "_id": ObjectId("5642876d332e1197e9ae246e"),
        "name": "FumadorTwo",
        "description": "Alienogeno pegador das coisa pra transformar em baseados",
        "type": "fumero",
        "attack": 420,
        "height": 70.1
    }
    {
        "_id": ObjectId("56428b1e6fd8dd5b36bf5ac3"),
        "name": "Dechavassauro",
        "description": "Dinossauro triturados de ervas diferenciadas",
        "type": "triturador",
        "attack": 666,
        "height": 1.6
    }
    {
        "_id": ObjectId("56428b1e6fd8dd5b36bf5ac4"),
        "name": "Isqueirozard",
        "description": "Dragão tocador de fogo nas ervinhas diferenciadas",
        "type": "dragão",
        "attack": 9999,
        "height": 99.9
    }
    {
        "_id": ObjectId("56428b1e6fd8dd5b36bf5ac6"),
        "name": "FumadorTwo",
        "description": "Alienogeno pegador das coisa pra transformar em baseados",
        "type": "fumero",
        "attack": 420,
        "height": 70.1
    }
    Fetched 7 record(s) in 3ms
```

## Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama;

```
    var query = {$and: [{height: {$lte: 0.5 }}, {type: 'grama'}]}
    db.pokemons.find(query)
    {
        "_id": ObjectId("5643d56da6492d36e4dcdbb7"),
        "name": "Bulbassauro",
        "description": "pokemons dinanossauro bem locaço",
        "type": "grama",
        "attack": 100,
        "height": 0.4
    }
    Fetched 1 record(s) in 225ms

```
## Liste todos Pokemons com o name Pikachu OU com attack menor ou igual que 0.5
```
        var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5 }}]}
    db.pokemons.find(query)
    {
        "_id": ObjectId("56428890332e1197e9ae246f"),
        "name": "Pikachu",
        "description": "Ratão do matagal, tocador de raio nus oto",
        "type": "eletric",
        "attack": 55,
        "height": 0.4
    }
    {
        "_id": ObjectId("56428b1e6fd8dd5b36bf5ac7"),
        "name": "Pikachu",
        "description": "Rato elétrico bem fofinho",
        "type": "eletric",
        "attack": 55,
        "height": 0.4
    }
    Fetched 2 record(s) in 88ms

```

## Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5
```
    var query = {$and: [{attack: {$gte: 48 }}, {height: {$lte: 0.5 }}]}
        db.pokemons.find(query)
    {
        "_id": ObjectId("56428890332e1197e9ae246f"),
        "name": "Pikachu",
        "description": "Ratão do matagal, tocador de raio nus oto",
        "type": "eletric",
        "attack": 55,
        "height": 0.4
    }
    {
        "_id": ObjectId("56428b1e6fd8dd5b36bf5ac7"),
        "name": "Pikachu",
        "description": "Rato elétrico bem fofinho",
        "type": "eletric",
        "attack": 55,
        "height": 0.4
    }
    {
        "_id": ObjectId("5643d56da6492d36e4dcdbb7"),
        "name": "Bulbassauro",
        "description": "pokemons dinanossauro bem locaço",
        "type": "grama",
        "attack": 100,
        "height": 0.4
    }
    Fetched 3 record(s) in 3ms

```
