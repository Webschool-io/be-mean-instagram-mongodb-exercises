# MongoDB - Aula 04 - Exercício
autor: Alex de Miranda

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var query = {$or:[{name:/Pikachu/i}, {name:/Squirtle/i}, {name:/Bulbasaur/i}, {name:/Charmander/i}]}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var ataques = ['soco', 'chute']
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var mod = {$pushAll:{moves:ataques}}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var options = {multi:true}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 2ms
WriteResult({
    "nMatched": 4,
    "nUpserted": 0,
    "nModified": 4
})


## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var query =  {}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var mod = {$push:{moves:"desvio"}}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var options = {multi:true}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 10 existing record(s) in 2ms
WriteResult({
    "nMatched": 10,
    "nUpserted": 0,
    "nModified": 10
})


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var query = {name:/AindaNaoExisteMon/i}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var mod = {
...     $setOnInsert:{
...     "name": "AindaNaoExisteMon",
...     "description": "Sem maiores informações",
...     "type": null,
...     "attack": null,
...     "height": null,
...     "defense": null,
...     "active": null,
...     }
... }
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var options = {upsert:true}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 12ms
WriteResult({
    "nMatched": 0,
    "nUpserted": 1,
    "nModified": 0,
    "_id": ObjectId("564dee7f86c109a7d95f300b")
})
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.find(query)

{
    "_id": ObjectId("564dee7f86c109a7d95f300b"),
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "height": null,
    "defense": null,
    "active": null
}
Fetched 1 record(s) in 3ms

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var query = {$or:[{moves:{$in:['investida']}}, {name:/Beedrill/i}]}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.find(query)

{
    "_id": ObjectId("564be4defce4b69d2e4bae20"),
    "name": "Butterfree",
    "description": "tem uma capacidade superior de procurar delicioso mel de flores",
    "attack": 45,
    "defense": 50,
    "height": "1,1m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564be50cfce4b69d2e4bae21"),
    "name": "Weedle",
    "description": "tem o olfato bem apurado",
    "attack": 35,
    "defense": 30,
    "height": "0,3m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564be524fce4b69d2e4bae22"),
    "name": "Kakuna",
    "description": "permanece parado numa arvore até sua evolução",
    "attack": 25,
    "defense": 50,
    "height": "0,6m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564be52efce4b69d2e4bae23"),
    "name": "Beedrill",
    "description": "Extremamente territorial, ninguém deve se aproximar do seu ninho",
    "attack": 90,
    "defense": 40,
    "height": "1,0m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d271adb7f49312ba9c955"),
    "description": "Pokemon de teste",
    "name": "Testemon",
    "attack": 8000,
    "defense": 8000,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d4505fee3823495524f34"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "agua",
    "attack": 48,
    "height": 0.5,
    "active": false,
    "moves": [
        "investida",
        "hidro bomba",
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d6684ba4cd09d6940713d"),
    "name": "Bulbasaur",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha",
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d68c1ba4cd09d6940713f"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d2d69db7f49312ba9c956"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 100,
    "height": 0.4,
    "moves": [
        "investida",
        "choque do trovão",
        "desvio",
        "soco",
        "chute"
    ],
    "active": false
}
{
    "_id": ObjectId("564d687bba4cd09d6940713e"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.8,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "soco",
        "chute",
        "desvio"
    ]
}
Fetched 10 record(s) in 36ms

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var query = {moves:{$in:['chute', 'soco']}}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.find(query)

