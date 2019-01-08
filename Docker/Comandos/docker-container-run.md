# `docker container run <nome da imagem>`

Roda um comando em específico em um novo container. Irá baixar a imagem se não existir.

## Opções:

#### `--rm`

Exemplo:

```shell
docker container run --rm <nome da imagem>
```

Roda um comando em específico em um novo container. A opção `--rm` faz com que ele seja removido automaticamente da lista de _containers_ (`docker container ls -a`) após ser finalizado.
