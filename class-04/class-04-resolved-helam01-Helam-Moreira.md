# MongoDB - Aula 04 - Exercício
autor: Helam Moreira

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```
> var query = {name : {$in:[/pikachu|squirtle|bulbassauro|Charmander/i]} };
> var mod = { $pushAll:{moves:['Ataque Genérico 01', 'Ataque Genérico 02']} };
> var opt = {multi : true};
> db.pokemons.update(query, mod, opt)

WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })


> db.pokemons.find(query)

{ "_id" : ObjectId("564286c58abeb1bf550ec732"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02" ] }

{ "_id" : ObjectId("564289128abeb1bf550ec733"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02" ] }

{ "_id" : ObjectId("564289128abeb1bf550ec734"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02" ] }

{ "_id" : ObjectId("564289128abeb1bf550ec735"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02" ] }

```



## 2. **Adicionar** 1 movimento em todos os pokemons: desvio.
```
> var query = {};
> var mod = { $push:{moves:'Desvio'} };
> var opt = {multi : true};

> db.pokemons.update(query, mod, opt)

WriteResult({ "nMatched" : 10, "nUpserted" : 0, "nModified" : 10 })

> db.pokemons.find(query)

{ "_id" : ObjectId("56450b1553af3f25bd6b032c"), "name" : "Nidorina", "description" : "Fica nervoso quando separado de seu grupo", "type" : "Poison", "attack" : 36, "defense" : 14, "height" : 0.8, "moves" : [ "Desvio" ] }

{ "_id" : ObjectId("56450b1553af3f25bd6b032d"), "name" : "Clefairy", "description" : "Em noites de lua cheia este pokemon se reune com seu grupo para cantar para lua", "type" : "Fairy", "attack" : 10, "defense" : 3, "height" : 0.6, "moves" : [ "Desvio" ] }

{ "_id" : ObjectId("56450b1553af3f25bd6b032e"), "name" : "Ninetales", "description" : "É um pokemon que tem 9 rabos. Ele pode viver por até mil anos, por isso é solitário", "type" : "Fox", "attack" : 41, "defense" : 30, "height" : 1.1, "moves" : [ "Desvio" ] }

{ "_id" : ObjectId("56450b1553af3f25bd6b032f"), "name" : "Mewtwo", "description" : "Foi criado por humanos que utilizaram manipulação genética", "type" : "Psychic", "attack" : 100, "defense" : 80, "height" : 2, "moves" : [ "Desvio" ] }

{ "_id" : ObjectId("564286c58abeb1bf550ec732"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio" ] }

{ "_id" : ObjectId("564289128abeb1bf550ec733"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio" ] }

{ "_id" : ObjectId("564289128abeb1bf550ec734"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio" ] }

{ "_id" : ObjectId("564289128abeb1bf550ec735"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio" ] }

{ "_id" : ObjectId("56428a308abeb1bf550ec736"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio" ] }

{ "_id" : ObjectId("56450b1553af3f25bd6b032b"), "name" : "Sandshrew", "description" : "Seu corpo tem a capacidade de absorver água, sem perda, o que favorece sua sobrevivência no deserto", "type" : "Terra", "attack" : 32, "defense" : 20, "height" : 0.6, "moves" : [ "Desvio" ] }

```


## 3. **Adicionar** o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
> var query = {name : /AindaNaoExisteMon/i};
> var mod = { $setOnInsert:{name : "AindaNaoExisteMon", description : "Sem maiores informações", attack : null, defense : null, height : null, moves : null} };
> var opt = {upsert : true};
> db.pokemons.update(query, mod, opt)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("5650d7cede69a5a7bbb2fc1a")
})

