# Tipos (básicos)

O TypeScript fornece alguns tipos primitivos para se trabalhar. Para tipar um valor, usa-se a seguinte sintaxe:

```typescript
{variavel}:<tipo> = {valor}
```

Por exemplo:

```typescript
const myVariable: string = 'Content'
```

Funções e seus parâmetros também podem ser tipados. Veja abaixo:

```typescript
function myFunction (arg1: string, arg2: number): string {
  return `Hello, world! ${arg1} | ${arg2.toString()}`
}
```

## Booleanos `boolean`

O tipo `boolean` representa um valor verdadeiro/falso. Abaixo encontra-se um exemplo de seu uso:

```typescript
const isActive: boolean = false
```

## Números `number`

O tipo `number` representa um valor numérico, podendo ser inteiro ou decimal (float). Valores binários e hexadecimais também são suportados, conforme aponta a [documentação](https://www.typescriptlang.org/docs/handbook/basic-types.html#number). Abaixo encontra-se um exemplo de uso:

```typescript
const intVal: number = 157
const floatVal: number = 3.14
```

## Arrays `array`

O tipo `array` representa um array em JavaScript. Existem duas formas para se tipar um `array`, conforme exeplificado abaixo:

```typescript
const myFirstArray: number[] = [1, 2, 3]
const mySecondArray: Array<number> = [1, 2, 3]
```

**Nota**: Como é possível notar acima, diferentemente do JavaScript, os `array`s em TypeScript só aceitam os valores que foram apontados na sua tipagem, logo, o exemplo abaixo irá mostrar um erro:

```typescript
const myWrongArray: number[] = [1, 2 '3'] // '3' é uma string em um array que só deve conter números
```

## Tuplas