{
    "_id": ObjectId("564d4505fee3823495524f34"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "agua",
    "attack": 48,
    "height": 0.5,
    "active": false,
    "moves": [
        "investida",
        "hidro bomba",
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d6684ba4cd09d6940713d"),
    "name": "Bulbasaur",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha",
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d2d69db7f49312ba9c956"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 100,
    "height": 0.4,
    "moves": [
        "investida",
        "choque do trovão",
        "desvio",
        "soco",
        "chute"
    ],
    "active": false
}
{
    "_id": ObjectId("564d687bba4cd09d6940713e"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.8,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "soco",
        "chute",
        "desvio"
    ]
}
Fetched 4 record(s) in 63ms

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var query = {type:{$ne:'eletric'}}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.find(query)

{
    "_id": ObjectId("564be4defce4b69d2e4bae20"),
    "name": "Butterfree",
    "description": "tem uma capacidade superior de procurar delicioso mel de flo
res",
    "attack": 45,
    "defense": 50,
    "height": "1,1m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564be50cfce4b69d2e4bae21"),
    "name": "Weedle",
    "description": "tem o olfato bem apurado",
    "attack": 35,
    "defense": 30,
    "height": "0,3m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564be524fce4b69d2e4bae22"),
    "name": "Kakuna",
    "description": "permanece parado numa arvore até sua evolução",
    "attack": 25,
    "defense": 50,
    "height": "0,6m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564be52efce4b69d2e4bae23"),
    "name": "Beedrill",
    "description": "Extremamente territorial, ninguém deve se aproximar do seu n
inho",
    "attack": 90,
    "defense": 40,
    "height": "1,0m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d271adb7f49312ba9c955"),
    "description": "Pokemon de teste",
    "name": "Testemon",
    "attack": 8000,
    "defense": 8000,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d4505fee3823495524f34"),
    "name": "Squirtle",
    "description": "Ejeta água que passarinho não bebe",
    "type": "agua",
    "attack": 48,
    "height": 0.5,
    "active": false,
    "moves": [
        "investida",
        "hidro bomba",
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d6684ba4cd09d6940713d"),
    "name": "Bulbasaur",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha",
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d68c1ba4cd09d6940713f"),
    "name": "Caterpie",
    "description": "Larva lutadora",
    "type": "inseto",
    "attack": 30,
    "height": 0.3,
    "defense": 35,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d687bba4cd09d6940713e"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.8,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("564dee7f86c109a7d95f300b"),
    "name": "AindaNaoExisteMon",
    "description": "Sem maiores informações",
    "type": null,
    "attack": null,
    "height": null,
    "defense": null,
    "active": null
}
Fetched 10 record(s) in 35ms

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var query = {$and:[{mov
es:{$in:['investida']}},{attack:{$gte:49}}]}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.find(query)

{
    "_id": ObjectId("564be52efce4b69d2e4bae23"),
    "name": "Beedrill",
    "description": "Extremamente territorial, ninguém deve se aproximar do seu n
inho",
    "attack": 90,
    "defense": 40,
    "height": "1,0m",
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d271adb7f49312ba9c955"),
    "description": "Pokemon de teste",
    "name": "Testemon",
    "attack": 8000,
    "defense": 8000,
    "active": false,
    "moves": [
        "investida",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d6684ba4cd09d6940713d"),
    "name": "Bulbasaur",
    "description": "Chicote de trepadeira",
    "type": "grama",
    "attack": 49,
    "height": 0.4,
    "active": false,
    "moves": [
        "investida",
        "folha navalha",
        "soco",
        "chute",
        "desvio"
    ]
}
{
    "_id": ObjectId("564d2d69db7f49312ba9c956"),
    "name": "Pikachu",
    "description": "Rato elétrico bem fofinho",
    "type": "eletric",
    "attack": 100,
    "height": 0.4,
    "moves": [
        "investida",
        "choque do trovão",
        "desvio",
        "soco",
        "chute"
    ],
    "active": false
}
{
    "_id": ObjectId("564d687bba4cd09d6940713e"),
    "name": "Charmander",
    "description": "Esse é o cão chupando manga de fofinho",
    "type": "fogo",
    "attack": 52,
    "height": 0.8,
    "active": false,
    "moves": [
        "investida",
        "lança-chamas",
        "soco",
        "chute",
        "desvio"
    ]
}
Fetched 5 record(s) in 15ms

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> var query = {$and:[{type:/água/i}, {attack:{$lt:50}}]}
Alex(D:\mongodb\bin\mongod.exe-3.0.7) be-mean-instagram> db.pokemons.remove(query)
Removed 1 record(s) in 7ms
WriteResult({
    "nRemoved": 1
})