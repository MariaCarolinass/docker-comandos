# Docker

**O que é o Docker?** 

É um conjunto de produtos de plataforma como serviços que usam virtualização de nível, de sistema operacional, para entregar softwares em pacotes chamados contêineres.

**O que são contêineres?** 

Os contêineres são isolamentos, processos separados uns dos outros e que agrupam seus próprios softwares, bibliotecas e arquivos de configuração.

## Sumário

* [Comandos úteis](#comandos-úteis-terminal)
    * [Instalação](#instalação)
        * [Testando se o Docker foi instalado](#testando-se-o-docker-foi-instalado)
        * [Conferindo a versão instalada do Docker](#conferindo-a-versão-instalada-do-docker)
    * [Container](#container)
        * [Criando um container para o Centos](#criando-um-container-para-o-centos)
        * [Criando um container para o Nginx](#criando-um-container-para-o-nginx)
        * [Comandos básicos do container](#comandos-básicos-do-container)
        * [Dados de hardware do container](#dados-de-hardware-do-container)
    * [Start, stop, restart, pause e unpause container](#start-stop-restart-pause-e-unpause-container)
    * [Volumes](#volumes)
        * [Armazenando dados do container](#armazenando-dados-do-container)
    * [Imagens](#imagens)
        * [Criando uma imagem executável](#criando-uma-imagem-executável)
        * [Comandos básicos da imagem](#comandos-básicos-da-imagem)
    * [Apagar inativos](#apagar-inativos)
* [Rodando um container do PostgreSQL e guardando os dados no volume](#rodando-um-container-do-postgresql-e-guardando-os-dados-no-volume)
   * [Fazendo o backup dos dados](#fazendo-o-backup-dos-dados)
* [Criando um arquivo Dockfile para instalar o servidor Apache](#criando-um-arquivo-dockfile-para-instalar-o-servidor-apache)
   * [Subindo a imagem para o Docker Hub](#subindo-a-imagem-para-o-docker-hub)
   * [Subindo a imagem localmente usando registry](#subindo-a-imagem-localmente-usando-registry)
* [Links](#links) 

## Comandos úteis (terminal)

### Instalação:

    $ su
    # apt-get update
    # apt-get curl
    # curl -fsSL https://get.docker.com | bash

[Consulte a documentação do Docker](https://docs.docker.com/engine/install/)

#### Testando se o Docker foi instalado:

    # docker container run -ti hello-world

#### Conferindo a versão instalada do Docker:

    # docker version

### Container

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

#### Comandos básicos do container

Visualizando containers em execução:

    # docker container ls

Visualizando containers criados:

    # docker container ls -a
    
Checando informações do container:

    # docker container inspect id-container

Removendo um container:
    
    # docker container rm id-container
    # docker container rm -f id-container

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

### Start, stop, restart, pause e unpause container
    
    # docker container stop  id-container
    # docker container start  id-container
    # docker container restart  id-container
    # docker container pause  id-container
    # docker container unpause  id-container
    
### Volumes

Criando um volume:
    
    # docker volume create nome_volume

Visualizando volumes criados:
    
    # docker volume ls

Checando informações do volume

    # docker volume inspect nome_volume

#### Armazenando dados do container:
    
Tipo bind: (quando já tem um diretório para montar dentro do container)

    # docker container run -ti --mount type=bind,src=documentos/projeto,dst=projeto debian

Tipo volume:
    
    # docker container run -ti --mount type=volume,src=nome_volume,dst=projeto debian

### Imagens

#### Criando uma imagem executável

Iniciando projeto:

    # mkdir projeto-docker
    # cd projeto-docker
    # nano DockerFile
    
Colar no arquivo DockerFile:

    FROM debian
    LABEL app = ‘nome_app’
    ENV Docker = ‘nome_env’
    RUN apt-get update && apt-get install -y stress && apt-get clean 
    CMD stress --cpu 1 --vm-bytes 64M --vm 1
        
Criando imagem e executando no container:

    # docker image build -t nome_imagem:1.0
    # docker image ls
    # docker container run -d nome_container:1.0
    # docker container ls

#### Comandos básicos da imagem

Criando uma imagem:

    # docker image build -t nome_imagem:1.0

Visualizando imagens criadas:

    # docker image ls
    
Apagar uma imagem:

    # docker image rm id_image
    # docker image rm -f id_image

### Apagar inativos:
    
Apagar volumes inativos:

    # docker volume prune
    
Apagar containers inativos:

    # docker container prune

## Rodando um container do PostgreSQL e guardando os dados no volume

### Fazendo o backup dos dados

## Criando um arquivo Dockfile para instalar o servidor Apache

### Subindo a imagem para o Docker Hub
### Subindo a imagem localmente usando registry
   
## Links

- [O que é o Docker?](https://pt.wikipedia.org/wiki/Docker_(software))
