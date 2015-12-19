# MongoDB - Aula 04 - Exercício
autor: Edison Bosnyak

## **Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
	> var query = {name:{$in:['Abra','Alakazam','Kadabra','Voltorb','Electrode']}}
	> var options = {multi:true}
	> var attacks=['Soco','Chute']
	> var mod = {$pushAll:{moves:attacks}}
	> db.pokemons.update(query,mod,options)
	WriteResult({ "nMatched" : 5, "nUpserted" : 0, "nModified" : 5 })
	> db.pokemons.find()
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca670"),
	        "name" : "Abra",
	        "description" : "Abra sleeps for eighteen hours a day.",
	        "attack" : 20,
	        "defense" : 15,
	        "height" : 9,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca671"),
	        "name" : "Kadabra",
	        "description" : "Kadabra emite uma onda peculiar.",
	        "attack" : 35,
	        "defense" : 30,
	        "height" : 13,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca673"),
	        "name" : "Voltorb",
	        "description" : "Voltorb was first sighted at a company that manufactures Poké Balls. ",
	        "attack" : 30,
	        "defense" : 50,
	        "height" : 5,
	        "tipo" : "Elétrico",
	        "moves" : [
	                "Soco",
	                "Chute"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca674"),
	        "name" : "Electrode",
	        "description" : "Electrode eats electricity in the atmosphere.",
	        "attack" : 50,
	        "defense" : 70,
	        "height" : 12,
	        "tipo" : "Elétrico",
	        "moves" : [
	                "Soco",
	                "Chute"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca672"),
	        "name" : "Alakazam",
	        "description" : "Alakazam's brain continually grows, making its head far too heavy to support with its neck.",
	        "attack" : 50,
	        "defense" : 45,
	        "height" : 15,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute"
	        ]
	}

## **Adicionar** 1 movimento em todos os pokemons: `desvio`.##
	> var mod = {$push:{moves:'desvio'}}
	> var option = {multi:true}
	> db.pokemons.update({},mod,option)
	> WriteResult({ "nMatched" : 5, "nUpserted" : 0, "nModified" : 5 })
	> db.pokemons.find()
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca670"),
	        "name" : "Abra",
	        "description" : "Abra sleeps for eighteen hours a day.",
	        "attack" : 20,
	        "defense" : 15,
	        "height" : 9,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca671"),
	        "name" : "Kadabra",
	        "description" : "Kadabra emite uma onda peculiar.",
	        "attack" : 35,
	        "defense" : 30,
	        "height" : 13,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca672"),
	        "name" : "Alakazam",
	        "description" : "Alakazam's brain continually grows, making its head far too heavy to support with its neck.",
	        "attack" : 50,
	        "defense" : 45,
	        "height" : 15,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca673"),
	        "name" : "Voltorb",
	        "description" : "Voltorb was first sighted at a company that manufactures Poké Balls. ",
	        "attack" : 30,
	        "defense" : 50,
	        "height" : 5,
	        "tipo" : "Elétrico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca674"),
	        "name" : "Electrode",
	        "description" : "Electrode eats electricity in the atmosphere.",
	        "attack" : 50,
	        "defense" : 70,
	        "height" : 12,
	        "tipo" : "Elétrico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}


## **Adicionar** o pokemon `AindaNaoExisteMon` caso ele não exista com todos os dados com o valor `null` e a descrição: "Sem maiores informações".##
	> var query = {name:'AindaNaoExisteMon'}
	> var option = {upsert:true}
	> var mod = {
        "$set" : {
                "name" : "AindaNaoExisteMon",
                "description" : "Sem maiores informações",
                "attack" : null,
                "defense" : null,
                "height" : null,
                "tipo" : null,
                "moves" : null
        }
    }
    > db.pokemons.update(query,mod,option)
	WriteResult({
	        "nMatched" : 0,
	        "nUpserted" : 1,
	        "nModified" : 0,
	        "_id" : ObjectId("564d40b5906dfcf9c4b1663d")
	})
	> db.pokemons.find(query)
	{
	        "_id" : ObjectId("564d40b5906dfcf9c4b1663d"),
	        "name" : "AindaNaoExisteMon",
	        "description" : "Sem maiores informações",
	        "attack" : null,
	        "defense" : null,
	        "height" : null,
	        "tipo" : null,
	        "moves" : null
	}
