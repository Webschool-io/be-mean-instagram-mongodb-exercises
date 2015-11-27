# MongoDB - Aula 01 - Exercício
autor: **Thiago Aurélio da Cunha**

## Importando os restaurantes

    ```
     MacBook:bin thiagocunha$ mongoimport --db be-mean --collection restaurantes  --file /Users/thiagocunha/Desktop/mongo/bin/restaurantes.json
     2015-11-16T13:42:08.324-0200	connected to: localhost
     2015-11-16T13:42:09.667-0200	imported 25359 documents
     MacBook:bin thiagocunha$ 

    ```

## Contando os restaurantes

    ```
    MacBook(mongod-3.0.7) be-mean> db.restaurantes.find({}).count()
    25359
    MacBook(mongod-3.0.7) be-mean> 

    ```