# MongoDB - Aula 03 - Exercício
autor: Daniel Cruvinel

## 1.Liste todos os Pokemons com a altura MENOR QUE 0.5

    ```
     db.pokemons.find({'height': {$lt: 0.5}})

    ```

## 2.Liste todos Pokemons com a altura MAIOR OU IGUAL QUE 0.5

    ```
    db.pokemons.find({'height': {$gte: 0.5})

    ```

## 3.Liste todos Pokemons com a altura MENOR OU IGUAL QUE 0.5 E to tipo grama

    ```
    var type = {'tipo': 'grama'}
	var altura = {'height': {$lte: 0.5}}
	db.pokemons.find($and: [altura, type])

    ```

## 4.Liste todos Pokemons com o name 'Pikachu' OU com attack MENOR OU IGUAL QUE 0.5

    ```
    var query = {$or: [{name: 'Pikachu'}, {attack: {$lte: 0.5}}]}
	db.pokemons.find(query)

    ```

## 5.Liste todos Pokemons com o attack MAIOR OU IGUAL QUE 48 E com height MENOR OU IGUAL QUE 0.5

    ```
    var ataque = {$gte: 48}
	var altura = {$lte: 0.5}
	db.pokemons.find($and: [ataque, altura])

    ```