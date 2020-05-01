
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
    
