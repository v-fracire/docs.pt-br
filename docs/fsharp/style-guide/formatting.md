---
title: 'Código F # diretrizes de formatação'
description: 'Aprenda diretrizes para a formatação de código F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 9c6e80509e9a5654e6514674d38c02e2a6b44e37
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935931"
---
# <a name="f-code-formatting-guidelines"></a>Código F # diretrizes de formatação

Este artigo oferece diretrizes para formatar seu código para que seu código F # é:

* Geralmente é visto como mais legível
* Está de acordo com as convenções aplicadas por ferramentas de formatação no Visual Studio e outros editores
* Semelhante a outro código online

Essas diretrizes se baseiam [um guia abrangente para convenções de formatação do F #](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) pela [Anh-Dung Phan](https://github.com/dungpa).

## <a name="general-rules-for-indentation"></a>Regras gerais para recuo

F # usa o espaço em branco significativo por padrão. As diretrizes a seguir destinam-se a fornecer orientação sobre como manipular alguns desafios que isso pode impor.

### <a name="using-spaces"></a>Uso de espaços

Quando recuo é necessário, você deve usar espaços, tabulações não. Pelo menos um espaço é necessário. Sua organização pode criar padrões de codificação para especificar o número de espaços a serem usados para recuo; dois, três ou quatro espaços de recuo em cada nível em que ocorre o recuo é típico.

**Recomendamos 4 espaços por recuo.**

Dito isso, o recuo dos programas é uma questão subjetiva. Variações são Okey, mas é a primeira regra que você deve seguir *consistência de recuo*. Escolha um estilo de recuo de geralmente aceito e usá-lo sistematicamente em toda a sua base de código.

## <a name="formatting-blank-lines"></a>Formatação de linhas em branco

* Separado nível superior função e classe definições com duas linhas em branco.
* As definições de método dentro de uma classe são separadas por uma única linha em branco.
* Linhas em branco extra podem ser usadas (com moderação) para separar grupos de funções relacionadas. Linhas em branco podem ser omitidas entre um monte de linhas relacionadas (por exemplo, um conjunto de implementações fictícias).
* Use linhas em branco em funções, com moderação, para indicar seções lógicas.

## <a name="formatting-comments"></a>Comentários de formatação

Geralmente prefiro vários comentários de barra dupla ao longo de comentários do bloco de estilo de ML.

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

Comentários embutidos devem colocar em maiuscula a primeira letra.

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>Convenções de nomenclatura

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>Use camelCase para valores de limite de classe, expressão ligada à e padrão de associação e funções

É comum e aceitos F # estilo use camelCase para todos os nomes associados como variáveis locais ou em correspondências de padrões e as definições de função.

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

Funções associadas a localmente em classes também devem usar camelCase.

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a>Use camelCase para funções públicas de associação de módulo

Quando uma função associada de módulo fizer parte de uma API pública, ele deve usar camelCase:

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>Use camelCase para funções e os valores de limite de módulo internos e privados

Use camelCase para valores de associação de módulo privados, incluindo o seguinte:

* Funções ad hoc em scripts

* Valores que compõem a implementação interna de um módulo ou tipo

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a>Use camelCase para parâmetros

Todos os parâmetros devem usar camelCase de acordo com as convenções de nomenclatura do .NET.

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a>Usar PascalCase para módulos

Todos os módulos (nível superior, internos, privados, aninhados) devem usar PascalCase.

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a>Usar PascalCase para declarações de tipo, membros e rótulos

Classes, interfaces, estruturas, enumerações, delegados, registros e uniões discriminadas devem ser nomeadas com PascalCase. Os membros dentro de tipos e rótulos para registros e uniões discriminadas também devem usar PascalCase.

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a>Usar PascalCase para construções intrínsecas para o .NET

Namespaces, exceções, eventos e projeto /`.dll` nomes também devem usar PascalCase. Não apenas isso faz o consumo de outras linguagens .NET mais naturais para os consumidores, também é consistente com as convenções de nomenclatura do .NET que você provavelmente encontrará.

### <a name="avoid-underscores-in-names"></a>Evite sublinhados em nomes

Historicamente, algumas bibliotecas do F # usaram sublinhados em nomes. No entanto, isso não é mais amplamente é aceito, em parte porque ele estiver em conflito com as convenções de nomenclatura do .NET. Dito isso, alguns programadores em F # usam sublinhados intensamente, em parte por razões históricas e tolerância e respeito é importante. No entanto, lembre-se de que o estilo é geralmente disliked por outras pessoas que têm uma opção sobre se deve usá-lo.

Algumas exceções inclui interoperar com componentes nativos, onde os sublinhados são muito comuns.

### <a name="use-standard-f-operators"></a>Usar operadores de padrão F #

Os operadores a seguir são definidos na biblioteca padrão do F # e devem ser usados em vez de definir equivalentes. Usar esses operadores é recomendável como ele tende a tornar o código mais legível e expressões idiomáticas. Os desenvolvedores com experiência em OCaml ou outra linguagem de programação funcional talvez esteja acostumados a idiomas diferentes. A lista a seguir resume os operadores de F # recomendados.

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>Use a sintaxe de prefixo para genéricos (`Foo<T>`) em preferência a sintaxe de sufixo (`T Foo`)

F # herda de ambos os o estilo de ML sufixo de nomeação de tipos genéricos (por exemplo, `int list`), bem como o prefixo de estilo do .NET (por exemplo, `list<int>`). Preferir o estilo de .NET, exceto para quatro tipos específicos:

1. Para listas do F #, use a forma pós-fixada: `int list` em vez de `list<int>`.
2. Para opções de F #, use a forma pós-fixada: `int option` em vez de `option<int>`.
3. Para matrizes F #, use o nome sintático `int[]` em vez de `int array` ou `array<int>`.
4. Para as células de referência, use `int ref` em vez de `ref<int>` ou `Ref<int>`.

Para todos os outros tipos, use o formulário de prefixo.

## <a name="formatting-tuples"></a>As tuplas de formatação

Uma instanciação de tupla deve estar entre parênteses e vírgulas dentro de delimitadores devem ser seguidas por um único espaço, por exemplo: `(1, 2)`, `(x, y, z)`.

Normalmente, ela é aceita para omitir os parênteses na correspondência de padrão de tuplas:

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a>Formatação discriminada declarações de união

Recuar `|` na definição de tipo por 4 espaços:

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a>Formatação de uniões discriminadas

Uniões discriminadas instanciado divididas em várias linhas deve fornecer os dados contidos um novo escopo com recuo:

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

O parêntese de fechamento também pode ser em uma nova linha:

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a>Declarações de registro de formatação

Recuar `{` no tipo de definição por 4 espaços e iniciar a lista de campos na mesma linha:

```fsharp
// OK
type PostalAddress =
    { Address : string
      City : string
      Zip : string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address : string
    City : string
    Zip : string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
// Unusual in F#
type PostalAddress =
    { 
        Address : string
        City : string
        Zip : string
    }
```

Colocando o token de abertura na mesma linha e o token de fechamento em uma nova linha também é bom, mas lembre-se de que você precisa usar o [sintaxe detalhada](../language-reference/verbose-syntax.md) para definir os membros (o `with` palavra-chave):

```fsharp
//  OK, but verbose syntax required
type PostalAddress = { 
    Address : string
    City : string
    Zip : string
} with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
```

## <a name="formatting-records"></a>Formatação de registros

Registros curtos podem ser escritos em uma linha:

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

Os registros que são mais longas devem usar novas linhas para rótulos:

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

Também é bom colocar o token de abertura na mesma linha e o token de fechamento em uma nova linha:

```fsharp
let rainbow = {
    Boss1 = "Jeffrey"
    Boss2 = "Jeffrey"
    Boss3 = "Jeffrey"
    Boss4 = "Jeffrey"
    Boss5 = "Jeffrey"
    Boss6 = "Jeffrey"
    Boss7 = "Jeffrey"
    Boss8 = "Jeffrey"
    Lackeys = ["Zippy"; "George"; "Bungle"]
}
```

As mesmas regras se aplicam para elementos list e array.

## <a name="formatting-lists-and-arrays"></a>Formatando listas e matrizes

Gravar `x :: l` com espaços em torno de `::` operador (`::` é um operador de infixo, portanto, cercado por espaços) e `[1; 2; 3]` (`;` é um delimitador, portanto, seguido por um espaço).

Sempre use pelo menos um espaço entre os dois operadores semelhante de chave distintos. Por exemplo, deixar um espaço entre um `[` e um `{`.

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

Listas e matrizes que são dividem em várias linhas seguem uma regra semelhante como registros:

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a>Formatação se expressões

Recuo de condicionais depende dos tamanhos das expressões que compõem-los. Se `cond`, `e1` e `e2` são curto, simplesmente gravá-los em uma única linha:

```fsharp
if cond then e1 else e2
```

Se qualquer um dos `cond`, `e1` ou `e2` são mais tempo, mas não de várias linhas:

```fsharp
if cond
then e1
else e2
```

Se qualquer uma das expressões são várias linhas:

```fsharp
if cond then
    e1
else
    e2
```

Várias condições com `elif` e `else` são recuadas no mesmo escopo que o `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>Construções de correspondência de padrão

Use um `|` para cada cláusula de uma correspondência com nenhum recuo. Se a expressão for curta, você pode considerar usando uma única linha, se cada subexpressão também é simple.

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

Se a expressão à direita da seta para a correspondência for muito grande, mova-o para a seguinte linha, recuado em uma etapa do `match` / `|`.

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

Correspondência de padrões de funções anônimas, começando pelo `function`, não geralmente deve Recuar muito longe. Por exemplo, é bom recuar um escopo da seguinte maneira:

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

Correspondência de padrão de funções definidas pelo `let` ou `let rec` deve ser recuados 4 espaços após a inicialização do `let`, mesmo se `function` palavra-chave é usada:

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

Não recomendamos alinhando setas.

## <a name="formatting-trywith-expressions"></a>Formatação de try / com expressões

Correspondência de padrão em que o tipo de exceção deve ser recuado no mesmo nível como `with`.

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a>Aplicativo de parâmetro de função de formatação

Em geral, a maioria dos aplicativos de parâmetro de função é feito na mesma linha.

Se você quiser aplicar os parâmetros para uma função em uma nova linha, recuo-los por um escopo.

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

As mesmas diretrizes se aplicam para as expressões lambda como argumentos de função. Se o corpo de uma expressão lambda, o corpo pode ter outra linha, recuada de acordo com um escopo

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

No entanto, se o corpo de uma expressão lambda é a mais de uma linha, considere fatorá-lo em uma função separada em vez de ter uma construção de várias linha aplicada como um único argumento para uma função.

### <a name="formatting-infix-operators"></a>Operadores infixos de formatação

Operadores separados por espaços. Óbvias exceções a essa regra são as `!` e `.` operadores.

Expressões de infixo são Okey para o antecipação da linha na mesma coluna:

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>Formatação de operadores de pipeline

Pipeline `|>` operadores devem ficar sob eles operam em expressões.

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a>Formatação de módulos

Em um módulo local deve ser recuado em relação ao módulo, mas o código em um módulo de nível superior não deve ser recuado. Não tem elementos do Namespace a ser recuado.

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a>Formatação de expressões de objeto e interfaces

Expressões de objeto e as interfaces devem ser alinhados da mesma forma com `member` sendo recuado após 4 espaços.

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a>Formatação de espaço em branco em expressões

Evite espaço em branco estranhos em expressões de F #.

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

Argumentos nomeados também não devem ter espaço em torno de `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
