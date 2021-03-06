Guia de estilo de código
==================

Este guia estende e expande sobre a [PSR-1][], os padrões básicos de codificação.

A intenção deste guia é reduzir a fricção cognitiva durante a codificação de diferentes autores. Ele faz isso por enumerar um conjunto compartilhado de regras e
expectativas sobre como formatar o código PHP.

As regras de estilo daqui são derivadas de semelhanças entre membros de vários projetos. Quando vários autores colaboram em vários projetos, ajuda a ter um conjunto de diretrizes para serem usadas em todos os projetos. Assim, o benefício deste guia não está nas regras em si, mas sim no compartilhamento dessas regras.

[PSR-0]: https://github.com/enricopereira/PSR_PT-BR/blob/master/PSR-0.md
[PSR-1]: https://github.com/enricopereira/PSR_PT-BR/blob/master/PSR-1.md


1. Visão geral
-----------

- Código deve seguir a [PSR-1][].

- Código deve usar 4 espaços para identação ao invés de tabs.

- Não deve existir um limite rigoroso no comprimento das linhas; o limite suave deve ser de 120 caracteres; linhas devem ser de 80 caracteres ou menos.

- Deve ter uma linha em branco depois da declaração de `namespace` e outra linha após o bloco das declarações de `use`.

- A abertura de chaves para classes deve estar na próxima linha e o fechamento na próxima linha após o corpo.

- A abertura de chaves para métodos deve estar na próxima linha e o fechamento na próxima linha após o corpo.

- Visibilidade deve ser declarada em todas as propriedades e métodos; `abstract` e `final` deve ser declarada antes da visibilidade; `static` após a visibilidade.

- Palavras-chaves das estruturas de controle devem ter um espaço após elas; chamadas de métodos e funções não devem.

- A abertura de chaves para classes deve estar na mesma linha e o fechamento na próxima linha após o corpo.

- A abertura de parênteses para estruturas de controle não devem ter um espaço após ela e também não deve ter um espaco antes do fechamento dos parênteses.

### 1.1. Exemplo

Este exemplo engloba algumas das regras abaixo como uma visão geral:

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // corpo do método
    }
}
```

2. Geral
----------

### 2.1 Padrão básico de codificação

Código deve seguir todas as regras descritas na [PSR-1][].

### 2.2 Arquivos

Todos os arquivos PHP deve usar o fim da linha Unix LF (linefeed).

Todos os arquivos PHP devem terminar com uma única linha em branco.

A tag de fechamento `?>` deve ser omitida em arquivos que só contém código PHP.

### 2.3. Linhas

Não deve existir um limite rigoroso no comprimento das linhas.

O limite suave deve ser de 120 caracteres; verificadores de estilo automatizados devem avisar mas não devem assinalar como erro no limite suave.

Linhas não devem ser maiores do que 80 caracteres; linhas longas devem ser quebradas em linhas com menos de 80 caracteres cada.

Não deve ter linhas em branco no final de linhas não em branco.

Linhas em branco podem ser adcionadas para aumentar a legibilidade e para indicar blocos relacionados de código.

Não deve ter mais de um comando por linha.

### 2.4. Indentação

Código deve usar uma identação de 4 espacos, e não deve usar tabs para identação.

> Note bem: Usando apenas espaços, e não misturando espaços com tabs, ajuda a evitaar
> problemas com diffs, patches, history e annotations. O uso de espaços
> também torna mais fácil para inserir sub-identação.

### 2.5. Palavras-chave e as constantes True/False/Null

[Palavras-chave][] do PHP devem estar em letra minúscula.

As constantes do PHP `true`, `false` e `null` devem estar em letra minúscula.

[Palavras-chave]: http://php.net/manual/pt_BR/reserved.keywords.php



3. Namespace e declarações de 'use'
---------------------------------

Quando presente, deve haver uma linha em branco depois da declaração da `namespace`.

Quando presente, todas as declarações `use` devem vir depois da declaração da `namespace`.

Deve haver uma palavra-chave `use` para cada declaração.

Deve haver uma linha em branco após o bloco de declarações `use`.

Por exemplo:

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... código PHP adcional ...

```


4. Classes, propriedades e métodos
-----------------------------------

O termo "classes" é uma referência para todas as classes, interfaces e traits.

