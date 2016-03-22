# MongoDB - Aula 02 - Exercício
autor: Kayo glauco

## Criar o banco

```
> use be-mean-pokemons

```

## Exibir os bancos no servidor
    
    ```
    > show databases

    ```

## Exibir as coleções no banco

    ```
    > show collections

    ```

## Inserindo 5 pokemons

    ```
	
    > db.pokemons.insert({'name':'Hoothoot', 'description':'Coruja da hora', 'attack':20, 'defense': 20, height:0.7})
    Inserted 1 record(s) in 2ms
    WriteResult({
      "nInserted": 1
    })

    > db.pokemons.insert({'name':'Ledyba', 'description':'Joaninha ruim de briga', 'attack':10, 'defense': 20, height:1.0})
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })

    > db.pokemons.insert({'name':'Ledian', 'description':'Abelha mascarada', 'attack':20, 'defense': 20, height:1.4})
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })

    > db.pokemons.insert({'name':'Spinarak', 'description':'Spider terror', 'attack':30, 'defense': 20, height:0.5})
    Inserted 1 record(s) in 2ms
    WriteResult({
      "nInserted": 1
    })

    > db.pokemons.insert({'name':'Crobat', 'description':'Mascote do batman', 'attack':50, 'defense': 40, height:1.8})
    Inserted 1 record(s) in 1ms
    WriteResult({
      "nInserted": 1
    })
	
    ```
    
## Listar os pokemons na coleção

    
    ```
	
    > db.pokemons.find()
    {
      "_id": ObjectId("56f0a0bb5eaa73b462f79f98"),
      "name": "Hoothoot",
      "description": "Coruja da hora",
      "attack": 20,
      "defense": 20,
      "height": 0.7
    }
    {
      "_id": ObjectId("56f0a0f15eaa73b462f79f99"),
      "name": "Ledyba",
      "description": "Joaninha ruim de briga",
      "attack": 10,
      "defense": 20,
      "height": 1
    }
    {
      "_id": ObjectId("56f0a17c5eaa73b462f79f9a"),
      "name": "Ledian",
      "description": "Abelha mascarada",
      "attack": 20,
      "defense": 20,
      "height": 1.4
    }
    {
      "_id": ObjectId("56f0a2055eaa73b462f79f9b"),
      "name": "Spinarak",
      "description": "Spider terror",
      "attack": 30,
      "defense": 20,
      "height": 0.5
    }
    {
      "_id": ObjectId("56f0a4165eaa73b462f79f9c"),
      "name": "Crobat",
      "description": "Mascote do batman",
      "attack": 50,
      "defense": 40,
      "height": 1.8
    }
    Fetched 5 record(s) in 2ms
	
    ```

## Consultar pokemon

    ```
    > var poke = db.pokemons.findOne({'name':'Crobat'})
    > poke
    {
      "_id": ObjectId("56f0a4165eaa73b462f79f9c"),
      "name": "Crobat",
      "description": "Mascote do batman",
      "attack": 50,
      "defense": 40,
      "height": 1.8
    }

    ```

## Alterar a description do pokemon

    ```
    > poke.description = 'Mascote assassino do batman'
    > db.pokemons.save(poke)
    Updated 1 existing record(s) in 1ms
    WriteResult({
      "nMatched": 1,
      "nUpserted": 0,
      "nModified": 1
    })


    ```
    

