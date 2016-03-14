# MongoDB - Aula 04 - Exercício
Autor: Simone Amorim

##1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```
var query = {name: {$in:['Pikachu', 'Squirtle', 'Bulbassauro' ,'Charmander'] }}
var attacks = ["Surf", "Raio Solar"]
var mod = {$pushAll: {moves: attacks}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 4, "nUpserted" : 0, "nModified" : 4 })
db.pokemons.find(query)
{ "_id" : ObjectId("56afa23a198cc7e091288cf1"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "Surf", "Raio Solar" ] }
{ "_id" : ObjectId("56afa4cf198cc7e091288cf2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Surf", "Raio Solar" ] }
{ "_id" : ObjectId("56afa5a7198cc7e091288cf3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Surf", "Raio Solar" ] }
{ "_id" : ObjectId("56afa68e198cc7e091288cf4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Surf", "Raio Solar" ] }
```  
<br/>  

##2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.##

```
var query = {}
var mod = {$push: {moves: 'Desvio'}}
var options = {multi: true}
db.pokemons.update(query, mod, options)
WriteResult({ "nMatched" : 10, "nUpserted" : 0, "nModified" : 10 })
db.pokemons.find()
{ "_id" : ObjectId("56b0dbb8d50150923e9d15af"), "name" : "Mew", "description" : "Gatinho mais fofinho que já vi!", "type" : "psíquico", "attack" : 100, "height" : 0.41, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b0"), "name" : "Raikou", "description" : "A fera lendária do raio", "type" : "elétrico", "attack" : 85, "height" : 1.91, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b1"), "name" : "Entei", "description" : "Veloz pokemon do fogo", "type" : "fogo", "attack" : 115, "height" : 2.11, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b2"), "name" : "Suicine", "description" : "Cão lendário que controla as águas", "type" : "água", "attack" : 75, "height" : 2.01, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b3"), "name" : "Charizard", "description" : "Conhecido como dragão inimigo de são jorge", "type" : "fogo", "attack" : 84, "height" : 1.7, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56afa23a198cc7e091288cf1"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa4cf198cc7e091288cf2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa5a7198cc7e091288cf3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa68e198cc7e091288cf4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afb07f198cc7e091288cf5"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio" ] }
```
<br/> 
##3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##

```
var query ={name: /AindaNaoExisteMon/i}
var mod = {$set: {active: true}, $setOnInsert: {name: "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "moves": [null]} }
var options = {upsert: true}
ddb.pokemons.update(query, mod, options)
WriteResult({
        "nMatched" : 0,
        "nUpserted" : 1,
        "nModified" : 0,        
        "_id" : ObjectId("56b2434467f4037b35688b9c")
})

db.pokemons.find(query)
{ "_id" : ObjectId("56b2434467f4037b35688b9c"), "active" : true, "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "moves" : [ null ] }

```
<br/>
##4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##

```
var query = { moves: {$in: ['Investida', 'Surf']}}
> db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b1"), "name" : "Entei", "description" : "Veloz pokemon do fogo", "type" : "fogo", "attack" : 115, "height" : 2.11, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b3"), "name" : "Charizard", "description" : "Conhecido como dragão inimigo de são jorge", "type" : "fogo", "attack" : 84, "height" : 1.7, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56afa23a198cc7e091288cf1"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa4cf198cc7e091288cf2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa5a7198cc7e091288cf3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa68e198cc7e091288cf4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afb07f198cc7e091288cf5"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio", "Investida" ] }

```
<br/>
##5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##

```
var query = { moves: {$in: ['Surf', 'Raio Solar']}}
db.pokemons.find(query)
{ "_id" : ObjectId("56afa23a198cc7e091288cf1"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa4cf198cc7e091288cf2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa5a7198cc7e091288cf3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa68e198cc7e091288cf4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
```
<br/>
##6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##

```
var query = { type: {$ne: "elétrico"}}
db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15af"), "name" : "Mew", "description" : "Gatinho mais fofinho que já vi!", "type" : "psíquico", "attack" : 100, "height" : 0.41, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b1"), "name" : "Entei", "description" : "Veloz pokemon do fogo", "type" : "fogo", "attack" : 115, "height" : 2.11, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b2"), "name" : "Suicine", "description" : "Cão lendário que controla as águas", "type" : "água", "attack" : 75, "height" : 2.01, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b3"), "name" : "Charizard", "description" : "Conhecido como dragão inimigo de são jorge", "type" : "fogo", "attack" : 84, "height" : 1.7, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56afa4cf198cc7e091288cf2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa5a7198cc7e091288cf3"), "name" : "Charmander", "description" : "Esse é o cão chupando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa68e198cc7e091288cf4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afb07f198cc7e091288cf5"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56b2434467f4037b35688b9c"), "active" : true, "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "moves" : [ null ] }
```
<br/>
##7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##

```
var query = {$and: [{moves: 'Investida'}, {defense: {$not: {$lte: 49}}}]}
db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b1"), "name" : "Entei", "description" : "Veloz pokemon do fogo", "type" : "fogo", "attack" : 115, "height" : 2.11, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b3"), "name" : "Charizard", "description" : "Conhecido como dragão inimigo de são jorge", "type" : "fogo", "attack" : 84, "height" : 1.7, "moves" : [ "Desvio", "Investida" ] }
```

<br/>

##8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

```
var query = {$and: [{type: 'água'}, {attack: {$lte: 50}}]}
db.pokemons.find(query)
{ "_id" : ObjectId("56afa68e198cc7e091288cf4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }

db.pokemons.remove(query)
WriteResult({ "nRemoved" : 1 })
```

<br/>
##9. Demonstre qual a diferença entre os operadores $ne e $not.

**$ne** Testa diretamente o conteúdo dos campos.
O exemplo abaixo retorna todos os objetos da coleção `pokemons` que não possuem o campo `type = fogo`:
```
var query = { type: {$ne: "fogo"}}
db.pokemons.find(query)
{ "_id" : ObjectId("56b0dbb8d50150923e9d15af"), "name" : "Mew", "description" : "Gatinho mais fofinho que já vi!", "type" : "psíquico", "attack" : 100, "height" : 0.41, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b0"), "name" : "Raikou", "description" : "A fera lendária do raio", "type" : "elétrico", "attack" : 85, "height" : 1.91, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56b0dbb8d50150923e9d15b2"), "name" : "Suicine", "description" : "Cão lendário que controla as águas", "type" : "água", "attack" : 75, "height" : 2.01, "moves" : [ "Desvio" ] }
{ "_id" : ObjectId("56afa23a198cc7e091288cf1"), "name" : "Pikachu", "description" : "Rato elétrico bem fofinho", "type" : "elétrico", "attack" : 55, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa4cf198cc7e091288cf2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa68e198cc7e091288cf4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afb07f198cc7e091288cf5"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56b2434467f4037b35688b9c"), "active" : true, "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "moves" : [ null ] }
```

**$not** Testa uma expressão lógica.
O exemplo abaixo retorna todos os objetos da coleção `pokemons` que não possuem o campo `attak >= 50` :
```
var query = { attack: {$not: {$gte: 50}}}
db.pokemons.find(query)
{ "_id" : ObjectId("56afa4cf198cc7e091288cf2"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afa68e198cc7e091288cf4"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5, "moves" : [ "Surf", "Raio Solar", "Desvio" ] }
{ "_id" : ObjectId("56afb07f198cc7e091288cf5"), "name" : "Caterpie", "description" : "Larva lutadora", "type" : "inseto", "attack" : 30, "height" : 0.3, "defense" : 35, "moves" : [ "Desvio", "Investida" ] }
{ "_id" : ObjectId("56b2434467f4037b35688b9c"), "active" : true, "name" : "AindaNaoExisteMon", "description" : "Sem maiores informações", "type" : null, "attack" : null, "height" : null, "moves" : [ null ] }
```