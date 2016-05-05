# MongoDB - Aula 04 - Exercício
autor: Higor Diego

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var attacks = ["add 1","add2"]

m0nk3y(mongod-3.0.7) be-mean-pokemons> var mod = {$pushAll: {moves: attacks}}

m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {name: "Squirtle"},{name: "Bulbassauro"},{name: "Charmander"}]}
m0nk3y(mongod-3.0.7) be-mean-pokemons> var options = {multi: true}


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var mod = {$push: {moves: "Desvio"}};
m0nk3y(mongod-3.0.7) be-mean-pokemons> var options = {multi: true};
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.update({}, mod, options);

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {name: /AindaNaoExisteMon/i}
m0nk3y(mongod-3.0.7) be-mean-pokemons> var mod = {$setOnInsert: {name: "AindaNaoExisteMon", attack: null, defense: null, height: null, description: "Sem maio res informações", moves: []}};
m0nk3y(mongod-3.0.7) be-mean-pokemons> var options = {upsert: true};
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.update(query,mod,options);


```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ["investida","testando essa porra"]}}

m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)

m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a26"),
  "name": "testando5",
  "description": "tetando essa porra",
  "type": "teste5",
  "attack": 5,
  "defense": 500,
  "height": 5.6,
  "moves": [
    "testando essa porra",
    "Desvio"
  ]
}
Fetched 1 record(s) in 


```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {moves: {$in: ["testando essa porra","Desvio"]}}

m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)

{
  "_id": ObjectId("5644ca6d147c29f4b7f73a22"),
  "name": "Testandomon",
  "description": "teste",
  "type": "exercio",
  "attack": 7001,
  "defense": 600,
  "height": 0.69,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "Pokemon além do teste",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a24"),
  "name": "testando3",
  "description": "testando3",
  "type": "teste3",
  "attack": 3,
  "defense": 300,
  "height": 3.6,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a25"),
  "name": "testando4",
  "description": "testando4",
  "type": "teste4",
  "attack": 4,
  "defense": 400,
  "height": 4.6,
  "active": true,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a26"),
  "name": "testando5",
  "description": "tetando essa porra",
  "type": "teste5",
  "attack": 5,
  "defense": 500,
  "height": 5.6,
  "moves": [
    "testando essa porra",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a27"),
  "description": "tetando novamente",
  "moves": [
    "Desvio"
  ]
}
F

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
m0nk3y(mongod-3.0.7) be-mean-pokemons>  var query = {type: {$ne: "eletric"}}
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a22"),
  "name": "Testandomon",
  "description": "teste",
  "type": "exercio",
  "attack": 7001,
  "defense": 600,
  "height": 0.69,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a23"),
  "name": "testando2",
  "description": "Pokemon além do teste",
  "type": "teste2",
  "attack": 2,
  "defense": 100,
  "height": 2.6,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a24"),
  "name": "testando3",
  "description": "testando3",
  "type": "teste3",
  "attack": 3,
  "defense": 300,
  "height": 3.6,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a25"),
  "name": "testando4",
  "description": "testando4",
  "type": "teste4",
  "attack": 4,
  "defense": 400,
  "height": 4.6,
  "active": true,
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a26"),
  "name": "testando5",
  "description": "tetando essa porra",
  "type": "teste5",
  "attack": 5,
  "defense": 500,
  "height": 5.6,
  "moves": [
    "testando essa porra",
    "Desvio"
  ]
}
{
  "_id": ObjectId("5644ca6d147c29f4b7f73a27"),
  "description": "tetando novamente",
  "moves": [
    "Desvio"
  ]
}
{
  "_id": ObjectId("56593cbe375659d7c1ed4837"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maio res informações",
  "moves": [ ]
}
Fetched 7 record(s) in 

```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{moves: {$in: ["investida"]}}, {defense: {$not: {$lte: 49}}}]}

m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
m0nk3y(mongod-3.0.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 

```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
m0nk3y(mongod-3.0.7) be-mean-pokemons> var query = {$and: [{"type" : "água"}, {attack: {$lt: 50}}]}

m0nk3y(mongod-3.0.7) be-mean-pokemons>  db.pokemons.remove(query)


```

## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores `$ne` e `$not`.

```
$ne: Esse item retorna documento e não suporta REGEX.

$not: negação do objeto e suporta REGEX


```
