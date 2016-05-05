# MongoDB - Aula 02 - Exercício
autor: Rodolfo Vidal

## Listagem das databases (passo 2)

		labspace(mongod-2.6.11) use be-mean-pokemons  
		switched to db be-mean-pokemons 

		labspace(mongod-2.6.11) be-mean-pokemons> show dbs    
		be-mean-instagram       		0.078GB 	
		be-mean-pokemons    			0.078GB 	
		local               			0.078GB 	
		admin               			(empty) 	

## Listagem das coleções (passo 3)

		labspace(mongod-2.6.11) be-mean-pokemons> show collections		
		pokemons        				0.001MB / 0.008MB		
		system.indexes  				0.000MB / 0.008MB		

## Cadastro dos pokemons (passo 4)	

		labspace(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Meowth','description':'Este pokemon ama moedas brilhantes que brilham com a luz','type':'normal','attack':'45','height':'4','defense':'35' }		
		labspace(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)		
		Inserted 1 record(s) in 7ms		
		WriteResult({		
		  "nInserted": 1		
		})		

		labspace(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Nidoran','description':'Este pokemon possue farpas que segregam um potente veneno','type':'venenoso','attack':'47','height':'4','defense':'52'}
		labspace(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
		Inserted 1 record(s) in 77ms
		WriteResult({
		  "nInserted": 1
		})

		labspace(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Jigglypuff','description':'Este pokemon usa suas habilidades de cantar precisamente no comprimento da onda fazendo com que os seus inimigos caiam no sono','type':'fada','attack':'45','height':'5','defense':'20'}
		labspace(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
		Inserted 1 record(s) in 2ms
		WriteResult({
		  "nInserted": 1
		})

		labspace(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Psyduck','description':'Este pokemon possui um poder misterioso','type':'água','attack':'52','height':'8','defense':'48'}
		labspace(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
		Inserted 1 record(s) in 3ms
		WriteResult({
		  "nInserted": 1
		})

		labspace(mongod-2.6.11) be-mean-pokemons> var pokemon = {'name':'Growlithe','description':'Este pokemon usa o seu sentido olfativo avançado para determinar as emoções de outros seres vivos','type':'fogo','attack':'70','height':'7','defense':'45'}
		labspace(mongod-2.6.11) be-mean-pokemons> db.pokemons.insert(pokemon)
		Inserted 1 record(s) in 1ms
		WriteResult({
		  "nInserted": 1
		})

		labspace(mongod-2.6.11) be-mean-pokemons> db.pokemons.save(pokemon)
		Inserted 1 record(s) in 1ms
		WriteResult({
		  "nInserted": 1
		})

## Listando os pokemons da minha coleção (passo 5)

		labspace(mongod-2.6.11) be-mean-pokemons> db.pokemons.find()
		{
		  "_id": ObjectId("564df741c25a4141e92297a7"),
		  "name": "Pikachu",
		  "description": "Rato elétrico bem fofinho",
		  "type": "electric",
		  "attack": "55",
		  "height": "0.4"
		}
		{
		  "_id": ObjectId("564df888c25a4141e92297a8"),
		  "name": "Charmander",
		  "description": "Esse é o cão chupando manga de fofinho",
		  "type": "fogo",
		  "attack": "52",
		  "height": "0.6"
		}
		{
		  "_id": ObjectId("564df9d7c25a4141e92297a9"),
		  "name": "Bulbassauro",
		  "description": "Chicote de trepadeira",
		  "type": "grama",
		  "attack": "49",
		  "height": "0.4"
		}
		{
		  "_id": ObjectId("564dfa68c25a4141e92297aa"),
		  "name": "Squirtle",
		  "description": "Ejeta água que passarinho não bebe",
		  "type": "água",
		  "attack": "48",
		  "height": "0.5"
		}
		{
		  "_id": ObjectId("564dfe19c25a4141e92297ab"),
		  "name": "Caterpie",
		  "description": "Larva lutadora",
		  "type": "inseto",
		  "attack": "30",
		  "height": "0.3",
		  "defense": "35"
		}
		{
		  "_id": ObjectId("564e884ca785af2b7ce74344"),
		  "name": "Meowth",
		  "description": "Este pokemon ama moedas brilhantes que brilham com a luz",
		  "type": "normal",
		  "attack": "45",
		  "height": "4",
		  "defense": "35"
		}
		{
		  "_id": ObjectId("564e8944a785af2b7ce74345"),
		  "name": "Nidoran",
		  "description": "Este pokemon possue farpas que segregam um potente veneno",
		  "type": "venenoso",
		  "attack": "47",
		  "height": "4",
		  "defense": "52"
		}
		{
		  "_id": ObjectId("564e8a26a785af2b7ce74346"),
		  "name": "Jigglypuff",
		  "description": "Este pokemon usa suas habilidades de cantar precisamente no comprimento da onda fazendo com que os seus inimigos caiam no sono",
		  "type": "fada",
		  "attack": "45",
		  "height": "5",
		  "defense": "20"
		}
		{
		  "_id": ObjectId("564e8aefa785af2b7ce74347"),
		  "name": "Psyduck",
		  "description": "Este pokemon possui um poder misterioso",
		  "type": "água",
		  "attack": "52",
		  "height": "8",
		  "defense": "48"
		}
		{
		  "_id": ObjectId("564e8bbea785af2b7ce74348"),
		  "name": "Growlithe",
		  "description": "Este pokemon usa o seu sentido olfativo avançado para determinar as emoções de outros seres vivos",
		  "type": "fogo",
		  "attack": "70",
		  "height": "7",
		  "defense": "45"
		}
		{
		  "_id": ObjectId("564e8be6a785af2b7ce74349"),
		  "name": "Growlithe",
		  "description": "Este pokemon usa o seu sentido olfativo avançado para determinar as emoções de outros seres vivos",
		  "type": "fogo",
		  "attack": "70",
		  "height": "7",
		  "defense": "45"
		}
		Fetched 11 record(s) in 2ms

## Buscando um pokemon pelo nome e armazena-lo na variável "poke" (passo 6)

		labspace(mongod-2.6.11) be-mean-pokemons> var query = {name:'Psyduck'}

		labspace(mongod-2.6.11) be-mean-pokemons> var poke = db.pokemons.findOne(query)	

		labspace(mongod-2.6.11) be-mean-pokemons> poke
		{
		  "_id": ObjectId("564e8aefa785af2b7ce74347"),
		  "name": "Psyduck",
		  "description": "Este pokemon possui um poder misterioso",
		  "type": "água",
		  "attack": "52",
		  "height": "8",
		  "defense": "48"
		}

## Modificando a 'description' e salvando (passo 7)

		labspace(mongod-2.6.11) be-mean-pokemons> poke.description = 'Quando este pokemon usa o seu poder misterioso, ele não consegue se lembrar porque ele entra em um estado muito parecido com o sono profundo'
Quando este pokemon usa o seu poder misterioso, ele não consegue se lembrar porque ele entra em um estado muito parecido com o sono profundo

		labspace(mongod-2.6.11) be-mean-pokemons> db.pokemons.save(poke)

		Updated 1 existing record(s) in 6ms
		WriteResult({
		  "nMatched": 1,
		  "nUpserted": 0,
		  "nModified": 1
		})
