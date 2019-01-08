# `docker container run (...)`

Roda um comando em específico em um novo container. Irá baixar a imagem se não existir.
Após o `run`, **deve** se passar como argumento o nome da **imagem** a ser baixada, por exemplo:

```shell
docker container run <image-name>
```

## Opções:

#### `--rm`

Remove automaticamente o _container_ após ser finalizado e sair do processo. Isso irá impedir que o _container_ seja exibido na lista de _containers_ (`docker container run ls -a`)_ após ser finalizado.

#### `--tty` (`-t`)

Aloca um pseudo terminal para ser utilizado.

#### `--interactive` (`-i`)

Abre no modo interativo. De acordo com a ajuda:

> _Keep STDIN open even if not attached._

#### `--name`

Atribui um nome customizado para o _container_ que está sendo criado. Isso é útil para que este mesmo _container_ possa ser reutilizado no futuro.

Exemplo:
```shell
docker container run --name <container-name> <image-name>
```
