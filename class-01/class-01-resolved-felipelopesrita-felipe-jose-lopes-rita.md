# MongoDB - Aula 01 - Exercício
autor: Felipe José Lopes Rita

## Importando os restaurantes

```js
mongoimport -d be-mean -c restaurante --drop --file /home/felipe/Documentos/Estudos/beMEAN/Aula01/restaurantes.json 
2016-02-04T14:57:10.786-0200	connected to: localhost
2016-02-04T14:57:10.787-0200	dropping: be-mean.restaurante
2016-02-04T14:57:13.783-0200	[########################] be-mean.restaurante	11.3 MB/11.3 MB (100.0%)
2016-02-04T14:57:13.794-0200	[########################] be-mean.restaurante	11.3 MB/11.3 MB (100.0%)
2016-02-04T14:57:13.795-0200	imported 25359 documents

```

## Contando os restaurantes

```js
> db.restaurantes.find({}).count()
25359
```


