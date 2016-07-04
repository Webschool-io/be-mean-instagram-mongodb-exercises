# MongoDB - Aula 01 - Exercício
autor: Ronaiza Cardoso

## Importando os pokemons (não consegui encontrar o arquivo restaurantes.json)

    ```
> mongoimport --db be-mean --collection pokemons --host=127.0.0.1 --drop --file pokemon.json
 2016-07-04T13:12:01.713-0300    connected to: 127.0.0.1
 2016-07-04T13:12:01.716-0300    dropping: be-mean.pokemons
 2016-07-04T13:12:02.173-0300    imported 1 document
    ```

## Contando os pokemons

    ```
   db.restaurantes.find({}).count()
   0

    ```
