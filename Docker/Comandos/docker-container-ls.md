# `docker-container-ls`

Lista todos os _containers_.  
Também pode ser executado com os _aliases_ `ls`, `ps`, `list`.

## Opções:

#### `--all` (`-a`)

Mostra todos os _containers_, inclusive aqueles que já foram rodados, já que, sem essa opção (por padrão), este comando só mostra os _containers_ que estão ativos.

### `--size` (`-s`)

Mostra o tamanho dos arquivos.

### `--quiet`(`-q`)

Retorna somente o ID dos _containers_, separados por uma quebra de linha. Muito útil para remover todos os _containers_, através da junção dos comandos `docker container rm` e `docker container ls`:

```shell
docker container rm $(docker container ls -aq)
```
