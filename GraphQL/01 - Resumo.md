# Notas — GraphQL

Minhas notas sobre a especificação "GraphQL".  
Documento escrito no dia 31 de dezembro de 2018.

---

## 01. Introdução

Linguagem de query para API's e um runtime no lado do servidor para executar essas queries.  
Uma API em GraphQL é criada definindo tipos (types) e campos (fields) nesses tipos.

---

## 02. _Queries_ e _Mutations_

De modo geral, uma API GraphQL é requisitar campos de um objeto em específico para o servidor. E isso é um dos pontos chaves dessa tecnologia. **Você recebe somente o que solicitou através da sua query.**

Um exemplo de query:

```graphql
{
  hero {
    name
  }
}
```

### Argumentos

Ao realizar uma query, também há a possibilidade de passar um argumento, se definido pelo esquema. Exemplo:

```graphql
{
  user(id: 4) {
    name
    email
  }
}
```

Também há a possibilidade de passar argumentos para _scalar types_, conforme é mostrado [no segundo exemplo, em código, desta sessão](https://graphql.github.io/learn/queries/#arguments).

### _Aliases_

Como o retorno de uma GraphQL combina com o nome da _query_, você não pode requisitar a mesma coisa mais de uma vez com diferentes argumentos:

```graphql
# Errado!
{
  user(id: 1) {
    name
  }
  user(id: 2) {
    name
  }
}
```

Para fazer isso, você **deve usar _aliases_**. Deste modo, corrigindo o exemplo acima, ficamos com:

```graphql
{
  user1: user(id: 1) {
    name
  }
  user2: user(id: 2) {
    name
  }
}
```

Para consultar exemplos e seus resultados, queira verificar [esta sessão](https://graphql.github.io/learn/queries/#aliases).

### _Fragments_

Em queries mais complexas, muitas vezes acabamos por repetir os campos que requisitamos em uma determinada consulta. Para saber mais, consulte [este exemplo](https://graphql.github.io/learn/queries/#fragments).

### Nome de Operação

Em todos os exemplos de queries anteriores, omitimos a palavra-chave `query` e o nome da consulta. De modo geral, é uma boa prática sempre nomear a operação, para deixarmos claro o que estamos fazendo.

Exemplo:

```graphql
query UserOneData {
  user(id: 1) {
    name
    lastName
  }
}
```

Note que depois da palavra-chave `query`, definimos um nome (_deve-se usar um nome customizado, de acordo com a query em que estamos realizando_) para a nossa operação.

Os **tipos** de operação disponíveis são:

- `query`
- `mutation`
- `subscription`

E descrevem o tipo de operação que estamos querendo fazer. O tipo de operação é **obrigatório**, exceto quando se usa a notação especial para **`query`**, conforme indicado acima.
