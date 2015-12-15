# MongoDB - Aula 04 - Exercício
autor: Filipe Fernandes

### 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {name: {$in: [/pikachu/i, /squirtle/i, /charmander/i, /Bulbassauro/i]}}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var attack = ['Hadouken', 'Shoryuken']
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var mod = {$pushAll:{moves:attack}}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var options = {multi : true}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.update(query, mod, options)
Updated 4 existing record(s) in 56ms
WriteResult({
	"nMatched": 4,
	"nUpserted": 0,
	"nModified": 4
})
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
{
	"_id": ObjectId("565d9ac0120d94deb1c21e07"),
	"name": "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grama",
	"attack": 49,
	"height": 0.4,
	"active": false,
	"moves": [
		"investida",
		"folha navalha",
		"Hadouken",
		"Shoryuken"
	]
}
{
	"_id": ObjectId("565d9b06120d94deb1c21e08"),
	"name": "Charmander",
	"description": "Esse é o cão chupando manga de fofinho",
	"type": "fogo",
	"attack": 52,
	"height": 0.6,
	"active": false,
	"moves": [
		"investida",
		"lança chamas",
		"Hadouken",
		"Shoryuken"
	]
}
{
	"_id": ObjectId("565d9b42120d94deb1c21e09"),
	"name": "Squirtle",
	"description": "Ejeta água que passarinho não bebe",
	"type": "água",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
		"investida",
		"hidro bomba",
		"Hadouken",
		"Shoryuken"
	]
}
{
	"_id": ObjectId("565d9a5b120d94deb1c21e06"),
	"name": "Pikachu",
	"description": "Rato elétrico bem fofinho",
	"type": "electric",
	"attack": 55,
	"height": 0.4,
	"moves": [
		"investida",
		"Choque do trovão",
		"Hadouken",
		"Shoryuken"
	],
	"active": false
}
Fetched 4 record(s) in 70ms
```

### 2. **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {}                            
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var mod = {$push: {moves: 'desvio'}}      
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var options = {multi : true}              
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.update(query, mod, options)   
Updated 6 existing record(s) in 5ms                                                              
WriteResult({                                                                                    
	"nMatched": 6,                                                                               
	"nUpserted": 0,                                                                              
	"nModified": 6                                                                               
})                                                                                               

FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
{
	"_id": ObjectId("565d9ac0120d94deb1c21e07"),
	"name": "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grama",
	"attack": 49,
	"height": 0.4,
	"active": false,
	"moves": [
		"investida",
		"folha navalha",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d015b43191174148523d6"),
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
	"_id": ObjectId("565da08b120d94deb1c21e0a"),
	"description": "Pokemon de teste",
	"name": "Testemon",
	"attack": 8001,
	"defense": 8000,
	"active": false,
	"moves": [
		"investida",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9a5b120d94deb1c21e06"),
	"name": "Pikachu",
	"description": "Rato elétrico bem fofinho",
	"type": "electric",
	"attack": 55,
	"height": 0.4,
	"moves": [
		"investida",
		"Choque do trovão",
		"Hadouken",
		"Shoryuken",
		"desvio"
	],
	"active": false
}
{
	"_id": ObjectId("565d9b06120d94deb1c21e08"),
	"name": "Charmander",
	"description": "Esse é o cão chupando manga de fofinho",
	"type": "fogo",
	"attack": 52,
	"height": 0.6,
	"active": false,
	"moves": [
		"investida",
		"lança chamas",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9b42120d94deb1c21e09"),
	"name": "Squirtle",
	"description": "Ejeta água que passarinho não bebe",
	"type": "água",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
		"investida",
		"hidro bomba",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
Fetched 6 record(s) in 52ms
```

### 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {name: /AindaNaoExisteMon/i}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var mod = { $setOnInsert: { "name": 'AindaNaoExisteMon', "description": "Sem maiores informações", "type": null, "attack": null, "height": null, "active": false, "moves": null } }
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var options = {upsert: true}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.update(query, mod, options)
Updated 1 new record(s) in 40ms
WriteResult({
	"nMatched": 0,
	"nUpserted": 1,
	"nModified": 0,
	"_id": ObjectId("565e2c0cdb767bc4a12d287f")
})

FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
{
	"_id": ObjectId("565e2c0cdb767bc4a12d287f"),
	"name": "AindaNaoExisteMon",
	"description": "Sem maiores informações",
	"type": null,
	"attack": null,
	"height": null,
	"active": false,
	"moves": null
}
Fetched 1 record(s) in 20ms
```


### 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {moves: {$in: [/investida/i, /shoryuken/i]}}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
{
	"_id": ObjectId("565d9ac0120d94deb1c21e07"),
	"name": "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grama",
	"attack": 49,
	"height": 0.4,
	"active": false,
	"moves": [
		"investida",
		"folha navalha",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d015b43191174148523d6"),
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
	"_id": ObjectId("565da08b120d94deb1c21e0a"),
	"description": "Pokemon de teste",
	"name": "Testemon",
	"attack": 8001,
	"defense": 8000,
	"active": false,
	"moves": [
		"investida",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9a5b120d94deb1c21e06"),
	"name": "Pikachu",
	"description": "Rato elétrico bem fofinho",
	"type": "electric",
	"attack": 55,
	"height": 0.4,
	"moves": [
		"investida",
		"Choque do trovão",
		"Hadouken",
		"Shoryuken",
		"desvio"
	],
	"active": false
}
{
	"_id": ObjectId("565d9b06120d94deb1c21e08"),
	"name": "Charmander",
	"description": "Esse é o cão chupando manga de fofinho",
	"type": "fogo",
	"attack": 52,
	"height": 0.6,
	"active": false,
	"moves": [
		"investida",
		"lança chamas",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9b42120d94deb1c21e09"),
	"name": "Squirtle",
	"description": "Ejeta água que passarinho não bebe",
	"type": "água",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
		"investida",
		"hidro bomba",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
Fetched 6 record(s) in 97ms
```

