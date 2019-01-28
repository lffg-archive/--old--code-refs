# `docker image tag (...)`

Cria uma referência da **imagem de origem** para a **imagem de destino**.

```shell
docker image tag <source-image-name> <target-image-name>
```

Como se fosse criado um _alias_ para a imagem de origem.

Exemplo:

```shell
docker image tag nginx:latest my-nginx
```

Rodando o exemplo acima, a imagem `nginx:latest` também pode ser acessada através de `my-nginx`, já que a segunda é uma **referência**.
