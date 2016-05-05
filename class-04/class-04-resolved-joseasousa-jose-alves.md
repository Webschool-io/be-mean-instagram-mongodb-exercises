# MongoDB - Aula 04 - Exercício
autor: Jose Alves de Sousa Neto

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

    $var query = {name: {$in : [/pikachu/i,/squirtle/i,/bulbassauro/i]} }
     var mod ={$pushAll: {moves:['investida', 'ataque rápido']}}
    $ var options = {multi:true}
    $ db.pokemons.update(query,mod,options)
    Updated 1 existing record(s) in 11ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })


## 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
    
    > var query = {}
    > var mod = {$push:{moves:'desvio'}}
    > var options = {multi:true}
    > db.pokemons.update(query,mod,options)
    Updated 16 existing record(s) in 12ms
    WriteResult({
      "nMatched": 16,
      "nUpserted": 0,
      "nModified": 16
    })



## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

    > var query = {name: /AindaNaoExisteMon/i}
    > var mod = {$set:{'description': 'Sem maiores informações'},$setOnInsert: {name: 'AindaNaoExisteMon',defese: null,height: null}}
    > var options = {upsert:true}
    >  db.pokemon.update(query, mod, options)
    Updated 1 new record(s) in 5ms
    WriteResult({
      "nMatched": 0,
      "nUpserted": 1,
      "nModified": 0,
      "_id": ObjectId("564ddd23cffcf2b3417bc6a3")
    })



## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
    
    > var query = { "moves" : { "$all" : [ "investida", "desvio" ] } }
    > db.pokemons.find(query)
    {
      "_id": ObjectId("564dd971ba377a04f9c97bb2"),
      "name": "Pikachu",
      "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
      "attack": 30,
      "defense": 20,
      "height": 0.4,
      "moves": [
        "investida",
        "ataque rápido",
        "desvio"
      ]
    }
    Fetched 1 record(s) in 2ms

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

    > var query = {moves: {$all : ['ataque rápido', 'investida']}}
    > db.pokemons.find(query)
    {
      "_id": ObjectId("564dd971ba377a04f9c97bb2"),
      "name": "Pikachu",
      "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
      "attack": 30,
      "defense": 20,
      "height": 0.4,
      "moves": [
        "investida",
        "ataque rápido",
        "desvio"
      ]
    }
    Fetched 1 record(s) in 2ms



## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

    > var query = {type: {$ne : 'elétrico'}}
    > db.pokemons.find(query)
    {
      "_id": ObjectId("564c833b36bb50ed7beca73f"),
      "name": "Nidoran",
      "description": "É um roedor maroto",
      "attack": 3,
      "defense": 2,
      "height": 0.4,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564c833b36bb50ed7beca740"),
      "name": "Meowth",
      "description": "É um gatinho maroto",
      "attack": 2,
      "defense": 2,
      "height": 0.4,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564c833b36bb50ed7beca741"),
      "name": "Psyduck",
      "description": "Um pato meio adoidado",
      "attack": 3,
      "defense": 2,
      "height": 0.8,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564c833b36bb50ed7beca742"),
      "name": "Machop",
      "description": "Pokemn maromba",
      "attack": 4,
      "defense": 2,
      "height": 0.8,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564c833b36bb50ed7beca743"),
      "name": "Krabby",
      "description": "Parente do Sirigueijo",
      "attack": 5,
      "defense": 4,
      "height": 0.4,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564d1609622f43a77568e194"),
      "name": "Gengar",
      "description": "Fantasma bolado",
      "atack": 30,
      "defense": 55,
      "height": 0.5,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564d1609622f43a77568e195"),
      "name": "Infernape",
      "description": "Macaco em chamas",
      "atack": 300,
      "defense": 130,
      "height": 1,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564d1609622f43a77568e196"),
      "name": "Salamancer",
      "description": "Dragao crazy",
      "atack": 300,
      "defense": 140,
      "height": 3,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564d1618622f43a77568e197"),
      "name": "Gengar",
      "description": "Fantasma bolado",
      "atack": 30,
      "defense": 55,
      "height": 0.5,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564d161d622f43a77568e198"),
      "name": "Gengar",
      "description": "Fantasma bolado",
      "atack": 30,
      "defense": 55,
      "height": 0.5,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564dd971ba377a04f9c97baf"),
      "name": "Bulbasaur",
      "description": "Bulbasaur can be seen napping in bright sunlight. There is a seed on its back. By soaking up the sun's rays, the seed grows progressively larger.",
      "attack": 30,
      "defense": 20,
      "height": 0.7,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564dd971ba377a04f9c97bb0"),
      "name": "Charmander",
      "description": "The flame that burns at the tip of its tail is an indication of its emotions. The flame wavers when Charmander is enjoying itself. If the Pokémon becomes enraged, the flame burns fiercely. ",
      "attack": 30,
      "defense": 20,
      "height": 0.6,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564dd971ba377a04f9c97bb1"),
      "name": "Blastoise",
      "description": "Blastoise has water spouts that protrude from its shell. The water spouts are very accurate. They can shoot bullets of water with enough accuracy to strike empty cans from a distance of over 160 feet. ",
      "attack": 40,
      "defense": 40,
      "height": 1.6,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564dd971ba377a04f9c97bb2"),
      "name": "Pikachu",
      "description": "Whenever Pikachu comes across something new, it blasts it with a jolt of electricity. If you come across a blackened berry, it's evidence that this Pokémon mistook the intensity of its charge. ",
      "attack": 30,
      "defense": 20,
      "height": 0.4,
      "moves": [
        "investida",
        "ataque rápido",
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564dd971ba377a04f9c97bb3"),
      "name": "Alakazam",
      "description": "Alakazam's brain continually grows, making its head far too heavy to support with its neck. This Pokémon holds its head up using its psychokinetic power instead. ",
      "attack": 30,
      "defense": 20,
      "height": 1.5,
      "moves": [
        "desvio"
      ]
    }
    {
      "_id": ObjectId("564c833b36bb50ed7beca744"),
      "name": "Yveltal",
      "description": "When this legendary Pokemon wings and tail feathers spread wide and glow red, it absorbs the life force of living creatures",
      "attack": 7,
      "defense": 4,
      "height": 5.8,
      "moves": [
        "desvio"
      ]
    }
    Fetched 16 record(s) in 14ms



## 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
    
    > var query = {$and: [ { moves: "investida"}, {defense: {$gt: 49}}]}
    > db.pokemons.find(query)
    Fetched 0 record(s) in 1ms




## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
    
    > var query = {$and : [{type: 'água'},{attack:{$lt: 50} }] }
    > db.pokemons.remove(query)
    Removed 0 record(s) in 3ms
    WriteResult({
      "nRemoved": 0
    })

## 9. Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

    ´´´
    $ne seleciona o valor que não e igual ao valor especificado
    > db.pokemons.find({attack:{$ne: 30}})
    nesse caso ele seleciona todos os pokemons com attack diferente de 30
    
    $not ele vai inverter a logica do operador o caso de der true vem como false e vice e versa 
    > db.pokemons.find({attack: {$not:{$ne: 30}}})
    nessa query ele retorna o inverso da anterior
