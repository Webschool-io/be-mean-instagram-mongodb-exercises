# MongoDB - Aula 04 - Exercício
autor: Douglas Caina

## 1 Adicionando dois ataques

    ```

db.pokemons.find({"height":{$lt:0.5}})
{ "_id" : ObjectId("564276f8732d8896c19164c1"), "name" : "Pikachu", "description" : "Raio amarelo", "attack" : 45, "defense" : 4, "height" : 0.3 }
{ "_id" : ObjectId("564276f8732d8896c19164c2"), "name" : "Charmander", "description" : "Dragonino", "attack" : 32, "defense" : 80, "height" : 0.4 }
{ "_id" : ObjectId("564276f8732d8896c19164c4"), "name" : "Jiglipuf", "description" : "Adormece tudo", "attack" : 99, "defense" : 2, "height" : 0.1 }
{ "_id" : ObjectId("564276f8732d8896c19164c5"), "name" : "Bullbassaur", "description" : "Plana legal", "attack" : 65, "defense" : 1, "height" : 0.3 }

var attack_list = ["Furia","Cura"];
var query = {name:{$in:[/pikachu/i,/squirtle/i,/Bullbassaur/i,/charmander/i]}}
var modificador = {$pushAll:{moves:attack_list}}
var options = {multi:true}
db.pokemons.update(query,modificador,options);

    ```

## 2 Adicionar o movimento Desvio

```
var query = {};
var attack_list = ['desvio'];
var mod = {$pushAll:{moves:attack_list}}
var options = {multi:true}
db.pokemons.update(query,mod,options);

```

## 3 Adicionar o pokemon AindaNaoExisteMon caso ele nao exista com todos os valores null

```
var query = {name:/AindaNaoExisteMon/i}
var mod = {$setOnInsert:{name:"AindaNaoExisteMon",attack:null, defense:null,height:null}}
var opt = {upsert:true}
db.pokemons.update(query, mod, opt);
```

## 4 Pesquisar todos os pokemons que possuam o ataque investida e mais um que eu quiser
```
var query = {moves:{$in:[/investida/i,/cura/i]}}
db.pokemons.find(query)
```

## 5 Pesquisar Todos pokemons com ataque que eu adicinei

```
var query = {moves:{$in:[/cura/i]}}
db.pokemons.find(query)
```

## 6 Pesquisar todos os pekemons do tipo eletrico
```
var query = {type:/eletrico/i}
db.pokemons.find(query)
```

## 7 Pesquisar todos os pekemons do tipo eletrico
```
var query = {$and:[{moves:{$in:[/investida/i]}},{defense:{$lte:49}}]}
db.pokemons.find(query)
```

## 8 Remover todos os pokemons do tipo agua com ataque menor que 50
```
var query = {$and:[{type:/agua/i},{attack:{$lt:50}}]}
db.pokemons.remove(query)
```



