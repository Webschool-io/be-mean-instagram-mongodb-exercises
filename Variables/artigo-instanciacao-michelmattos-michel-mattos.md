# Artigo
**autor**: Michel Mattos

**Prazo**: até dia 18 de Novembro de 2015

Explique, com teoria e código, nesse artigo como o JavaScript cria e instancia as variáveis, seguindo os seguintes tópicos.

## Hoisting

Hoisting é uma característica do JavaScript onde as variáveis e funções estão disponíveis para todo o escopo onde foram declaradas, independente da ordem em que foram declaradas.

Vamos ver alguns exemplos.

```javascript
// hoisting_01.js
console.log(a); // Dispara um erro do tipo ReferenceError
```
```javascript
// hoisting_02.js
console.log(a); // Retorna undefined, e não mais um erro

var a;
```
No primeiro exemplo, um `ReferenceError` é disparado pois a variável `a` não foi declarada previamente. Isso pode ser solucionado colocando um `var a;` no início do arquivo, mas graças ao hoisting, essa declaração pode ficar em qualquer lugar *daquele escopo*.


```javascript
// hoisting_03.js
console.log(a); // Retorna undefined

var a = 1;
```
O código acima continua retornando `undefined`. O motivo é que apenas a declaração da variável fica disponível, e não a sua atribuição. Isso acontece porque o compilador javascript divide a declaração `var a = 1;` em duas: `var a;` e `a = 1;`. Então a variável `a` estará disponível para todo o escopo onde ela foi declarada, mas o valor só será atribuido à variável depois daquele ponto.


```javascript
// hoisting_04.js
log('Teste'); // Funciona

function log(texto) {
  console.log(texto);
}
```
```javascript
// hoisting_05.js
log('Teste'); // Não funciona, retorna TypeError

var log = function (texto) {
  console.log(texto);
}
```
Com funções, o funcionamento é o mesmo. O primeiro funciona porque a função é definida de forma *declarativa*. Porém, no segundo exemplo, um erro do tipo `TypeError` é retornado, pois apenas a declaração `log` com o valor inicial `undefined` está disponível naquele momento (por isso o erro do tipo `TypeError` é disparado, pois `undefined` não é uma `Function`).


## Closure

Closure permite uma função "lembrar" o escopo onde ela foi definida, mesmo quando ela é invocada fora desse escopo. Isso acontece porque toda função tem acesso ao seu escopo e aos escopos superiores (até o escopo global).

Isso permite coisas como variáveis privadas, persistir informações entre várias execuções, etc.

```javascript
// closure.js
var fibonacci = (function() {
  var valor1 = 0,
      valor2 = 0;
  return function() {
    var proximo = valor1 + valor2 || 1;
    valor1 = valor2;
    valor2 = proximo;
    return proximo;
  }
})();

fibonacci(); // 1
fibonacci(); // 1
fibonacci(); // 2
fibonacci(); // 3
fibonacci(); // 5
fibonacci(); // 8
fibonacci(); // 13
```
O exemplo acima é um ótimo exemplo de quando usar um closure. Veja que a função retornada pela IIFE continua tendo acesso às variáveis `valor1` e `valor2`, mesmo após o término da execução da IIFE.

## Variável Global

Toda variável e função declarada fora de uma função se tornam globais, ou seja, podem ser acessadas de qualquer lugar da aplicação. Apesar de declarar variáveis e funções globais serem consideradas uma má prática, muitas bibliotecas criam, ao menos, uma variável global, usada para acessar as APIs expostas por elas (usar a global aumenta o risco de "colisões", principalmente quando são usados códigos/bibliotecas de terceiros, onde você não sabe quais variáveis globais cada um está criando).

Atribuir um valor a uma variável que nunca foi declarada, fará com que a engine javascript crie a variável como global, exceto se o modo strict (`"use strict";`) for usado.
```javascript
// Sem o modo strict
function multiplicar(v1, v2) {
  resultado = v1 * v2;
  return resultado;
}

multiplicar(2, 2); // 4
console.log(resultado); // 4!!! A variável resultado vazou!
```
```javascript
// Com o modo strict
function multiplicar(v1, v2) {
  "use strict";
  resultado = v1 * v2;
  return resultado;
}

multiplicar(2, 2); // 4
console.log(resultado); // ReferenceError: resultado não existe
```

## Variável por parâmetro

Variáveis geralmente são passadas *por valor* para uma função, ou seja, uma cópia delas é repassada para a função, protegendo os valores originais de serem alterados:
```javascript
function maisUm(valor) {
  valor += 1;
  console.log(valor);
}

var a = 1;
maisUm(a); // 2
console.log(a); // 1
```

Porém, variáveis do tipo `Object` ou `Array` são passadas *por referência*. Alterações em seus valores serão refletidas nos valores originais:
```javascript
function inserir(lista, valor) {
  lista.push(valor);
}

var lista = [1];
inserir(lista, 2);
console.log(lista); // [1, 2]
```

## Instanciação usando uma IIFE

Explique como uma variável pode receber um valor de uma IIFE.
Explique como passar uma variável por parâmetro para a IIFE e acontece com ela dentro da função.

Uma IIFE pode ser usada para criar um padrão de projeto (design pattern) conhecido como **Módulo**:
```javascript
var $ = (function() {
  /* código do módulo: APIs, variáveis privadas, etc */
  return module;
})();
```

Caso o módulo tenha dependências, elas também podem ser passadas para a IIFE:
```javascript
var $ = (function(moduloA, moduloB) {
  /* código do módulo: APIs, variáveis privadas, etc */
  return module;
})(mod1, mod2);
```

## Considerações

Quanto mais explicado melhor.

Lembre que isso fará parte do seu currículo como aluno e será disponilizado no sistema de vagas, ou seja, o contratante poderá ver todos seus projetos e trabalhos feitos nesse curso.

Boa sorte.

# Envio

1. Fork [esse repositório](https://github.com/Webschool-io/be-mean-instagram-artigos/) 
2. Nomeie seu artigo usando o seguinte padrão: artigo-instanciacao-githubuser-nome-completo.md
3. Adicione seu exercício aqui na Pasta Variables
4. Faça um Pull Requst enviando seu artigo.
