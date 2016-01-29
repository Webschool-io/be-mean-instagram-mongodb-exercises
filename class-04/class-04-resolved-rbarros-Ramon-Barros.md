# MongoDB - Aula 04 - Exercício
autor: Ramon Barros


## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = {name: /Pikachu/i};
var mod = {$pushAll: {moves: ['choque elétrico', 'investida']}};
db.pokemons.update(query, mod);
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
db.pokemons.find(query)
{
  "_id": ObjectId("564fe98fc5812313fda55362"),
  "name": "Pikachu",
  "description": "Tem a capacidade de armazenar eletricidade.",
  "attack": 55,
  "defense": 40,
  "height": 4,
  "type": [
    "elétrico"
  ],
  "moves": [
    "choque elétrico",
    "investida"
  ]
}

var query = {name: /Squirtle/i};
var mod = {$pushAll: {moves: ['jatos de água', 'bolhas d`água']}};
db.pokemons.update(query, mod);
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

db.pokemons.find(query)
{
  "_id": ObjectId("564fec23c5812313fda55363"),
  "name": "Squirtle",
  "description": "É um pokémon tartaruga do tipo Água",
  "attack": 48,
  "defense": 65,
  "height": 5,
  "type": [
    "água"
  ],
  "moves": [
    "jatos de água",
    "bolhas d`água"
  ]
}

var query = {name: /Bulbassauro/i};
var mod = {$pushAll: {moves: ['raio solar', 'folha navalha']}};
db.pokemons.update(query, mod);
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

db.pokemons.find(query)
{
  "_id": ObjectId("564fed4ac5812313fda55364"),
  "name": "Bulbassauro",
  "description": "Pokémon dos tipos Grama e Venenoso",
  "attack": 49,
  "defense": 49,
  "height": 7,
  "type": [
    "veneno",
    "grama"
  ],
  "moves": [
    "raio solar",
    "folha navalha"
  ]
}

var query = {name: /Charmander/i};
var mod = {$pushAll: {moves: ['garra de metal', 'giro de fogo']}};
db.pokemons.update(query, mod);
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

db.pokemons.find(query)
{
  "_id": "564fedb1c5812313fda55365",
  "name": "Charmander",
  "description": "É um pokémon lagarto do tipo Fogo.",
  "attack": 52,
  "defense": 43,
  "height": 6,
  "type": [
    "fogo"
  ],
  "moves": [
    "garra de metal",
    "giro de fogo",
    "desvio"
  ]
}
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {};
var mod = {$push: {moves: 'desvio'}};
var options = {multi: true};
db.pokemons.update(query, mod, options);
WriteResult({ "nMatched" : 12, "nUpserted" : 0, "nModified" : 12 })
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = {name: /AindaNaoExisteMon/i};
var mod = {
    $setOnInsert: {
        name: 'AindaNaoExisteMon',
        attack: null, 
        defense: null, 
        height: null, 
        description: 'Sem maiores informações',
        type: [],
        moves: []
    }
};
var options = {$upsert: true};
db.pokemons.update(query, mod, options);

