# MongoDB - Aula 01 - Exercício
autor: Renan Roger Ferreira da silva
## Importando os restaurantes

    ```
    2017-04-28T11:49:59.810-0300	connected to: localhost
    2017-04-28T11:49:59.810-0300	dropping: teste.restaurantes
    2017-04-28T11:50:02.090-0300	imported 25359 documents

    ```
##Contando restaurantes

```
    teste> db.restaurantes.find({}).count()
    25359

```