# MongoDB - Aula 02 - Exercício
Autor: Paulo Henrique Reis

##Criando uma database chamada be-mean-pokemons

```
use be-mean-pokemons
switched to db be-mean-pokemons
```

##Listando todas databases

```
show dbs
be-mean             → 0.078GB
be-mean-instagram() → 0.078GB
local               → 0.078GB
pokemon             → 0.078GB
test                → 0.078GB
teste               → 0.078GB

```

##Listando coleções existentes em be-mean-pokemons

```
show collections

```


##Inserindo 5 pokemons

```
db.pokemons.insert({name:"Bulbasaur", description: "Bulbasaur pode ser visto cochilando sob luz solar intensa. H uma semente em suas costas. Ao absorver os raios do sol, a semente cresce progressivamente maior", attack: 3,defense: 2, height: 0.7})

Inserted 1 record(s) in 4ms
WriteResult({
  "nInserted": 1
})

db.pokemons.insert({name:"Charmander", description: "A chama que queima na ponta de sua cauda  uma indicaço de suas emoçes. A chama oscila quando Charmander est se divertindo. Se o Pokmon ficar enfurecido, a chama arde ferozmente", attack: 3,defense: 2, height: 0.7})

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})


db.pokemons.insert({name:"Squirtle", description: "O escudo de Squirtle no  apenas usado para proteço. A forma arredondada da casca e as ranhuras na sua superfcie ajudam a minimizar a resistncia na gua, permitindo a este Pokmon nadar a altas velocidades", attack: 3,defense: 3, height: 0.5})

Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})


db.pokemons.insert({name:"Pidgey", description: "Pidgey tem um sentido extremamente afiado de direço.  capaz de retornar infalivelmente para casa a seu ninho, porm distante pode ser removido de seus arredors familiares", attack: 2,defense: 2, height: 0.3})

Inserted 1 record(s) in 26ms
WriteResult({
  "nInserted": 1
})

db.pokemons.insert({name:"Nidoran", description: "Nidoran (macho) tem farpas que secretam um poderoso veneno. Eles foram desenvolvidos como proteço para este Pokmon de corpo pequeno. Quando enfurecido, libera uma toxina horrvel de seu chifre", attack: 3,defense: 3, height: 0.4})

Inserted 1 record(s) in 1ms
WriteResult({
  "nInserted": 1
})

```


##Listar pokemons existentes

```
be-mean-pokemons> db.pokemons.find({})
{
  "_id": ObjectId("5946bead80961ceae52ee0c5"),
  "name": "Bulbasaur",
  "description": "Bulbasaur pode ser visto cochilando sob luz solar intensa. H uma semente em suas costas. Ao absorver os raios do sol, a semente cresce progressivamente maior",
  "attack": 3,
  "defense": 2,
  "height": 0.7
}
{
  "_id": ObjectId("5946bedb80961ceae52ee0c6"),
  "name": "Charmander",
  "description": "A chama que queima na ponta de sua cauda  uma indicaço de suas emoçes. A chama oscila quando Charmander est se divertindo. Se o Pokmon ficar enfurecido, a chama arde ferozmente",
  "attack": 3,
  "defense": 2,
  "height": 0.7
}
{
  "_id": ObjectId("5946bf0e80961ceae52ee0c7"),
  "name": "Squirtle",
  "description": "O escudo de Squirtle no  apenas usado para proteço. A forma arredondada da casca e as ranhuras na sua superfcie ajudam a minimizar a resistncia na gua, permitindo a este Pokmon nadar a altas velocidades",
  "attack": 3,
  "defense": 3,
  "height": 0.5
}
{
  "_id": ObjectId("5946bf3b80961ceae52ee0c8"),
  "name": "Pidgey",
  "description": "Pidgey tem um sentido extremamente afiado de direço.  capaz de retornar infalivelmente para casa a seu ninho, porm distante pode ser removido de seus arredors familiares",
  "attack": 2,
  "defense": 2,
  "height": 0.3
}
{
  "_id": ObjectId("5946bf6680961ceae52ee0c9"),
  "name": "Nidoran",
  "description": "Nidoran (macho) tem farpas que secretam um poderoso veneno. Eles foram desenvolvidos como proteço para este Pokmon de corpo pequeno. Quando enfurecido, libera uma toxina horrvel de seu chifre",
  "attack": 3,
  "defense": 3,
  "height": 0.4
}

```

##Buscando Pikachu

```
var poke = {name: 'Pikachu'}

db.pokemons.find(poke)

{
  "_id": ObjectId("5928d5124130db184bba0a73"),
  "name": "Pikachu",
  "description": "Rato eletrico bem fofinho",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}

```
## Modificando a description e salvando 

```
var query = {name: "Pikachu"}

var poke = db.pokemons.findOne(query)
poke.description = "Modificando descrição"
Modificando descrição

db.pokemons.save(poke)

Updated 1 existing record(s) in 122ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

db.pokemons.find(query)
{
  "_id": ObjectId("5928d5124130db184bba0a73"),
  "name": "Pikachu",
  "description": "Modificando descrição",
  "type": "eletric",
  "attack": 55,
  "height": 0.4
}


```