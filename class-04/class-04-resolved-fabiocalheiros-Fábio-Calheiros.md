# MongoDB - Aula 04 - Exercício
autor: Fábio Calheiros (conta: fabiocalheiros)

# 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemos: Pikachu, Squirtle, Bulbassauro e Charmander.

```

fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {name: /Pikachu/i}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['esfera elétrica', 'investida trovão']}}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648e8d99f352c534ac8813d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão"
  ]
}
Fetched 1 record(s) in 1ms



fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {name: /Squirtle/i}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['raio de gelo', 'giro rápido']}}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565cd29e5ccc6465c4b53b25"),
  "active": false,
  "type": "água",
  "name": "Squirtle",
  "attack": 48,
  "height": 0.5,
  "description": "Ejeta água que passarinho não bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "raio de gelo",
    "giro rápido"
  ]
}
Fetched 1 record(s) in 1ms

fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {name: /Bulbassauro/i}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['raio solar', 'dança de pétalas']}}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648e96b9f352c534ac8813e"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "dança de pétalas"
  ]
}
Fetched 1 record(s) in 0ms


fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {name: /Charmander/i}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: ['brasas', 'encarar']}}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648e96b9f352c534ac8813f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar"
  ]
}
Fetched 1 record(s) in 1ms

```

# 2. **Adicionar** 1 movimento em todos os pokemons: 'desvio'.

```

fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: 'desvio'}}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 11 existing record(s) in 2ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648df98b054309b54e25e10"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "Water",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e11"),
  "name": "Charizard",
  "description": "Pokemon ninja doidao",
  "type": "Fire",
  "attack": 40,
  "height": 1.7,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e12"),
  "name": "Jigglypuff",
  "description": "Jigglypuffs vocal cords canfreely adjust the wavelength of its voice",
  "type": "Normal",
  "attack": 20,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e13"),
  "name": "Zubat",
  "description": "Zubat remains quietly unmoving ina dark spot during the bright daylight hours",
  "type": "Poison",
  "attack": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e7c79f352c534ac8813c"),
  "name": "Electrike",
  "description": "Electrike stores electricity in its long body hair",
  "type": "Eletric",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e96b9f352c534ac8813e"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a5bf39c3c0df5b76d7ab0"),
  "name": "Testemon",
  "attack": 7900,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e8d99f352c534ac8813d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e96b9f352c534ac8813f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar",
    "desvio"
  ]
}
{
  "_id": ObjectId("565cd29e5ccc6465c4b53b25"),
  "active": false,
  "type": "água",
  "name": "Squirtle",
  "attack": 48,
  "height": 0.5,
  "description": "Ejeta água que passarinho não bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "raio de gelo",
    "giro rápido",
    "desvio"
  ]
}
Fetched 10 record(s) in 3ms


```

# 3. **Adicionar** o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações".

```

fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert:
...   {
...     name: 'AindaNaoExisteMon',
...     type: null,
...     attack: null, 
...     defense: null, 
...     height: null, 
...     description: "Sem maiores informações"
...   }
... }
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query, mod)
Updated 1 existing record(s) in 2ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 0
})
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("565b82565ccc6465c4b4d815"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms

```

# 4. Pesquisar todos os pokemons que possuem o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.

```

fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ['investida', 'esfera elétrica']}}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648df98b054309b54e25e10"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "Water",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e11"),
  "name": "Charizard",
  "description": "Pokemon ninja doidao",
  "type": "Fire",
  "attack": 40,
  "height": 1.7,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e12"),
  "name": "Jigglypuff",
  "description": "Jigglypuffs vocal cords canfreely adjust the wavelength of its voice",
  "type": "Normal",
  "attack": 20,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e13"),
  "name": "Zubat",
  "description": "Zubat remains quietly unmoving ina dark spot during the bright daylight hours",
  "type": "Poison",
  "attack": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e7c79f352c534ac8813c"),
  "name": "Electrike",
  "description": "Electrike stores electricity in its long body hair",
  "type": "Eletric",
  "attack": 30,
  "height": 0.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e96b9f352c534ac8813e"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a5bf39c3c0df5b76d7ab0"),
  "name": "Testemon",
  "attack": 7900,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("565b82565ccc6465c4b4d815"),
  "name": "AindaNaoExisteMon",
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
  "_id": ObjectId("5648e8d99f352c534ac8813d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e96b9f352c534ac8813f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar",
    "desvio"
  ]
}
{
  "_id": ObjectId("565cd29e5ccc6465c4b53b25"),
  "active": false,
  "type": "água",
  "name": "Squirtle",
  "attack": 48,
  "height": 0.5,
  "description": "Ejeta água que passarinho não bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "raio de gelo",
    "giro rápido",
    "desvio"
  ]
}
Fetched 11 record(s) in 4ms



```

