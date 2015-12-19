# MongoDB - Aula 04 - Exercício
autor: Geriel Castro

### **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```javascript
var query = { $or: [ {name: /pikachu/i}, {name: /squirtle/i}, {name: /bulbassauro/i}, {name: /charmander/i} ]};
var mod = {$pushAll:{moves:['Investida Dupla','Ataque combinado']}}
var opt = {multi: true}

db.pokemons.update(query, mod, opt)

Updated 4 existing record(s) in 18ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

### **Adicionar** 1 movimento em todos os pokemons: `desvio`.###
```javascript
var query = {};
var mod = {$push: {moves: "desvio"}}
var opt = {multi: true}
db.pokemons.update(query, mod, opt)
Updated 6 existing record(s) in 25ms
WriteResult({
  "nMatched": 6,
  "nUpserted": 0,
  "nModified": 6
})
```

### **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".###
```javascript
var query = {name: /AindaNaoExisteMon/i };
var mod = { $setOnInsert: {name: "AindaNaoExisteMon", attack: null, height: null, defense: null, moves: [], description: "Sem maiores informações"}};
var opt = {upsert: true};

db.pokemons.update(query, mod, opt);

Updated 1 new record(s) in 24ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564f373f98e11be042005d78")
})

```

### Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.###
```javascript
var query = {moves: {$in: [/investida/i, /Ataque combinado/i]}}
db.pokemons.find(query)
{
  "_id": ObjectId("5642e16fced08cfd55d2bc02"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e3bbced08cfd55d2bc03"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "folha navalha",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e3ddced08cfd55d2bc04"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Lanca chamas",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e40fced08cfd55d2bc05"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Hidro Bomba",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
Fetched 4 record(s) in 7ms
```

### Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.###
```javascript
var query = { moves: { $in: [/Ataque combinado/i] }};
db.pokemons.find(query)
{
  "_id": ObjectId("5642e16fced08cfd55d2bc02"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e3bbced08cfd55d2bc03"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "folha navalha",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e3ddced08cfd55d2bc04"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Lanca chamas",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e40fced08cfd55d2bc05"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Hidro Bomba",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
Fetched 4 record(s) in 37ms
```

### Pesquisar **todos** os pokemons que não são do tipo `elétrico`.###
```javascript
var query = {type: {$ne: 'eletric'}}
db.pokemons.find(query)
{
  "_id": ObjectId("5642e3bbced08cfd55d2bc03"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "folha navalha",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e4f4ced08cfd55d2bc06"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35,
  "active": false,
  "moves": [
    "Investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("564dbbc298e11be042005d77"),
  "active": false,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem mais descrição",
  "moves": [
    "Investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e3ddced08cfd55d2bc04"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Lanca chamas",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e40fced08cfd55d2bc05"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Hidro Bomba",
    "Investida Dupla",
    "Ataque combinado",
    "desvio"
  ]
}
{
  "_id": ObjectId("564f373f98e11be042005d78"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "height": null,
  "defense": null,
  "moves": [ ],
  "description": "Sem maiores informações"
}
Fetched 6 record(s) in 31ms
```

### Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.###
```javascript
var query = {$and : [{moves: /investida/i}, {attack : {$not : {$lte: 49}}}]}
db.pokemons.find(query)
Fetched 0 record(s) in 3ms

Quote break.

> *Acredite, eu fiquei meio intrigado de não ter vindo nenhum Resultado, mas moves não tem nenhum ataque investida. rs*

#### Nova busca após adicionar ataque investida nos pokemonss: Pikachu, Squirtle, Bulbassauro e Charmander.

var query = {$and : [{moves: /investida/i}, {attack : {$not : {$lte: 49}}}]}
db.pokemons.find(query)
{
  "_id": ObjectId("564dbbc298e11be042005d77"),
  "active": false,
  "name": "NãoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem mais descrição",
  "moves": [
    "Investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5642e3ddced08cfd55d2bc04"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "Lanca chamas",
    "Investida Dupla",
    "Ataque combinado",
    "desvio",
    "Investida Dupla",
    "Investida"
  ]
}
{
  "_id": ObjectId("5642e16fced08cfd55d2bc02"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "active": false,
  "moves": [
    "Investida",
    "Investida Dupla",
    "Ataque combinado",
    "desvio",
    "Investida Dupla",
    "Investida"
  ]
}
Fetched 3 record(s) in 21ms

```

### Remova **todos** os pokemons do tipo água e com attack menor que 50.###
```javascript

var query = { $and:[ { type: /água/i }, { attack: { $lt: 50 }} ]};
db.pokemons.find(query)
{
  "_id": ObjectId("5642e40fced08cfd55d2bc05"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "Hidro Bomba",
    "Investida Dupla",
    "Ataque combinado",
    "desvio",
    "Investida Dupla",
    "Investida"
  ]
}
Fetched 1 record(s) in 3ms

db.pokemons.remove(query)
Removed 1 record(s) in 6ms
WriteResult({
  "nRemoved": 1
})

```
