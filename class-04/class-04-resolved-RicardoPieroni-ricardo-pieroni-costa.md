## MongoDb Aula - 04

Autor: Ricardo Pieroni Costa

## 1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, squartle, bulbasauro e charmande
```

var query = {$or:[{nome:/charizard/i},{nome:/pikachu/i},{nome:/caterpie/i},{nome:/bulbasaur/i}]}
var attacks = ['ataque rápido', 'racha mortal'] 
var mod = {$pushAll:{attacks}} 
var options = {multi:true}
db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
db.pokemons.find(query)
{ "_id" : ObjectId("56facd2df085eb276b1d94bc"), "nome" : "Bulbasaur", "description" : "Javali", "type" : "grama", "atack
" : 50, "height" : 0.7, "defense" : 20, "moves" : [ "investida", "foha navalha" ], "attacks" : [ "ataque rápido", "racha
 mortal" ] }
{ "_id" : ObjectId("56facf4ff085eb276b1d94bd"), "nome" : "Caterpie", "description" : "Larva", "type" : "grama", "atack"
: 0.4, "height" : 0.3, "defense" : 20, "moves" : [ "investida" ], "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56fad0f5f085eb276b1d94be"), "nome" : "Pikachu", "description" : "bixa", "type" : "eletrico", "atack"
 : 50, "height" : 0.3, "defense" : 20, "moves" : [ "investida", "choque do trovao" ], "attacks" : [ "ataque rápido", "ra
cha mortal" ] }
{ "_id" : ObjectId("56f1f86073ed2430c3fed72b"), "nome" : "Charizard", "description" : "Lagartão do mangue", "type" : "fl
ame", "atack" : 60, "height" : 1.7, "defense" : 50, "moves" : [ "investida", "salto" ], "attacks" : [ "ataque rápido", "
racha mortal" ] }


```
## 2. Adicionar 1 movimento em todos os pokemons: "desvio"
```

var query ={}
var mod = {$set:{moves:"desvio"}}
var options = {mult:true}
db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
var options = {multi:true}
db.pokemons.update(query,mod,options)
WriteResult({ "nMatched" : 10, "nUpserted" : 0, "nModified" : 9 })
db.pokemons.find(query)
{ "_id" : ObjectId("56f28653cc5cba5a6e01385f"), "nome" : "Blastoise", "description" : "Cabeça das tartarugas", "type" :
"Shellfish", "atack" : 40, "height" : 1.6, "defense" : 50, "moves" : "desvio" }
{ "_id" : ObjectId("56f28746cc5cba5a6e013860"), "nome" : "Beedrill", "description" : "Abelha do CV", "type" : "Bug, pois
on", "atack" : 42, "height" : 1, "defense" : 30, "moves" : "desvio" }
{ "_id" : ObjectId("56f28862cc5cba5a6e013861"), "nome" : "Pidgeot", "description" : "Gavião", "type" : "Flying", "atack"
 : 38, "height" : 1.5, "defense" : 40, "moves" : "desvio" }
{ "_id" : ObjectId("56f288eecc5cba5a6e013862"), "nome" : "Sandslash", "description" : "Rato", "type" : "Ground", "atack"
 : 40, "height" : 1, "defense" : 45, "moves" : "desvio" }
{ "_id" : ObjectId("56facd2df085eb276b1d94bc"), "nome" : "Bulbasaur", "description" : "Javali", "type" : "grama", "atack
" : 50, "height" : 0.7, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56facf4ff085eb276b1d94bd"), "nome" : "Caterpie", "description" : "Larva", "type" : "grama", "atack"
: 0.4, "height" : 0.3, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56fad0f5f085eb276b1d94be"), "nome" : "Pikachu", "description" : "bixa", "type" : "eletrico", "atack"
 : 50, "height" : 0.3, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56fc5cc97d76ed5b78c4f605"), "description" : "Pokemon teste", "nome" : "Testemon", "atack" : 8001, "d
efese" : 8000, "height" : 2.1, "moves" : "desvio" }
{ "_id" : ObjectId("56fd0b5a0b01e714b307fa73"), "active" : true, "nome" : "NaoExisteMon", "type" : "", "atack" : null, "
defense" : null, "height" : 1, "descripion" : "", "moves" : "desvio" }
{ "_id" : ObjectId("56f1f86073ed2430c3fed72b"), "nome" : "Charizard", "description" : "Lagartão do mangue", "type" : "fl
ame", "atack" : 60, "height" : 1.7, "defense" : 50, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ]
}


```
## 3. Adicionar o pokemon 'AindaNãoExisteMon' caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações"
```

var query = {nome:"AindaNãoExisteMon"}
var mod = {$set:{nome:"AindaNãoExisteMon"},$setOnInsert:{defense:null,atack:null,height:null,description:"Sem mais inf
ormações",type:null}}
var options = {upsert:true}
db.pokemons.update(query,mod,options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("56fd6b500b01e714b307fa74")
})
db.pokemons.find(query)
{ "_id" : ObjectId("56fd6b500b01e714b307fa74"), "nome" : "AindaNãoExisteMon", "defense" : null, "atack" : null, "height"
 : null, "description" : "Sem mais informações", "type" : null }


```
## 4. Pesquisar todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito 
```

var query = {attacks:{$in:[/investida/i,/racha mortal/i]}}
db.pokemons.find(query)
{ "_id" : ObjectId("56facd2df085eb276b1d94bc"), "nome" : "Bulbasaur", "description" : "Javali", "type" : "grama", "atack
" : 50, "height" : 0.7, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56facf4ff085eb276b1d94bd"), "nome" : "Caterpie", "description" : "Larva", "type" : "grama", "atack"
: 0.4, "height" : 0.3, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56fad0f5f085eb276b1d94be"), "nome" : "Pikachu", "description" : "bixa", "type" : "eletrico", "atack"
 : 50, "height" : 0.3, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56f1f86073ed2430c3fed72b"), "nome" : "Charizard", "description" : "Lagartão do mangue", "type" : "fl
ame", "atack" : 60, "height" : 1.7, "defense" : 50, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ]
}


```
## 5. Pesquisar todos os pokemons que possuam ataques que você adicionou, escolha seu pokemon favorito
```

var query = {attacks:{$in:[/ataque rápido/i,/racha mortal/i]}}
cb.pokemons.find(query)
2016-03-31T15:50:38.812-0300 E QUERY    [thread1] ReferenceError: cb is not defined :
@(shell):1:1
db.pokemons.find(query)
{ "_id" : ObjectId("56facd2df085eb276b1d94bc"), "nome" : "Bulbasaur", "description" : "Javali", "type" : "grama", "atack
" : 50, "height" : 0.7, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56facf4ff085eb276b1d94bd"), "nome" : "Caterpie", "description" : "Larva", "type" : "grama", "atack"
: 0.4, "height" : 0.3, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56fad0f5f085eb276b1d94be"), "nome" : "Pikachu", "description" : "bixa", "type" : "eletrico", "atack"
 : 50, "height" : 0.3, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56f1f86073ed2430c3fed72b"), "nome" : "Charizard", "description" : "Lagartão do mangue", "type" : "fl
ame", "atack" : 60, "height" : 1.7, "defense" : 50, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ]
}


```
## 6. Pesquisar todos que não são do tipo 'elétrico'
```

var query = {type:{$nin:[/eletric/i]}}
db.pokemons.find(query)
{ "_id" : ObjectId("56f28653cc5cba5a6e01385f"), "nome" : "Blastoise", "description" : "Cabeça das tartarugas", "type" :
"Shellfish", "atack" : 40, "height" : 1.6, "defense" : 50, "moves" : "desvio" }
{ "_id" : ObjectId("56f28746cc5cba5a6e013860"), "nome" : "Beedrill", "description" : "Abelha do CV", "type" : "Bug, pois
on", "atack" : 42, "height" : 1, "defense" : 30, "moves" : "desvio" }
{ "_id" : ObjectId("56f28862cc5cba5a6e013861"), "nome" : "Pidgeot", "description" : "Gavião", "type" : "Flying", "atack"
 : 38, "height" : 1.5, "defense" : 40, "moves" : "desvio" }
{ "_id" : ObjectId("56f288eecc5cba5a6e013862"), "nome" : "Sandslash", "description" : "Rato", "type" : "Ground", "atack"
 : 40, "height" : 1, "defense" : 45, "moves" : "desvio" }
{ "_id" : ObjectId("56facd2df085eb276b1d94bc"), "nome" : "Bulbasaur", "description" : "Javali", "type" : "grama", "atack
" : 50, "height" : 0.7, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56facf4ff085eb276b1d94bd"), "nome" : "Caterpie", "description" : "Larva", "type" : "grama", "atack"
: 0.4, "height" : 0.3, "defense" : 20, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ] }
{ "_id" : ObjectId("56fc5cc97d76ed5b78c4f605"), "description" : "Pokemon teste", "nome" : "Testemon", "atack" : 8001, "d
efese" : 8000, "height" : 2.1, "moves" : "desvio" }
{ "_id" : ObjectId("56fd0b5a0b01e714b307fa73"), "active" : true, "nome" : "NaoExisteMon", "type" : "", "atack" : null, "
defense" : null, "height" : 1, "descripion" : "", "moves" : "desvio" }
{ "_id" : ObjectId("56f1f86073ed2430c3fed72b"), "nome" : "Charizard", "description" : "Lagartão do mangue", "type" : "fl
ame", "atack" : 60, "height" : 1.7, "defense" : 50, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ]
}
{ "_id" : ObjectId("56fd6b500b01e714b307fa74"), "nome" : "AindaNãoExisteMon", "defense" : null, "atack" : null, "height"
 : null, "description" : "Sem mais informações", "type" : null }


```
## 7. Pesquisar todos pokemons que tenham ataque 'racha mortal' e tenham a defesa não menor ou igual a 49
```
var query = {$and:[{attacks:{$in:[/racha*/i]}},{defense:{$not:{$lte:49}}}]}
db.pokemons.find(query)
{ "_id" : ObjectId("56f1f86073ed2430c3fed72b"), "nome" : "Charizard", "description" : "Lagartão do mangue", "type" : "fl
ame", "atack" : 60, "height" : 1.7, "defense" : 50, "moves" : "desvio", "attacks" : [ "ataque rápido", "racha mortal" ]
}


```
## 8. Remova todos os pokemons do tipo water e com attack menor que 50.
```
var aux1 = {type:/water/i}
var aux2 = {atack:{$lt:50}}
var query = {$and:[aux1,aux2]}
db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })

```
