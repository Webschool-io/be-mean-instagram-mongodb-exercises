# MongoDB - Aula 04 - Exercício
autor: Bruno Motta Azevedo do Nascimento

## Lista de pokemons
```js
{
  "_id": ObjectId("5805bc1bff84434c5f720a96"),
  "name": "Charizard",
  "description": "Dragão de fogo, cabuloso, fodastico, super poderoso de todos os tempos",
  "type": "Fire",
  "attack": 100,
  "defense": 100,
  "height": 10.17,
  "moves": [
    "investida",
    "Força Sismica"
  ],
  "active": false
}
{
  "_id": ObjectId("5805bc1eff84434c5f720a97"),
  "name": "Blastoise",
  "description": "Tartaruga Gigante",
  "type": "water",
  "attack": 90,
  "defense": 90,
  "height": 9.8,
  "moves": [
    "investida",
    "Bomba d'agua"
  ],
  "active": false
}
{
  "_id": ObjectId("5805bc21ff84434c5f720a98"),
  "name": "Zapdos",
  "description": "Passaro Eletrico fodastico",
  "type": "elétrico",
  "attack": 150,
  "defense": 150,
  "height": 10,
  "moves": [
    "investida",
    "Choque do Trovão"
  ],
  "active": false
}
{
  "_id": ObjectId("5805bc24ff84434c5f720a99"),
  "name": "Articuno",
  "description": "Passaro de Gelo",
  "type": "ice",
  "attack": 150,
  "defense": 100,
  "height": 11,
  "moves": [
    "investida",
    "Raio de gelo"
  ],
  "active": false
}
{
  "_id": ObjectId("5805bc27ff84434c5f720a9a"),
  "name": "Moltres",
  "description": "Passaro de Fogo",
  "type": "fire",
  "attack": 100,
  "defense": 150,
  "height": 13.08,
  "moves": [
    "investida",
    "Chama do vulcão"
  ],
  "active": false
}
{
  "_id": ObjectId("5808319dd08108f8b654b549"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": 200,
  "defense": 250,
  "description": "Pokemon de teste...",
  "moves": [
    "investida",
    "Inexistência"
  ]
}
{
  "_id": ObjectId("5852fc32dce593b3bfc2ada0"),
  "active": false,
  "name": "Pikachu",
  "type": "elétrico",
  "height": 4,
  "attack": 50,
  "defense": 20,
  "description": "Pika Pika!",
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5852fc82dce593b3bfc2ada1"),
  "active": false,
  "name": "Squirtle",
  "type": "Aquatico",
  "height": 5,
  "attack": 40,
  "defense": 40,
  "description": "Pika Pika!",
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5852fcb3dce593b3bfc2ada2"),
  "active": false,
  "name": "Bulbassauro",
  "type": "Grama",
  "height": 3,
  "attack": 20,
  "defense": 50,
  "description": "rato verde",
  "moves": [
    "investida",
    "Raio Solar"
  ]
}
{
  "_id": ObjectId("5852fcf1dce593b3bfc2ada3"),
  "active": false,
  "name": "Charmander",
  "type": "Fogo",
  "height": 3,
  "attack": 60,
  "defense": 10,
  "description": "Filhote do supremo dragão de fogo que não é do tipo dragão",
  "moves": [
    "investida"
  ]
}
```



## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
```js
query = {name:{$in:[/Pikachu/i, /Squirtle/i,/Bulbassauro/i,/Charmander/i]}};  
db.pokemons.find(query);  
{
  "_id": ObjectId("5852fc32dce593b3bfc2ada0"),
  "active": false,
  "name": "Pikachu",
  "type": "elétrico",
  "height": 4,
  "attack": 50,
  "defense": 20,
  "description": "Pika Pika!",
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5852fc82dce593b3bfc2ada1"),
  "active": false,
  "name": "Squirtle",
  "type": "Aquatico",
  "height": 5,
  "attack": 40,
  "defense": 40,
  "description": "Pika Pika!",
  "moves": [
    "investida"
  ]
}
{
  "_id": ObjectId("5852fcb3dce593b3bfc2ada2"),
  "active": false,
  "name": "Bulbassauro",
  "type": "Grama",
  "height": 3,
  "attack": 20,
  "defense": 50,
  "description": "rato verde",
  "moves": [
    "investida",
    "Raio Solar"
  ]
}
{
  "_id": ObjectId("5852fcf1dce593b3bfc2ada3"),
  "active": false,
  "name": "Charmander",
  "type": "Fogo",
  "height": 3,
  "attack": 60,
  "defense": 10,
  "description": "Filhote do supremo dragão de fogo que não é do tipo dragão",
  "moves": [
    "investida"
  ]
}  
mod = {$pushAll:{moves:["esquiva","Arranhar"]}}  
db.pokemons.update(query,mod,{multi:true});
Updated 4 existing record(s) in 2ms
WriteResult({
  "nMatched": 4,
  "nUpserted": 0,
  "nModified": 4
})

db.pokemons.find(query);  
{
  "_id": ObjectId("5852fc32dce593b3bfc2ada0"),
  "active": false,
  "name": "Pikachu",
  "type": "elétrico",
  "height": 4,
  "attack": 50,
  "defense": 20,
  "description": "Pika Pika!",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar"
  ]
}
{
  "_id": ObjectId("5852fc82dce593b3bfc2ada1"),
  "active": false,
  "name": "Squirtle",
  "type": "Aquatico",
  "height": 5,
  "attack": 40,
  "defense": 40,
  "description": "Pika Pika!",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar"
  ]
}
{
  "_id": ObjectId("5852fcb3dce593b3bfc2ada2"),
  "active": false,
  "name": "Bulbassauro",
  "type": "Grama",
  "height": 3,
  "attack": 20,
  "defense": 50,
  "description": "rato verde",
  "moves": [
    "investida",
    "Raio Solar",
    "esquiva",
    "Arranhar"
  ]
}
{
  "_id": ObjectId("5852fcf1dce593b3bfc2ada3"),
  "active": false,
  "name": "Charmander",
  "type": "Fogo",
  "height": 3,
  "attack": 60,
  "defense": 10,
  "description": "Filhote do supremo dragão de fogo que não é do tipo dragão",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar"
  ]
}
Fetched 4 record(s) in 3ms

```

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.

```js
mod = {$push:{moves:'desvio'}}
b.pokemons.update({},mod,{multi:true});
Updated 10 existing record(s) in 1ms
WriteResult({
  "nMatched": 10,
  "nUpserted": 0,
  "nModified": 10
})

```

## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".

```js
query = {name:/AindaNaoExisteMon/i};
mod = {
	$setOnInsert:{
	  "active": false,
	  "name": "AindaNaoExisteMon",
	  "type": null,
	  "height": null,
	  "attack": null,
	  "defense": null,
	  "description": "Sem maiores informações",
	  "moves": [  ]
	}
}
  
db.pokemons.update(query,mod,{upsert:true});
Updated 1 new record(s) in 2ms
WriteResult({
  "nMatched": 0,
  "nUpserted": 1,
  "nModified": 0,
  "_id": ObjectId("58530023a47a5c5364b71502")
})
```

## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
ataques = [/investida/i,/força/i];
db.pokemons.find({moves:{$all:ataques}});
{
  "_id": ObjectId("5805bc1bff84434c5f720a96"),
  "name": "Charizard",
  "description": "Dragão de fogo, cabuloso, fodastico, super poderoso de todos os tempos",
  "type": "Fire",
  "attack": 100,
  "defense": 100,
  "height": 10.17,
  "moves": [
    "investida",
    "Força Sismica",
    "desvio"
  ],
  "active": false
}
Fetched 1 record(s) in 2ms