db.pokemons.find(query);
{
  "_id": "564feff6c5812313fda55366",
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "type": [],
  "moves": []
}
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves: {$in: ['investida', 'giro de fogo']}};
db.pokemons.find(query);
{
  "_id": ObjectId("564312e2af9b736e94f81e54"),
  "name": "Pidgey",
  "description": "Esse sabe onde fica o Alegrete",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "type": "bird",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564315a6af9b736e94f81e55"),
  "name": "Sandslash",
  "description": "Um rato com espinhos pontiagudos",
  "attack": 45,
  "defense": 55,
  "height": 0.7,
  "type": "ground",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564315baaf9b736e94f81e56"),
  "name": "Jigglypuff",
  "description": "Faz o inimigo dormir como um anjo.",
  "attack": 45,
  "defense": 25,
  "height": 0.5,
  "type": "fairy",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564315c8af9b736e94f81e57"),
  "name": "Ninetales",
  "description": "Dizem que pode viver até mil anos.",
  "attack": 81,
  "defense": 100,
  "height": 0.2,
  "type": "fire",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564ef2076ca5edf1d4c4985b"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("564f8bd8c5812313fda55361"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564fedb1c5812313fda55365"),
  "name": "Charmander",
  "description": "É um pokémon lagarto do tipo Fogo.",
  "attack": 52,
  "defense": 43,
  "height": 6,
  "type": [
    "fogo"
  ],
  "moves": [
    "garra de metal",
    "giro de fogo",
    "desvio"
  ]
}
{
  "_id": ObjectId("56431288af9b736e94f81e53"),
  "name": "Blastoise",
  "description": "Ele pode dispara balas de águas com precisão.",
  "attack": 85,
  "defense": 105,
  "height": 0.5,
  "type": "water",
  "active": false,
  "moves": [
    "investida",
    "balas de água",
    "desvio"
  ]
}
{
  "_id": ObjectId("564fe98fc5812313fda55362"),
  "name": "Pikachu",
  "description": "Tem a capacidade de armazenar eletricidade.",
  "attack": 55,
  "defense": 40,
  "height": 4,
  "type": [
    "elétrico"
  ],
  "moves": [
    "choque elétrico",
    "investida",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
var query = {moves: {$all: [/giro de fogo/, /garra de metal/]}}
db.pokemons.find(query);
{
  "_id": ObjectId("564fedb1c5812313fda55365"),
  "name": "Charmander",
  "description": "É um pokémon lagarto do tipo Fogo.",
  "attack": 52,
  "defense": 43,
  "height": 6,
  "type": [
    "fogo"
  ],
  "moves": [
    "garra de metal",
    "giro de fogo",
    "desvio"
  ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = {type: {$not: /eletrico/}};
db.pokemons.find(query);
{
  "_id": ObjectId("564312e2af9b736e94f81e54"),
  "name": "Pidgey",
  "description": "Esse sabe onde fica o Alegrete",
  "attack": 45,
  "defense": 40,
  "height": 0.3,
  "type": "bird",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("564315a6af9b736e94f81e55"),
  "name": "Sandslash",
  "description": "Um rato com espinhos pontiagudos",
  "attack": 45,
  "defense": 55,
  "height": 0.7,
  "type": "ground",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("564315baaf9b736e94f81e56"),
  "name": "Jigglypuff",
  "description": "Faz o inimigo dormir como um anjo.",
  "attack": 45,
  "defense": 25,
  "height": 0.5,
  "type": "fairy",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("564315c8af9b736e94f81e57"),
  "name": "Ninetales",
  "description": "Dizem que pode viver até mil anos.",
  "attack": 81,
  "defense": 100,
  "height": 0.2,
  "type": "fire",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("564ef2076ca5edf1d4c4985b"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}{
  "_id": ObjectId("564f8bd8c5812313fda55361"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("564fedb1c5812313fda55365"),
  "name": "Charmander",
  "description": "É um pokémon lagarto do tipo Fogo.",
  "attack": 52,
  "defense": 43,
  "height": 6,
  "moves": [
    "garra de metal",
    "giro de fogo",
    "desvio"
  ],
  "type": [
    "fogo"
  ]
}{
  "_id": ObjectId("56431288af9b736e94f81e53"),
  "name": "Blastoise",
  "description": "Ele pode dispara balas de águas com precisão.",
  "attack": 85,
  "defense": 105,
  "height": 0.5,
  "type": "water",
  "active": false,
  "moves": [
    "investida",
    "balas de água",
    "desvio"
  ]
}{
  "_id": ObjectId("564fec23c5812313fda55363"),
  "name": "Squirtle",
  "description": "É um pokémon tartaruga do tipo Água",
  "attack": 48,
  "defense": 65,
  "height": 5,
  "moves": [
    "jatos de água",
    "bolhas d`água",
    "desvio"
  ],
  "type": [
    "água"
  ]
}{
  "_id": ObjectId("564fed4ac5812313fda55364"),
  "name": "Bulbassauro",
  "description": "Pokémon dos tipos Grama e Venenoso",
  "attack": 49,
  "defense": 49,
  "height": 7,
  "moves": [
    "raio solar",
    "folha navalha",
    "desvio"
  ],
  "type": [
    "veneno",
    "grama"
  ]
}{
  "_id": ObjectId("564feff6c5812313fda55366"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
var query = {
    $and: [
        {
            moves: {
                $in: [ /investida/i ]
            }
        },
        {
            defense: {
                $not: {
                    $lte: 49
                }
            }
        }
    ]
};

db.pokemons.find(query);
{
  "_id": ObjectId("564315a6af9b736e94f81e55"),
  "name": "Sandslash",
  "description": "Um rato com espinhos pontiagudos",
  "attack": 45,
  "defense": 55,
  "height": 0.7,
  "type": "ground",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("564315c8af9b736e94f81e57"),
  "name": "Ninetales",
  "description": "Dizem que pode viver até mil anos.",
  "attack": 81,
  "defense": 100,
  "height": 0.2,
  "type": "fire",
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("564ef2076ca5edf1d4c4985b"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}{
  "_id": ObjectId("564f8bd8c5812313fda55361"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações",
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("564ef68ac5812313fda55360"),
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}{
  "_id": ObjectId("56431288af9b736e94f81e53"),
  "name": "Blastoise",
  "description": "Ele pode dispara balas de águas com precisão.",
  "attack": 85,
  "defense": 105,
  "height": 0.5,
  "type": "water",
  "active": false,
  "moves": [
    "investida",
    "balas de água",
    "desvio"
  ]
}
```


## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = {$and: [ {type: /água/i }, {$attack: {$lt: 50}} ] };
 db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })
```