> db.pokemons.find(query)
{ "_id" : ObjectId("5650d7cede69a5a7bbb2fc1a"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "attack" : null, "defense" : null, "height" : null, "moves" : null }

```


## 4. Pesquisar todos o pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.
```
> var query = {moves : {$in : [/investida/i, /Ataque Genérico 01/i]} };
> db.pokemons.find(query)

{ "_id" : ObjectId("56450b1553af3f25bd6b032c"), "name" : "Nidorina", "description" : "Fica nervoso quando separado de seu grupo", "type" : "Poison", "attack" : 36, "defense" : 14, "height" : 0.8, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032e"), "name" : "Ninetales", "description" : "É um pokemon que tem 9 rabos. Ele pode viver por até mil anos, por isso é solitário", "type" : "Fox", "attack" : 41, "defense" : 30, "height" : 1.1, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032f"), "name" : "Mewtwo", "description" : "Foi criado por humanos que utilizaram manipulação genética", "type" : "Psychic", "attack" : 100, "defense" : 80, "height" : 2, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("564286c58abeb1bf550ec732"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec733"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec735"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("56428a308abeb1bf550ec736"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032b"), "name" : "Sandshrew", "description" : "Seu corpo tem a capacidade de absorver água, sem perda, o que favorece sua sobrevivência no deserto", "type" : "Terra", "attack" : 32, "defense" : 20, "height" : 0.6, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032d"), "name" : "Clefairy", "description" : "Em noites de lua cheia este pokemon se reune com seu grupo para cantar para lua", "type" : "Fairy", "attack" : 10, "defense" : 3, "height" : 0.6, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec734"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }

```


## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
> var query = {moves : /Ataque Genérico 02/i };

> db.pokemons.find(query)

{ "_id" : ObjectId("564286c58abeb1bf550ec732"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "electric", "attack" : 55, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec733"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec735"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec734"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
>

```


## 6. Pesquisar **todos** os pokemons que não são do tipo 'elétrico'.
```
> var query = {type : {$not:/electric/i} };

> db.pokemons.find(query)

{ "_id" : ObjectId("56450b1553af3f25bd6b032c"), "name" : "Nidorina", "description" : "Fica nervoso quando separado de seu grupo", "type" : "Poison", "attack" : 36, "defense" : 14, "height" : 0.8, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032e"), "name" : "Ninetales", "description" : "É um pokemon que tem 9 rabos. Ele pode viver por até mil anos, por isso é solitário", "type" : "Fox", "attack" : 41, "defense" : 30, "height" : 1.1, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032f"), "name" : "Mewtwo", "description" : "Foi criado por humanos que utilizaram manipulação genética", "type" : "Psychic", "attack" : 100, "defense" : 80, "height" : 2, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec733"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec735"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("56428a308abeb1bf550ec736"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032b"), "name" : "Sandshrew", "description" : "Seu corpo tem a capacidade de absorver água, sem perda, o que favorece sua sobrevivência no deserto", "type" : "Terra", "attack" : 32, "defense" : 20, "height" : 0.6, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("5650d7cede69a5a7bbb2fc1a"), "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "attack" : null, "defense" : null, "height" : null, "moves" : null }
{ "_id" : ObjectId("56450b1553af3f25bd6b032d"), "name" : "Clefairy", "description" : "Em noites de lua cheia este pokemon se reune com seu grupo para cantar para lua", "type" : "Fairy", "attack" : 10, "defense" : 3, "height" : 0.6, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec734"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
>

```


## 7. Pesquisar **todos** os pokemons que tenham o ataque 'investida' **E** tenham a defesa **menor ou igual** a 49.
```
> var query = { $and : [{ moves : /investida/i }, {defense : {$lte : 49}}]  };

> db.pokemons.find(query)

{ "_id" : ObjectId("56450b1553af3f25bd6b032c"), "name" : "Nidorina", "description" : "Fica nervoso quando separado de seu grupo", "type" : "Poison", "attack" : 36, "defense" : 14, "height" : 0.8, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032e"), "name" : "Ninetales", "description" : "É um pokemon que tem 9 rabos. Ele pode viver por até mil anos, por isso é solitário", "type" : "Fox", "attack" : 41, "defense" : 30, "height" : 1.1, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56428a308abeb1bf550ec736"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032b"), "name" : "Sandshrew", "description" : "Seu corpo tem a capacidade de absorver água, sem perda, o que favorece sua sobrevivência no deserto", "type" : "Terra", "attack" : 32, "defense" : 20, "height" : 0.6, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032d"), "name" : "Clefairy", "description" : "Em noites de lua cheia este pokemon se reune com seu grupo para cantar para lua", "type" : "Fairy", "attack" : 10, "defense" : 3, "height" : 0.6, "moves" : [ "Desvio", "Investida" ] }

```


## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.
```
> var query = { attack : {$lte : 50}  };

> db.pokemons.find(query)

{ "_id" : ObjectId("56450b1553af3f25bd6b032c"), "name" : "Nidorina", "description" : "Fica nervoso quando separado de seu grupo", "type" : "Poison", "attack" : 36, "defense" : 14, "height" : 0.8, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032e"), "name" : "Ninetales", "description" : "É um pokemon que tem 9 rabos. Ele pode viver por até mil anos, por isso é solitário", "type" : "Fox", "attack" : 41, "defense" : 30, "height" : 1.1, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec733"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("564289128abeb1bf550ec735"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Ataque Genérico 01", "Ataque Genérico 02", "Desvio", "Investida" ] }
{ "_id" : ObjectId("56428a308abeb1bf550ec736"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032b"), "name" : "Sandshrew", "description" : "Seu corpo tem a capacidade de absorver água, sem perda, o que favorece sua sobrevivência no deserto", "type" : "Terra", "attack" : 32, "defense" : 20, "height" : 0.6, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56450b1553af3f25bd6b032d"), "name" : "Clefairy", "description" : "Em noites de lua cheia este pokemon se reune com seu grupo para cantar para lua", "type" : "Fairy", "attack" : 10, "defense" : 3, "height" : 0.6, "moves" : [ "Desvio", "Investida" ] }

```