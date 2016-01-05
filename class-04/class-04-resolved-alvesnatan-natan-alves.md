# MongoDB - Aula 04 - Exercício
autor: Natan Alves

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
natan-stark(mongod-3.0.7) be-mean-instagram> var query = { $or: [ { name: /pikachu/i }, { name: /squirtle/i }, { name: /bulbassauro/i }, { name: /charmander/i } ] };

natan-stark(mongod-3.0.7) be-mean-instagram> var attacks = [ 'voadora louca', 'soco do poder' ];

natan-stark(mongod-3.0.7) be-mean-instagram> var mod = { $pushAll: { attacks: attacks} };

natan-stark(mongod-3.0.7) be-mean-instagram> var options = { multi: true };

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.update( query, mod, options );
Updated 4 existing record(s) in 1ms
WriteResult({
    "nMatched": 4,
    "nUpserted": 0,
    "nModified": 4
})

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.find( query );
{
    "_id": ObjectId("566c71e78549b41c1791da17"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4,
    "moves": [
        "investida",
        "choque do trovão"
    ],
    "active": false,
    "attacks": [
        "voadora louca",
        "soco do poder",
    ]
}
{
    "_id": ObjectId("566c72318549b41c1791da18"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c725b8549b41c1791da19"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72798549b41c1791da1a"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "active": false,
    "moves": [
        "investida",
        "hidro bomba"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
Fetched 4 record(s) in 23ms
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
natan-stark(mongod-3.0.7) be-mean-instagram> var query = {};

natan-stark(mongod-3.0.7) be-mean-instagram> var mod = { $push: { moves: 'desvio' } };

natan-stark(mongod-3.0.7) be-mean-instagram> var options = { multi: true };

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.update( query, mod, options );
Updated 11 existing record(s) in 1ms
WriteResult({
    "nMatched": 11,
    "nUpserted": 0,
    "nModified": 11
})

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.find( query );
{
    "_id": ObjectId("566c769c8549b41c1791da1b"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d896bb376adb121891013"),
    "name": "Mewtwo",
    "description": "Pokemon de laboratório foda pra caralho",
    "type": "psychic",
    "attack": 110,
    "height": 2,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d896eb376adb121891014"),
    "name": "Charizard",
    "description": "Dragão foda que cospe fogo",
    "type": "fire",
    "attack": 84,
    "height": 1.7,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d8972b376adb121891015"),
    "name": "Zubat",
    "description": "Morcego do batman",
    "type": "poison",
    "attack": 45,
    "height": 0.8,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d8976b376adb121891016"),
    "name": "Alakazam",
    "description": "Pira sua cabeça",
    "type": "rock",
    "attack": 50,
    "height": 1.5,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d897cb376adb121891017"),
    "name": "Onix",
    "description": "Snake de pedra",
    "type": "psychic",
    "attack": 45,
    "height": 8.8,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d9991b376adb121891019"),
    "description": "Pokemon de teste",
    "name": "Testemon",
    "attack": 8000,
    "defense": 8000,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566c71e78549b41c1791da17"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4,
    "moves": [
        "investida",
        "choque do trovão",
        "desvio"
    ],
    "active": false,
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72318549b41c1791da18"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c725b8549b41c1791da19"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72798549b41c1791da1a"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "active": false,
    "moves": [
        "investida",
        "hidro bomba",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
Fetched 11 record(s) in 127ms
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
natan-stark(mongod-3.0.7) be-mean-instagram> var query = { name: /AindaNaoExisteMon/i };

natan-stark(mongod-3.0.7) be-mean-instagram> var mod = { $setOnInsert: { name: 'AindaNaoExisteMon', attack: null, defense: null, height: null, description: 'Sem maiores informações' } };

natan-stark(mongod-3.0.7) be-mean-instagram> var options = { upsert: true };

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.update( query, mod, options );
Updated 1 new record(s) in 4ms
WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("566db6d76da63523ce3ff586")
})

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.find( query );
{
    "_id": ObjectId("566db6d76da63523ce3ff586"),
    "name": "AindaNaoExisteMon",
    "attack": null,
    "defense": null,
    "height": null,
    "description": "Sem maiores informações"
}
Fetched 1 record(s) in 2ms
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
natan-stark(mongod-3.0.7) be-mean-instagram> var query = { $and: [ { attacks: { $in: [ 'soco do poder' ] } }, { moves: { $in: [ 'investida' ] } } ] };

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.find( query );
{
    "_id": ObjectId("566c71e78549b41c1791da17"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4,
    "moves": [
        "investida",
        "choque do trovão",
        "desvio"
    ],
    "active": false,
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72318549b41c1791da18"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c725b8549b41c1791da19"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72798549b41c1791da1a"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "active": false,
    "moves": [
        "investida",
        "hidro bomba",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
Fetched 4 record(s) in 27ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
natan-stark(mongod-3.0.7) be-mean-instagram> var query = { attacks: { $all: [ 'soco do poder', 'voadora louca' ] } };

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.find( query );
{
    "_id": ObjectId("566c71e78549b41c1791da17"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4,
    "moves": [
        "investida",
        "choque do trovão",
        "desvio"
    ],
    "active": false,
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72318549b41c1791da18"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c725b8549b41c1791da19"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72798549b41c1791da1a"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "active": false,
    "moves": [
        "investida",
        "hidro bomba",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
Fetched 4 record(s) in 24ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
natan-stark(mongod-3.0.7) be-mean-instagram> var query = { type: { $not: /eletric/i } };

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.find( query );
{
    "_id": ObjectId("566c769c8549b41c1791da1b"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d896bb376adb121891013"),
    "name": "Mewtwo",
    "description": "Pokemon de laboratório foda pra caralho",
    "type": "psychic",
    "attack": 110,
    "height": 2,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d896eb376adb121891014"),
    "name": "Charizard",
    "description": "Dragão foda que cospe fogo",
    "type": "fire",
    "attack": 84,
    "height": 1.7,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d8972b376adb121891015"),
    "name": "Zubat",
    "description": "Morcego do batman",
    "type": "poison",
    "attack": 45,
    "height": 0.8,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d8976b376adb121891016"),
    "name": "Alakazam",
    "description": "Pira sua cabeça",
    "type": "rock",
    "attack": 50,
    "height": 1.5,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d897cb376adb121891017"),
    "name": "Onix",
    "description": "Snake de pedra",
    "type": "psychic",
    "attack": 45,
    "height": 8.8,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d9991b376adb121891019"),
    "description": "Pokemon de teste",
    "name": "Testemon",
    "attack": 8000,
    "defense": 8000,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566c72318549b41c1791da18"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c725b8549b41c1791da19"),
    "name": "Bulbassauro",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72798549b41c1791da1a"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "água",
    "attack": 48,
    "height": 0.5,
    "active": false,
    "moves": [
        "investida",
        "hidro bomba",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566db6d76da63523ce3ff586"),
    "name": "AindaNaoExisteMon",
    "attack": null,
    "defense": null,
    "height": null,
    "description": "Sem maiores informações"
}
Fetched 11 record(s) in 102ms

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
natan-stark(mongod-3.0.7) be-mean-instagram> var query = { $and: [ { moves: { $in: [ /investida/i ] } }, { attack: { $not: { $lte: 49 } } } ] };

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.find( query );
{
    "_id": ObjectId("566d896bb376adb121891013"),
    "name": "Mewtwo",
    "description": "Pokemon de laboratório foda pra caralho",
    "type": "psychic",
    "attack": 110,
    "height": 2,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d896eb376adb121891014"),
    "name": "Charizard",
    "description": "Dragão foda que cospe fogo",
    "type": "fire",
    "attack": 84,
    "height": 1.7,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d8976b376adb121891016"),
    "name": "Alakazam",
    "description": "Pira sua cabeça",
    "type": "rock",
    "attack": 50,
    "height": 1.5,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566d9991b376adb121891019"),
    "description": "Pokemon de teste",
    "name": "Testemon",
    "attack": 8000,
    "defense": 8000,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("566c71e78549b41c1791da17"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 55,
    "height": 0.4,
    "moves": [
        "investida",
        "choque do trovão",
        "desvio"
    ],
    "active": false,
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
{
    "_id": ObjectId("566c72318549b41c1791da18"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.6,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "desvio"
    ],
    "attacks": [
        "voadora louca",
        "soco do poder"
    ]
}
Fetched 6 record(s) in 40ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
natan-stark(mongod-3.0.7) be-mean-instagram> var query = { $and: [ { type: /água/i }, { attack: { $lt: 50 } } ] };

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.remove( query );
Removed 1 record(s) in 3ms
WriteResult({
    "nRemoved": 1
})

natan-stark(mongod-3.0.7) be-mean-instagram> db.pokemons.find( query );
Fetched 0 record(s) in 1ms
```