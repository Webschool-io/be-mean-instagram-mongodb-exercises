### 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: 

* Pikachu
* Squirtle
* Bulbassauro 
* Charmander

```JS
var query = { 
  name : { 
    $in : [/Pikachu/i,/Squirtle/i,/Bulbassauro/i,/Charmander/i] 
  }
}; 

var mod = {
  $pushAll : { 
    moves : ["voadora", "mata leão"] 
  } 
};

var options = { multi : true };

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options);
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

```

**Resultado: Questão 01**

```JS
leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56509221e9f5531ca2501ac6"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "type": "electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "voadora",
    "mata leão"
  ]
}
{
  "_id": ObjectId("56509282e9f5531ca2501ac7"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection.",
  "type": "agua",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "voadora",
    "mata leão"
  ]
}
{
  "_id": ObjectId("565092ece9f5531ca2501ac8"),
  "name": "Bulbassauro",
  "description": "Bulbasaur can be seen napping in bright sunlight",
  "type": "grama",
  "attack": 80,
  "height": 0.7,
  "moves": [
    "voadora",
    "mata leão"
  ]
}
{
  "_id": ObjectId("56509324e9f5531ca2501ac9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "voadora",
    "mata leão"
  ]
}

```

### 2 Adicionar 1 movimento em todos os pokemons: desvio.

```JS
var query = {}; 

var mod = {
  $push : { moves : "desvio" }
};

var opt = { 
  multi : true 
};

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, opt);
Updated 9 existing record(s) in 3ms
WriteResult({
  "nMatched": 9,
  "nUpserted": 0,
  "nModified": 9
})

```

**Resultado da questão 02:**

```JS
leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("5644d6cbf92dd546a6b25ae4"),
  "name": "Charizard",
  "description": "Dragão feroz",
  "type": "Flame",
  "attack": 80,
  "height": 1.7,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d72cf92dd546a6b25ae5"),
  "name": "Pidgeot",
  "description": "This Pokémon is beatiful",
  "type": "Bird",
  "attack": 25,
  "height": 1.5,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d887f92dd546a6b25ae8"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "Shellfish",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d791f92dd546a6b25ae6"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "type": "Mouse",
  "attack": 50,
  "height": 0.8,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("56509282e9f5531ca2501ac7"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection.",
  "type": "agua",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("565092ece9f5531ca2501ac8"),
  "name": "Bulbassauro",
  "description": "Bulbasaur can be seen napping in bright sunlight",
  "type": "grama",
  "attack": 80,
  "height": 0.7,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d807f92dd546a6b25ae7"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. ",
  "type": "Legendary",
  "attack": 30,
  "height": 1.9,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("56509221e9f5531ca2501ac6"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "type": "electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("56509324e9f5531ca2501ac9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
Fetched 9 record(s) in 4ms

```  

### 3- Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

**Certificando que esse pokemon não existe no banco**

```JS
var query = { 
  name : /AindaNaoExisteMon/i
}; 

db.pokemons.find(query);

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
Fetched 0 record(s) in 0ms
```

**Executando o setOnInsert**

```JS
var query = { 
  name : /AindaNaoExisteMon/i
}; 

var mod = {
  $setOnInsert: {
    name: "AindaNaoExisteMon",
    description: "Sem maiores informações",
    type: null,
    attack: null,
    defense: null, 
    height: null
  }
};

var opt = { 
  upsert : true 
};

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.update( query, mod, opt );
Updated 1 new record(s) in 3ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("565098ebf80ec727f977334a")
})

```
**Verificando existência após executar**

```JS
leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find({_id: ObjectId("565098ebf80ec727f977334a")})
{
  "_id": ObjectId("565098ebf80ec727f977334a"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 1 record(s) in 1ms
```

### 4-Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.


**Adicionando Investida em Dois**

```JS

var query = { 
  name : { 
    $in : [/Pikachu/i,/Squirtle/i] 
  }
}; 

var mod = {
  $push : { moves : "investida" } 
};

var options = { multi : true };

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.update(query, mod, options);
Updated 2 existing record(s) in 1ms
WriteResult({
  "nMatched": 2,
  "nUpserted": 0,
  "nModified": 2
})

```

**Verificando se foi atualizado**

```JS

var query = { 
  name : { 
    $in : [/Pikachu/i,/Squirtle/i] 
  }
}; 

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56509282e9f5531ca2501ac7"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection.",
  "type": "agua",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56509221e9f5531ca2501ac6"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "type": "electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ]
}
Fetched 2 record(s) in 1ms
```

**Executando a query que a questão 04 pede**

> Optei pelo $all pelo fato de retornar documentos se todos os valores foram encontrados, já que o $in retorna se pelo menos um existir no array

```JS
var query = { 
  { $all : { moves : ['investida', 'voadora' ] } }
}; 

db.pokemons.find(query)
```