### 4.1. Extends e Implements

As palavras-chave `extends` e `implements` devem ser declaradas na mesma linha do nome da classe.

A abertura de chaves para a classe deve vir na próxima linha; o fechamento das chaves deve vir na linha seguinte do fechamento do corpo.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constantes, propriedades e métodos
}
```

A lista de `implements` pode ser divida em múltiplas linhas, onde cada linha subsequente é identada uma vez. Quando fizer isto, o primeiro item na lista deve estar na próxima linha e deve haver uma interface por linha.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constantes, propriedades e métodos
}
```

### 4.2. Propriedades

Visibilidade deve ser declarada em todas as propriedades.

A palavra-chave `var` não deve ser utilizada para declarar uma propriedade.

Não deve haver mais de uma propriedade declarada por instrução.

Nome das propriedades não devem ser prefixados com um único undeline para indicar a visibilidade protegida ou privada.

Uma declaração de propriedade se parece com o seguinte:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3. Métodos

Visibilidade deve ser declarada em todos os métodos.

Nome dos métodos não devem ser prefixados com um único undeline para indicar a visibilidade protegida ou privada.

Nome dos métodos não devem ser declarados com um espaço após ao nome do método. A abertura de chave deve vir na próxima linha e o fechamento deve vir na linha seguinte do fechamento do corpo. Não deve haver um espaço depois da abertura dos parênteses e nem um espaço antes do fechamento dos parênteses.

Uma declaração de método se parece com o seguinte. Note a colocação dos
parênteses, vírgulas, espaços e chaves:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // corpo do método
    }
}
```

### 4.4. Argumentos dos métodos

Na lista de argumentos, não deve haver um espaço antes de cada vírgula e deve haver um espaço após cada vírtgula.

Argumentos de métodos com valores padrão deve vir no final da lista de argumentos.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // corpo do método
    }
}
```

Listas de argumentos podem ser dividas em múltiplas linhas, onde cada linha subsequente é identada uma vez. Quando fizer isto, o primeiro item na lista deve estar na próxima linha e deve haver um argumento por linha.

Quando a lista de argumento for dividida em múltiplas linhas, o fechamento de parênteses e a abertura de chaves devem ser colocadas na mesma linha com um espaço entre eles.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function umNomeDeMetodoMuitoLongo(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // corpo do método
    }
}
```

### 4.5. Palavras-chave `abstract`, `final`, e `static`

Quando presentes, as declarações `abstract` e `final` devem preceder a declaração da visibilidade.

Quando presente, a declaração `static` deve vir depois da declaração da visibilidade.

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // corpo do método
    }
}
```

### 4.6. Chamadas de métodos e funções

Quando fazemos uma chamada de método ou de função, não deve haver um espaço entre o método ou o nome da função e a abertura dos parênteses, não deve haver um espaço depois da abertura de parênteses e não deve haver um espaço antes do fechamento de parênteses. Na lista de argumentos não deve haver um espaço antes de cada vírgula e deve ter uma espaço depois de cada vírgula.

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```
Listas de argumentos podem ser dividas em múltiplas linhas, onde cada linha subsequente é identada uma vez. Quando fizer isto, o primeiro item na lista deve estar na próxima linha e deve haver um argumento por linha.

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

5. Estruturas de controle
---------------------

As regras gerais de estilo para estruturas de controle são as seguintes:

- Deve haver um espaço depois da palavra-chave da estrutura de controle
- Não deve haver um espaço depois da abertura de parênteses
- Não deve haver um espaço antes do fechamento de parênteses
- Deve haver um espaço entre o fechamento de parênteses e a abertura de chaves
- A estrutura do corpo deve ser identada uma vez
- O fechamento das chaves devem vir na próxima linha após o corpo

O corpo de cada estrutura deve ser delimitado por chaves. Isto padroniza como
as estruturas aparecem e reduz o risco de introdução de erros como novas linhas sejam adcionadas ao corpo.

### 5.1. `if`, `elseif`, `else`

Uma estrutura `if` se parece com o seguinte. Note a posição dos parênteses, espaços e chaves; e que `else` e `elseif` são na mesma linha do fechamento das chaves do corpo anterior.

```php
<?php
if ($expr1) {
    // if corpo
} elseif ($expr2) {
    // elseif corpo
} else {
    // else corpo;
}
```
A palavra-chave `elseif` deve ser usada ao invés de `elseif` de modo que todas as estruturas de controle pareçam uma única palavra.

### 5.2. `switch`, `case`

Uma estrutura `switch` se parece com o seguinte. Note a posição dos parênteses, espaços e chaves. A declaração `case` deve ser identada uma vez do `switch`, e a palavra-chave `break` (ou outra palavra-chave de finalização) deve ser identada no mesmo nível do corpo do `case`. Deve haver um comentário como
`// no break` quando "continuar" é intencional e não for um `case` com corpo vazio.

