# MongoDB - Aula 01 - Exercício
autor: Fernando Lucas

## Importando os restaurantes

    ```  
     mongoimport --db be-mean-instagram --collection restaurantes --drop --file restaurantes.json 
     connected to: 127.0.0.1
     2016-04-10T18:12:15.330-0300 dropping: be-mean-instagram.restaurantes
     2016-04-10T18:12:16.496-0300 check 9 25359
     2016-04-10T18:12:16.759-0300 imported 25359 objects

    
    ```

## Contando os restaurantes

    ```
    > use be_mean
    switched to db be_mean
    > db.restaurantes.find({}).count()
    25359
    >

    ```