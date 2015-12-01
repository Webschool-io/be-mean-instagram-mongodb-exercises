MongoDB - Aula 04 - Exercício
autor: Angelo Rogério Rubin

### Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

var query = { $or: [ 
    {name: /pikachu/i}, 
    {name: /squirtle/i}, 
    {name: /bulbassauro/i}, 
    {name: /charmander/i} ]};
var mod = { $pushAll: { moves: ['Agilidade','Poder Secreto']}};
var opts = { multi: true };
db.pokemons.update(query, mod, opts);

Updated 4 existing record(s) in 1ms

/* 1 */
{
    "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"),
    "name" : "Bulbassauro",
    "description" : "O chicote estrala",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "folha navalha", 
        "Agilidade", 
        "Poder Secreto"
    ]
}

/* 2 */
{
    "_id" : ObjectId("5644f44da2c7f2543fe0ff49"),
    "name" : "Charmander",
    "description" : "Taca fogo nele chessuis",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "moves" : [ 
        "investida", 
        "lança-chamas", 
        "Agilidade", 
        "Poder Secreto"
    ]
}

/* 3 */
{
    "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"),
    "name" : "Squirtle",
    "description" : "Ejeta agua",
    "type" : "agua",
    "attack" : 48.0000000000000000,
    "height" : 0.5000000000000000,
    "active" : true,
    "moves" : [ 
        "investida", 
        "hidro bomba", 
        "Agilidade", 
        "Poder Secreto"
    ]
}

/* 4 */
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "moves" : [ 
        "investida"
    ]
}

/* 5 */
{
    "_id" : ObjectId("564d960f6649e8f84410a7f8"),
    "description" : "Pokemon de teste",
    "name" : "Testmon",
    "attack" : 7900.0000000000000000,
    "defense" : 8000.0000000000000000,
    "height" : 2.1000000000000001,
    "moves" : [ 
        "investida"
    ]
}

/* 6 */
{
    "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"),
    "name" : "Pikachu",
    "description" : "Rato Elétrico",
    "type" : "eletric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "choque do trovão", 
        "Agilidade", 
        "Poder Secreto"
    ]
}

### Adicionar 1 movimento em todos os pokemons: desvio.

var query = {};
var mod = { $push: { moves: "desvio"}}
var opts = { multi: true }
db.pokemons.update(query, mod, opts)

Updated 6 existing record(s) in 1ms