### 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {moves: {$all: [/Hadouken/i, /shoryuken/i]}}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
{
	"_id": ObjectId("565d9ac0120d94deb1c21e07"),
	"name": "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grama",
	"attack": 49,
	"height": 0.4,
	"active": false,
	"moves": [
		"investida",
		"folha navalha",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9a5b120d94deb1c21e06"),
	"name": "Pikachu",
	"description": "Rato elétrico bem fofinho",
	"type": "electric",
	"attack": 55,
	"height": 0.4,
	"moves": [
		"investida",
		"Choque do trovão",
		"Hadouken",
		"Shoryuken",
		"desvio"
	],
	"active": false
}
{
	"_id": ObjectId("565d9b06120d94deb1c21e08"),
	"name": "Charmander",
	"description": "Esse é o cão chupando manga de fofinho",
	"type": "fogo",
	"attack": 52,
	"height": 0.6,
	"active": false,
	"moves": [
		"investida",
		"lança chamas",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9b42120d94deb1c21e09"),
	"name": "Squirtle",
	"description": "Ejeta água que passarinho não bebe",
	"type": "água",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
		"investida",
		"hidro bomba",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
Fetched 4 record(s) in 86ms
```

### 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {type: {$ne: 'electric'}}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
{
	"_id": ObjectId("565d9ac0120d94deb1c21e07"),
	"name": "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grama",
	"attack": 49,
	"height": 0.4,
	"active": false,
	"moves": [
		"investida",
		"folha navalha",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d015b43191174148523d6"),
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
	"_id": ObjectId("565da08b120d94deb1c21e0a"),
	"description": "Pokemon de teste",
	"name": "Testemon",
	"attack": 8001,
	"defense": 8000,
	"active": false,
	"moves": [
		"investida",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9b06120d94deb1c21e08"),
	"name": "Charmander",
	"description": "Esse é o cão chupando manga de fofinho",
	"type": "fogo",
	"attack": 52,
	"height": 0.6,
	"active": false,
	"moves": [
		"investida",
		"lança chamas",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9b42120d94deb1c21e09"),
	"name": "Squirtle",
	"description": "Ejeta água que passarinho não bebe",
	"type": "água",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
		"investida",
		"hidro bomba",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565e2c0cdb767bc4a12d287f"),
	"name": "AindaNaoExisteMon",
	"description": "Sem maiores informações",
	"type": null,
	"attack": null,
	"height": null,
	"active": false,
	"moves": null
}
Fetched 6 record(s) in 72ms
```


### 7. Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = { $and: [{moves: {$in: [/investida/i]}}, {defense : {$not: {$lte: 49}}}]}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
{
	"_id": ObjectId("565d9ac0120d94deb1c21e07"),
	"name": "Bulbassauro",
	"description": "Chicote de trepadeira",
	"type": "grama",
	"attack": 49,
	"height": 0.4,
	"active": false,
	"moves": [
		"investida",
		"folha navalha",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565da08b120d94deb1c21e0a"),
	"description": "Pokemon de teste",
	"name": "Testemon",
	"attack": 8001,
	"defense": 8000,
	"active": false,
	"moves": [
		"investida",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9a5b120d94deb1c21e06"),
	"name": "Pikachu",
	"description": "Rato elétrico bem fofinho",
	"type": "electric",
	"attack": 55,
	"height": 0.4,
	"moves": [
		"investida",
		"Choque do trovão",
		"Hadouken",
		"Shoryuken",
		"desvio"
	],
	"active": false
}
{
	"_id": ObjectId("565d9b06120d94deb1c21e08"),
	"name": "Charmander",
	"description": "Esse é o cão chupando manga de fofinho",
	"type": "fogo",
	"attack": 52,
	"height": 0.6,
	"active": false,
	"moves": [
		"investida",
		"lança chamas",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
{
	"_id": ObjectId("565d9b42120d94deb1c21e09"),
	"name": "Squirtle",
	"description": "Ejeta água que passarinho não bebe",
	"type": "água",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
		"investida",
		"hidro bomba",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
Fetched 5 record(s) in 49ms
```


### 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query= { $and: [{type: /água/i}, {attack : {$lt: 50}}]}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
{
	"_id": ObjectId("565d9b42120d94deb1c21e09"),
	"name": "Squirtle",
	"description": "Ejeta água que passarinho não bebe",
	"type": "água",
	"attack": 48,
	"height": 0.5,
	"active": false,
	"moves": [
		"investida",
		"hidro bomba",
		"Hadouken",
		"Shoryuken",
		"desvio"
	]
}
Fetched 1 record(s) in 25ms

FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.remove(query)
Removed 1 record(s) in 56ms
WriteResult({
	"nRemoved": 1
})

FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query)
```
Fetched 0 record(s) in 1ms

### 9. Demonstre qual a diferença entre os operadores $ne e $not.

>Primeiro vamos listar os pokemons com attack menor que 8000.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {attack: {$lt : 8000}}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var mod = {"name": 1, "attack": 1}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query,mod)
{
"_id": ObjectId("565d9ac0120d94deb1c21e07"),
"name": "Bulbassauro",
"attack": 49
}
{
"_id": ObjectId("565d015b43191174148523d6"),
"name": "Caterpie",
"attack": 30
}
{
"_id": ObjectId("565d9a5b120d94deb1c21e06"),
"name": "Pikachu",
"attack": 55
}
{
"_id": ObjectId("565d9b06120d94deb1c21e08"),
"name": "Charmander",
"attack": 52
}
Fetched 4 record(s) in 27ms

```

>Agora utilizando o $not para negar e trazer o oposto.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {attack: { $not : {$lt : 8000}}}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query,mod)
{
    "_id": ObjectId("565da08b120d94deb1c21e0a"),
    "name": "Testemon",
    "attack": 8001
}
{
    "_id": ObjectId("565e2c0cdb767bc4a12d287f"),
    "name": "AindaNaoExisteMon",
    "attack": null
}
Fetched 2 record(s) in 5ms

```

>Se no mesmo exemplo fosse utilizado o $ne não teria um resultado satisfatório, pois ele não consegue utilizar a lógida do opedaor $lt e lista todos os pokemons que não sejam iguais a attack 8000.

```js
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> var query = {attack: { $ne : {$lt : 8000}}}
FilipeFernandes(C:\mongodb\bin\mongod.exe) test> db.pokemons.find(query,mod)
{
    "_id": ObjectId("565d9ac0120d94deb1c21e07"),
    "name": "Bulbassauro",
    "attack": 49
}
{
    "_id": ObjectId("565d015b43191174148523d6"),
    "name": "Caterpie",
    "attack": 30
}
{
    "_id": ObjectId("565da08b120d94deb1c21e0a"),
    "name": "Testemon",
    "attack": 8001
}
{
    "_id": ObjectId("565d9a5b120d94deb1c21e06"),
    "name": "Pikachu",
    "attack": 55
}
{
    "_id": ObjectId("565d9b06120d94deb1c21e08"),
    "name": "Charmander",
    "attack": 52
}
{
    "_id": ObjectId("565e2c0cdb767bc4a12d287f"),
    "name": "AindaNaoExisteMon",
    "attack": null
}
Fetched 6 record(s) in 44ms

```


### Concluindo
######O operador $not é indicado para fazer operações lógicas usando em conjuntos `$lt,$lte, $gt, $gte` e não permite a utilização do `/regex/i`

######Já o operador $ne é indica para fazer buscas em conteúdo expecifico como um certo número ou um string! Neste caso é possível utilizar '/regex/i'










