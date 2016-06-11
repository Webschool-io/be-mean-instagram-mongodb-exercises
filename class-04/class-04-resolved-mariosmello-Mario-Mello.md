# MongoDB - Aula 04 - Exercício
autor: Mário Mello


#1. Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
## No meu caso, Fischer Morse, Marilyn Aguirre, Donovan Hicks, Wiley Marquez
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = { $or: [ {name: /Fischer Morse/i}, {name: /Marilyn Aguirre/i}, {name: /Donovan Hicks/i}, {name: /Wiley Marquez/i} ]}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var mod = {$pushAll:{moves:['Choro', 'Desmaiada']}}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var options = {multi:true}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 4 existing record(s) in 13ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("574a395efcca4f82dc2c87bc"),
  "name": "Fischer Morse",
  "description": "Ex officia quis duis minim amet id esse. Tempor nisi Lorem laboris cillum qui labore minim eiusmod veniam aliqua ipsum. Velit nostrud sunt ut occaecat ullamco est deserunt labore consectetur.\r\n",
  "type": "Fogo",
  "attack": 730,
  "defense": 111,
  "height": 2.0518,
  "active": false,
  "moves": [
    "Chute",
    "Tiro",
    "Chute",
    "Choro",
    "Desmaiada"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87bd"),
  "name": "Marilyn Aguirre",
  "description": "Mollit nisi tempor aliqua duis aliquip quis id exercitation do laboris culpa. Veniam velit fugiat consectetur laboris. Reprehenderit adipisicing ex incididunt ipsum ullamco cillum culpa deserunt nostrud adipisicing culpa nostrud magna. Irure consequat irure aute non velit laborum officia reprehenderit nostrud veniam. Voluptate dolore occaecat nulla mollit eiusmod nulla excepteur cupidatat non labore. Elit ullamco eiusmod nostrud amet incididunt voluptate mollit. Reprehenderit Lorem labore do ullamco enim nulla reprehenderit deserunt labore elit ullamco fugiat.\r\n",
  "type": "Grama",
  "attack": 910,
  "defense": 449,
  "height": 4.0785,
  "active": false,
  "moves": [
    "Investida",
    "Grito",
    "Chute",
    "Choro",
    "Desmaiada"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87be"),
  "name": "Donovan Hicks",
  "description": "Incididunt laboris eiusmod veniam nisi. Deserunt ipsum occaecat et anim enim cillum nulla fugiat fugiat est ut et. Proident nulla do est incididunt aliquip. Ipsum consectetur ullamco laborum elit duis ut est labore tempor qui est voluptate sint magna. Labore esse voluptate enim occaecat magna id dolor sint. Fugiat laborum voluptate est sint quis est cillum anim id enim. Ullamco enim veniam incididunt magna proident consectetur eu exercitation qui ex.\r\n",
  "type": "Água",
  "attack": 439,
  "defense": 924,
  "height": 2.571,
  "active": true,
  "moves": [
    "Tiro",
    "Investida",
    "Grito",
    "Grito",
    "Choro",
    "Desmaiada"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87bf"),
  "name": "Wiley Marquez",
  "description": "Mollit nulla minim velit irure. Qui eiusmod laborum ut duis pariatur exercitation nostrud amet fugiat in ipsum velit dolor cupidatat. Officia consectetur aliqua ipsum dolore duis laborum.\r\n",
  "type": "Fogo",
  "attack": 854,
  "defense": 829,
  "height": 0.1019,
  "active": true,
  "moves": [
    "Chute",
    "Investida",
    "Investida",
    "Choro",
    "Desmaiada"
  ]
}
Fetched 4 record(s) in 4ms
```

#2. Adicionar 1 movimento em todos os pokemons: desvio.

```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var mod = {$push:{moves:'desvio'}}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var options = {multi:true}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 20 existing record(s) in 1ms
WriteResult({
  "nMatched": 20,
  "nUpserted": 0,
  "nModified": 20
})
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("574a395efcca4f82dc2c87bc"),
  "name": "Fischer Morse",
  "description": "Ex officia quis duis minim amet id esse. Tempor nisi Lorem laboris cillum qui labore minim eiusmod veniam aliqua ipsum. Velit nostrud sunt ut occaecat ullamco est deserunt labore consectetur.\r\n",
  "type": "Fogo",
  "attack": 730,
  "defense": 111,
  "height": 2.0518,
  "active": false,
  "moves": [
    "Chute",
    "Tiro",
    "Chute",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
```
OBS: Ocultei o resto do resultado para não ficar muito grande :P

#3. Adicionar o pokemon AindaNaoExisteMon caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {name:/AindaNaoExisteMon/i}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var options = {upsert:true}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var mod = {$set:{active:true}, $setOnInsert:{name : 'AindaNaoExisteMon', attack: null, defense: null, height: null, description: 'Sem maiores informações'}}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.update(query,mod,options)
Updated 1 new record(s) in 1ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("574a3b3afcca4f82dc2c87d1")
})
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {_id: ObjectId("574a3b3afcca4f82dc2c87d1")}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("574a3b3afcca4f82dc2c87d1"),
  "active": true,
  "name": "AindaNaoExisteMon",
  "attack": null,
  "defense": null,
  "height": null,
  "description": "Sem maiores informações"
}
Fetched 1 record(s) in 1ms
```

#4. Pesquisar todos o pokemons que possuam o ataque investida e mais um que você adicionou, escolha seu pokemon favorito.
## No meu caso usei Ivestida e Tiro
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {moves: {$in: ['Investida', 'Tiro']}}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("574a395efcca4f82dc2c87bc"),
  "name": "Fischer Morse",
  "description": "Ex officia quis duis minim amet id esse. Tempor nisi Lorem laboris cillum qui labore minim eiusmod veniam aliqua ipsum. Velit nostrud sunt ut occaecat ullamco est deserunt labore consectetur.\r\n",
  "type": "Fogo",
  "attack": 730,
  "defense": 111,
  "height": 2.0518,
  "active": false,
  "moves": [
    "Chute",
    "Tiro",
    "Chute",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87bd"),
  "name": "Marilyn Aguirre",
  "description": "Mollit nisi tempor aliqua duis aliquip quis id exercitation do laboris culpa. Veniam velit fugiat consectetur laboris. Reprehenderit adipisicing ex incididunt ipsum ullamco cillum culpa deserunt nostrud adipisicing culpa nostrud magna. Irure consequat irure aute non velit laborum officia reprehenderit nostrud veniam. Voluptate dolore occaecat nulla mollit eiusmod nulla excepteur cupidatat non labore. Elit ullamco eiusmod nostrud amet incididunt voluptate mollit. Reprehenderit Lorem labore do ullamco enim nulla reprehenderit deserunt labore elit ullamco fugiat.\r\n",
  "type": "Grama",
  "attack": 910,
  "defense": 449,
  "height": 4.0785,
  "active": false,
  "moves": [
    "Investida",
    "Grito",
    "Chute",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87be"),
  "name": "Donovan Hicks",
  "description": "Incididunt laboris eiusmod veniam nisi. Deserunt ipsum occaecat et anim enim cillum nulla fugiat fugiat est ut et. Proident nulla do est incididunt aliquip. Ipsum consectetur ullamco laborum elit duis ut est labore tempor qui est voluptate sint magna. Labore esse voluptate enim occaecat magna id dolor sint. Fugiat laborum voluptate est sint quis est cillum anim id enim. Ullamco enim veniam incididunt magna proident consectetur eu exercitation qui ex.\r\n",
  "type": "Água",
  "attack": 439,
  "defense": 924,
  "height": 2.571,
  "active": true,
  "moves": [
    "Tiro",
    "Investida",
    "Grito",
    "Grito",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87bf"),
  "name": "Wiley Marquez",
  "description": "Mollit nulla minim velit irure. Qui eiusmod laborum ut duis pariatur exercitation nostrud amet fugiat in ipsum velit dolor cupidatat. Officia consectetur aliqua ipsum dolore duis laborum.\r\n",
  "type": "Fogo",
  "attack": 854,
  "defense": 829,
  "height": 0.1019,
  "active": true,
  "moves": [
    "Chute",
    "Investida",
    "Investida",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
Fetched 14 record(s) in 11ms
```
OBS: Ocultei o resto do resultado para não ficar muito grande :P

#5. Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {moves:{$in: ["Desmaiada", "Choro"]}}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("574a395efcca4f82dc2c87bc"),
  "name": "Fischer Morse",
  "description": "Ex officia quis duis minim amet id esse. Tempor nisi Lorem laboris cillum qui labore minim eiusmod veniam aliqua ipsum. Velit nostrud sunt ut occaecat ullamco est deserunt labore consectetur.\r\n",
  "type": "Fogo",
  "attack": 730,
  "defense": 111,
  "height": 2.0518,
  "active": false,
  "moves": [
    "Chute",
    "Tiro",
    "Chute",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87bd"),
  "name": "Marilyn Aguirre",
  "description": "Mollit nisi tempor aliqua duis aliquip quis id exercitation do laboris culpa. Veniam velit fugiat consectetur laboris. Reprehenderit adipisicing ex incididunt ipsum ullamco cillum culpa deserunt nostrud adipisicing culpa nostrud magna. Irure consequat irure aute non velit laborum officia reprehenderit nostrud veniam. Voluptate dolore occaecat nulla mollit eiusmod nulla excepteur cupidatat non labore. Elit ullamco eiusmod nostrud amet incididunt voluptate mollit. Reprehenderit Lorem labore do ullamco enim nulla reprehenderit deserunt labore elit ullamco fugiat.\r\n",
  "type": "Grama",
  "attack": 910,
  "defense": 449,
  "height": 4.0785,
  "active": false,
  "moves": [
    "Investida",
    "Grito",
    "Chute",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87be"),
  "name": "Donovan Hicks",
  "description": "Incididunt laboris eiusmod veniam nisi. Deserunt ipsum occaecat et anim enim cillum nulla fugiat fugiat est ut et. Proident nulla do est incididunt aliquip. Ipsum consectetur ullamco laborum elit duis ut est labore tempor qui est voluptate sint magna. Labore esse voluptate enim occaecat magna id dolor sint. Fugiat laborum voluptate est sint quis est cillum anim id enim. Ullamco enim veniam incididunt magna proident consectetur eu exercitation qui ex.\r\n",
  "type": "Água",
  "attack": 439,
  "defense": 924,
  "height": 2.571,
  "active": true,
  "moves": [
    "Tiro",
    "Investida",
    "Grito",
    "Grito",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87bf"),
  "name": "Wiley Marquez",
  "description": "Mollit nulla minim velit irure. Qui eiusmod laborum ut duis pariatur exercitation nostrud amet fugiat in ipsum velit dolor cupidatat. Officia consectetur aliqua ipsum dolore duis laborum.\r\n",
  "type": "Fogo",
  "attack": 854,
  "defense": 829,
  "height": 0.1019,
  "active": true,
  "moves": [
    "Chute",
    "Investida",
    "Investida",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
Fetched 4 record(s) in 5ms
```

#6. Pesquisar todos os pokemons que não são do tipo elétrico.
## No meu caso Fogo
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {type:{$ne: "Fogo"}}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("574a395efcca4f82dc2c87bd"),
  "name": "Marilyn Aguirre",
  "description": "Mollit nisi tempor aliqua duis aliquip quis id exercitation do laboris culpa. Veniam velit fugiat consectetur laboris. Reprehenderit adipisicing ex incididunt ipsum ullamco cillum culpa deserunt nostrud adipisicing culpa nostrud magna. Irure consequat irure aute non velit laborum officia reprehenderit nostrud veniam. Voluptate dolore occaecat nulla mollit eiusmod nulla excepteur cupidatat non labore. Elit ullamco eiusmod nostrud amet incididunt voluptate mollit. Reprehenderit Lorem labore do ullamco enim nulla reprehenderit deserunt labore elit ullamco fugiat.\r\n",
  "type": "Grama",
  "attack": 910,
  "defense": 449,
  "height": 4.0785,
  "active": false,
  "moves": [
    "Investida",
    "Grito",
    "Chute",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87be"),
  "name": "Donovan Hicks",
  "description": "Incididunt laboris eiusmod veniam nisi. Deserunt ipsum occaecat et anim enim cillum nulla fugiat fugiat est ut et. Proident nulla do est incididunt aliquip. Ipsum consectetur ullamco laborum elit duis ut est labore tempor qui est voluptate sint magna. Labore esse voluptate enim occaecat magna id dolor sint. Fugiat laborum voluptate est sint quis est cillum anim id enim. Ullamco enim veniam incididunt magna proident consectetur eu exercitation qui ex.\r\n",
  "type": "Água",
  "attack": 439,
  "defense": 924,
  "height": 2.571,
  "active": true,
  "moves": [
    "Tiro",
    "Investida",
    "Grito",
    "Grito",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
Fetched 14 record(s) in 13ms
```
OBS: Ocultei o resto do resultado para não ficar muito grande :P

#7. Pesquisar todos pokemons que tenham o ataque investida E tenham a defesa não menor ou igual a 49.
## No meu caso defesa não é menor ou igual a 800
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{moves:{$in:['Investida']},defense:{$not:{$lte: 800}}}]}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("574a395efcca4f82dc2c87be"),
  "name": "Donovan Hicks",
  "description": "Incididunt laboris eiusmod veniam nisi. Deserunt ipsum occaecat et anim enim cillum nulla fugiat fugiat est ut et. Proident nulla do est incididunt aliquip. Ipsum consectetur ullamco laborum elit duis ut est labore tempor qui est voluptate sint magna. Labore esse voluptate enim occaecat magna id dolor sint. Fugiat laborum voluptate est sint quis est cillum anim id enim. Ullamco enim veniam incididunt magna proident consectetur eu exercitation qui ex.\r\n",
  "type": "Água",
  "attack": 439,
  "defense": 924,
  "height": 2.571,
  "active": true,
  "moves": [
    "Tiro",
    "Investida",
    "Grito",
    "Grito",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87bf"),
  "name": "Wiley Marquez",
  "description": "Mollit nulla minim velit irure. Qui eiusmod laborum ut duis pariatur exercitation nostrud amet fugiat in ipsum velit dolor cupidatat. Officia consectetur aliqua ipsum dolore duis laborum.\r\n",
  "type": "Fogo",
  "attack": 854,
  "defense": 829,
  "height": 0.1019,
  "active": true,
  "moves": [
    "Chute",
    "Investida",
    "Investida",
    "Choro",
    "Desmaiada",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87c4"),
  "name": "Lola Lowery",
  "description": "Officia voluptate irure quis Lorem enim pariatur consectetur est duis. Velit ex proident in elit. Nisi laboris esse esse sint do veniam sunt irure cillum proident. Amet consectetur consectetur Lorem dolor irure ex proident culpa eu commodo laboris incididunt fugiat cillum.\r\n",
  "type": "Água",
  "attack": 385,
  "defense": 939,
  "height": 2.3959,
  "active": false,
  "moves": [
    "Chute",
    "Grito",
    "Investida",
    "Chute",
    "Investida",
    "desvio"
  ]
}
{
  "_id": ObjectId("574a395efcca4f82dc2c87cb"),
  "name": "Shawna Melton",
  "description": "Mollit et esse tempor ullamco ut nulla ullamco nulla velit magna ullamco exercitation. Dolor laboris eiusmod irure ipsum. Laborum do amet Lorem nisi mollit commodo enim consectetur minim Lorem dolore. Veniam ullamco excepteur non commodo ea mollit dolor magna qui ad aliquip. Nostrud officia excepteur labore nulla officia ipsum qui. Incididunt sit aute velit esse sit esse elit dolore incididunt et proident.\r\n",
  "type": "Água",
  "attack": 951,
  "defense": 902,
  "height": 0.4003,
  "active": false,
  "moves": [
    "Soco",
    "Investida",
    "Grito",
    "desvio"
  ]
}
Fetched 4 record(s) in 4ms
```

#8. Remova todos os pokemons do tipo água e com attack menor que 50.
## No meu caso ataque menor que 500
```
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> var query = {$and: [{type:{$in:['Água']},attack:{$lt: 500}}]}
macbook-mariosmello(mongod-3.2.6) be-mean-pokemons> db.pokemons.remove(query)
Removed 4 record(s) in 1ms
WriteResult({
  "nRemoved": 4
})
```