```php
<?php
switch ($expr) {
    case 0:
        echo 'Primeiro caso, com uma quebra';
        break;
    case 1:
        echo 'Segundo caso, sem uma quebra, continuando para o(s) caso(s) seguintes';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Quarto caso, return é usado para fazer a quebra ao invés de break';
        return;
    default:
        echo 'Caso padrão';
        break;
}
```


### 5.3. `while`, `do while`

Uma estrutura `while` se parece com o seguinte. Note a posição dos parênteses, espaços e chaves.

```php
<?php
while ($expr) {
    // estrutura
}
```

Igualmente, uma estrutura `do while` se parece com o seguinte. Note a posição dos parênteses, espaços e chaves.

```php
<?php
do {
    // estrutura;
} while ($expr);
```

### 5.4. `for`

Uma estrutura `for` se parece com o seguinte. Note a posição dos parênteses, espaços e chaves.

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // for corpo
}
```

### 5.5. `foreach`

Uma estrutura `foreach` se parece com o seguinte. Note a posição dos parênteses, espaços e chaves.

```php
<?php
foreach ($iterable as $key => $value) {
    // foreach corpo
}
```

### 5.6. `try`, `catch`

Um bloco `try catch` se parece com o seguinte. Note a posição dos parênteses, espaços e chaves.

```php
<?php
try {
    // try corpo
} catch (FirstExceptionType $e) {
    // catch corpo
} catch (OtherExceptionType $e) {
    // catch corpo
}
```

6. Closures
-----------

Closures devem ser declaradas com um espaço depois da palavra-chave `function` e um espaço antes e depois da palavra-chave `use`.

A abertura da chave deve vir na mesma linha e o fechamento da chave deve vir na próxima linha após o corpo.

Não deve haver um espaço após a abertura de parênteses de uma lista de argumentos ou uma lista de variáveis, e não deve haver um espaço antes do fechamento dos parênteses da lista de argumentos ou de variáveis.

Na lista de argumentos e na lista de variáveis, não deve haver um espaço antes de cada vírgula e deve haver um espaço depois de cada vírgula.

Argumentos de uma Closure com valores padrão devem vir depois da lista de argumentos.

Uma declaração de closure se parece com o seguinte. Note a posição de parênteses, vírgulas, espaços e chaves:

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // corpo
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // corpo
};
```

Listas de argumentos e de variáveis podem ser divididas em múltiplas linhas, onde cada linha subsequente é identada uma vez. Quando fizer isto, o primeiro item na lista deve estar na próxima linha e deve haver um argumento ou variável por linha.

Quando a lista de argumento for dividida em múltiplas linhas, o fechamento de parênteses e a abertura de chaves devem ser colocadas na mesma linha com um espaço entre eles.

Os seguintes são exemplos de closure com e sem listas de argumentos e variáveis divididas em múltiplas linhas.

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // corpo
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // corpo
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // corpo
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // corpo
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // corpo
};
```

Note que as regras de formatação também se aplicam quando o fechamento é usado diretamente em uma chamada de função ou método como um argumento.

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // corpo
    },
    $arg3
);
```


7. Conclusão
--------------

Há muitos elementos de estilo e práticas intencionalmente omitidos por este guia. Estes incluem, mas não estão limitados para:

- Declaração de variáveis globais e constantes globais

- Declaração de funções

- Operadores e atribuição

- Alinhamento entre linhas

- Comentários e blocos de documentação

- Prefixos e sufixos de nomes de classes

- Boas práticas

Futuras recomendações podem ser revisadas e pode se estender este guia para abordar outros elementos de estilo e prática.