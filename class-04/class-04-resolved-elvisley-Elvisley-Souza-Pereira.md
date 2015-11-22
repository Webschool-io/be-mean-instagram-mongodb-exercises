# MongoDB - Aula 04 - Exercício
autor: Elvisley Souza Pereira

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
var query = {name : {$in : [ /pikachu/i,/squirtle/i,/bulbassauro/i ] } }
var mod = { $set : { moves : ['Ataque 1' , 'Ataque 2'] } }
var options = {multi:true}
db.pokemons.update(query , mod , options);

Updated 3 existing record(s) in 5ms
WriteResult({
  "nMatched": 3,
  "nUpserted": 0,
  "nModified": 3
})

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
var query = {}
var mod = { $set : { moves : ['desvio'] } }
var options = {multi:true}
db.pokemons.update(query , mod , options);

Updated 8 existing record(s) in 5ms
WriteResult({
  "nMatched": 8,
  "nUpserted": 0,
  "nModified": 8
})
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
var query = {name: /AindaNaoExisteMon/i}
var mod = {
  $setOnInsert: {
    name: "AindaNaoExisteMon",
    attack: null,
    defense: null,
    height: null,
    description: "Sem maiores informações"
  }
}
var options = {upsert: true}
db.pokemons.update(query, mod, options)

Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("564e60849def54eff92a2c9a")
})

{
  "_id": ObjectId("564e60849def54eff92a2c9a"),
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}

```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
var query = { moves : { $all : [/investida/i , /Ataque 1/i]} }
db.pokemons.find(query);
Fetched 0 record(s) in 0ms
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
var query = { moves : { $all : [/Ataque 2/i , /Ataque 1/i]} }
db.pokemons.find(query);

{
  "_id": ObjectId("564e5fac5b266b337f1c97c2"),
  "name": "Pikachu",
  "description": "Passaro voador",
  "type": "passaro",
  "attack": 40,
  "height": 0.5,
  "moves": [
    "Ataque 1",
    "Ataque 2"
  ]
}
{
  "_id": ObjectId("564e5fbd5b266b337f1c97c3"),
  "name": "Squirtle",
  "description": "Passaro voador",
  "type": "passaro",
  "attack": 40,
  "height": 0.5,
  "moves": [
    "Ataque 1",
    "Ataque 2"
  ]
}
{
  "_id": ObjectId("564e5fd35b266b337f1c97c4"),
  "name": "Bulbassauro",
  "description": "Passaro voador",
  "type": "passaro",
  "attack": 40,
  "height": 0.5,
  "moves": [
    "Ataque 1",
    "Ataque 2"
  ]
}
Fetched 3 record(s) in 4ms

```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
var query = { type : { $ne : 'elétrico' } }
db.pokemons.find(query);

{
  "_id": ObjectId("56427a70d00be8bdf3d3ec6d"),
  "name": "Beedrill",
  "description": "Abelha",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "moves": [
    "desvio"
  ]
}
{
  "_id": ObjectId("56427a77d00be8bdf3d3ec6e"),
  "name": "Pidgey",
  "description": "Galinha Normal ",
  "type": "passaro",
  "attack": 35,
  "height": 0.4,
  "moves": [
    "desvio"
  ]
}

....

```
## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
var query = { $and : [ {moves : 'investida' } , {defense: { $gt : 49 } } ] }
db.pokemons.find(query);
Fetched 0 record(s) in 0ms
```
## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
var query = { $and : [ {type : 'agua' } , {attack: { $lt : 49 } } ] }
db.pokemons.remove(query);

//Removendo os tipos passaro , porque nao tinha nenhum pokemon com o tipo agua
Removed 5 record(s) in 5ms
WriteResult({
  "nRemoved": 5
})

```
