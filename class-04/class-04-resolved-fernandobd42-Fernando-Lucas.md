# MongoDb - Aula 04
autor: Fernando Lucas

Antes de continuar com nossos operadores, iremos aprender como alterar nossos documentos, pois precisaremos adicionar um *Array* em algum documento para posteriormente voltarmos a mais operadores de busca.

- [Update](./../../module-mongodb/update.md)


## Parte 1

Falei sobre onde enviar os exercícios oficialmente [https://github.com/Webschool-io/be-mean-instagram-mongodb-excercises](https://github.com/Webschool-io/be-mean-instagram-mongodb-excercises)

Sobre o artigo que tem prazo até dia 18 de novembro. [https://github.com/Webschool-io/be-mean-instagram-artigos](https://github.com/Webschool-io/be-mean-instagram-artigos)

Aí começamos o `update()`.

```
db.colecao.update(query, mod, options);
```

Mostrei o que acontece quando não se passa um operador de modificação para o `update`.

![](http://generator-meme.com/inc/media/memes/evil-kid.jpg)

Depois mostrei o `$set`, `$unset` e `$inc` para dai irmos para os Operadores de Array: `$push`, `$pushAll`, `$pull`, `$pullAll`.


## Parte 2

Falar sobre a documentação do MongoDb e como ela é boa.

Comecei a aula continuando no `update`, dessa vez falando do objeto options e seus atributos internos como: `upsert`, `multi` e `writeConcern`.

Depois de trabalharmos com os Arrays, agora voltaremos para nossas buscas, onde poderemos agora testar nossos operadores de busca em Arrays.

Utilizamos os operadores: `$in`, `$nin` e `$all`.


Se der tempo mostrar como buscar em objetos embedados.


## Exercício

### 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {name: /pikachu/i}
fernando(mongod-3.2.6) be-mean-pokemons> var mod = {$pushAll: {moves: ['Trovão neles', 'Raio verde']}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fernando(mongod-3.2.6) be-mean-pokemons> var query = {name: /squirtle/i}
fernando(mongod-3.2.6) be-mean-pokemons> var mod = {$pushAll: {moves: ['Wave frozen', 'Sessao 7 golpes']}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fernando(mongod-3.2.6) be-mean-pokemons> var query = {name: /bulbassauro/i}
fernando(mongod-3.2.6) be-mean-pokemons> var mod = {$pushAll: {moves: ['Wave fire', 'dança de pétalas']}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fernando(mongod-3.2.6) be-mean-pokemons> var query = {name: /charmander/i}
fernando(mongod-3.2.6) be-mean-pokemons> var mod = {$pushAll: {moves: ['Fire wave', 'Porrada']}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 3ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

### 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {}
fernando(mongod-3.2.6) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
fernando(mongod-3.2.6) be-mean-pokemons> var options = {multi: true}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 12 existing record(s) in 2ms
WriteResult({
  "nMatched": 12,
  "nUpserted": 0,
  "nModified": 12
})
```

### 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
fernando(mongod-3.2.6) be-mean-pokemons> var mod = {$setOnInsert: {name: 'AindaNaoExisteMon', type: null, attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
fernando(mongod-3.2.6) be-mean-pokemons> var options = {upsert: true}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("572e780de2d38a15d1fdf9b6")
})
```

### 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /fire wave/i]}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572b61faa1e3052ea6fd023a"),
  "name": "CunhaCu",
  "description": "Pokemon Ladrao/Safado",
  "type": "Ladrao",
  "attack": 9999,
  "defense": 9999,
  "height": 1.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023b"),
  "name": "AecioPo",
  "description": "Aspirador de Po",
  "type": "Cherador",
  "attack": 9999,
  "defense": 9999,
  "height": 1.82,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023c"),
  "name": "Fernando Collor",
  "description": "Aspirador Philco 2000",
  "type": "Cherador Nato",
  "attack": 8000,
  "defense": 8000,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023d"),
  "name": "Bolsonada",
  "description": "Militar Conservador",
  "type": "Careta",
  "attack": 5000,
  "defense": 5000,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023e"),
  "name": "Luladrao",
  "description": "Rouba de pobre",
  "type": "Cara Dura",
  "attack": 1000,
  "defense": 1000,
  "height": 1.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d7672dcb3b48d2bc977b8"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d7702dcb3b48d2bc977ba"),
  "name": "Charmander",
  "description": "O Cão chupando manga",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Fire wave",
    "Porrada",
    "desvio"
  ]
}
{
  "_id": ObjectId("572e5763ab2e5b5b52b063d3"),
  "description": "PokeTeste",
  "name": "The Teste",
  "attack": 8001,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d76c7dcb3b48d2bc977b9"),
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("572e66e1ab2e5b5b52b063d4"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Trovão neles",
    "Raio verde",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("572d772adcb3b48d2bc977bb"),
  "name": "Squirtle",
  "description": "Ejeta água destilada",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Wave frozen",
    "Sessao 7 golpes",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d7a5a7f16df60b250723e"),
  "name": "Bulbassauro",
  "description": "Chicote de bater em careta",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "Wave fire",
    "dança de pétalas",
    "desvio"
  ]
}
Fetched 12 record(s) in 8ms
```

### 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {moves: {$all: [/investida/i, /fire wave/i]}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d7702dcb3b48d2bc977ba"),
  "name": "Charmander",
  "description": "O Cão chupando manga",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Fire wave",
    "Porrada",
    "desvio"
  ]
}
Fetched 1 record(s) in 3ms
```

### 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {type: {$not: /elétrico/i}}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572b61faa1e3052ea6fd023a"),
  "name": "CunhaCu",
  "description": "Pokemon Ladrao/Safado",
  "type": "Ladrao",
  "attack": 9999,
  "defense": 9999,
  "height": 1.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023b"),
  "name": "AecioPo",
  "description": "Aspirador de Po",
  "type": "Cherador",
  "attack": 9999,
  "defense": 9999,
  "height": 1.82,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023c"),
  "name": "Fernando Collor",
  "description": "Aspirador Philco 2000",
  "type": "Cherador Nato",
  "attack": 8000,
  "defense": 8000,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023d"),
  "name": "Bolsonada",
  "description": "Militar Conservador",
  "type": "Careta",
  "attack": 5000,
  "defense": 5000,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023e"),
  "name": "Luladrao",
  "description": "Rouba de pobre",
  "type": "Cara Dura",
  "attack": 1000,
  "defense": 1000,
  "height": 1.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d7672dcb3b48d2bc977b8"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d7702dcb3b48d2bc977ba"),
  "name": "Charmander",
  "description": "O Cão chupando manga",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Fire wave",
    "Porrada",
    "desvio"
  ]
}
{
  "_id": ObjectId("572e5763ab2e5b5b52b063d3"),
  "description": "PokeTeste",
  "name": "The Teste",
  "attack": 8001,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d76c7dcb3b48d2bc977b9"),
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("572e66e1ab2e5b5b52b063d4"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Trovão neles",
    "Raio verde",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("572d772adcb3b48d2bc977bb"),
  "name": "Squirtle",
  "description": "Ejeta água destilada",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Wave frozen",
    "Sessao 7 golpes",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d7a5a7f16df60b250723e"),
  "name": "Bulbassauro",
  "description": "Chicote de bater em careta",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "folha navalha",
    "Wave fire",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("572e780de2d38a15d1fdf9b6"),
  "name": "AindaNaoExisteMon",
  "type": null,
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 13 record(s) in 10ms
```

### 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a attack **não menor ou igual** a 49.
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {$and:[ {moves: {$in: [/investida/i]}}, {attack: {$not: {$lte: 49}}}]}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572b61faa1e3052ea6fd023a"),
  "name": "CunhaCu",
  "description": "Pokemon Ladrao/Safado",
  "type": "Ladrao",
  "attack": 9999,
  "defense": 9999,
  "height": 1.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023b"),
  "name": "AecioPo",
  "description": "Aspirador de Po",
  "type": "Cherador",
  "attack": 9999,
  "defense": 9999,
  "height": 1.82,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023c"),
  "name": "Fernando Collor",
  "description": "Aspirador Philco 2000",
  "type": "Cherador Nato",
  "attack": 8000,
  "defense": 8000,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023d"),
  "name": "Bolsonada",
  "description": "Militar Conservador",
  "type": "Careta",
  "attack": 5000,
  "defense": 5000,
  "height": 1.9,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572b61faa1e3052ea6fd023e"),
  "name": "Luladrao",
  "description": "Rouba de pobre",
  "type": "Cara Dura",
  "attack": 1000,
  "defense": 1000,
  "height": 1.8,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d7702dcb3b48d2bc977ba"),
  "name": "Charmander",
  "description": "O Cão chupando manga",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "lança-chamas",
    "Fire wave",
    "Porrada",
    "desvio"
  ]
}
{
  "_id": ObjectId("572e5763ab2e5b5b52b063d3"),
  "description": "PokeTeste",
  "name": "The Teste",
  "attack": 8001,
  "defense": 8000,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("572d76c7dcb3b48d2bc977b9"),
  "moves": [
    "investida",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("572e66e1ab2e5b5b52b063d4"),
  "name": "Pikachu",
  "description": "Rato elétrico",
  "type": "eletric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "Trovão neles",
    "Raio verde",
    "desvio"
  ],
  "active": false
}
Fetched 9 record(s) in 8ms
```

### 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
fernando(mongod-3.2.6) be-mean-pokemons> var query = {$and: [ {type: /água/i}, {attack: {$lt : 50}} ]}
fernando(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("572d772adcb3b48d2bc977bb"),
  "name": "Squirtle",
  "description": "Ejeta água destilada",
  "type": "água",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "hidro bomba",
    "Wave frozen",
    "Sessao 7 golpes",
    "desvio"
  ]
}
Fetched 1 record(s) in 2ms
```

### 9. Demonstre qual a diferença entre os operadores '$ne' e '$not'
```
$ne, not equal, operador de comparação, não aceita rejex. Necessariamente o banco tem que ter o campo o qual está sendo buscado na função.
$not, note lógico, aceita regex.
```
