# MongoDB - Aula 02 - Exercício
autor: Fco Ronaldo Aragão

## Crie uma database chamada be-mean-pokemons

    ```
    > use be-mean-pokemons

    ```

## Liste quais databases você possui nesse servidor

    ```
    > show dbs
    test              → 0.078GB
    local             → 0.078GB
    be-mean-instagram → 0.078GB
    be-mean           → 0.078GB
    be-mean-pokemons  → 0.078GB

    ```
## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

    ```
    {'name':'Blastoise','description': 'Descrição do blastoise','type': 'Água', 'attack': 85, height: 16 }
    {'name':'Charizard','description': 'Descrição do Charizard','type': 'Fogo', 'attack': 50, height: 45 }
    {'name':'Pikachu','description': 'Descrição do pikachu','type': 'Elétrico', 'attack': 100, height: 60 }
    {'name':'Butterfly','description': 'Descrição do butterfly','type': 'Inseto', 'attack': 48, height: 38 }
    {'name':'Twitter','description': 'Twitter não é um pokemon','type': 'Rede social', 'attack': 140, height: 140 }
    
    ```    
## Liste os pokemons existentes na sua coleção

    ```
	be-mean-pokemons> db.pokemons.find()
	{
	  "_id": ObjectId("56452c6f8dfbf85d4ae2dee4"),
	  "name": "Charizard",
	  "description": "Descrição do charizard",
	  "type": "Fogo",
	  "attack": 85,
	  "height": 16
	}
	{
	  "_id": ObjectId("56452e938dfbf85d4ae2dee5"),
	  "name": "Blastoise",
	  "description": "Descrição do blastoise",
	  "type": "Água",
	  "attack": 85,
	  "height": 16
	}
	{
	  "_id": ObjectId("56452eb18dfbf85d4ae2dee6"),
	  "name": "Pikachu",
	  "description": "Descrição do pikachu",
	  "type": "Elétrico",
	  "attack": 100,
	  "height": 60
	}
	{
	  "_id": ObjectId("56452ed88dfbf85d4ae2dee7"),
	  "name": "Butterfly",
	  "description": "Descrição do butterfly",
	  "type": "Inseto",
	  "attack": 48,
	  "height": 38
	}
	{
	  "_id": ObjectId("56452eee8dfbf85d4ae2dee8"),
	  "name": "Twitter",
	  "description": "Twitter não é um pokemon",
	  "type": "Rede social",
	  "attack": 140,
	  "height": 140
	}
	Fetched 5 record(s) in 2ms

    ```   
## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`

    ```
      var query = {name: 'Pikachu'}
      var poke = db.pokemons.findOne(query)
      be-mean-pokemons> poke
      {
        "_id": ObjectId("56452eb18dfbf85d4ae2dee6"),
        "name": "Pikachu",
        "description": "Descrição do pikachu",
        "type": "Elétrico",
        "attack": 100,
        "height": 60
      }


    ```    
## Modifique sua `description` e salvê-o

    ```
   be-mean-pokemons> poke.description = "Nova descrição do pikachu"
	Nova descrição do pikachu
   
   be-mean-pokemons> db.pokemons.save(poke)
	Updated 1 existing record(s) in 14ms
	WriteResult({
  	  "nMatched": 1,
          "nUpserted": 0,
  	  "nModified": 1
	})

    ```   
