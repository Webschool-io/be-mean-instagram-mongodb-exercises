# MongoDB - Aula 01 - Exercício
autor: Lucas Duarte Anício

## Importando os restaurantes

```
lucas@lucas-Aspire-E5-573G:~$ mongoimport --db be-mean --collection restaurantes --drop --file ~/Dropbox/Be\ MEAN/MongoDB/Aula\ 1/restaurantes.json  
connected to: 127.0.0.1  
2016-01-29T23:19:50.317-0200 dropping: be-mean.restaurantes  
2016-01-29T23:19:50.760-0200 check 9 25359  
2016-01-29T23:19:50.779-0200 imported 25359 objects  
```

## Contando os restaurantes

```
> use be-mean  
switched to db be-mean  
> db.restaurantes.find({}).count()  
25359  
```

