## Aula 1 - MongoDB - Exercicío
autor - Igor Oliveira (github.com/DevIgor)

## Importando 
> mongoimport --db WorkShopBeMEAN --collection restaurantes --drop --file restaurantes.json 
2016-06-19T21:54:34.954-0300	connected to: localhost
2016-06-19T21:54:34.954-0300	dropping: WorkShopBeMEAN.restaurantes
2016-06-19T21:54:36.482-0300	imported 25359 documents

## Fazendo a contagem
> db.restaurantes.find({}).count()
25359