/* 1 */
{
    "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"),
    "name" : "Bulbassauro",
    "description" : "O chicote estrala",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "folha navalha", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("5644f44da2c7f2543fe0ff49"),
    "name" : "Charmander",
    "description" : "Taca fogo nele chessuis",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "moves" : [ 
        "investida", 
        "lança-chamas", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"),
    "name" : "Squirtle",
    "description" : "Ejeta agua",
    "type" : "agua",
    "attack" : 48.0000000000000000,
    "height" : 0.5000000000000000,
    "active" : true,
    "moves" : [ 
        "investida", 
        "hidro bomba", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 4 */
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 5 */
{
    "_id" : ObjectId("564d960f6649e8f84410a7f8"),
    "description" : "Pokemon de teste",
    "name" : "Testmon",
    "attack" : 7900.0000000000000000,
    "defense" : 8000.0000000000000000,
    "height" : 2.1000000000000001,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 6 */
{
    "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"),
    "name" : "Pikachu",
    "description" : "Rato Elétrico",
    "type" : "eletric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "choque do trovão", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

### Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

var query = { name: /AindaNaoExisteMon/i };
var mod = { $setOnInsert: {
    name: "AindaNaoExisteMon",
    attack: null,
    height: null,
    defense: null,
    moves: [],
    description: "Sem maiores informações"
}};
var opts = { upsert: true };
db.pokemons.update(query, mod, opts);

Updated 1 new record(s) in 1ms

/* 1 */
{
    "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"),
    "name" : "Bulbassauro",
    "description" : "O chicote estrala",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "folha navalha", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("5644f44da2c7f2543fe0ff49"),
    "name" : "Charmander",
    "description" : "Taca fogo nele chessuis",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "moves" : [ 
        "investida", 
        "lança-chamas", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"),
    "name" : "Squirtle",
    "description" : "Ejeta agua",
    "type" : "agua",
    "attack" : 48.0000000000000000,
    "height" : 0.5000000000000000,
    "active" : true,
    "moves" : [ 
        "investida", 
        "hidro bomba", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 4 */
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 5 */
{
    "_id" : ObjectId("564d960f6649e8f84410a7f8"),
    "description" : "Pokemon de teste",
    "name" : "Testmon",
    "attack" : 7900.0000000000000000,
    "defense" : 8000.0000000000000000,
    "height" : 2.1000000000000001,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 6 */
{
    "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"),
    "name" : "Pikachu",
    "description" : "Rato Elétrico",
    "type" : "eletric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "choque do trovão", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 7 */
{
    "_id" : ObjectId("564e7add584789425c447007"),
    "name" : "AindaNaoExisteMon",
    "attack" : null,
    "height" : null,
    "defense" : null,
    "moves" : [],
    "description" : "Sem maiores informações"
}

### Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.

var query = { moves: { $in: ['investida', /choque do trovão/i] }};
db.pokemons.find(query);

/* 1 */
{
    "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"),
    "name" : "Bulbassauro",
    "description" : "O chicote estrala",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "folha navalha", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("5644f44da2c7f2543fe0ff49"),
    "name" : "Charmander",
    "description" : "Taca fogo nele chessuis",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "moves" : [ 
        "investida", 
        "lança-chamas", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"),
    "name" : "Squirtle",
    "description" : "Ejeta agua",
    "type" : "agua",
    "attack" : 48.0000000000000000,
    "height" : 0.5000000000000000,
    "active" : true,
    "moves" : [ 
        "investida", 
        "hidro bomba", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 4 */
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 5 */
{
    "_id" : ObjectId("564d960f6649e8f84410a7f8"),
    "description" : "Pokemon de teste",
    "name" : "Testmon",
    "attack" : 7900.0000000000000000,
    "defense" : 8000.0000000000000000,
    "height" : 2.1000000000000001,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 6 */
{
    "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"),
    "name" : "Pikachu",
    "description" : "Rato Elétrico",
    "type" : "eletric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "choque do trovão", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

### Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

var query = { moves: { $in: [/desvio/i] }};
db.pokemons.find(query);

/* 1 */
{
    "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"),
    "name" : "Bulbassauro",
    "description" : "O chicote estrala",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "folha navalha", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("5644f44da2c7f2543fe0ff49"),
    "name" : "Charmander",
    "description" : "Taca fogo nele chessuis",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "moves" : [ 
        "investida", 
        "lança-chamas", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"),
    "name" : "Squirtle",
    "description" : "Ejeta agua",
    "type" : "agua",
    "attack" : 48.0000000000000000,
    "height" : 0.5000000000000000,
    "active" : true,
    "moves" : [ 
        "investida", 
        "hidro bomba", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 4 */
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 5 */
{
    "_id" : ObjectId("564d960f6649e8f84410a7f8"),
    "description" : "Pokemon de teste",
    "name" : "Testmon",
    "attack" : 7900.0000000000000000,
    "defense" : 8000.0000000000000000,
    "height" : 2.1000000000000001,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 6 */
{
    "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"),
    "name" : "Pikachu",
    "description" : "Rato Elétrico",
    "type" : "eletric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "choque do trovão", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

### Pesquisar todos os pokemons que não são do tipo elétrico.

var query = { type: { $ne: "eletric" }};
db.pokemons.find(query)

/* 1 */
{
    "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"),
    "name" : "Bulbassauro",
    "description" : "O chicote estrala",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "folha navalha", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("5644f44da2c7f2543fe0ff49"),
    "name" : "Charmander",
    "description" : "Taca fogo nele chessuis",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "moves" : [ 
        "investida", 
        "lança-chamas", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("5644f4bca2c7f2543fe0ff4a"),
    "name" : "Squirtle",
    "description" : "Ejeta agua",
    "type" : "agua",
    "attack" : 48.0000000000000000,
    "height" : 0.5000000000000000,
    "active" : true,
    "moves" : [ 
        "investida", 
        "hidro bomba", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 4 */
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 5 */
{
    "_id" : ObjectId("564d960f6649e8f84410a7f8"),
    "description" : "Pokemon de teste",
    "name" : "Testmon",
    "attack" : 7900.0000000000000000,
    "defense" : 8000.0000000000000000,
    "height" : 2.1000000000000001,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 6 */
{
    "_id" : ObjectId("564e7add584789425c447007"),
    "name" : "AindaNaoExisteMon",
    "attack" : null,
    "height" : null,
    "defense" : null,
    "moves" : [],
    "description" : "Sem maiores informações"
}

### Pesquisar todos os pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.

var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $lte: 49 }}]};
db.pokemons.find(query)

/* 1 */
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

Remova todos os pokemons do tipo água e com attack menor que 50.

var query = { $and:[ { type: "agua" }, { attack: { $lt: 50 }} ]};
db.pokemons.remove(query);

Removed 1 record(s) in 1ms

/* 1 */
{
    "_id" : ObjectId("5644f3f9a2c7f2543fe0ff48"),
    "name" : "Bulbassauro",
    "description" : "O chicote estrala",
    "type" : "grama",
    "attack" : 49.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "folha navalha", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 2 */
{
    "_id" : ObjectId("5644f44da2c7f2543fe0ff49"),
    "name" : "Charmander",
    "description" : "Taca fogo nele chessuis",
    "type" : "fogo",
    "attack" : 52.0000000000000000,
    "height" : 0.6000000000000000,
    "moves" : [ 
        "investida", 
        "lança-chamas", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 3 */
{
    "_id" : ObjectId("5644fd892d657aa215659584"),
    "name" : "Caterpie",
    "description" : "Larva lutadora",
    "type" : "inseto",
    "attack" : 30.0000000000000000,
    "height" : 0.3000000000000000,
    "defense" : 35.0000000000000000,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 4 */
{
    "_id" : ObjectId("564d960f6649e8f84410a7f8"),
    "description" : "Pokemon de teste",
    "name" : "Testmon",
    "attack" : 7900.0000000000000000,
    "defense" : 8000.0000000000000000,
    "height" : 2.1000000000000001,
    "moves" : [ 
        "investida", 
        "desvio"
    ]
}

/* 5 */
{
    "_id" : ObjectId("5644ead9a2c7f2543fe0ff45"),
    "name" : "Pikachu",
    "description" : "Rato Elétrico",
    "type" : "eletric",
    "attack" : 55.0000000000000000,
    "height" : 0.4000000000000000,
    "moves" : [ 
        "investida", 
        "choque do trovão", 
        "Agilidade", 
        "Poder Secreto", 
        "desvio"
    ]
}

/* 6 */
{
    "_id" : ObjectId("564e7add584789425c447007"),
    "name" : "AindaNaoExisteMon",
    "attack" : null,
    "height" : null,
    "defense" : null,
    "moves" : [],
    "description" : "Sem maiores informações"
}