# 5. Pesquisar **todos** os pokemons que possuem os ataques que você adicionou, escolha o seu pokemon favorito

 var query = {moves: {$all: [/investida trovão/i, /esfera elétrica/i]}}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("5648e8d99f352c534ac8813d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
Fetched 1 record(s) in 1ms


```

# 6. Pesquisar **todos** os pokemons que não são do tipo 'eletrico'.

```
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$not: /electric/i}}
 db.pokemons.find(query)
{
  "_id": ObjectId("5648df98b054309b54e25e10"),
  "name": "Blastoise",
  "description": "Blastoise has water spouts that protrude from its shell",
  "type": "Water",
  "attack": 40,
  "height": 1.6,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e11"),
  "name": "Charizard",
  "description": "Pokemon ninja doidao",
  "type": "Fire",
  "attack": 40,
  "height": 1.7,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e12"),
  "name": "Jigglypuff",
  "description": "Jigglypuffs vocal cords canfreely adjust the wavelength of its voice",
  "type": "Normal",
  "attack": 20,
  "height": 0.5,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648df98b054309b54e25e13"),
  "name": "Zubat",
  "description": "Zubat remains quietly unmoving ina dark spot during the bright daylight hours",
  "type": "Poison",
  "attack": 20,
  "height": 0.8,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e96b9f352c534ac8813e"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4,
  "moves": [
    "investida",
    "folha navalha",
    "raio solar",
    "dança de pétalas",
    "desvio"
  ]
}
{
  "_id": ObjectId("564a5bf39c3c0df5b76d7ab0"),
  "name": "Testemon",
  "attack": 7900,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("565b82565ccc6465c4b4d815"),
  "name": "AindaNaoExisteMon",
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
  "_id": ObjectId("5648e96b9f352c534ac8813f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar",
    "desvio"
  ]
}
{
  "_id": ObjectId("565cd29e5ccc6465c4b53b25"),
  "active": false,
  "type": "água",
  "name": "Squirtle",
  "attack": 48,
  "height": 0.5,
  "description": "Ejeta água que passarinho não bebe",
  "moves": [
    "investida",
    "hidro bomba",
    "raio de gelo",
    "giro rápido",
    "desvio"
  ]
}
Fetched 9 record(s) in 2ms


```

# 7. Pesquisar **todos** os pokemons que tenham o ataque 'investida' **E** tenham a defesa **Não menor ou igual a 49**.


```

fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in: ['investida']}}, {attack: {$not: {$lte: 49}}}]}
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("564a5bf39c3c0df5b76d7ab0"),
  "name": "Testemon",
  "attack": 7900,
  "defense": 8000,
  "description": "Pokemon de teste",
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("565b82565ccc6465c4b4d815"),
  "name": "AindaNaoExisteMon",
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
  "_id": ObjectId("5648e8d99f352c534ac8813d"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attack": 55,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "esfera elétrica",
    "investida trovão",
    "desvio"
  ]
}
{
  "_id": ObjectId("5648e96b9f352c534ac8813f"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6,
  "moves": [
    "investida",
    "lança-chamas",
    "brasas",
    "encarar",
    "desvio"
  ]
}
Fetched 4 record(s) in 1ms



```

# 8. Remova **todos** os pokemons do tipo água e com attack menor que 50

```
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> var query = { $and: [ {type: 'água'}, { attack: { $lt: 50 } } ] }
fabio-Inspiron-7520(mongod-3.0.7) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})


```

# 9. Demonstre qual a diferença entre os operadores '$ne' e '$not'.

$ne: Esse item retorna documento e não suporta REGEX.

$not: negação do objeto e suporta REGEX


