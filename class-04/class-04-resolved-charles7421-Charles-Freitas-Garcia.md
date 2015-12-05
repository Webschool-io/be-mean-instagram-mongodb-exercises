# MongoDB - Aula 04 - Exercício
autor: Charles de Freitas Garcia

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

> var consulta = {$or: [{name:'Pikachu'}, {name:'Squirtle'}, {name:'Bulbassauro'}, {name:'Charmander'}]}
> var mod = {$set: {attack: ['100', '120']}} 
> var options = {multi: true}
> db.pokemons.update(consulta, mod, options) 
  ...
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

> var consulta = {}
> var mod = {$set: {moves: ['desvio']}} 
> var options = {multi: true}
> db.pokemons.update(consulta, mod, options) 
  ...
WriteResult({ "nMatched" : 5, "nUpserted" : 0, "nModified" : 5 })

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

> var consulta = {name : "/AindaNaoExisteMon/i"}
> var mod = {
	$setOnInsert: {
	  name : "null",
	  attack : null,
	  height : null,
	  description: "Sem maiores informações"
   }
}
> var options = {upsert: true}
> db.pokemons.update(consulta, mod, options)

WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("5657c3931eb7e817bb3fc312")
})
> db.pokemons.find()

{ "_id" : ObjectId("5642ac9ec71f884d2e5c4cce"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : [ "100", "120" ]
, "height" : 0.4, "moves" : [ "desvio" ] }

{ "_id" : ObjectId("5642ad88c71f884d2e5c4ccf"), "name" : "Bulbassauro", "descrip
tion" : "Chicote de trepadeira", "type" : "grama", "attack" : [ "100", "120" ],
"height" : 0.4, "moves" : [ "desvio" ] }

{ "_id" : ObjectId("5642adc2c71f884d2e5c4cd0"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "
100", "120" ], "height" : 0.6, "moves" : [ "desvio" ] }

{ "_id" : ObjectId("5642adeec71f884d2e5c4cd1"), "name" : "Squirtle", "descriptio
n" : "Ejeta água que passarinho não bebe", "type" : "agua", "attack" : [ "100",
"120" ], "height" : 0.5, "moves" : [ "desvio" ] }

{ "_id" : ObjectId("5642aed7c71f884d2e5c4cd2"), "name" : "Caterpie", "descriptio
n" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defens
e" : 35, "moves" : [ "desvio" ] }

{ "_id" : ObjectId("5657c3931eb7e817bb3fc312"), "name" : "null", "attack" : null
, "height" : null, "description" : "Sem maiores informações" }


## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

-- Meu DB não tem outros moves, então vou inserir.

> var consulta = {}
> var mod = {$push: {moves: ['explosão galatica']}}
> var options = {multi: true}
> db.pokemons.update(consulta, mod, options) 
-----------------------------------------------------------
> var consulta = {moves: {$all: ['explosão galática', 'investida']}}
> db.pokemons.find(consulta)
... 
> db.pokemons.find(consulta)
{ "_id" : ObjectId("5642ac9ec71f884d2e5c4cce"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : [ "100", "120" ]
, "height" : 0.4, "moves" : [ "investida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5642ad88c71f884d2e5c4ccf"), "name" : "Bulbassauro", "descrip
tion" : "Chicote de trepadeira", "type" : "grama", "attack" : [ "100", "120" ],
"height" : 0.4, "moves" : [ "investida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5642adeec71f884d2e5c4cd1"), "name" : "Squirtle", "descriptio
n" : "Ejeta água que passarinho não bebe", "type" : "agua", "attack" : [ "100",
"120" ], "height" : 0.5, "moves" : [ "investida", "desvio", "explosão galática"
] }

{ "_id" : ObjectId("5642aed7c71f884d2e5c4cd2"), "name" : "Caterpie", "descriptio
n" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defens
e" : 35, "moves" : [ "investida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5657c3931eb7e817bb3fc312"), "name" : "null", "attack" : null
, "height" : null, "description" : "Sem maiores informações", "moves" : [ "inves
tida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5642adc2c71f884d2e5c4cd0"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "
100", "120" ], "height" : 0.6, "moves" : [ "investida", "desvio", "explosão galá
tica" ] }

-----------------------------------------------------------
> var consulta = {name : 'Charmander'}
> db.pokemons.find(consulta)
... 
{ "_id" : ObjectId("5642adc2c71f884d2e5c4cd0"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "
100", "120" ], "height" : 0.6, "moves" : [ "investida", "desvio", "explosão galá
tica" ] }


## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

> var consulta = {attack: {$in: ['100', '120']}}
> db.pokemons.find(consulta)

{ "_id" : ObjectId("5642ac9ec71f884d2e5c4cce"), "name" : "Pikachu", "description
" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : [ "100", "120" ]
, "height" : 0.4, "moves" : [ "investida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5642ad88c71f884d2e5c4ccf"), "name" : "Bulbassauro", "descrip
tion" : "Chicote de trepadeira", "type" : "grama", "attack" : [ "100", "120" ],
"height" : 0.4, "moves" : [ "investida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5642adeec71f884d2e5c4cd1"), "name" : "Squirtle", "descriptio
n" : "Ejeta água que passarinho não bebe", "type" : "agua", "attack" : [ "100",
"120" ], "height" : 0.5, "moves" : [ "investida", "desvio", "explosão galática"
] }

{ "_id" : ObjectId("5642adc2c71f884d2e5c4cd0"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "
100", "120" ], "height" : 0.6, "moves" : [ "investida", "desvio", "explosão galá
tica" ] }

-----------------------------------------------------------
> var consulta = {name : 'Caterpie'}
> db.pokemons.find(consulta)
... 
{ "_id" : ObjectId("5642aed7c71f884d2e5c4cd2"), "name" : "Caterpie", "descriptio
n" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defens
e" : 35, "moves" : [ "investida", "desvio", "explosão galática" ] }


## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

> var consulta = {type : {$ne: 'eletric'}}
> db.pokemons.find(consulta)

{ "_id" : ObjectId("5642ad88c71f884d2e5c4ccf"), "name" : "Bulbassauro", "descrip
tion" : "Chicote de trepadeira", "type" : "grama", "attack" : [ "100", "120" ],
"height" : 0.4, "moves" : [ "investida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5642adeec71f884d2e5c4cd1"), "name" : "Squirtle", "descriptio
n" : "Ejeta água que passarinho não bebe", "type" : "agua", "attack" : [ "100",
"120" ], "height" : 0.5, "moves" : [ "investida", "desvio", "explosão galática"
] }

{ "_id" : ObjectId("5642aed7c71f884d2e5c4cd2"), "name" : "Caterpie", "descriptio
n" : "Larva Lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defens
e" : 35, "moves" : [ "investida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5657c3931eb7e817bb3fc312"), "name" : "null", "attack" : null
, "height" : null, "description" : "Sem maiores informações", "moves" : [ "inves
tida", "desvio", "explosão galática" ] }

{ "_id" : ObjectId("5642adc2c71f884d2e5c4cd0"), "name" : "Charmander", "descript
ion" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : [ "
100", "120" ], "height" : 0.6, "moves" : [ "investida", "desvio", "explosão galá
tica" ] }


## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

> var consulta = {$and: [{moves: 'investida'}, {defense: {$gte: 49}}]}
> db.pokemons.find(consulta)



## Remova **todos** os pokemons do tipo água e com attack menor que 50.
> var consulta = {$and: [{type: 'water'}, {attack: {$lt: 50}}]}
> db.pokemons.remove(consulta)
...
db.pokemons.remove(consulta)


## Esse item não está no vídeo e se você fizer significa que você lê as coisas, nesse exercício demonstre qual a diferença entre os operadores $ne e $not.

$ne
É um operador de comparação, not Equal, e retorna documentos se o valor que NÃO SÃO IGUAIS a consulta solicitada. 
Para comparar os campos, eles devem existir no documento.
** Não aceita REGEX **

Se precisar restringir os caracteres, deve ser feito assim:
** db.inventory.find( { item: { $not: /^p.*/ } } ) ** 
Esta consulta iria selecionar todos os documentos da Collection inventário onde o item não começar com a letra "P".


$not
É um operador lógico, not, e retorna documentos que NÃO CORRESPONDEM ao valor da consulta solicitada.
Para comparar os campos, eles não precisam existir no documento.
** Aceita REGEX **

Recomendação do Manual do MongoDB
"So, use the $not operator for logical disjunctions and the $ne operator to test the contents of fields directly." - 
Então, use o operador $not para disjunções logicas e o operador $ne para testar o conteudo de um campo diretamente.
