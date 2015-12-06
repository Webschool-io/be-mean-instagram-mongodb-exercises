
# MongoDB - Aula 06 - Exercício
autor: Roland Gabriel


## 1. Fazer a query sem indíce para o campo 'name'
```js
be-mean> p.find({name: 'Omanyte'}).explain('executionStats').executionStats.totalDocsExamined
610
```

#### 1.2. Fazer a query com indíce para o campo 'name'

```js
be-mean> p.find({name: 'Omanyte'}).explain('executionStats').executionStats.totalDocsExamined
1
```

## 2. Fazer a query sem indíce para dois campos juntos ('height' e 'type: ['water']')
```js
be-mean> p.find({height:'2', types:'psychic'}).explain('executionStats').executionStats.totalDocsExamined
610
```

## 2.2. Fazer a query sem indíce para dois campos juntos ('height' e 'type: ['water']')
```js
be-mean> p.find({height:'2', types:'psychic'}).limit(1).explain('executionStats').executionStats.totalDocsExamined
1
```
