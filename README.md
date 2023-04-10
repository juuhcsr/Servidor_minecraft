# Servidor_minecraft
Repositório com guia de como abrir um servidor de minecraft no google cloud

## Introdução

Para criar uma vm com um servidor de minecraft a gente vai:

- criar uma vm no google cloud
- Instalar o minecraft
- criar a regra de firewall para o nosso servidor aceitar tráfego



### Passo 1 - Criar uma VM

O primeiro passo é criar uma VM no Google Cloud. Certifique-se permitir o acesso a todas as APIs e reservar o endereço ip externo.

1. No console do google cloud clique no menu de navegação ( ≣ ), clique em **Compute engine** > **instâncias de vm**

2. Clique em **Criar instância **

3. Especifique as seguintes configurações e deixe o resto como padrão

![image](https://user-images.githubusercontent.com/110038530/230805247-4fa88b34-6045-42ad-a1c5-d99a304c57ea.png)

 Clique em Opções avançadas e vá em Rede e especifique essas configurações

![image](https://user-images.githubusercontent.com/110038530/230805425-66bdad73-6994-48ae-8b2a-f79264b7c49c.png)

clique em reservar e crie a máquina virtual

### Passo 2 - Configurações na Máquina virtual

1. Entre na VM com SSH

Depois de criada a máquina virtual, clique em SSH para se conectar ao terminal da máquina

2. Instale o java (JRE)

sudo apt-get update

sudo apt-get install -y default-jre-headless

3. Crie um diretório para o minecraft e entre nele

sudo mkdir -p /home/minecraft

cd /home/minecraft

4. instale o wget 

sudo apt-get install wget

5. instale a versão 1.14.3 do minecraft server

sudo wget https://launcher.mojang.com/v1/objects/d0d0fe2b1dc6ab4c65554cb734270872b72dadd6/server.jar

6. Instale o Screen para iniciar o servidor

O Screen é uma ferramente que permite que você crie várias telas dentro de um terminal 

sudo apt-get install -y screen

7.Inicie o servidor

sudo screen -S mcs java -Xmx1024M -Xms1024M -jar server.jar nogui

8. Aceite a EULA do servidor 

sudo nano eula.txt

Altere a linha de "eula=false" para "eula=true"

9. Inicie o servidor novamente 

sudo screen -S mcs java -Xmx1024M -Xms1024M -jar server.jar nogui

10. Saindo da tela 

Para sair da tela sem desligar, pressione "ctrl+a" e depois "ctrl+D".

11. Retornando para a tela

Para retornar a tela utilize o comando:

sudo screen -r mcs

### Passo 3 - Criando a regra de firewall

Para liberar o acesso ao servidor, é necessário criar uma regra de firewall para isso:

1. No console do google cloud clique no menu de navegação ( ≣ ), clique em **Rede VPC** > **Firewall**

2. Clique em **Criar Regra de Firewall **

3. Especifique as seguintes configurações:

![image](https://user-images.githubusercontent.com/110038530/230806082-ffd1a94a-a859-4e3e-8b17-832d07bb263f.png)

4. Crie a regra de firewall


E aí está! Agora você tem seu próprio servidor de Minecraft

