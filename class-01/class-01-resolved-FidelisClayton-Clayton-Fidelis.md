# MongoDB - Aula 01 - Exercício
autor: Clayton Fidelis

## Breve introdução mongoimport e mongoexport
  **mongoexport**: Serve para exportar os dados de uma coleção para um arquivo json.

  **mongoimport**: Serve para importar os dados de um arquivo json para uma coleção.

![Rlly](http://img4.wikia.nocookie.net/__cb20121224013155/adventuretimewithfinnandjake/images/b/be/Rlly.jpg )

## Importando os restaurantes

    ```
    clayton@bytez:~/Documentos/be-mean-instagram-mongodb-excercises$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
    2015-11-24T22:43:44.645-0200    connected to: localhost
    2015-11-24T22:43:44.645-0200    dropping: be-mean.restaurantes
    2015-11-24T22:43:47.579-0200    [####################....] be-mean.restaurantes 9.8 MB/11.3 MB (86.3%)
    2015-11-24T22:43:48.194-0200    imported 25359 documents
    ```

## Contando os restaurantes

    ```
    bytez(mongod-3.0.7) be-mean> db.restaurantes.find().count();
    25359
    ```
