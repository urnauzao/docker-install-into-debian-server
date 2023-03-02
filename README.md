# Sobre
- Todo o material contido neste tutorial está presente no vídeo asseguir, sugiro que veja o vídeo, pois poderá sanar todas suas dúvida além de ser uma abordagem na prática de como realizar toda a instalação.
  - [Clique Aqui para ver o Tutorial em Vídeo](https://teste.io/#)
- O conteúdo aqui presente foi extrado do guia oficial de instalação do Docker. [acessar guia gficial](https://docs.docker.com/engine/install/debian/)

# Requisitos:
- Em caso de ambiente local de desenvolvimento, ter uma versão do Linux compatível com o Docker Engine.
[Versões de Linux compativeis](https://docs.docker.com/engine/install/)

- Em caso de ambiente de produção, ter escolhido uma hospedagem e estar com acesso Root SSH a ela. 
  - Na dúvida veja este tutorial sobre como escolher uma hospedagem e fazer o primeiro acesso SSH. [Ver Tutorial Agora](https://youtu.be/oQX7KyUsH3g)
  - Sugestão para constração de <b>Hospedagem com 20% de desconto</b>, [clique aqui](https://hostinger.com.br?REFERRALCODE=1JULIOCESAR92)

# Ajuda
- Como ver a versão do seu Linux, execute no terminal
```sh
  hostnamectl
```

```sh
-- Exemplo de saída
Static hostname: vps.urnau.com.br
Icon name: computer-container
Chassis: container
Machine ID: 8719463e9a638aa1bb58c333cec521dc
Boot ID: 99bb23647000aaabb7c9ba1c3c17aeac
Virtualization: openvz
Operating System: Debian GNU/Linux 11 (bullseye)
Kernel: Linux 4.19.0
Architecture: x86-64
```

# Iniciando instalação no servidor Debian

- Acessar pasta raiz do usuário
```sh
cd ~
```

- Remover docker antigo
```sh
sudo apt-get remove docker docker-engine docker.io containerd runc
```

- Repositorio Docker
````sh
sudo apt-get update &&
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
````

- Adicionar chave GPG oficial do Docker
```sh
sudo mkdir -m 0755 -p /etc/apt/keyrings &&
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

- Concluir adição do repositório
```sh
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

- Atualizando o sistema
```sh
sudo apt-get update
```
  - Em caso de erro execute
  ```sh
    sudo chmod a+r /etc/apt/keyrings/docker.gpg &&
    sudo apt-get update
  ```
  
- Instalando a última versão do Docker
```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

- Testando o Docker
```sh
sudo docker run hello-world
```










