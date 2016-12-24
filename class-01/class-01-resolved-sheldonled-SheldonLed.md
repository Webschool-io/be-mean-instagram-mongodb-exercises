# MongoDB - Aula 01 - Exercício
autor: Sheldon Led

## Importando os restaurantes

    ```
    mongoimport -d newdb -c restaurantes --drop --file restaurantes.json 
    connected to: 127.0.0.1
    Fri May  6 10:16:39.868 dropping: newdb.restaurantes
    Fri May  6 10:16:40.361 check 9 25359
    Fri May  6 10:16:40.745 imported 25359 objects
        

    ```

## Contando os restaurantes

    ```
    db.restaurantes.find({}).count()
    25359
    
    ```