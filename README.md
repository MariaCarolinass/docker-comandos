# Docker

**O que é Docker?** 

É um conjunto de produtos de plataforma como serviço que usam virtualização de nível de sistema operacional para entregar software em pacotes chamados contêineres.

**O que são contêineres?** 

Os contêineres são isolamentos, processos separados uns dos outros e que agrupam seus próprios softwares, bibliotecas e arquivos de configuração.

[Referência](https://pt.wikipedia.org/wiki/Docker_(software))

## Comandos útils (terminal)

Instalação do Docker:

    $ su
    # apt-get update
    # apt-get curl
    # curl -fsSL https://get.docker.com | bash

Testando se Docker foi instalado:

    # docker container run -ti hello-world

Conferindo versão instalada do Docker:

    # docker version

Conferindo containers em execução:

    # docker container ls

Conferindo containers criados:

    # docker container ls -a

Criando um container da imagem Centos:

Executando e interagindo
    
    # docker container run -ti centos

Conectando container:
    
    # docker container attach id-imagem 

Criando um container da imagem nginx:

Executando e rodando como daemon (primeiro plano)
    
    # docker container run -d nginx

Conectando container:
  
    # docker container exec -ti  id-imagem ls /

Start, stop, restart, pause e unpause container:
    
    # docker container stop  id-imagem
    # docker container start  id-imagem
    # docker container restart  id-imagem
    # docker container pause  id-imagem
    # docker container unpause  id-imagem

Checar informações de uma imagem do container:
    
    # docker container inspect id-imagem

Remover imagem do container:
    
    # docker container rm id-imagem
    # docker container rm -f id-imagem

Dados de hardware da imagem no container: 

Informações de memória:

    # docker container stats id-imagem

Processos em execução:

    # docker container top id-imagem

Rodando container definindo memória e cpu da imagem:
    
    # docker container run -d -m 128M nginx

    # docker container run -d -m 128M --cpus 0.5 nginx

Atualizando quantidade da cpu e memória:

    # docker container update --cpus 0.2 id-imagem
    # docker container update --memory 64M id-imagem

Conferindo imagens criadas:

    # docker image ls

Criando um novo volume:
    
    # docker volume create nome_volume

Criar container com ponto de montagem para guardar dados:
    
Tipo bind: (quando já tem um diretório para montar dentro do container)

    # docker container run -ti --mount type=bind,src=documentos/projeto,dst=projeto debian

Tipo volume:
    
    # docker container run -ti --mount type=volume,src=nome_volume,dst=projeto debian

Conferindo volumes criados:
    
    # docker volume ls

    # docker volume inspect nome_volume

Apagar inativos:
    
Volume:

    # docker volume prune
    
Container:

    # docker container prune
