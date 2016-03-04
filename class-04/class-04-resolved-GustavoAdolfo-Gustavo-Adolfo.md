# MongoDB - Aula 03 - Exercício
autor: Gustavo Adolfo

##1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons, Pikachu, Squirtle, Bulbassauro e Charmander.

> var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};  
> var mod = { $pushAll: { moves: ['ataque disfrente','ataque discosta']}};  
> var option = { multi: true };  
> db.pokemons.update(query, mod, option);  
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })  

##2. Adicionar 1 movimento em todos os pokemons: 'desvio'.

> var query = {}  
> var mod = { $push: { moves: 'desvio'}};  
> var option = { multi: true };  
> db.pokemons.update(query, mod, option);  
WriteResult({ "nMatched" : 6, "nUpserted" : 0, "nModified" : 6 })  

##3. Adicionar o pokemon 'AindaNaoExisteMon' caso ele nao exista com todos os dados com o valor 'null' e a descricao: 'Sem maiores informacoes'.

> var query = { name: /AindaNaoExisteMon/i };  
> var mod = { $setOnInsert: {  
    name: "AindaNaoExisteMon"  
  , attack: null  
  , height: null  
  , defense: null  
  , moves: []  
  , description: "Sem maiores informações"  
}};    
> var option = { upsert: true };  
> db.pokemons.update(query, mod, option);  
WriteResult({  
    "nMatched" : 0,  
    "nUpserted" : 1,  
    "nModified" : 0,  
    "_id" : ObjectId("56d593365d01e7f9af4a972a"))  
})

##4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que voce adicionou, escolha seu pokemon favorito.

> var query = { moves: { $in: ['investida', 'lança-chamas']}};  
> db.pokemons.find(query).pretty();
{
        "_id" : ObjectId("56c860be06d4893022ac072c"),
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
        "type" : "electric",
        "attack" : 100,
        "height" : 0.4,
        "active" : false,
        "moves" : [
                "investida",
                "choque do trovão",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac072d"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4,
        "active" : false,
        "moves" : [
                "investida",
                "folha navalha",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac072e"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6,
        "active" : false,
        "moves" : [
                "investida",
                "lança-chamas",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac072f"),
        "name" : "Squirtle",
        "description" : "Pokemon mijão",
        "type" : "água",
        "attack" : 48,
        "height" : 0.5,
        "active" : false,
        "moves" : [
                "investida",
                "hidrobomba",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac0730"),
        "name" : "Caterpie",
        "description" : "Larva lutadora",
        "type" : "inseto",
        "attack" : 30,
        "height" : 0.3,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56d582b95d01e7f9af4a9728"),
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}

##5. Pesquisar todos os pokemons que possuam os ataques que voce adicionou, escolha seu pokemon favorito.

> var query = { moves: { $all: [/ataque disfrente/i, /ataque discosta/i]}}
> db.pokemons.find(query).pretty();
{
        "_id" : ObjectId("56c860be06d4893022ac072c"),
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
        "type" : "electric",
        "attack" : 100,
        "height" : 0.4,
        "active" : false,
        "moves" : [
                "investida",
                "choque do trovão",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac072d"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4,
        "active" : false,
        "moves" : [
                "investida",
                "folha navalha",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac072e"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6,
        "active" : false,
        "moves" : [
                "investida",
                "lança-chamas",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac072f"),
        "name" : "Squirtle",
        "description" : "Pokemon mijão",
        "type" : "água",
        "attack" : 48,
        "height" : 0.5,
        "active" : false,
        "moves" : [
                "investida",
                "hidrobomba",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac0730"),
        "name" : "Caterpie",
        "description" : "Larva lutadora",
        "type" : "inseto",
        "attack" : 30,
        "height" : 0.3,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56d582b95d01e7f9af4a9728"),
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}

##6. Pesquisar todos os pokemons que nao sao do tipo 'eletrico'.

> var query = { type: {$ne: "electric"}}  
> db.pokemons.find(query).pretty();
{
        "_id" : ObjectId("56c860be06d4893022ac072d"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4,
        "active" : false,
        "moves" : [
                "investida",
                "folha navalha",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac072e"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6,
        "active" : false,
        "moves" : [
                "investida",
                "lança-chamas",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac072f"),
        "name" : "Squirtle",
        "description" : "Pokemon mijão",
        "type" : "água",
        "attack" : 48,
        "height" : 0.5,
        "active" : false,
        "moves" : [
                "investida",
                "hidrobomba",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56c860be06d4893022ac0730"),
        "name" : "Caterpie",
        "description" : "Larva lutadora",
        "type" : "inseto",
        "attack" : 30,
        "height" : 0.3,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56d582b95d01e7f9af4a9728"),
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("56d593365d01e7f9af4a972a"),
        "name" : "AindaNaoExistemon",
        "attack" : null,
        "height" : null,
        "defense" : null,
        "moves" : [ ],
        "description" : "Sem maiores informações"
}

##7. Pesquisar todos os pokemons que tenha o ataque 'investida' E tenham a defesa nao menor ou igual a  49.

> var query = { moves: {$in:['investida']}, defesa : {$gte: 49} };
> db.pokemons.find(query).pretty();
{
        "_id" : ObjectId("56c860be06d4893022ac072d"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4,
        "active" : false,
        "moves" : [
                "investida",
                "folha navalha",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ],
        "defesa" : 71
}
{
        "_id" : ObjectId("56c860be06d4893022ac072f"),
        "name" : "Squirtle",
        "description" : "Pokemon mijão",
        "type" : "água",
        "attack" : 48,
        "height" : 0.5,
        "active" : false,
        "moves" : [
                "investida",
                "hidrobomba",
                "ataque difrente",
                "ataque discosta",
                "desvio"
        ],
        "defesa" : 71
}
{
        "_id" : ObjectId("56c860be06d4893022ac0730"),
        "name" : "Caterpie",
        "description" : "Larva lutadora",
        "type" : "inseto",
        "attack" : 30,
        "height" : 0.3,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ],
        "defesa" : 71
}

##8. Remova todos os pokemons do tipo agua e com attack menor que 50.

> var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]};  
> db.pokemons.remove(query);  
WriteResult({ "nRemoved" : 3 })  