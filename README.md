# Docker

**O que é Docker?** 

É um conjunto de produtos de plataforma como serviço que usam virtualização de nível de sistema operacional para entregar software em pacotes chamados contêineres.

**O que são contêineres?** 

Os contêineres são isolamentos, processos separados uns dos outros e que agrupam seus próprios softwares, bibliotecas e arquivos de configuração.

[Referência](https://pt.wikipedia.org/wiki/Docker_(software))

## Comandos útils (terminal)

### Instalação do Docker:

    $ su
    # apt-get update
    # apt-get curl
    # curl -fsSL https://get.docker.com | bash

[Consulte a documentação do Docker](https://docs.docker.com/engine/install/)

Testando se o Docker foi instalado:

    # docker container run -ti hello-world

Conferindo a versão instalada do Docker:

    # docker version

### Start, stop, restart, pause e unpause container
    
    # docker container stop  id-container
    # docker container start  id-container
    # docker container restart  id-container
    # docker container pause  id-container
    # docker container unpause  id-container

### Container

Visualizando containers em execução:

    # docker container ls

Visualizando containers criados:

    # docker container ls -a
    
Checando informações do container:

    # docker container inspect id-container

Remover um container:
    
    # docker container rm id-container
    # docker container rm -f id-container

#### Criando um container para o Centos

Executando e interagindo com o container:
    
    # docker container run -ti centos

Acessando o container:
    
    # docker container attach id-container

#### Criando um container para o Nginx

Executando e criando o container como daemon (primeiro plano):
    
    # docker container run -d nginx

Acessando o container:
  
    # docker container exec -ti  id-container ls /

#### Dados de hardware do container: 

Informações de memória:

    # docker container stats id-imagem

Processos em execução:

    # docker container top id-imagem

Criando um container e definindo tamanho da memória

    # docker container run -d -m 128M nginx

Criando um container e definindo tamanho da memória e cpu:
    
    # docker container run -d -m 128M --cpus 0.5 nginx

Atualizando tamanho da memória:

    # docker container update --memory 64M id-imagem
    
Atualizando tamanho da cpu:

    # docker container update --cpus 0.2 id-imagem
    
### Volumes

Criando um novo volume:
    
    # docker volume create nome_volume

Visualizando volumes criados:
    
    # docker volume ls

Checando informações do volume

    # docker volume inspect nome_volume

#### Criando container com ponto de montagem para guardar dados:
    
Tipo bind: (quando já tem um diretório para montar dentro do container)

    # docker container run -ti --mount type=bind,src=documentos/projeto,dst=projeto debian

Tipo volume:
    
    # docker container run -ti --mount type=volume,src=nome_volume,dst=projeto debian

### Apagar inativos:
    
Apagar volumes inativos:

    # docker volume prune
    
Apagar containers inativos:

    # docker container prune

### Imagens do container

Visualizando imagens criadas:

    # docker image ls