```

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
ataques = [/arranhar/i,/raio/i,/chama/i];
db.pokemons.find({moves:{$in:ataques}});
{
  "_id": ObjectId("5805bc24ff84434c5f720a99"),
  "name": "Articuno",
  "description": "Passaro de Gelo",
  "type": "ice",
  "attack": 150,
  "defense": 100,
  "height": 11,
  "moves": [
    "investida",
    "Raio de gelo",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5805bc27ff84434c5f720a9a"),
  "name": "Moltres",
  "description": "Passaro de Fogo",
  "type": "fire",
  "attack": 100,
  "defense": 150,
  "height": 13.08,
  "moves": [
    "investida",
    "Chama do vulcão",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5852fc32dce593b3bfc2ada0"),
  "active": false,
  "name": "Pikachu",
  "type": "elétrico",
  "height": 4,
  "attack": 50,
  "defense": 20,
  "description": "Pika Pika!",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5852fc82dce593b3bfc2ada1"),
  "active": false,
  "name": "Squirtle",
  "type": "Aquatico",
  "height": 5,
  "attack": 40,
  "defense": 40,
  "description": "Pika Pika!",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5852fcb3dce593b3bfc2ada2"),
  "active": false,
  "name": "Bulbassauro",
  "type": "Grama",
  "height": 3,
  "attack": 20,
  "defense": 50,
  "description": "rato verde",
  "moves": [
    "investida",
    "Raio Solar",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5852fcf1dce593b3bfc2ada3"),
  "active": false,
  "name": "Charmander",
  "type": "Fogo",
  "height": 3,
  "attack": 60,
  "defense": 10,
  "description": "Filhote do supremo dragão de fogo que não é do tipo dragão",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
Fetched 6 record(s) in 4ms
```

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js
db.pokemons.find({type:/elétrico/i});db.pokemons.find({type:{$not:/elétrico/i}});
{
  "_id": ObjectId("5805bc1bff84434c5f720a96"),
  "name": "Charizard",
  "description": "Dragão de fogo, cabuloso, fodastico, super poderoso de todos os tempos",
  "type": "Fire",
  "attack": 100,
  "defense": 100,
  "height": 10.17,
  "moves": [
    "investida",
    "Força Sismica",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5805bc1eff84434c5f720a97"),
  "name": "Blastoise",
  "description": "Tartaruga Gigante",
  "type": "water",
  "attack": 90,
  "defense": 90,
  "height": 9.8,
  "moves": [
    "investida",
    "Bomba d'agua",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5805bc24ff84434c5f720a99"),
  "name": "Articuno",
  "description": "Passaro de Gelo",
  "type": "ice",
  "attack": 150,
  "defense": 100,
  "height": 11,
  "moves": [
    "investida",
    "Raio de gelo",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5805bc27ff84434c5f720a9a"),
  "name": "Moltres",
  "description": "Passaro de Fogo",
  "type": "fire",
  "attack": 100,
  "defense": 150,
  "height": 13.08,
  "moves": [
    "investida",
    "Chama do vulcão",
    "desvio"
  ],
  "active": false
}
{
  "_id": ObjectId("5808319dd08108f8b654b549"),
  "active": false,
  "name": "NaoExisteMon",
  "attack": 200,
  "defense": 250,
  "description": "Pokemon de teste...",
  "moves": [
    "investida",
    "Inexistência",
    "desvio"
  ]
}
{
  "_id": ObjectId("5852fc82dce593b3bfc2ada1"),
  "active": false,
  "name": "Squirtle",
  "type": "Aquatico",
  "height": 5,
  "attack": 40,
  "defense": 40,
  "description": "Pika Pika!",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5852fcb3dce593b3bfc2ada2"),
  "active": false,
  "name": "Bulbassauro",
  "type": "Grama",
  "height": 3,
  "attack": 20,
  "defense": 50,
  "description": "rato verde",
  "moves": [
    "investida",
    "Raio Solar",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5852fcf1dce593b3bfc2ada3"),
  "active": false,
  "name": "Charmander",
  "type": "Fogo",
  "height": 3,
  "attack": 60,
  "defense": 10,
  "description": "Filhote do supremo dragão de fogo que não é do tipo dragão",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
{
  "_id": ObjectId("58530023a47a5c5364b71502"),
  "active": false,
  "name": "AindaNaoExisteMon",
  "type": null,
  "height": null,
  "attack": null,
  "defense": null,
  "description": "Sem maiores informações",
  "moves": [ ]
}
Fetched 9 record(s) in 5ms
```

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.
```js
db.pokemons.find({moves:{$in:[/investida/i]},defense:{$gt:49}});
{
  "_id": ObjectId("5852fc32dce593b3bfc2ada0"),
  "active": false,
  "name": "Pikachu",
  "type": "elétrico",
  "height": 4,
  "attack": 50,
  "defense": 20,
  "description": "Pika Pika!",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5852fc82dce593b3bfc2ada1"),
  "active": false,
  "name": "Squirtle",
  "type": "Aquatico",
  "height": 5,
  "attack": 40,
  "defense": 40,
  "description": "Pika Pika!",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
{
  "_id": ObjectId("5852fcf1dce593b3bfc2ada3"),
  "active": false,
  "name": "Charmander",
  "type": "Fogo",
  "height": 3,
  "attack": 60,
  "defense": 10,
  "description": "Filhote do supremo dragão de fogo que não é do tipo dragão",
  "moves": [
    "investida",
    "esquiva",
    "Arranhar",
    "desvio"
  ]
}
Fetched 3 record(s) in 3ms

```

## Remova **todos** os pokemons do tipo água E com attack menor que 50.

```js
db.pokemons.remove({type:/Aquatico/i,defense:{$lt:50}});
Removed 1 record(s) in 1ms
WriteResult({
  "nRemoved": 1
})

```

