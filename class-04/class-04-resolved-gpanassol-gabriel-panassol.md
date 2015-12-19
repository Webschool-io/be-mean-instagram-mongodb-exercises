# MongoDB - Aula 04 - Exercício
autor: Gabriel Panassol

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
> var query = {name:{$in:['Pikachu','Squirtle','Bulbasaur']}}
> var mod = {$set:{moves:['investida','ataque direto']}}
> db.pokemons.update(query,mod)
WriteResult({ "nMatched" : 3, "nUpserted" : 0, "nModified" : 3 })
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564fd22c8df483ce2eebad5e"),
        "name" : "Bulbasaur",
        "description" : "Bichinho verde",
        "type" : "Grama",
        "attack" : 49,
        "defense" : 49,
        "height" : 0.71,
        "moves" : [
                "investida",
                "ataque direto"
        ]
}
{
        "_id" : ObjectId("564fd2358df483ce2eebad5f"),
        "name" : "Squirtle",
        "description" : "Tartaruga Azul",
        "type" : "Água",
        "attack" : 48,
        "defense" : 65,
        "height" : 0.51,
        "moves" : [
                "investida",
                "ataque direto"
        ]
}
{
        "_id" : ObjectId("564fd23c8df483ce2eebad60"),
        "name" : "Pikachu",
        "description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its e
vidence that this Pokémon mistook the intensity of its charge.",
        "attack" : 55,
        "defense" : 40,
        "height" : 4,
        "moves" : [
                "investida",
                "ataque direto"
        ]
}

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
```
> var query = {}
> var mod = { $push: { moves: "desvio"}}
> var options = {multi : true}
> db.pokemons.update(query,mod,options)

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
> var query = {name: /AindaNaoExisteMon/i}
> var mod = {
... $set:{active:true},
... $setOnInsert:{
... name:'AindaNaoExisteMon',
... attack:null,
... defense:null,
... height:null,
... description:"Sem maiores informações"}
... }
> var options = {upsert:true}
> db.pokemons.update(query,mod,options);
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
> var query = {moves:{$all:['investida']}, name:{$in:['Raichu']}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("5642992f154818645f78c7ff"),
        "name" : "Raichu",
        "description" : "Pokemon Eletrico fudido!!",
        "type" : "Eletrico",
        "attack" : 90,
        "height" : 0.8,
        "moves" : [
                "investida",
                "desvio"
        ],
        "active" : false
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
> var query = {moves:{$all:['investida','ataque direto']}, name:{$in:['Pikachu']}}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564fd23c8df483ce2eebad60"),
        "name" : "Pikachu",
        "description" : "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, its e
vidence that this Pokémon mistook the intensity of its charge.",
        "attack" : 55,
        "defense" : 40,
        "height" : 4,
        "moves" : [
                "investida",
                "ataque direto"
        ]
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
var query = {type: {$ne:'eletrico'} }
> var query = {type: {$ne:'eletrico'} }
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("56429921154818645f78c7fe"),
        "name" : "Pidgeotto",
        "description" : "Pidgeotto reivindica uma grande área como seu próprio território. Este Pokémon voa ao redor, patrulhando o seu espaço de vida. Se
 seu território for violado, ele não mostra misericórdia em cuidadosamente punir o inimigo com suas garras afiadas.",
        "type" : "Voador",
        "attack" : 80,
        "height" : 1.5,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564d1a819f1230058c23b4ff"),
        "description" : "Pokemon de teste",
        "name" : "Testemon",
        "attack" : 8001,
        "defense" : 8000,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564d2c70c664c78ff8058aa8"),
        "active" : false,
        "name" : "NaoExisteMon",
        "attack" : null,
        "defense" : null,
        "height" : null,
        "description" : "Sem maiores informações",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564298e0154818645f78c7fc"),
        "name" : "Blastoise",
        "description" : "Um Pokémon brutal com jatos de água pressurizada em seu escudo. Eles são usados para aborda alta velocidade",
        "type" : "Água",
        "attack" : 83,
        "height" : 1.6,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("5642990e154818645f78c7fd"),
        "name" : "Beedrill",
        "description" : "Ele pode derrubar qualquer oponente com suas poderosas ferrões filho poi. Ele às vezes ataques em enxames.",
        "type" : "grama",
        "attack" : 83,
        "height" : 1.6,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564d2a9ac664c78ff8058aa7"),
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564fd2278df483ce2eebad5d"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6,
        "defense" : 43,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564fd2358df483ce2eebad5f"),
        "name" : "Squirtle",
        "description" : "Tartaruga Azul",
        "type" : "Água",
        "attack" : 48,
        "defense" : 65,
        "height" : 0.51,
        "moves" : [
                "investida",
                "desvio",
                [
                        "investida",
                        "ataque direto",
                        "desvio"
                ]
        ]
}
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
```
> var query = { $and:[ { moves: { $in: [/investida/i]} }, { defense: { $gte: 49 } } ]}
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564d1a819f1230058c23b4ff"),
        "description" : "Pokemon de teste",
        "name" : "Testemon",
        "attack" : 8001,
        "defense" : 8000,
        "active" : false,
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564fd2358df483ce2eebad5f"),
        "name" : "Squirtle",
        "description" : "Tartaruga Azul",
        "type" : "Água",
        "attack" : 48,
        "defense" : 65,
        "height" : 0.51,
        "moves" : [
                "investida",
                "desvio",
                [
                        "investida",
                        "ataque direto",
                        "desvio"
                ]
        ]
}
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
> var query = { $and:[ { type: {$ne:'agua'} }, { attack: { $lt: 50 } } ]}
> db.pokemons.remove(query)
```
