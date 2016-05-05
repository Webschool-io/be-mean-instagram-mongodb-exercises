# MongoDB - Aula 04 - Exercício
autor: Mauricio Ruiz Diaz

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
> var query = { name : { $in : [ /pikachu/i, /squirtle/i, /bulbassauro/i, /charmander/i ] } }
> var mod = { $pushAll : { moves : [ 'cosada de saco', 'soneca' ] } }
> var options = { multi : true }

> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564e3f4778195b9fe343ecca"),
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
        "type" : "electric",
        "attack" : 100,
        "defense" : 50,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca"
        ]
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccb"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "defense" : 50,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca"
        ]
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccc"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "defense" : 50,
        "height" : 0.6,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca"
        ]
}
{
        "_id" : ObjectId("564e43a378195b9fe343ecce"),
        "name" : "Squirtle",
        "description" : "Tartaruga que gosta muito de auga",
        "attack" : 48,
        "defense" : 65,
        "height" : "5",
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca"
        ]
}
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.
```
> var query = {}
> var mod = { $push : { moves : 'desvio' } }
> var options = { multi : true }

> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 10, "nUpserted" : 0, "nModified" : 10 })

> db.pokemons.find().pretty()
{
        "_id" : ObjectId("564406426f3a5df04e2a86f7"),
        "name" : "Quilava",
        "description" : "Tira fogo e sopra ar quente",
        "attack" : 55,
        "defense" : 40,
        "height" : 2.11,
        "type" : "grama",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86f8"),
        "name" : "Cloyster",
        "description" : "Atira espinhas",
        "attack" : 65,
        "defense" : 65,
        "height" : 2.4,
        "type" : "inseto",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86f9"),
        "name" : "Donphan",
        "description" : "Vira bola e bate em todo mundo",
        "attack" : 120,
        "defense" : 120,
        "height" : 3.07,
        "type" : "fogo",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86fa"),
        "name" : "Magnezone",
        "description" : "Paraliza todo mundo com magnetismo",
        "attack" : 70,
        "defense" : 115,
        "height" : 0.12,
        "type" : "magnetismo",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564bc8c83ceb150c97391e01"),
        "name" : "Testemon",
        "attack" : 8000,
        "defense" : 8000,
        "height" : 2.1,
        "description" : "Pokemon de teste",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e3f4778195b9fe343ecca"),
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
        "type" : "electric",
        "attack" : 100,
        "defense" : 50,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccb"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "defense" : 50,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccc"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "defense" : 50,
        "height" : 0.6,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e43a378195b9fe343ecce"),
        "name" : "Squirtle",
        "description" : "Tartaruga que gosta muito de auga",
        "attack" : 48,
        "defense" : 65,
        "height" : "5",
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86fb"),
        "name" : "Archen",
        "description" : "Revivido de um fosil. O ancestro de todos os passaros pokemon",
        "attack" : 112,
        "defense" : 45,
        "height" : 0.5,
        "type" : "ave",
        "moves" : [
                "investida",
                "desvio"
        ]
}

```
## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".
```

> query = { name : /AindaNaoExisteMon/i }
> var mod = { $setOnInsert : { name : 'AindaNaoExisteMon', attack : null, defense : null, height : null, type : null, moves : null, description : 'Sem maiores informações' } }
> mod
{
        "$setOnInsert" : {
                "name" : "AindaNaoExisteMon",
                "attack" : null,
                "defense" : null,
                "height" : null,
                "type" : null,
                "moves" : null,
                "description" : "Sem maiores informações"
        }
}

> var options = { upsert : true }
> db.pokemons.update(query, mod, options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("564e5141664c44dcdc20cb26")
})

```
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```
> var query = { moves : { $all : [ 'investida', 'soneca' ] } }
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564e3f4778195b9fe343ecca"),
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
        "type" : "electric",
        "attack" : 100,
        "defense" : 50,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccb"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "defense" : 50,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccc"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "defense" : 50,
        "height" : 0.6,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e43a378195b9fe343ecce"),
        "name" : "Squirtle",
        "description" : "Tartaruga que gosta muito de auga",
        "attack" : 48,
        "defense" : 65,
        "height" : "5",
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```
> var query = { moves : { $nin : ['soneca', 'cosada de saco'] } }
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564406426f3a5df04e2a86f7"),
        "name" : "Quilava",
        "description" : "Tira fogo e sopra ar quente",
        "attack" : 55,
        "defense" : 40,
        "height" : 2.11,
        "type" : "grama",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86f8"),
        "name" : "Cloyster",
        "description" : "Atira espinhas",
        "attack" : 65,
        "defense" : 65,
        "height" : 2.4,
        "type" : "inseto",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86f9"),
        "name" : "Donphan",
        "description" : "Vira bola e bate em todo mundo",
        "attack" : 120,
        "defense" : 120,
        "height" : 3.07,
        "type" : "fogo",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86fa"),
        "name" : "Magnezone",
        "description" : "Paraliza todo mundo com magnetismo",
        "attack" : 70,
        "defense" : 115,
        "height" : 0.12,
        "type" : "magnetismo",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564bc8c83ceb150c97391e01"),
        "name" : "Testemon",
        "attack" : 8000,
        "defense" : 8000,
        "height" : 2.1,
        "description" : "Pokemon de teste",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86fb"),
        "name" : "Archen",
        "description" : "Revivido de um fosil. O ancestro de todos os passaros pokemon",
        "attack" : 112,
        "defense" : 45,
        "height" : 0.5,
        "type" : "ave",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e5141664c44dcdc20cb26"),
        "name" : "AindaNaoExisteMon",
        "attack" : null,
        "defense" : null,
        "height" : null,
        "type" : null,
        "moves" : null,
        "description" : "Sem maiores informações"
}
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```
> var query = { type : { $ne : 'electric' } }
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564406426f3a5df04e2a86f7"),
        "name" : "Quilava",
        "description" : "Tira fogo e sopra ar quente",
        "attack" : 55,
        "defense" : 40,
        "height" : 2.11,
        "type" : "grama",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86f8"),
        "name" : "Cloyster",
        "description" : "Atira espinhas",
        "attack" : 65,
        "defense" : 65,
        "height" : 2.4,
        "type" : "inseto",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86f9"),
        "name" : "Donphan",
        "description" : "Vira bola e bate em todo mundo",
        "attack" : 120,
        "defense" : 120,
        "height" : 3.07,
        "type" : "fogo",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86fa"),
        "name" : "Magnezone",
        "description" : "Paraliza todo mundo com magnetismo",
        "attack" : 70,
        "defense" : 115,
        "height" : 0.12,
        "type" : "magnetismo",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564bc8c83ceb150c97391e01"),
        "name" : "Testemon",
        "attack" : 8000,
        "defense" : 8000,
        "height" : 2.1,
        "description" : "Pokemon de teste",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccb"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "defense" : 50,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccc"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "defense" : 50,
        "height" : 0.6,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e43a378195b9fe343ecce"),
        "name" : "Squirtle",
        "description" : "Tartaruga que gosta muito de auga",
        "attack" : 48,
        "defense" : 65,
        "height" : "5",
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86fb"),
        "name" : "Archen",
        "description" : "Revivido de um fosil. O ancestro de todos os passaros pokemon",
        "attack" : 112,
        "defense" : 45,
        "height" : 0.5,
        "type" : "ave",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e5141664c44dcdc20cb26"),
        "name" : "AindaNaoExisteMon",
        "attack" : null,
        "defense" : null,
        "height" : null,
        "type" : null,
        "moves" : null,
        "description" : "Sem maiores informações"
}
```

## Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```
> var query1 = { moves : { $in : [ 'investida' ] } }
> var query2 = { defense : { $not : { $lte : 49 } } }
> var query = { $and : [query1, query2] }
> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564406426f3a5df04e2a86f8"),
        "name" : "Cloyster",
        "description" : "Atira espinhas",
        "attack" : 65,
        "defense" : 65,
        "height" : 2.4,
        "type" : "inseto",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86f9"),
        "name" : "Donphan",
        "description" : "Vira bola e bate em todo mundo",
        "attack" : 120,
        "defense" : 120,
        "height" : 3.07,
        "type" : "fogo",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564406426f3a5df04e2a86fa"),
        "name" : "Magnezone",
        "description" : "Paraliza todo mundo com magnetismo",
        "attack" : 70,
        "defense" : 115,
        "height" : 0.12,
        "type" : "magnetismo",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564bc8c83ceb150c97391e01"),
        "name" : "Testemon",
        "attack" : 8000,
        "defense" : 8000,
        "height" : 2.1,
        "description" : "Pokemon de teste",
        "moves" : [
                "investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("564e3f4778195b9fe343ecca"),
        "name" : "Pikachu",
        "description" : "Rato elétrico bem fofinho",
        "type" : "electric",
        "attack" : 100,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ],
        "defense" : 50
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccb"),
        "name" : "Bulbassauro",
        "description" : "Chicote de trepadeira",
        "type" : "grama",
        "attack" : 49,
        "height" : 0.4,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ],
        "defense" : 50
}
{
        "_id" : ObjectId("564e43a378195b9fe343ecce"),
        "name" : "Squirtle",
        "description" : "Tartaruga que gosta muito de auga",
        "attack" : 48,
        "defense" : 65,
        "height" : "5",
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ],
        "type" : "agua"
}
{
        "_id" : ObjectId("564e3f4b78195b9fe343eccc"),
        "name" : "Charmander",
        "description" : "Esse é o cão chupando manga de fofinho",
        "type" : "fogo",
        "attack" : 52,
        "height" : 0.6,
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ],
        "defense" : 50
}
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
> var query1 = { type : 'agua' }
> var query2 = { attack : { $lt : 50 } }
> var query = { $and : [query1, query2] }

> db.pokemons.find(query).pretty()
{
        "_id" : ObjectId("564e43a378195b9fe343ecce"),
        "name" : "Squirtle",
        "description" : "Tartaruga que gosta muito de auga",
        "attack" : 48,
        "defense" : 65,
        "height" : "5",
        "moves" : [
                "investida",
                "cosada de saco",
                "soneca",
                "desvio"
        ],
        "type" : "agua"
}

> db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })
```