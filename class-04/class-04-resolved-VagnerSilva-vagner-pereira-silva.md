# MongoDB - Aula 04 - Exercício
autor: Vagner Pereira Silva

## 1. **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.

```js

var q  = {name:/pikachu/i};
	var mod  = {$pushAll:{moves:['Descarga','Levitação Magnética']}}

	> db.pokemons.update(q,mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> db.pokemons.find(q).pretty()
{
        "_id" : ObjectId("567b8a2119e6c47b0b11c1ac"),
        "name" : "Pikachu",
        "description" : "Pika-Pika",
        "type" : "Electric",
        "attack" : 55,
        "height" : 4,
        "active" : false,
        "moves" : [
                "Choque do trovão",
                "Investida",
                "Descarga",
                "Levitação Magnética"
        ]
}


var q  = {name:/squirtle/i};
	var mod  = {$pushAll:{moves:['Ataque de bolhas','Jato de água']}}
	
	> db.pokemons.update(q,mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

db.pokemons.find(q).pretty()

      "_id" : ObjectId("567b8a4e19e6c47b0b11c1af"),
      "name" : "Squirtle",
      "description" : "Tartaruga",
      "type" : "Water",
      "attack" : 48,
      "height" : 5,
      "active" : false,
      "moves" : [
              "Hidro bomba",
              "Investida",
              "Ataque de bolhas",
              "Jato de água"
      ]


var q  = {name:/bulbassauro/i};
	var mod  = {$pushAll:{moves:['Lamina de folha','Chicote de cipó']}}
	
	> db.pokemons.update(q,mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

	db.pokemons.find(q).pretty()

      "_id" : ObjectId("5686ee656aa2c7623f0a551d"),
      "name" : "Bulbassauro",
      "description" : "Bulbassauro",
      "attack" : 49,
      "height" : 0.7,
      "active" : false,
      "moves" : [
              "Investida",
              "Lamina de folha",
              "Chicote de cipó"
      ],
      "type" : "Seed"


var q  = {name:/charmander/i};
	var mod  = {$pushAll:{moves:['Chute flamejante','Lança chamas']}}
	
	> db.pokemons.update(q,mod)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

db.pokemons.find(q).pretty()

      "_id" : ObjectId("5686eece6aa2c7623f0a551e"),
      "name" : "Charmander",
      "description" : "Chaaaar",
      "attack" : 52,
      "height" : 0.7,
      "active" : false,
      "moves" : [
              "Investida",
              "Chute flamejante",
              "Lança chamas"
      ],
      "type" : "Fire"

```

## 2. **Adicionar** 1 movimento em todos os pokemons: desvio.

```js

 var q = {}
      		var mod = {$push:{moves:'desvio'}}
      			var op  = {multi:true}

      			> db.pokemons.update(q,mod,op)
WriteResult({ "nMatched" : 8, "nUpserted" : 0, "nModified" : 8 })

```

## 3. **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor null e a descrição: "Sem maiores informações".

```js


var q = {name:'AindaNaoExisteMon'}
	var mod = {$setOnInsert:{

		name: 'AindaNaoExisteMon',
		description:'Sem maiores informações',
		attack:null,
		active:false,
		type:null,
		moves:[]

	}}

	var op = {upsert:true}

	db.pokemons.update(q,mod,op)
iteResult({
      "nMatched" : 0,
      "nUpserted" : 1,
      "nModified" : 0,
      "_id" : ObjectId("568718a3481d8afee55eaeab")


      var q  = { "_id" : ObjectId("568718a3481d8afee55eaeab")}

      > db.pokemons.find(q).pretty()
{
        "_id" : ObjectId("568718a3481d8afee55eaeab"),
        "name" : "AindaNaoExisteMon",
        "description" : "Sem maiores informações",
        "attack" : null,
        "active" : false,
        "type" : null,
        "moves" : [ ]
}


```

## 4. Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.

```js
var q  = {
	moves:{
		$in:[
			/investida/i,
			/choque do trovão/i
		]
	}
}


> db.pokemons.find(q).pretty()
{
        "_id" : ObjectId("567b8a3a19e6c47b0b11c1ae"),
        "name" : "Charizard",
        "description" : "Dragao",
        "type" : "Fire",
        "attack" : 84,
        "height" : 17,
        "active" : false,
        "moves" : [
                "Investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("567b8a4e19e6c47b0b11c1af"),
        "name" : "Squirtle",
        "description" : "Tartaruga",
        "type" : "Water",
        "attack" : 48,
        "height" : 5,
        "active" : false,
        "moves" : [
                "Investida",
                "Ataque de bolhas",
                "Jato de água",
                "desvio"
        ]
}
{
        "_id" : ObjectId("5685cd5fb84942ffd48e96f1"),
        "name" : "Testemon",
        "description" : "pokemon teste",
        "type" : "teste",
        "attack" : 1000,
        "height" : 2.1,
        "active" : false,
        "moves" : [
                "Investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("567b8a2f19e6c47b0b11c1ad"),
        "name" : "Psyduck",
        "description" : "Pato",
        "type" : "Water",
        "attack" : 52,
        "height" : 8,
        "active" : false,
        "moves" : [
                "Investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("567b8a5f19e6c47b0b11c1b0"),
        "name" : "Meowth",
        "description" : "Gato",
        "type" : "Normal",
        "attack" : 45,
        "height" : 4,
        "active" : false,
        "moves" : [
                "Investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("5686ee656aa2c7623f0a551d"),
        "name" : "Bulbassauro",
        "description" : "Bulbassauro",
        "attack" : 49,
        "height" : 0.7,
        "active" : false,
        "type" : "Seed",
        "moves" : [
                "Investida",
                "Lamina de folha",
                "Chicote de cipó",
                "desvio"
        ]
}
{
        "_id" : ObjectId("5686eece6aa2c7623f0a551e"),
        "name" : "Charmander",
        "description" : "Chaaaar",
        "attack" : 52,
        "height" : 0.7,
        "active" : false,
        "type" : "Fire",
        "moves" : [
                "Investida",
                "Chute flamejante",
                "Lança chamas",
                "desvio"
        ]
}
{
        "_id" : ObjectId("567b8a2119e6c47b0b11c1ac"),
        "name" : "Pikachu",
        "description" : "Pika-Pika",
        "type" : "Electric",
        "attack" : 55,
        "height" : 4,
        "active" : false,
        "moves" : [
                "Investida",
                "Choque do trovão",
                "Descarga",
                "Levitação Magnético",
                "desvio"
        ]
}
{
        "_id" : ObjectId("568718a3481d8afee55eaeab"),
        "name" : "AindaNaoExisteMon",
        "description" : "Sem maiores informações",
        "attack" : null,
        "active" : false,
        "type" : null,
        "moves" : [
                "Investida"
        ]
}
>

```

