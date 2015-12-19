+# MongoDB - Aula 04 - Exercício
+autor: Marco Aurellio
+
+## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.


> var query = { name: {$in : ["Bulbassauro", "Charmander"]} }
> var mod = { $inc: { attack: 2}}
> var options = { multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 2, "nUpserted" : 0, "nModified" : 2 })



+## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

> var query = {}
> var mod = { $push: { moves: "desvio" }}
> var options = { multi: true}
> db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 9, "nUpserted" : 0, "nModified" : 9 })
>


+## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
+
> var query ={name : /AindaNaoExisteMon/i}
> var mod = {
		$setOnInsert : {
						"active" : false,
						"nome":"AindaNaoExisteMon",
						"attack":null,"defense":null ,
						"height":null,"
						description":"Sem maiores Informações" 
					   }
			}
> var op ={ upsert : true}
> db.pokemons.update(query, mod ,op)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,
        "_id" : ObjectId("564cf65866323780fdce764e")
})
>



+

+## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
+

> var query = { moves: { $all:  ["investida", "desvio"]}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56437e8683be273596123134"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type"
: "electric", "attack" : 55, "height" : 0.4, "movies" : [ "choque do trovao", "desvio" ], "active" : false, "moves" : [
"investida", "desvio" ] }
{ "_id" : ObjectId("56437f5083be273596123135"), "name" : "Furicu", "description" : "Pokemon peidão", "type" : "gas", "at
tack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio" ], "movies" : [ "desvio" ] }
{ "_id" : ObjectId("56437f9283be273596123136"), "description" : "mudando com o set", "name" : "testemon", "attack" : 800
0, "defense" : 8000, "movies" : [ "choque do trovao", "desvio" ], "moves" : [ "investida", "desvio" ], "active" : false
}
{ "_id" : ObjectId("56437fe683be273596123137"), "name" : "Xotinha", "description" : "teste aaaa", "type" : "feminino", "
attack" : 105, "height" : 0.6, "active" : false, "moves" : [ "investida", "desvio" ], "movies" : [ "desvio" ] }
{ "_id" : ObjectId("564c5d517f06996ec92d8698"), "description" : "mudei porra", "name" : "Testemon", "attack" : 8000, "de
fense" : 7998, "movies" : [ "choque do trovão", "desvio" ], "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("564cb1e466323780fdce764d"), "active" : false, "name" : "NaoExisteMon", "attack" : null, "defense" :
null, "height" : null, "description" : "Sem maiores Informações", "moves" : [ "investida", "desvio" ], "movies" : [ "des
vio" ] }
>
+
+## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
+
> var query = { moves: { $all: ["investida", "desvio"]}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56437e8683be273596123134"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type"
: "electric", "attack" : 55, "height" : 0.4, "movies" : [ "choque do trovao", "desvio" ], "active" : false, "moves" : [
"investida", "desvio" ] }
{ "_id" : ObjectId("56437f5083be273596123135"), "name" : "Furicu", "description" : "Pokemon peidão", "type" : "gas", "at
tack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio" ], "movies" : [ "desvio" ] }
{ "_id" : ObjectId("56437f9283be273596123136"), "description" : "mudando com o set", "name" : "testemon", "attack" : 800
0, "defense" : 8000, "movies" : [ "choque do trovao", "desvio" ], "moves" : [ "investida", "desvio" ], "active" : false
}
{ "_id" : ObjectId("56437fe683be273596123137"), "name" : "Xotinha", "description" : "teste aaaa", "type" : "feminino", "
attack" : 105, "height" : 0.6, "active" : false, "moves" : [ "investida", "desvio" ], "movies" : [ "desvio" ] }
{ "_id" : ObjectId("564c5d517f06996ec92d8698"), "description" : "mudei porra", "name" : "Testemon", "attack" : 8000, "de
fense" : 7998, "movies" : [ "choque do trovão", "desvio" ], "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("564cb1e466323780fdce764d"), "active" : false, "name" : "NaoExisteMon", "attack" : null, "defense" :
null, "height" : null, "description" : "Sem maiores Informações", "moves" : [ "investida", "desvio" ], "movies" : [ "des
+
+## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
+
> var query = { type: {$ne: "electric"}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56437f5083be273596123135"), "name" : "Furicu", "description" : "Pokemon peidão", "type" : "gas", "at
tack" : 55, "height" : 0.4, "active" : false, "moves" : [ "investida", "desvio" ], "movies" : [ "desvio" ] }
{ "_id" : ObjectId("56437f9283be273596123136"), "description" : "mudando com o set", "name" : "testemon", "attack" : 800
0, "defense" : 8000, "movies" : [ "choque do trovao", "desvio" ], "moves" : [ "investida", "desvio" ], "active" : false
}
{ "_id" : ObjectId("56437fe683be273596123137"), "name" : "Xotinha", "description" : "teste aaaa", "type" : "feminino", "
attack" : 105, "height" : 0.6, "active" : false, "moves" : [ "investida", "desvio" ], "movies" : [ "desvio" ] }
{ "_id" : ObjectId("564c5d517f06996ec92d8698"), "description" : "mudei porra", "name" : "Testemon", "attack" : 8000, "de
fense" : 7998, "movies" : [ "choque do trovão", "desvio" ], "active" : false, "moves" : [ "investida", "desvio" ] }
{ "_id" : ObjectId("564cb1e466323780fdce764d"), "active" : false, "name" : "NaoExisteMon", "attack" : null, "defense" :
null, "height" : null, "description" : "Sem maiores Informações", "moves" : [ "investida", "desvio" ], "movies" : [ "des
vio" ] }
{ "_id" : ObjectId("564cc9f324f342965094dd4f"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type"
: "grama", "attack" : 51, "height" : 0.4, "movies" : [ "desvio" ], "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564cca2724f342965094dd50"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de f
ofinho", "type" : "fogo", "attack" : 54, "height" : 0.6, "movies" : [ "desvio" ], "moves" : [ "desvio" ] }
{ "_id" : ObjectId("564cca7724f342965094dd51"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe
", "type" : "água", "attack" : 48, "height" : 0.5, "movies" : [ "desvio" ], "moves" : [ "desvio" ] }
>



+
+## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
+
> var queryInvestida = { $all: ["investida"]}
> var queryDefesa = { $not: { $gte: 49}}
> var query = { moves: queryInvestida, attack: queryDefesa }
> db.pokemons.find(query)
{ "_id" : ObjectId("564cb1e466323780fdce764d"), "active" : false, "name" : "NaoExisteMon", "attack" : null, "defense" :
null, "height" : null, "description" : "Sem maiores Informações", "moves" : [ "investida", "desvio" ], "movies" : [ "des
vio" ] }
>

+
+## Remova **todos** os pokemons do tipo água e com attack menor que 50.
+
+```
> var query = { $and:[ { type: "água" }, { attack: { $lt: 50 }} ]};
> db.pokemons.remove(query);
WriteResult({ "nRemoved" : 1 })
>


+
+