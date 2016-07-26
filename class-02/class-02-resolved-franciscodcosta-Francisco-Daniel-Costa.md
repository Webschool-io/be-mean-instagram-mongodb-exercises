# MongoDB - Aula 02 - Exercício
autor: Francisco Daniel Costa

## Crie uma database chamada be-mean-pokemons

    ```
	> use be-mean-pokemons
	switched to db be-mean-pokemons

    ```

## Liste quais databases você possui nesse servidor

    ```
	> show dbs
	be-mean            0.005GB
	be-mean-instagram  0.000GB
	local              0.000GB
	 
    ```

## Liste quais coleções você possui nessa database

    ```
	> show collections
	> 

    ```

## Insira pelo menos 5 pokemons A SUA ESCOLHA utilizando o mesmo padrão de campos utilizado: name, description, attack, defense e height

    ```
	> var pokemons = [{'name':'Roska','description':'Quebra e depois conserta','defense': 10, attack: 55, height: 0.
	5 }, {'name':'Xikó','description':'Grão de bico violento','defense': 1, attack: 90, height: 0.4 }, {'name':'Borr
	ão','description':'HAHAHAHAHAHA','defense': 5, attack: 90, height: 0.2 }, {'name':'Ameba','description':'Nossa, 
	cara','defense': 40, attack: 60, height: 0.6 }, {'name':'Bruxa','description':'Põe a 5','defense': 50, attack: 1
	0, height: 0.7 }, {'name':'Moncherry','description':'O macho nunca afina','defense': 70, attack: 5, height: 0.8 
	}]

    ```

## Liste os pokemons existentes na sua coleção

    ```
	> pokemons
	[
	        {
	                "name" : "Roska",
	                "description" : "Quebra e depois conserta",
	                "defense" : 10,
	                "attack" : 55,
	                "height" : 0.5
	        },
	        {
	                "name" : "Xikó",
	                "description" : "Grão de bico violento",
	                "defense" : 1,
	                "attack" : 90,
	                "height" : 0.4
	        },
	        {
	                "name" : "Borrão",
	                "description" : "HAHAHAHAHAHA",
	                "defense" : 5,
	                "attack" : 90,
	                "height" : 0.2
	        },
	        {
	                "name" : "Ameba",
	                "description" : "Nossa, cara",
	                "defense" : 40,
	                "attack" : 60,
	                "height" : 0.6
	        },
	        {
	                "name" : "Bruxa",
	                "description" : "Põe a 5",
	                "defense" : 50,
	                "attack" : 10,
	                "height" : 0.7
	        },
	        {
	                "name" : "Moncherry",
	                "description" : "O macho nunca afina",
	                "defense" : 70,
	                "attack" : 5,
	                "height" : 0.8
	        }
	]

    ```

## Busque o pokemons a sua escolha, pelo nome, e armazene-o em uma variável chamada `poke`

    ```
	> var poke = db.pokemons.findOne({"name" : "Borrão"})
	> poke
	{
	        "_id" : ObjectId("5797945b44587c1c68fd89dd"),
	        "name" : "Borrão",
	        "description" : "HAHAHAHAHAHA",
	        "defense" : 5,
	        "attack" : 90,
	        "height" : 0.2
	}
	> 
    ```

## Modifique sua `description` e salvê-o

    ```
	> poke.description = "Jungle Lui"
	Jungle Lui
	> db.pokemons.save(poke)
	WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

	> db.pokemons.findOne({"name" : "Borrão"})
	{
	        "_id" : ObjectId("5797945b44587c1c68fd89dd"),
	        "name" : "Borrão",
	        "description" : "Jungle Lui",
	        "defense" : 5,
	        "attack" : 90,
	        "height" : 0.2
	}
	> 

    ```

