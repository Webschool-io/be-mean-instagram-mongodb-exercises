# MongoDB - Aula 01 - Exercício  
**User:** [willianlauber](https://github.com/willianlauber)  
**Autor:** Willian Lauber
**Date** 1475846381

## Importando os restaurantes


lc@lubuntu ~

```bash
 $ mongoimport -db class1 --colection restaurantes --drop --file /home/lc/Downloads/restaurantes.json
 connected to: 127.0.0.1
2016-10-07T10:09:46.667-0300 dropping: class1.restaurantes
2016-10-07T10:09:47.980-0300 check 9 25359
2016-10-07T10:09:48.038-0300 imported 25359 objects

```
## Contando os restaurantes

```bash
 $ mongo
 ```
 ```MongoDB
 > db.restaurantes.count({})
25359
 ```