## Pesquisar todos o pokemons que possuam o ataque `investida` e mais um que você adicionou, escolha seu pokemon favorito.##
	> var query = {moves:{$all:['Investida','Soco']}}
	> db.pokemons.find(query)

## Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.##
	> var query = {moves:{$all:['Soco','desvio','Chute']}}
	> db.pokemons.find(query)
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca670"),
	        "name" : "Abra",
	        "description" : "Abra sleeps for eighteen hours a day.",
	        "attack" : 20,
	        "defense" : 15,
	        "height" : 9,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca671"),
	        "name" : "Kadabra",
	        "description" : "Kadabra emite uma onda peculiar.",
	        "attack" : 35,
	        "defense" : 30,
	        "height" : 13,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca672"),
	        "name" : "Alakazam",
	        "description" : "Alakazam's brain continually grows, making its head far too heavy to support with its neck.",
	        "attack" : 50,
	        "defense" : 45,
	        "height" : 15,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca673"),
	        "name" : "Voltorb",
	        "description" : "Voltorb was first sighted at a company that manufactures Poké Balls. ",
	        "attack" : 30,
	        "defense" : 50,
	        "height" : 5,
	        "tipo" : "Elétrico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca674"),
	        "name" : "Electrode",
	        "description" : "Electrode eats electricity in the atmosphere.",
	        "attack" : 50,
	        "defense" : 70,
	        "height" : 12,
	        "tipo" : "Elétrico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}

## Pesquisar **todos** os pokemons que não são do tipo `elétrico`.##
	> var query = {tipo:{$ne:'Elétrico'}}
	> db.pokemons.find(query)
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca670"),
	        "name" : "Abra",
	        "description" : "Abra sleeps for eighteen hours a day.",
	        "attack" : 20,
	        "defense" : 15,
	        "height" : 9,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca671"),
	        "name" : "Kadabra",
	        "description" : "Kadabra emite uma onda peculiar.",
	        "attack" : 35,
	        "defense" : 30,
	        "height" : 13,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("5642dba9135c3c27f86ca672"),
	        "name" : "Alakazam",
	        "description" : "Alakazam's brain continually grows, making its head far too heavy to support with its neck.",
	        "attack" : 50,
	        "defense" : 45,
	        "height" : 15,
	        "tipo" : "Físico",
	        "moves" : [
	                "Soco",
	                "Chute",
	                "desvio"
	        ]
	}
	{
	        "_id" : ObjectId("564d40b5906dfcf9c4b1663d"),
	        "name" : "AindaNaoExisteMon",
	        "description" : "Sem maiores informações",
	        "attack" : null,
	        "defense" : null,
	        "height" : null,
	        "tipo" : null,
	        "moves" : null
	}	

## Pesquisar **todos** os pokemons que tenham o ataque `investida` **E** tenham a defesa **não menor ou igual** a 49.##
	> var query = {
		$and:[
			{moves:'investida'},
			{defesa:{$ne:{lte:49}}}
		]}
	> db.pokemons.find(query)

## Remova **todos** os pokemons do tipo água e com attack menor que 50.
	> var query = {$and:[{tipo:'Água'},{attack:{$lt:50}}]}
	> db.pokemons.remove(query)
	WriteResult({ "nRemoved" : 0 })

## Demonstre qual a diferença entre os operadores $ne e $not.
	De acordo com a documentação, o $ne é um operador de comparação, já o $not é um operador lógico.
	Enquanto $ne não aceita regex, o $not 'só' aceita regex 

	> var query = {tipo:{$ne:/eletrico/i}}
	> db.pokemons.find(query)
	Error: error: {
	        "$err" : "Can't canonicalize query: BadValue Can't have regex as arg to $ne.",
	        "code" : 17287
	}

	> var query = {tipo:{$not:'Elétrico'}}
	> db.pokemons.find(query)
	Error: error: {
	        "$err" : "Can't canonicalize query: BadValue $not needs a regex or a document",
	        "code" : 17287
	}