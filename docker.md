
# Docker Expert

## Day 1

### O que é container?
- [x] Uma forma de promover o isolamento, que pode ser: 
    - Lógico: processo, usuário, networking, mountpoint ... (**namespaces**)
    - Físico: cpu, memória, i/o rede, i/o bloco, ... (**Cgroups**)
    

- **_Docker é a popularização dos container_**

**Antes:** 
- *Chroot*: primeira forma de fazer isolamento (disco do filesytem)
- *LXC*(Linux container): forma de executar containers no Linux
- *Outros*: jails, solarisonis, openvz (VPS: servidor dedicado pra rodar app. Virtuoso). Parelos: abrir o código

2008: Google, ibm e virtuoso => Começaram a desenvolver o LXC(usava cgroups, namespace e chroot). Start para o DOCKER.

2013: Dotcloud => pass pra rodar as aplicações. 
Março de 2013: DOCKER =>  Disponibilizou o cor de das ferramentas que eles usavam para gerenciar os containers. (Scripts lxc)

## O que é o docker?
- [x] Imagen (copy on write): 
    - Cada instrução faz uma camada
    - Última camada (read and white) única que pode ser escrita
    - Imagen única: varios containes podem ser gerados a partir de uma unica imagem
    - Espaço usado pelos containers: quantidade de recursos é igual ao da imagem usada para criar o container + o que for criado para cada container (arquivos, logs,...) 
 

**Componentes do Docker e o que é necessário para ele funcionar?**
- [x] Kernel linux oferece recursos necessários para o docker funcionar
    - [x] kernel linux (host):  
        - [x] **Netfilter**: utiliza o iptable que é comando para interagir com o netfilter (filtro de pacotes, redirect)
        - [x] **Namespaces**: ipc uts netnamespace nmtnamespace usernamespace
        - [x] **cgroups**: isolamento de cpu, memória, network e disco
        - [x] **outros modulos**: (netlink, clinux, capability)
        
- **Containers é bom pra quem?**
    - **Dev**: rápido pra rodar (composefile) e garantia que vai rodar em produção (container iquais). Mais controle e recursos disponíveis. **(Qualidade)**
    - **sysADM e DevOps**:  mais controle e menor diferenças em nivel de servidor e não precisa se preocupar com as diferenças de tecnologias. (Controle e Segurança)
    - **Empressário**: Mais agilidade, mais sinergia entre equipes de dev e operação e economia de recursos. **(Economia e agilidade: tempo e dinheiro)**  

## Instalando o docker
- **Docker CE** free 
- **Docker EE** paga

- Digitando `curl -fsSL https://get.docker.com | bash` no terminal o SO é identificado e instala versão mais atual do Docker 

- [x] Docker Client: o comandos cli
- [x] Docker Server (Daemon): quem gerencia os containers

## Administrando containers docker

**Pra não ter que usar root em todos os comandos**
`sudo usermod -aG docker myUserDocker`

`history`: mostra os ultimos comandos digitados no terminal

**Docker Comandos**
- `docker ps -a` x `docker container ls -a` listagem de containers
- `docker run` x `docker container run -ti hello-world` executar um container
(-ti executa o container com terminal de interatividade, já roda o container e entra no container para fazer as interações internamente) => `ps -ef`

- [x] Ao rodar um `docker run`: O `docker client` vai interpretar o comando e falar com o `docker Daemon` que vai verificar se o container existe localmente, se não ele faz o dowload da imagem e na seguencia cria um container dessa imagem localmente. Caso esteja em modo -ti vai mostrar a saida do entrypoint

-  `docker conatainer attach [CONTAINER ID]` para desconectar `ctrl+P+Q`
-  `docker conatiner exec -ti idcontainer comand` roda um comnado dentro do container
-  `docker container start [CONTAINER ID]` inicia o container
-  `docker container stop [CONTAINER ID]` para de rodar um container
-  `docker container restart [CONTAINER ID]` reinicia container que foi parado
-  `docker container pause [CONTAINER ID]` pausa o coantainer
-  `docker container unpause [CONTAINER ID]` despausa o container
-  `docker container inspect [CONTAINER ID]` mostrar as informações do container
-  `docker container logs -f [CONTAINER ID]` maostra os logs gerados pela interação com o container
-  `docker container rm [CONTAINER ID]` remove um container (deleta) que está parado
-  `docker container attach [CONTAINER ID]` 
-  `docker container rm -f [CONTAINER ID]` remove um container que está em execução
-  `docker container exec -ti [CONTAINER ID] [COMANDO]` pra rodar os comando dentro do container, o processo pricipal é bloquenate
-  `docker container run -d nginx`

## Mémoria e CPU
Controlar a quantidade de memoria e cpu que será disponibilizado para cada container 
- `docker container stats [CONTAINER ID]`
- `docker container top [CONTAINER ID]`
- `docker container run -d -m 128M --cpus 0.5 nginx`
- `docker container update --memory 64M --cpus 0.4 nginx`
- `docker container inspect [CONTAINER ID]`
- `docker container stats [CONTAINER ID]`
- `docker container top [CONTAINER ID]`

Comando executados dentro do container:

- `apt-get update`
- `apt-get install stress`
- `stress --cpu 1 --vm-bytes 128M --vm1`
