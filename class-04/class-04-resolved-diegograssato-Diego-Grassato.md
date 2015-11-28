# MongoDB - Aula 04 - Exercício
autor: Diego Pereira Grassato

### **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```javascript

var query = {name: /Pikachu/i}
var mod = {$pushAll: {moves: ['raio de luz', 'raio do trovão']}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms

var query = {name: /Squirtle/i}
var mod = {$pushAll: {moves: ['raio congelante', 'raio de gelo']}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms

var query = {name: /Bulbassauro/i}
var mod = {$pushAll: {moves: ['raio solar', 'semente sanguesuga']}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms

var query = {name: /Charmander/i}
var mod = {$pushAll: {moves: ['brasas', 'arranhão']}}
db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms

```

### **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```javascript

var query = {};
var mod = { $push: { moves: "desvio"}}
var opts = { multi: true }
db.pokemons.update(query, mod, opts)
Updated 6 existing record(s) in 1ms

```

### **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```javascript

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
Updated 1 new record(s) in 21ms

```

### Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```javascript

var query = {moves: {$in: [/investida/i, /arranhão/i]}}
db.pokemons.find(query);
{
  "_id": ObjectId("5645012b15f94b334d7d340e"),
  "attack": 55,
  "description": "Ponto forte: Ozzy",
  "height": 16.5,
  "moves": [
    "brasas",
    "arranhão",
    "desvio"
  ],
  "name": "Zubat",
  "type": "normal"
}
{
  "_id": ObjectId("5653ace3d30519df6a4f4e84"),
  "type": "elétrico",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "brasas",
    "arranhão"
  ],
  "name": "Charmander"
}

Fetched 2 record(s) in 2ms

```

### Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```javascript

var query = {moves: {$all: [/raio solar/i, /semente sanguesuga/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("5653acddd30519df6a4f4e83"),
  "moves": [
    "raio solar",
    "semente sanguesuga"
  ],
  "name": "Bulbassauro"
}

Fetched 1 record(s) in 1ms

```

### Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```javascript

var query = {type: {$ne: /elétrico/i}}
db.pokemons.find(query)
{{
  "_id": ObjectId("5645012b15f94b334d7d340b"),
  "attack": 95,
  "description": "Sapo ninja",
  "height": 88.2,
  "moves": [
    "desvio"
  ],
  "name": "Greninja",
  "type": "water"
}
{
  "_id": ObjectId("5645012b15f94b334d7d340c"),
  "attack": 110,
  "description": "Volcano",
  "height": 429.9,
  "moves": [
    "desvio"
  ],
  "name": "Volcanion",
  "type": "fire"
}
{
  "_id": ObjectId("5645012b15f94b334d7d340d"),
  "attack": 60,
  "description": "Quase o jack",
  "height": 4.4,
  "moves": [
    "desvio"
  ],
  "name": "Spearow",
  "type": "normal"
}
{
  "_id": ObjectId("5645012b15f94b334d7d340e"),
  "attack": 55,
  "description": "Ponto forte: Ozzy",
  "height": 16.5,
  "moves": [
    "brasas",
    "arranhão",
    "desvio"
  ],
  "name": "Zubat",
  "type": "normal"
}
{
  "_id": ObjectId("5653acd9d30519df6a4f4e82"),
  "moves": [
    "raio congelante",
    "raio de gelo"
  ],
  "name": "Squirtle"
}
{
  "_id": ObjectId("5653acddd30519df6a4f4e83"),
  "moves": [
    "raio solar",
    "semente sanguesuga"
  ],
  "name": "Bulbassauro"
}
{
  "_id": ObjectId("5645012b15f94b334d7d340a"),
  "attack": 125,
  "description": "Jiraiya",
  "height": 518.1,
  "moves": [
    "desvio",
    "semente sanguesuga"
  ],
  "name": "Gyarados",
  "type": "water"
}
{
  "_id": ObjectId("5653ac43d30519df6a4f4e81"),
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "height": null,
  "moves": [
    "desvio",
    "semente sanguesuga"
  ],
  "name": "AindaNaoExisteMon"
}
Fetched 8 record(s) in 5ms

```

### Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```javascript

var query = {$and: [ {moves: {$in: [/investida/i]}}, {defense: {$not: {$lte: 49}}} ]}
{
  "_id": ObjectId("5645012b15f94b334d7d340e"),
  "attack": 59,
  "description": "Ponto forte: Ozzy",
  "height": 16.5,
  "defense": 50,
  "moves": [
    "brasas",
    "arranhão",
    "desvio",
    "investida"
  ],
  "name": "Zubat",
  "type": "normal"
}
Fetched 1 record(s) in 2ms

```

### Remova **todos** os pokemons do tipo água E com attack menor que 50.

```javascript

var query = {$and: [ {type: /água/i}, {attack: {$lt: 50}} ]}
db.pokemons.remove(query)

```

### Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.

`$ne`**: seleciona os documentos onde o valor do campo não é igual (not equal em inglês) do especificado, ele não aceita REGEX.**

```javascript

var query = {description: {$ne: 'Jiraiya'}}
db.pokemons.find(query)

var query = {description: {$ne: /Jiraiya/i}}
db.pokemons.find(query)
error: {
  "$err": "invalid regular expression operator",
  "code": 13454
}

```

`$not`**: executa uma operação lógica NOT selecionando somente os documentos que não correspondem ao operador, ele também pode negar o resultadado de um operador, ele não aceita REGEX mas suporta expressões com //.**


```javascript

var query = {description: {$not: /Jiraiya/i}}
db.pokemons.find(query)

var query = {description: {$not: /^J/}}
db.pokemons.find(query)

var query = { attack: { $not: { $lt: 1.99 } } }
db.pokemons.find(query)

```
