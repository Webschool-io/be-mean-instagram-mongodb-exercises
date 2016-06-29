# MongoDB - Aula 04 - Exercício
autor: Guilherme Felipe de Sousa

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {name: {$in: [/pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i]}}
fedora(mongod-3.0.8) be-mean-pokemons> var mod = {$pushAll: {moves: ["tacador de pedra","vai pra cima"]}}
fedora(mongod-3.0.8) be-mean-pokemons> var options = {multi: true}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 10ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
fedora(mongod-3.0.8) be-mean-pokemons> var mod = {$push: {moves: "desvio}}
fedora(mongod-3.0.8) be-mean-pokemons> var query = {}
fedora(mongod-3.0.8) be-mean-pokemons> var options = {multi: true}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 11 existing record(s) in 9ms
WriteResult({
  "nMatched": 11,
  "nUpserted": 0,
  "nModified": 11
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {name: /aindanaoexistemon/i}
fedora(mongod-3.0.8) be-mean-pokemons> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", description: "Sem maiores informações",type: null, attack: null, height: null, active: null, moves: [] }}
fedora(mongod-3.0.8) be-mean-pokemons> var options = {upsert: true}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("56b8df6266c9900d1d00800f")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {moves: {$in: [/investida/i, /vai pra cima/i]}}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8d38aeabe906da437029d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "Grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8d59beabe906da437029f"),
  "name": "teste",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "Agua",
  "attack": 50,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ad056653448d2fab7f1dfd"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "Fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8d360eabe906da437029c"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b8d392eabe906da437029e"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "Agua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
Fetched 5 record(s) in 4ms
fedora(mongod-3.0.8) be-mean-pokemons> var favorito = {"_id": ObjectId("56ad056653448d2fab7f1dfd")}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {moves: {$in: [/tacador de pedra/i, /vai pra cima/i]}}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56b8d38aeabe906da437029d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "Grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ad056653448d2fab7f1dfd"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "Fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8d360eabe906da437029c"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b8d392eabe906da437029e"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "Agua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
Fetched 4 record(s) in 2ms
fedora(mongod-3.0.8) be-mean-pokemons> var favorito = {"_id": ObjectId("56ad056653448d2fab7f1dfd")}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {moves: {$nin: ["elétrico"]}}
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("56ad072b4484bcd68498514f"),
  "name": "Spearow",
  "description": "Galisé minuscula que machuca",
  "attack": 30,
  "defense": 20,
  "height": 0.4,
  "type": "Voador",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56ad07954484bcd684985150"),
  "name": "Ekans",
  "description": "A famosa cascavel (sogra)",
  "attack": 30,
  "defense": 20,
  "height": 6.9,
  "type": "Terra",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56ad07d54484bcd684985151"),
  "name": "Sandshrew",
  "description": "Tatu bolinha manso",
  "attack": 0.5,
  "defense": 40,
  "height": 12,
  "type": "Terra",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56ad0a1740706acf8c2cc9c1"),
  "name": "Vileplume",
  "description": "Cogumelo azul do ventania",
  "attack": 40,
  "defense": 40,
  "height": 18.6,
  "type": "Grama",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56aeb87aa166121ef17e6464"),
  "description": "Pokemon de teste",
  "name": "Testemon",
  "attack": 8000,
  "defense": 8000,
  "moves": [
    "Novo Movimento1",
    "Novo 2",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8d38aeabe906da437029d"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "Grama",
  "attack": 49,
  "height": 0.4,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8d59beabe906da437029f"),
  "name": "teste",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "Agua",
  "attack": 50,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ad056653448d2fab7f1dfd"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "Fogo",
  "attack": 52,
  "height": 0.6,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
{
  "_id": ObjectId("56ad06b64484bcd68498514e"),
  "name": "Raticate",
  "description": "Tem presas grandes e elas crescem de forma constatante, ele mastiga até paredes",
  "attack": 40,
  "defense": 30,
  "height": 18.5,
  "type": "Normal",
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8d360eabe906da437029c"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 100,
  "height": 0.4,
  "moves": [
    "investida",
    "choque do trovão",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("56b8d392eabe906da437029e"),
  "name": "Squirtle",
  "description": "Ejeta agua que passarinho nao bebe",
  "type": "Agua",
  "attack": 48,
  "height": 0.5,
  "active": false,
  "moves": [
    "investida",
    "tacador de pedra",
    "vai pra cima",
    "desvio"
  ]
}
{
  "_id": ObjectId("56b8df6266c9900d1d00800f"),
  "name": "AindaNaoExisteMon",
  "description": "Sem maiores informações",
  "type": null,
  "attack": null,
  "height": null,
  "active": null,
  "moves": null
}
Fetched 12 record(s) in 2ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
    fedora(mongod-3.0.8) be-mean-pokemons> var query = {$and: [{name: "Bulbassauro"}, {defense: {$lte: 49}}] }
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 0ms
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
fedora(mongod-3.0.8) be-mean-pokemons> var query = {$and: [{type: /agua/i}, {attack: {$lt: 50}}] }
fedora(mongod-3.0.8) be-mean-pokemons> db.pokemons.remove(query)
Removed 1 record(s) in 19ms
WriteResult({
  "nRemoved": 1
})
```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício dem
onstre qual a diferença entre os operadores $ne e $not.

```
$ne : Encontra  valores não iguais  ao  valor especificado sem poder usar Regular Expression.
$not Inverte  o efeito  da  consulta  e retorna os  documentos  que não  satisfazem  a expressão  informada e diferente do $ne aceita Regular Expression
```