## 5. Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

```js
var q  = {
	moves:{
		$all:[
			/investida/i,
			/Jato de água/i
		]
	}
}


> db.pokemons.find(q).pretty()
{
        "_id" : ObjectId("567b8a4e19e6c47b0b11c1af"),
        "name" : "Squirtle",
        "description" : "Tartaruga",
        "type" : "Water",
        "attack" : 48,
        "height" : 5,
        "active" : false,
        "moves" : [
                "Investida",
                "Ataque de bolhas",
                "Jato de água",
                "desvio"
        ]


```


## 6. Pesquisar **todos** os pokemons que não são do tipo `elétrico`.

```js

var q = {

	moves: {

		$nin:[
			/electric/i
		]
	}

}


> db.pokemons.find(q).pretty()
{
        "_id" : ObjectId("567b8a3a19e6c47b0b11c1ae"),
        "name" : "Charizard",
        "description" : "Dragao",
        "type" : "Fire",
        "attack" : 84,
        "height" : 17,
        "active" : false,
        "moves" : [
                "Investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("567b8a4e19e6c47b0b11c1af"),
        "name" : "Squirtle",
        "description" : "Tartaruga",
        "type" : "Water",
        "attack" : 48,
        "height" : 5,
        "active" : false,
        "moves" : [
                "Investida",
                "Ataque de bolhas",
                "Jato de água",
                "desvio"
        ]
}
{
        "_id" : ObjectId("5685cd5fb84942ffd48e96f1"),
        "name" : "Testemon",
        "description" : "pokemon teste",
        "type" : "teste",
        "attack" : 1000,
        "height" : 2.1,
        "active" : false,
        "moves" : [
                "Investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("567b8a2f19e6c47b0b11c1ad"),
        "name" : "Psyduck",
        "description" : "Pato",
        "type" : "Water",
        "attack" : 52,
        "height" : 8,
        "active" : false,
        "moves" : [
                "Investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("567b8a5f19e6c47b0b11c1b0"),
        "name" : "Meowth",
        "description" : "Gato",
        "type" : "Normal",
        "attack" : 45,
        "height" : 4,
        "active" : false,
        "moves" : [
                "Investida",
                "desvio"
        ]
}
{
        "_id" : ObjectId("5686ee656aa2c7623f0a551d"),
        "name" : "Bulbassauro",
        "description" : "Bulbassauro",
        "attack" : 49,
        "height" : 0.7,
        "active" : false,
        "type" : "Seed",
        "moves" : [
                "Investida",
                "Lamina de folha",
                "Chicote de cipó",
                "desvio"
        ]
}
{
        "_id" : ObjectId("5686eece6aa2c7623f0a551e"),
        "name" : "Charmander",
        "description" : "Chaaaar",
        "attack" : 52,
        "height" : 0.7,
        "active" : false,
        "type" : "Fire",
        "moves" : [
                "Investida",
                "Chute flamejante",
                "Lança chamas",
                "desvio"
        ]
}
{
        "_id" : ObjectId("567b8a2119e6c47b0b11c1ac"),
        "name" : "Pikachu",
        "description" : "Pika-Pika",
        "type" : "Electric",
        "attack" : 55,
        "height" : 4,
        "active" : false,
        "moves" : [
                "Investida",
                "Choque do trovão",
                "Descarga",
                "Levitação Magnético",
                "desvio"
        ]
}
{
        "_id" : ObjectId("568718a3481d8afee55eaeab"),
        "name" : "AindaNaoExisteMon",
        "description" : "Sem maiores informações",
        "attack" : null,
        "active" : false,
        "type" : null,
        "moves" : [
                "Investida"
        ]
}

```

## 7. Pesquisar **todos** pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.

```js

var q =  {

	$and:[

		{
			moves:'investida'
		},
		{
			defense:{
				$lte:49
			}
		}
	]

}

> db.pokemons.find(q).pretty()

```

## 8. Remova **todos** os pokemons do tipo água e com attack menor que 50.

```js

var q  = {
	$and:[
		{
			type: /água/i
		},
		{
			attack: {
				$lt: 50
			}
		}
	]
}

> db.pokemons.remove(q)
WriteResult({ "nRemoved" : 1 })
>

```
