# MongoDB - Aula 01 - Exercício
autor: Robson Maia

## Importando os restaurantes

    ```
    2017-04-25T19:23:26.060-0300	connected to: localhost
    2017-04-25T19:23:26.060-0300	dropping: be-mean-vip.restaurantes
    2017-04-25T19:23:26.816-0300	Failed: error processing document #15597: invalid character '\n' in string literal
    2017-04-25T19:23:26.816-0300	imported 15596 documents


    ```

## Contando os restaurantes
	
	> use be-mean-vip
	switched to db be-mean-vip
	> db.restaurantes.find({}).count()
	15000

