
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

