# MongoDb - Aula 03 - Exercício
Autor: Hélio Marcondes

## Liste todos pokemons com a altura menor que 0.5

```
    db.pokemons.find({ "height" : { $lt: 0.5 } } );
    { "_id" : ObjectId("56a7f43c52aa820658a17400"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }
    { "_id" : ObjectId("56a7f45a52aa820658a17401"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
```

## Liste todos pokemons com a altura maior ou igual que 0.5

```
    db.pokemons.find({ "height" : { $gte: 0.5 } } );
    { "_id" : ObjectId("56a7f3a952aa820658a173fe"), "name" : "Eevee", "description" : "Raposinha bonitinha", "type" : "normal", "attack" : 30, "defense" : 20, "height" : 6.5 }
    { "_id" : ObjectId("56a7f40052aa820658a173ff"), "name" : "Umbreon", "description" : "Raposinha bonitinha versão do mau", "type" : "dark", "attack" : 45, "defense" : 30, "height" : 27 }
    { "_id" : ObjectId("56a7f47052aa820658a17402"), "name" : "Charmandar", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
    { "_id" : ObjectId("56a7f47e52aa820658a17403"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
    { "_id" : ObjectId("56a7f50f52aa820658a17404"), "name" : "Flareon", "description" : "Raposinha bonitinha versão de fogo", "type" : "fire", "attack" : 40, "defense" : 40, "height" : 0.9 }
    { "_id" : ObjectId("56a7f51952aa820658a17405"), "name" : "Jolteon", "description" : "Raposinha braba versão de choque", "type" : "eletric", "attack" : 50, "defense" : 25, "height" : 1.5 }
    { "_id" : ObjectId("56a7f52652aa820658a17406"), "name" : "Vaporeon", "description" : "Raposinha bonitinha versão de água", "type" : "água", "attack" : 38, "defense" : 32, "height" : 1 }
```

## Liste todos pokemons com a altura menor ou igual que 0.5 E do tipo grama

```
    var and = { $and: [ { height: {$lte : 0.5}}, { type: 'grama' } ]} 
    db.pokemons.find(and)
    "_id" : ObjectId("56a7f45a52aa820658a17401"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
```

## Liste todos pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5

```
    db.pokemons.find({ $or : [ { name : 'Pikachu' } , {attack: { $lte : 0.5 }} ] })
    { "_id" : ObjectId("56a7f43c52aa820658a17400"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }
```

## Liste todos pokemons com o attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5

```
    var and2 = { $and: [ { attack: {$gte : 48}}, { height:{$lte : 0.5} } ]}
    db.pokemons.find(and2)
    { "_id" : ObjectId("56a7f43c52aa820658a17400"), "name" : "Pikachu", "description" : "Rato elétrico  bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }
    { "_id" : ObjectId("56a7f45a52aa820658a17401"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
    { "_id" : ObjectId("56a7f47e52aa820658a17403"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }
```