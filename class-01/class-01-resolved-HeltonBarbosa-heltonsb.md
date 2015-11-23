# MongoDB - Aula 01 - Exercício
**Autor:** Helton Barbosa

## 1º Passo 
### Importação dos documentos JSON;

```
helton@mongodb:~$ mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-15T10:57:55.043-0300    connected to: localhost
2015-11-15T10:57:55.056-0300    dropping: be-mean.restaurantes
2015-11-15T10:57:58.059-0300    [##########..............] be-mean.restaurantes 5.1 MB/11.4 MB (44.7%)
2015-11-15T10:58:01.047-0300    [##################......] be-mean.restaurantes 8.6 MB/11.4 MB (76.0%)
2015-11-15T10:58:03.724-0300    imported 25359 documents
```

## 2º Passo
### Contagem dos documentos;

```
mongodb(mongod-3.0.7) be-mean> db.restaurantes.count()
25359
```