# Instanciação de Variáveis no Javascript
autor: ** Pedro Henrique**

## Hoisting - Içaaaa (ps: de içar)

Hoisting é como um suporte à variáveis não previamente definidas, sendo elas içadas para cima (topo do escopo) caso estejam definidas no fim, ou ao longo, do script. Por exemplo, na maioria das linguagens como Java e C um bloco ( {} ) define o escopo de uma variável ou de uma função. O problema é que, quando eu definir uma variável dentro de um bloco eu só poderei utilizar esta variável por todo e SOMENTE este bloco (escopo). 

Em JavaScript o barato é loko... O escopo da minha variável será no nível da minha função, por exemplo, quando eu definir uma variável dentro de um bloco, poderei utilizá-la dentro ou fora do bloco que eu a declarei.
O JavaScript pode também pegar uma função, que pode estar até mesmo em qualquer lugar dentro de uma função e definir a sua definição no topo da função, nos bastidores, of corse. :)

Isso é chamado de Hoisting, e, basicamente, ele permite que você chame uma função que é definida após o código em que você está chamando-a.


Exemplo:
```js
mestreSuissa function () {
  maciota();
  
  maciota function () {
    console.log ('yay, só na maciota mano...');
  }
}

mestreSuissa();
```

O código de exemplo acima funciona em todos os browsers, porque, por trás dos panos, o JavaScript faz o hoisting da função interna para a parte superior da função externa.

## Closure

Closures (fechamentos) são funções que se referem a variáveis livres (independentes).

Em outras palavras, a função definida no closure "lembra" do ambiente em que ela foi criada.
Vamos começar falando de Closure analisando este exemplo simples:

```js
function suissa() {
    var breja = "sopa";
    function beber() {
        console.log(breja);
    }
    beber();
}
suissa(); // Saída: sopa
```

O código acima, é um exemplo de escopo funcional: No JavaScript, o escopo de uma variável é definida pela sua localização dentro do código, e, as funções que encontram-se dentro de uma função tem total acesso à variáveis declaradas fora de seus escopos.

No exemplo a cima temos uma função definida dentro de outra função. A função interna utiliza de parâmetros e variáveis da função externa… basicamente, este é o conceito de closure.
 
```js
function suissa() {
    var breja = "sopa";
    function beber() {
        console.log(breja);
    }
    return beber();
}
var bebe = suissa();
bebe(); // Saída: sopa
```

Se você rodar este código o mesmo terá exatamente o mesmo efeito que o do exemplo anterior.

Nota: A função interna tem acesso às variáveis locais, mesmo depois de a função exterior retornar.



	
## Variável Global

Uma variável pode ser global ou local.

Quando usada fora de uma função ela é global, isto é, pode ser usada dentro das funções, se na mesma função não ter sido antes declarada outra variável com o mesmo nome.

Dentro das funções as variáveis declaradas são locais, isto é, só são acessíveis dentro da função onde foram declaradas. As variáveis locais têm de ser obrigatoriamente declaradas antes de sofrerem quaisquer atribuições de valores. Se declarar uma variável dentro duma função com igual nome de uma variável global, a variável global deixa de estar acessível após a declaração.

## Variável por parâmetro

O termo parâmetro muitas vezes é utilizado como sinónimo de argumento, mas geralmente utiliza-se "parâmetros" quando se faz referência às variáveis situadas na assinatura de um método ou função e "argumentos" aos valores atribuídos a esses parâmetros.

A maioria dos programadores utiliza estes termos sem distinção de significado. Na prática, não é necessário distinguir as diferenças entre os dois termos para que a descrição de um código esteja correta.

## Instanciação usando uma IIFE

Immediately-Invoked Function Expression (IIFE) são funções auto-executáveis.
Porquê utilizar? Uma IIFE remove variáveis do escopo global. Isso nos ajuda a previnir que funções e variáveis estejam disponíveis mais tempo do que esperado no escopo global, o que ajuda a evitar colisões de variáveis.

Quando nosso código é minificado e empacotado em um único arquivo para implantação em um servidor de produção, poderiamos ter colisão de variáveis e muitas variáveis globais. Um IIFE protege contra ambos, fornecendo escopo de variáveis para cada arquivo.

Vejamos:

```js
//não há variáveis globaiss deixadas para trás 

// Logger.js 
(função ()
    {'use strict';

    angular
        .module ('app')
        .factory ("logger", logger);

    function  logger () {}
}) ();

// Storage.js 
(função ()
    {'use strict';

    angular
        .module ('app')
        .factory ('armazenamento', armazenamento);

    function  armazenamento () {}
}) ();
```

Nota: Um IIFE impede que nossos testes alcancem membros privados, como expressões regulares ou funções auxiliares que são bons e geralmente utilizados para testes unitários.

## Fontes

* http://www.i-avington.com/Posts/Post/javascript-hoisting-firefox-ifthen-statements
* http://geniuscarrier.com/javascript-closure/
* http://mariooliveira.info/aulas-programacao/javascript-aula03-identificadores.html
* https://pt.wikipedia.org/wiki/Par%C3%A2metro_(ci%C3%AAncia_da_computa%C3%A7%C3%A3o)
* https://github.com/johnpapa/angular-styleguide