### 5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```JS
var query = {
  moves : { $in : [ /voadora/i, /mata leão/i ] }
};

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5644d6cbf92dd546a6b25ae4"),
  "name": "Charizard",
  "description": "Dragão feroz",
  "type": "Flame",
  "attack": 80,
  "height": 1.7,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d72cf92dd546a6b25ae5"),
  "name": "Pidgeot",
  "description": "This Pokémon is beatiful",
  "type": "Bird",
  "attack": 25,
  "height": 1.5,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d887f92dd546a6b25ae8"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "Shellfish",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d791f92dd546a6b25ae6"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "type": "Mouse",
  "attack": 50,
  "height": 0.8,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("56509282e9f5531ca2501ac7"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection.",
  "type": "agua",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("565092ece9f5531ca2501ac8"),
  "name": "Bulbassauro",
  "description": "Bulbasaur can be seen napping in bright sunlight",
  "type": "grama",
  "attack": 80,
  "height": 0.7,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d807f92dd546a6b25ae7"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. ",
  "type": "Legendary",
  "attack": 30,
  "height": 1.9,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("56509221e9f5531ca2501ac6"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "type": "electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("56509324e9f5531ca2501ac9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
Fetched 9 record(s) in 5ms

```  

### 6. Pesquisar todos os pokemons que não são do tipo elétrico.

**Consutando tipo elétrico**
```JS
leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find({type :'electric'});
{
  "_id": ObjectId("56509221e9f5531ca2501ac6"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "type": "electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ]
}
Fetched 1 record(s) in 1ms
```

```JS
var query = {
  type : { $ne  : 'electric' }
};

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5644d6cbf92dd546a6b25ae4"),
  "name": "Charizard",
  "description": "Dragão feroz",
  "type": "Flame",
  "attack": 80,
  "height": 1.7,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d72cf92dd546a6b25ae5"),
  "name": "Pidgeot",
  "description": "This Pokémon is beatiful",
  "type": "Bird",
  "attack": 25,
  "height": 1.5,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d887f92dd546a6b25ae8"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "Shellfish",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d791f92dd546a6b25ae6"),
  "name": "Raichu",
  "description": "If the electrical sacs become excessively charged, Raichu plants its tail in the ground and discharges.",
  "type": "Mouse",
  "attack": 50,
  "height": 0.8,
  "moves": [
    "ataque1",
    "ataque2",
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("56509282e9f5531ca2501ac7"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection.",
  "type": "agua",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ]
}
{
  "_id": ObjectId("565092ece9f5531ca2501ac8"),
  "name": "Bulbassauro",
  "description": "Bulbasaur can be seen napping in bright sunlight",
  "type": "grama",
  "attack": 80,
  "height": 0.7,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5644d807f92dd546a6b25ae7"),
  "name": "Arcanine",
  "description": "Arcanine is known for its high speed. It is said to be capable of running over 6,200 miles in a single day and night. ",
  "type": "Legendary",
  "attack": 30,
  "height": 1.9,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("56509324e9f5531ca2501ac9"),
  "name": "Charmander",
  "description": "The flame that burns at the tip of its tail is an indication of its emotions",
  "type": "fogo",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "voadora",
    "mata leão",
    "desvio"
  ]
}
{
  "_id": ObjectId("565098ebf80ec727f977334a"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null
}
Fetched 9 record(s) in 3ms
```

### 7. Pesquisar todos os pokemons que tenham o ataque investida e tenham a defesa não menor ou igual a 49.

```JS
var query = {
  moves : { $in : [/investida/i] },
  $and  : [ { defense : { $gt : 49 } }] 
};

db.pokemons.find(query);
```

**Resultado depois da consulta**
```JS
leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56509221e9f5531ca2501ac6"),
  "name": "Pikachu",
  "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity.",
  "type": "electric",
  "attack": 30,
  "height": 0.4,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ],
  "defense": 56
}
{
  "_id": ObjectId("56509282e9f5531ca2501ac7"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection.",
  "type": "agua",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ],
  "defense": 80
}
Fetched 2 record(s) in 2ms
``` 

### 8. Remova todos os pokemons do tipo água e com attack menor que 50.

**Verificando se tem algum do tipo agua**

```JS
leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("56509282e9f5531ca2501ac7"),
  "name": "Squirtle",
  "description": "Squirtle shell is not merely used for protection.",
  "type": "agua",
  "attack": 60,
  "height": 0.5,
  "moves": [
    "voadora",
    "mata leão",
    "desvio",
    "investida"
  ],
  "defense": 80
}
{
  "_id": ObjectId("5650b9f8eadbc35a898db833"),
  "name": "Golduck",
  "description": "The webbed flippers on its forelegs and hind legs and the streamlined body of Golduck give it frightening speed. ",
  "type": "agua",
  "attack": 40,
  "height": 1.7,
  "defense": 30
}
Fetched 2 record(s) in 2ms
```

```JS
var query = { 
  $and : [ 
    { 
      type   : "agua" 
    },
    { 
      attack : { $lt : 50 }
    }
  ]
};

leonardo(mongod-2.6.10) be-mean-pokemons> db.pokemons.remove(query);
Removed 1 record(s) in 2ms
WriteResult({
  "nRemoved": 1
})
```