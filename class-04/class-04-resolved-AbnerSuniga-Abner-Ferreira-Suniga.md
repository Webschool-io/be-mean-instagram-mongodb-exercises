# MongoDB - Aula 04 - Exercício
autor: Abner Ferreira Suniga

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

``` 
  > var query = or:[{name:"Pikachu"},{name:"Squirtle"},{name:"Bulbassauro"},{name:"Charmander"}]}
  > var mod = {$pushAll:{moves:["ataque forte","ataque fraco"]}}
  > var option = {multi: true}
  > db.pokemons.update(query,mod,option)
  WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
  > db.pokemons.find()
  { "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovao", "ataque forte", "ataque fraco"], "active" : false }
  { "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco" ] }
  { "_id" : ObjectId("57d419a9c953b335c0afd7ba"), "name" : "Charmander", "description" : "Esse e o cao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco" ] }
  { "_id" : ObjectId("57d419bcc953b335c0afd7bb"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco" ] }
  { "_id" : ObjectId("57d41cbcc953b335c0afd7bc"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida" ] }
  { "_id" : ObjectId("57d4a715b86de2349c165cc1"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 7901, "defense" : 8000, "active" : false, "moves" : [ "investida" ] }
```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
  > mod = {$push:{moves:"desvio"}}
  { "$push" : { "moves" : "desvio" } }
  > query = {}
  { }
  > db.pokemons.update(query,mod,option)
  WriteResult({ "nMatched" : 6, "nUpserted" : 0, "nModified" : 6 })
  > db.pokemons.find()
  { "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovao", "ataque forte", "ataque fraco","desvio" ], "active" : false }
  { "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419a9c953b335c0afd7ba"), "name" : "Charmander", "description" : "Esse e o cao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419bcc953b335c0afd7bb"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d41cbcc953b335c0afd7bc"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
  { "_id" : ObjectId("57d4a715b86de2349c165cc1"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 7901, "defense" : 8000, "active" : false, "moves" : [ "investida", "desvio" ] }
  >
```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
```
  > var query = {name:"AindaNaoExisteMon"}
  > var option = {upsert: true}
  > var mod = {$setOnInsert:{"name" : null, "description" : "Sem descricao", "type" : null, "attack" :null, "height" :null, "defense" : null, "active" : null, "moves" :null}}
  > db.pokemons.update(query,mod,option)
  WriteResult({
          "nMatched" : 0,
          "nUpserted" : 1,
          "nModified" : 0,
          "_id" : ObjectId("57d5cbfbd1d7180d5fa820fa")
  })
  > db.pokemons.findOne({"_id" : ObjectId("57d5cbfbd1d7180d5fa820fa")})
  {
          "_id" : ObjectId("57d5cbfbd1d7180d5fa820fa"),
          "name" : null,
          "description" : "Sem descricao",
          "type" : null,
          "attack" : null,
          "height" : null,
          "defense" : null,
          "active" : null,
          "moves" : null
  }
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
```
  > var poke = {"name" : "Abnermon", "description" : "Aprendiz", "type" : "humano", "attack" : 70, "height" : 0.3, "defense" : 75, "active" : false, "moves" : ["desvio" ]}
  > db.pokemons.insert(poke)
  > var query = {$or:[{moves:{$in:["investida"]}},{name:"Abnermon"}]}
  > db.pokemons.find(query)
  { "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovao", "ataque forte", "ataque fraco","desvio" ], "active" : false }
  { "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419a9c953b335c0afd7ba"), "name" : "Charmander", "description" : "Esse e o cao chupando manga de f
  ofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "ataque forte", "ata
  que fraco", "desvio" ] }
  { "_id" : ObjectId("57d419bcc953b335c0afd7bb"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d41cbcc953b335c0afd7bc"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
  { "_id" : ObjectId("57d4a715b86de2349c165cc1"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 7901, "defense" : 8000, "active" : false, "moves" : [ "investida", "desvio" ] }
  { "_id" : ObjectId("57d5ce151430ec15501d8a0c"), "name" : "Abnermon", "description" : "Aprendiz", "type" : "humano", "attack" : 70, "height" : 0.3, "defense" : 75, "active" : false, "moves" : [ "desvio" ] }
  >
```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
```
  > var query = {moves:{$in:["ataque forte","ataque fraco"]}}
  > db.pokemons.find(query)
  { "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovao", "ataque forte", "ataque fraco","desvio" ], "active" : false }
  { "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419a9c953b335c0afd7ba"), "name" : "Charmander", "description" : "Esse e o cao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419bcc953b335c0afd7bb"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  >
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
```
  > query = {type:{$ne:"eletric"}}
  { "type" : { "$ne" : "eletric" } }
  > db.pokemons.find(query)
  { "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419a9c953b335c0afd7ba"), "name" : "Charmander", "description" : "Esse e o cao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves": [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419bcc953b335c0afd7bb"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d41cbcc953b335c0afd7bc"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "active" : false, "moves" : [ "investida", "desvio" ] }
  { "_id" : ObjectId("57d4a715b86de2349c165cc1"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 7901 , "defense" : 8000, "active" : false, "moves" : [ "investida", "desvio" ] }
  { "_id" : ObjectId("57d5cbfbd1d7180d5fa820fa"), "name" : null, "description" : "Sem descricao", "type" : null, "attack": null, "height" : null, "defense" : null, "active" : null, "moves" : null }
  { "_id" : ObjectId("57d5ce151430ec15501d8a0c"), "name" : "Abnermon", "description" : "Aprendiz", "type" : "humano", "attack" : 70, "height" : 0.3, "defense" : 75, "active" : false, "moves" : [ "desvio" ] }
  >
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
  > query = {$and:[{moves:{$in:["investida"]}},{defense:{$not:{$lte:49}}}]}
  > db.pokemons.find(query)
  { "_id" : ObjectId("57d41812c953b335c0afd7b8"), "name" : "Pikachu", "description" : "Raio eletrico bem fofinho", "type": "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "investida", "choque do trovao", "ataque forte", "ataque fraco","desvio" ], "active" : false }
  { "_id" : ObjectId("57d4198ac953b335c0afd7b9"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type": "grama", "attack" : 49, "height" : 0.4, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419a9c953b335c0afd7ba"), "name" : "Charmander", "description" : "Esse e o cao chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d419bcc953b335c0afd7bb"), "name" : "Squirtle", "description" : "Ejeta agua que passarinho nao bebe", "type" : "agua", "attack" : 48, "height" : 0.5, "active" : false, "moves" : [ "investida", "ataque forte", "ataque fraco", "desvio" ] }
  { "_id" : ObjectId("57d4a715b86de2349c165cc1"), "description" : "Pokemon de teste", "name" : "Testemon", "attack" : 7901, "defense" : 8000, "active" : false, "moves" : [ "investida", "desvio" ] }
```

## Remova **todos** os pokemons do tipo água e com attack menor que 50.##

```
  > var query = {$and:[{type:"agua"},{attack:{$lt: 50}}]}
  > db.pokemons.remove(query)
  WriteResult({ "nRemoved" : 1 })
```