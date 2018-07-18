# Tipos (básicos)

O TypeScript fornece alguns tipos primitivos para se trabalhar. Para tipar um valor, usa-se a seguinte sintaxe:

```typescript
variavel: tipo = {valor}

// Por exemplo:
const myVariable: string = 'Content'
```

Funções e seus parâmetros também podem ser tipados. Veja abaixo:

```typescript
function myFunction (arg1: string, arg2: number): string {
  return `Hello, world! ${arg1} | ${arg2.toString()}`
}
```

### Índice

- [Booleano (`boolean`)](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#booleano-boolean);
- [Número (`number`)](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#n%C3%BAmero-number);
- [Array (`array`)](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#array-array);
- [Tupla](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#tupla);
- [Nunca (`never`)](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#nunca-never);
- [Qualquer (`any`)](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#qualquer-any);
- [Void (`void`)](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#void-void);
- [Nulo e Indefinido (`null` e `undefined`)](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#nulo-e-indefinido-null-e-undefined);
- [Objeto (`object`)](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#objeto-object);
- [Apêndice: Asserção de Tipos](https://github.com/lffg/code-refs/blob/master/TypeScript/001-tipos.md#ap%C3%AAndice-asser%C3%A7%C3%A3o-de-tipos).

## Booleano (`boolean`)

O tipo `boolean` representa um valor verdadeiro/falso. Abaixo encontra-se um exemplo de seu uso:

```typescript
const isActive: boolean = false
```

## Número (`number`)

O tipo `number` representa um valor numérico, podendo ser inteiro ou decimal (float). Valores binários e hexadecimais também são suportados, conforme aponta a [documentação](https://www.typescriptlang.org/docs/handbook/basic-types.html#number). Abaixo encontra-se um exemplo de uso:

```typescript
const intVal: number = 157
const floatVal: number = 3.14
```

## Array (`array`)

O tipo `array` representa um array em JavaScript. Existem duas formas para se tipar um `array`, conforme exeplificado abaixo:

```typescript
const myFirstArray: number[] = [1, 2, 3]
const mySecondArray: Array<number> = [1, 2, 3]
```

**Nota**: Como é possível notar acima, diferentemente do JavaScript, os `array`s em TypeScript só aceitam os valores que foram apontados na sua tipagem, logo, o exemplo abaixo irá mostrar um erro:

```typescript
const myWrongArray: number[] = [1, 2 '3'] // ERRO! '3' é uma string em um array que só deve conter números
```

## Tupla

**Perâmbulo**: Este tipo não está presente no JavaScript.

As tuplas são, em tese, `array`s com tamanho e tipos limitados. Veja o exemplo abaixo:

```typescript
const myTuple: [number, string, string] = [157, 'bala', ':p']
```

**Nota**: Como [apontado na documentação](https://www.typescriptlang.org/docs/handbook/basic-types.html#tuple), quando um elemento fora dos índices iniciais for acessado, um tipo _união (`union`)_ será retornado:

> When accessing an element outside the set of known indices, a union type is used instead [...]

## Nunca (`never`)

**Perâmbulo**: Este tipo não está presente no JavaScript.

Geralmente o tipo `never` é atribuido à funções que jamais retornarão um valor ou alcançaram o seu final, por exemplo, em _loops_ infinitos ou quando exceções são lançadas. Veja o exemplo abaixo:

```typescript
function error (message: string = ''): never {
  throw new Error(message)

  // Essa função nunca chegará a esse ponto, logo, como não retornou
  // nenhum valor anteriormente, pode ser atribuída ao tipo `never`.
}
```

## Qualquer (`any`)

O tipo `any` aceita qualquer outro tipo em seu valor, exceto `never`, conforme [apontado na documentação](https://www.typescriptlang.org/docs/handbook/basic-types.html#tuple).

Exemplo do uso do tipo `any`:

```typescript
const myFirstVariable: any = 'Olá, mundo!'
const mySecondVariable: any = 157
```

Geralmente usado para fornecer uma integração mais fácil com códigos JavaScript já existentes.

## Void (`void`)

O tipo `void`, geralmente atribuído à funções, é o oposto de `any`, isto é, oposto a qualquer outro tipo. Em outras palavras, o tipo `void` está associado à ausência de qualquer outro tipo, até mesmo `null` ou `undefined` — que são considerado tipos.

Veja abaixo um exemplo de uma função que não retorna **nada**, recebendo, portando, o tipo `void`:

```typescript
function main (): void {
  alert(1)

  // Note que a função não retorna nenhum valor, logo, pode receber o tipo `void`.
}
```

## Nulo e Indefinido (`null` e `undefined`)

Os tipos `null` e `undefined` representam valores nulos e indefinidos, respectivamente.  
Estes valores têm as mesmas características de `null` e `undefined` no JavaScript.

Exemplo:

```typescript
const nullValue: null = null
const undefinedValue: undefined = undefined
```

**Nota**: É importante frisar que `null` e `undefined` são **subtipos** de todos os outros tipos — como `string` ou `number`, por exemplo. Desse modo, você pode atribuir o tipo `null` em um número, por exemplo.

## Objeto (`object`)

O tipo `object` representa um objeto.  
É importante frisar que não é possível ler propriedades do tipo `object`, já que o TypeScript não as reconhece.

Por exemplo:

```typescript
const myObject: object = {
  name: 'Luiz Felipe',
  age: 15
}

alert(myObject.name) // ERRO! Property 'name' does not exist on type 'object'.
```

De modo geral, o tipo `object` não se faz muito usável, já que existe a possibilidade de criar tipos personalizados e interfaces, que são, basicamente, objetos pré-definidos. _Este conteúdo será visto mais à frente._

## Apêndice: Asserção de Tipos

Asserção de tipos é um importante recurso em que você tem mais conhecimento do que o compilador em relação ao tipo de um determinado elemento, por exemplo:

```typescript
const myString: any = prompt('What\'s your name?')
const length: number = (myString as string).length
alert(length.toString())
```

Note acima que a sintaxe utilizada para efetuar a asserção de tipos foi a seguinte:

```typescript
(variable as type)

// Por exemplo:
const myString = (myOtherVariable as string)
```

Mas também pode se utilizar a outra sintaxe:

```typescript
(<type>variable)

// Por exemplo:
const myString = (<string>myOtherVariable)
```

Observações Importantes:

1. As asserções de tipo **não provém nenhuma conversão de tipos**. São usadas somente pelo compilador, não afetando o código JavaScript final.
1. Quando usado em conjunto com o **JSX**, a segunda sintaxe (`(<type>variable)`) para asserção de tipos **não deve ser usada**. Nesse caso, prefira sempre usar a primeira sintaxe (`(variable as type)`).
