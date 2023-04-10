# Servidor_minecraft
Repositório com guia de como abrir um servidor de minecraft no google cloud

# Introdução

Para criar uma vm com um servidor de minecraft a gente vai:

- criar uma vm no google cloud
- Instalar o minecraft
- criar a regra de firewall para o nosso servidor aceitar tráfego



Passo 1 - Criar uma VM
O primeiro passo é criar uma VM no Google Cloud. Certifique-se de conceder permissões de leitura e gravação no disco, adicionar disco e configurar a rede. Para acessar as especificações das máquinas, você pode clicar no link na descrição abaixo.
Passo 2 - Entre na VM com SSH
Em seguida, você precisará entrar na VM com SSH.
Passo 3 - Crie um diretório para o servidor
Agora, crie um diretório para o servidor com o seguinte comando: "sudo mkdir -p /home/minecraft".
Passo 4 - Formate o disco
Formate o disco com o seguinte comando: "sudo mkfs.ext4 -F -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/disk/by-id/google-minecraft-disk".
Passo 5 - Monte o disco
Monte o disco com o seguinte comando: "sudo mount -o discard,defaults /dev/disk/by-id/google-minecraft-disk /home/minecraft".
Passo 6 - Instale e configure o JRE
O próximo passo é instalar e configurar o Java Runtime Environment (JRE). Atualize os diretórios Linux com o comando "sudo apt-get update". Em seguida, instale a versão headless do JRE com o comando "sudo apt-get install -y default-jre-headless". Depois disso, entre no diretório que você criou anteriormente digitando "cd /home/minecraft". Agora, instale o Wget com o comando "sudo apt-get install wget". Para instalar a versão atual do Minecraft Server, use o seguinte comando: "sudo wget https://launcher.mojang.com/v1/objects/d0d0fe2b1dc6ab4c65554cb734270872b72dadd6/server.jar".
Passo 7 - Instale o Screen e inicie o servidor
Agora, instale o Screen com o comando "sudo apt-get install -y screen". Em seguida, inicie o servidor na tela que você acabou de baixar com o seguinte comando: "sudo screen -S mcs java -Xmx1024M -Xms1024M -jar server.jar nogui".
Passo 8 - Aceite a EULA do servidor
Para aceitar a EULA do servidor, use o comando "sudo nano eula.txt". Mude a última linha de "eula=false para eula=true". Para sair do nano, pressione "ctrl+o" e depois "ctrl+x".
Passo 9 - Inicie o servidor novamente
Agora, inicie o servidor novamente na tela que você acabou de baixar com o seguinte comando: "sudo screen -S mcs java -Xmx1024M -Xms1024M -jar server.jar nogui".
Passo 10 - Criar um terminal virtual
Para criar um terminal virtual para iniciar o servidor Minecraft, use o seguinte comando: "sudo screen -r mcs".
Passo 11 - Sair da tela
Para sair da tela sem desligar, pressione "ctrl+a" e depois "ctrl+D".
E aí está! Agora você tem seu próprio servidor de Minecraft

