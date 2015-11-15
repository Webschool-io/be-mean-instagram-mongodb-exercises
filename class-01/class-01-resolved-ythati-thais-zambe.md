# MongoDB - Aula 01 - Exercício
Autor: Thais Barbosa Zambe

## Importando os restaurantes

    ```
    PS C:\Program Files\MongoDB\Server\3.0\bin> .\mongoimport.exe --db 'be-mean' --collection restaurantes --drop --file 'C:\Users\lolfa\Documents\GitHub\be-mean-instagram\apostila\module-mongodb\data\restaurantes.json'
    2015-11-12T19:37:26.164-0200    connected to: localhost
    2015-11-12T19:37:26.185-0200    dropping: be-mean.restaurantes
    2015-11-12T19:37:29.101-0200    [####################....] be-mean.restaurantes 9.8 MB/11.4 MB (86.2%)
    2015-11-12T19:37:29.761-0200    imported 25359 documents

    ```

**windows a shit**

## Contando os restaurantes

    ```
    > db.restaurantes.find({}).count()
    25359

    ```