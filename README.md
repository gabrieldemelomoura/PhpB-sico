## Básico ¶
As variáveis no PHP são representadas por um cifrão ($) seguido pelo nome da variável. Os nomes de variável são sensíveis a maiúsculas e minúsculas.

Um nome válido de variável inicia com uma letra (A-Z, a-z, ou os bytes de 128 a 255) ou sublinhado, seguido de qualquer número de letras, números ou sublinhados. Em uma expressão regular, poderia ser representado assim: ^[a-zA-Z_\x80-\xff][a-zA-Z0-9_\x80-\xff]*$
##
Nota: O PHP não suporta nomes de variáveis em Unicode, porém, algumas codificações de caracteres (tal como UTF-8) codificam os caracteres de uma forma que todos os bytes de um caractere multi-byte fiquem dentro da faixa permitida, fazendo com que o nome da variável seja válido.

Nota: $this é uma variável especial que não pode ser atribuída. Antes do PHP 7.1.0, atribuição indireta (por exemplo, usando variáveis variáveis) era possível.

Dica
Veja também o Guia de nomenclatura em espaço de usuário.
##
*Exemplo #1 Nomes de variáveis válidos*

*<?php

$var = 'Bob';

$Var = 'Joe';

echo "$var, $Var";      // exibe "Bob, Joe"

$_4site = 'not yet';    // válido; começa com um sublinhado

$täyte = 'mansikka';    // válido; 'ä' é um caracter ASCII (extendido) 228

?>
##
*Exemplo #2 Nomes de variáveis inválidos*

|*<?php

$4site = 'not yet';      // inválido; começa com um número
##
O PHP aceita uma sequência de quaisquer bytes como um nome de variável. Nomes de variáveis que não seguem as regras de nomenclatura mencionadas acima só podem ser acessadas dinamicamente no momento da execução. Consulte a seção sobre variáveis variáveis para informação sobre como acessá-las.

*Exemplo #3 Acessando nomes obscuros de variáveis*

<?php

${'invalid-name'} = 'bar';

$name = 'invalid-name';

echo ${'invalid-name'}, " ", $$name;

?>

*O exemplo acima produzirá:*

bar bar

Por padrão, as variáveis são sempre atribuídas por valor. Isto significa que ao atribuir uma expressão a uma variável, o valor da expressão original é copiado integralmente para a variável de destino. Isto significa também que, após atribuir o valor de uma variável a outra, a alteração de uma destas variáveis não afetará a outra. Para maiores informações sobre este tipo de atribuição, veja o capítulo em Expressões.

O PHP também oferece um outro meio de atribuir valores a variáveis: atribuição por referência. Isto significa que a nova variável simplesmente referencia (em outras palavras, "torna-se um apelido para" ou "aponta para") a variável original. Alterações na nova variável afetam a original, e vice-versa.

Para atribuir por referência, simplesmente adicione um e-comercial (&) na frente do nome da variável que estiver sendo atribuída (variável de origem). Por exemplo, o trecho de código abaixo exibe 'My name is Bob' duas vezes:

|*<?php

$foo = 'Bob';             // Atribui o valor 'Bob' a variável $foo

$bar = &$foo;              // Referecia $foo através de $bar.

$bar = "My name is $bar";  // Altera $bar...

echo $bar;

echo $foo;                 // $foo é alterada também.

?>*
##
Uma observação importante a se fazer, é que somente variáveis podem ser atribuídas por referência.

*<?php

$foo = 25;
$bar = &$foo;      // Esta atribuição é válida.

$bar = &(24 * 7);  // Inválido; referencia uma expressão sem nome.


function test()

{

   return 25;

}

$bar = &test();    // Inválido porque test() não retorna uma variável por referência.

?>*
##
**Não é necessário declarar variáveis no PHP, contudo é uma ótima prática. Acessar uma variável indefinida resultará em um E_WARNING (antes do PHP 8.0.0, E_NOTICE). Uma variável indefinida tem um valor padrão de null. O construtor de linguagem isset() pode ser usado para detectar se uma variável já foi inicializada.**
##

*Exemplo #4 Valor padrão de uma variável não inicializada*

*<?php

// Variável não definida E não referenciada (sem contexto de uso);

var_dump($unset_var);

?>*

*O exemplo acima produzirá:*

*Warning: Undefined variable $unset_var in ...
NULL
O PHP permite autovivificação de array (criação automática de novos arrays) a partir de uma variável indefinida. Anexar um elemento a uma variável indefinida criará um novo array e não gerará um alerta.*
##
Exemplo #5 Autovivificação de um array a partir de uma variável indefinida

*<?php

$unset_array[] = 'value'; // Não gera um alerta.

?>

## Aviso
**Depender do valor padrão de uma variável não inicializada é problemático ao incluir um arquivo em outro que usa o mesmo nome de variável.**

Uma variável pode ser destruída usando o construtor de linguagem unset().

Para obter informações sobre funções relacionadas a variáveis, consulte a Referência de funções variáveis.

Melhore Esta Página
Aprenda Como Melhorar Esta Página • Envie uma Solicitação de Modificação • Reporte um Problema
＋adicione uma nota
Notas Enviadas por Usuários (em inglês) 1 note
up
down
6anisgazig at gmail dot com ¶4 years ago
clear concept of variable declaration rules and classification 

variable declaration rules:

1.start with dollar sign($)

2.first letter of variable name comes from a-zA-z_

3.next letters of variable name comes from a-zA-Z0-9_

4.no space,no syntex

classification of variables:

Variable are mainly Two types

1.Predefined Variable

2.User Define Variable


Predefined Variable

There are 12 predefined variables in php 8

1.$GLOBALS

2.$_SERVER

3.$_REQUEST

4.$_FILES

5.$_ENV

6.$_SESSION

7.$_COOKIE

8.$_GET

9.$_POST

10.$http_response_header

11.$argc

12.$argv


User Define Variable

User Define variable are 3 types

1.variable scope

2.variable variables

3.reference variable


Variable Scope

variable scope are 3 types

1.local scope

2.global scope

3.static variable
