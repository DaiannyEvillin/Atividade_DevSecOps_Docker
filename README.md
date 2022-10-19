# Docker.

 De forma bem resumida, podemos dizer que o Docker é uma plataforma aberta, criada com o objetivo de facilitar o desenvolvimento, a implantação e a execução de aplicações em ambientes isolados. Foi desenhada especialmente para disponibilizar uma aplicação da forma mais rápida possível.
 Usando o Docker, você pode facilmente gerenciar a infraestrutura da aplicação, isso agilizará o processo de criação, manutenção e modificação do seu serviço.

 Todo processo é realizado sem necessidade de qualquer acesso privilegiado à infraestrutura corporativa. Assim, a equipe responsável pela aplicação pode participar da especificação do ambiente junto com a equipe responsável pelos servidores.

 O Docker viabilizou uma "linguagem" comum entre desenvolvedores e administradores de servidores. Essa nova "linguagem" é utilizada para construir arquivos com as definições da infraestrutura necessária e como a aplicação será disposta nesse ambiente, em qual porta fornecerá seu serviço, quais dados de volumes externos serão requisitados e outras possíveis necessidades.
 O Docker também disponibiliza uma nuvem pública para compartilhamento de ambientes prontos, que podem ser utilizados para viabilizar customizações para ambientes específicos. É possível obter uma imagem pronta do apache e configurar os módulos específicos necessários para a aplicação e, assim, criar seu próprio ambiente customizado. Tudo com poucas linhas de descrição.

 O Docker utiliza o modelo de container para “empacotar” a aplicação que, após ser transformada em imagem Docker, pode ser reproduzida em plataforma de qualquer porte; ou seja, caso a aplicação funcione sem falhas em seu notebook, funcionará também no servidor ou no mainframe. Construa uma vez, execute onde quiser.
Os containers são isolados a nível de disco, memória, processamento e rede. Essa separação permite grande flexibilidade, onde ambientes distintos podem coexistir no mesmo host, sem causar qualquer problema. Vale salientar que o overhead nesse processo é o mínimo necessário, pois cada container normalmente carrega apenas um processo, que é aquele responsável pela entrega do serviço desejado. Em todo caso, esse container também carrega todos os arquivos necessários (configuração, biblioteca e afins) para execução completamente isolada.

 Outro ponto interessante no Docker é a velocidade para viabilizar o ambiente desejado; como é basicamente o início de um processo e não um sistema operacional inteiro, o tempo de disponibilização é, normalmente, medido em segundos.
 
# Instalaçao do Docker no Windows.

# Passo 1: Requisitos do sistema.

Sua máquina Windows deve atender aos seguintes requisitos para instalar o Docker Desktop com êxito.

WSL 2 back-end
 
● `Windows 11 de 64 bits`: Home ou Pro versão 21H2 ou superior, ou Enterprise ou Education versão 21H2 ou superior.

● `Windows 10 de 64 bits`: Home ou Pro 21H1 (build 19043) ou superior, ou Enterprise ou Education 20H2 (build 19042) ou superior.

● Habilite o recurso WSL 2 no Windows. Para obter instruções detalhadas, consulte a documentação da Microsoft .

● Os seguintes pré-requisitos de hardware são necessários para executar com êxito o WSL 2 no Windows 10 ou Windows 11:

● Processador de 64 bits com tradução de endereço de segundo nível (SLAT)
4GB de RAM do sistema.

● O suporte à virtualização de hardware no nível do BIOS deve ser ativado nas configurações do BIOS. Para obter mais informações, consulte Virtualização.

● Baixe e instale o pacote de atualização do kernel Linux.

        Observação

        O Docker só oferece suporte ao Docker Desktop no Windows para as versões do Windows 10 que ainda estão dentro do cronograma de manutenção da Microsoft .

Os contêineres e imagens criados com o Docker Desktop são compartilhados entre todas as contas de usuário nas máquinas em que ele está instalado. Isso ocorre porque todas as contas do Windows usam a mesma VM para criar e executar contêineres. Observe que não é possível compartilhar contêineres e imagens entre contas de usuário ao usar o back-end do Docker Desktop WSL 2.

A execução do Docker Desktop dentro de um VMware ESXi ou VM do Azure é compatível com clientes do Docker Business. Ele requer a ativação da virtualização aninhada no hypervisor primeiro. Para obter mais informações, consulte Executando o Docker Desktop em um ambiente VM ou VDI .
    
# Passo 2: Instale o Docker Desktop no Windows.

# Instale interativamente.

1. Clique duas vezes em Docker Desktop Installer.exe para executar o instalador.

   Se você ainda não baixou o instalador ( Docker Desktop Installer.exe), pode obtê-lo no Docker Hub . Normalmente Downloads, ele é baixado para sua pasta ou você pode executá-lo na barra de downloads recentes na parte inferior do navegador da web.

2. Quando solicitado, verifique se a opção Usar WSL 2 em vez de Hyper-V na página Configuração está selecionada ou não, dependendo de sua escolha de back-end.

   Se o seu sistema suportar apenas uma das duas opções, você não poderá selecionar qual back-end usar.

3. Siga as instruções no assistente de instalação para autorizar o instalador e prosseguir com a instalação.

4. Quando a instalação for bem-sucedida, clique em Fechar para concluir o processo de instalação.

5. Se sua conta de administrador for diferente de sua conta de usuário, você deverá adicionar o usuário ao grupo docker-users . Execute o Gerenciamento do Computador como administrador e navegue até Usuários e Grupos Locais > Grupos > usuários docker . Clique com o botão direito do mouse para adicionar o usuário ao grupo. Saia e faça login novamente para que as alterações entrem em vigor.

# Instale a partir da linha de comando.
 
Após baixar o Docker Desktop Installer.exe , execute o seguinte comando em um terminal para instalar o Docker Desktop:

        "Docker Desktop Installer.exe" install

Se você estiver usando o PowerShell, execute-o como:

        Start-Process 'Docker Desktop         Installer.exe' -Wait install

Se estiver usando o prompt de comando do Windows:

        start /w "" "Docker Desktop Installer.exe" install

O comando de instalação aceita os seguintes sinalizadores:

● `--quiet`: suprime a saída de informações ao executar o instalador.

● `--accept-license`: aceita o contrato de serviço de assinatura do Docker agora, em vez de exigir que ele seja aceito quando o aplicativo for executado pela primeira vez.

● `--no-windows-containers`: desabilita a integração de contêineres do Windows.

● `--allowed-org=<org name>`: requer que o usuário faça login e faça parte da organização especificada do Docker Hub ao executar o aplicativo.

● `--backend=<backend name>`: seleciona o back-end padrão a ser usado para o Docker Desktop hyper-v, windowsou wsl-2(padrão).

Se sua conta de administrador for diferente da sua conta de usuário, você deverá adicionar o usuário ao grupo docker-users :

        net localgroup docker-users <user> /add
  
# Inicie o Docker Desktop.

O Docker Desktop não inicia automaticamente após a instalação. Para iniciar o Docker Desktop:

1. Pesquise Docker e selecione Docker Desktop nos resultados da pesquisa.

2. O menu Docker ( cardápio de baleias) exibe a janela Docker Subscription Service Agreement.

   Aqui está um resumo dos pontos principais:

   ● O Docker Desktop é gratuito para pequenas empresas (menos de 250 funcionários E menos de US$ 10 milhões em receita anual), uso pessoal, educação e projetos de código aberto não comerciais.

   ● Caso contrário, requer uma assinatura paga para uso profissional.
Assinaturas pagas também são necessárias para entidades governamentais.

   ● As assinaturas Docker Pro, Team e Business incluem o uso comercial do Docker Desktop.

3. Selecione Aceitar para continuar. O Docker Desktop é iniciado depois que você aceita os termos.

# Instalar o Docker Compose.

Se você tiver o Docker Desktop, terá uma instalação completa do Docker, incluindo o Compose.

Você pode verificar isso clicando em Sobre o Docker Desktop no menu Docker. 

# Subir uma aplicação WordPress + DB MySQL.

Crie um arquivo chamado docker-compose.yml no Visual Code no seu Windows.

Dentro desse arquivo iremos definir a versão do docker-compose.yml no nosso está a versão 3.9. 

Em seguida adicione a propriedade services. É nela que definimos os serviços que a nossa stack terá, simplificando muito podemos dizer que cada serviço equivale a um contêiner. No nosso teremos os serviços db e wordpress conforme o código abaixo. Um detalhe muito importante é não usar TABS, se não usarmos apenas espaços e formatarmos corretamente o nosso arquivo não será interpretado corretamente e por consequência não irá executar.

Agora definimos cada um dos nossos serviços vamos começar pelo db. 

Primeiro vamos escolher a Docker image a partir da qual o serviço/contêiner será inicializado no nosso caso o mysql:latest. Nesse caso iremos usar a tag latest (última versão estável da Docker image). 

Depois iremos definir uma propriedade command que funciona de modo similar à instrução COMMAND do Dockerfile. No nosso estamos usando o command para inicializar o MySQL no modo de autenticação nativo. Sem isso não conseguiríamos logar no nosso SGBD MySQL.
 
Em seguida vamos definir através de quais portas iremos acessar o MySQL. No meu caso 3306 no contêiner e 3308 no host, escolhi a 3308 por que na minha máquina eu tenho o MySQL instalado e se eu deixasse a 3306 ocorreria um conflito de portas.

Após isso vamos manter o db assim e vamos configurar o serviço do wordpress.

Primeiro vamos especificar a Docker image no nosso caso wordpress:latest. Mesmo que omitíssemos a TAG a latest seria baixada por padrão. Se quiséssemos poderíamos especificar uma TAG específica. Em seguida definimos as portas que no caso será a 80 tanto no contêiner quanto no host (minha máquina). No mesmo alinhamento de image e ports vamos adicionar uma nova propriedade chamada depends_on. Essa propriedade indica ao Docker Compose que o serviço do wordpress depende do serviço do db e por isso ele deve iniciar o db primeiro.

Agora vamos avançar um pouco mais e vamos ultilizar as propriedades environment e volumes. Environment como o próprio nome diz serve para definirmos valores de variáveis de ambiente dentro do contêiner. A maioria das variáveis são auto evidentes, mas algumas merecem uma explicação especial. A variável TZ serve para definirmos o TimeZone em que o contêiner está sendo executado. Se você está no Brasil com exceção de uns poucos estados seu timezone provavelmente será America/Sao_Paulo. A variável MYSQL_ROOT_PASSWORD é obrigatória e sua stack não irá subir sem ela. Ela é usada para definirmos a senha do usuário root do MySQL. As demais acredito que sejam auto explicativas. Em seguida temos os volumes que sendo bem simplista, é como se fosse um mapeamento de um diretório dentro de um contêiner com um diretório no host. No nosso caso o serviço do MySQL tem um volume e o serviço do WordPress tem dois volumes.

Apesar de o Docker Compose já criar uma rede default entre os contêineres/serviços por questões de prática nomearemos uma rede. Pra isso adicione a propriedade networks no mesmo alinhamento de services. O nome da nossa rede será wordpress-network e ela será inicializada em modo bridge. Feito isto basta adicionarmos a propriedade networks em cada serviço. Essa propriedade deve ficar no mesmo alinhamento que ports e environment e nela podemos definir uma ou mais redes. No nosso caso teremos apenas a rede wordpress-network.

Feito isto toda a nossa stack está configurada e já podemos executá-la.

Abaixo se encontra o arquivo docker-compose.yml que criamos:

    version: '3.9'

    services:

      db:

        image: mysql:latest

        volumes:

          - db_data:/var/lib/mysql

        command: mysqld --default_authentication_plugin=mysql_native_password

        environment:

          TZ: America/Sao_Paulo

          MYSQL_ROOT_PASSWORD: docker

          MYSQL_USER: docker

          MYSQL_PASSWORD: docker

          MYSQL_DATABASE: wordpress

        ports:

          - 3308:3306

        networks:

          - wordpress-network

 

       wordpress:

        image: wordpress:latest

        volumes:

          - ./config/php.conf.uploads.ini:/usr/local/etc/php/conf.d/uploads.ini

          - ./wp-app:/var/www/html

        environment:

          TZ: America/Sao_Paulo

          WORDPRESS_DB_HOST: db

          WORDPRESS_DB_NAME: wordpress

          WORDPRESS_DB_USER: root

          WORDPRESS_DB_PASSWORD: docker

        ports:

          - 80:80

        networks:

          - wordpress-network
          
       adminer:
       
        image: adminer:latest
        
        depends_on: 
        
          - mysql
          
        ports:
        
          - 4040:8080
 

    networks:

        wordpress-network:

          driver: bridge



# Executando nosso arquivo .yml.

Nosso próximo passo é acessar o diretório desse arquivo e abrir o terminal (se não for no mesmo diretório do arquivo não irá funcionar). Com o terminal aberto digite o comando
 
        docker-compose up -d 

para que o Docker Compose inicialize a stack. O parâmetro -d é opcional e é usado para que o Docker Compose inicie de modo detachado e libere o terminal pra que possamos continuar usando. Esse processo pode levar alguns minutos já que ele irá baixar as Docker images e inicializar os contêineres, algo que pode demorar dependendo da sua internet e de seu hardware.

Podemos ir direto ao navegador e conferir se tudo deu certo, mas vamos apenas usar o comando 

        docker-compose ps 

que lista os contêineres da stack em execução. Um detalhe fundamental é que todos os comandos do Docker compose precisam ser executados no mesmo diretório em que está o arquivo docker-compose.yml ou não funcionará. 
Se o estado contêiner for igual a up então significa que está funcionando.

# Interromper a Stack.

Imagine interromper uma stack com dezenas de contêineres usando o comando



        docker stop
 
 
Não preciso nem dizer que é praticamente inviável e é exatamente por isso que existe o comando docker-compose down. Dito isto vamos encerrar a nossa stack, pra isso digite o comando:
 
 
        docker-compose down
        
        
Além de parar os contêineres o Docker Compose também interrompe a rede. 


# Referência:

GOMES, Rafael. Docker para desenvolvedores. 2020. Disponível em: https://stack.desenvolvedor.expert/appendix/docker/oquee.html. Acesso em: 17 out. 2022.

Docker site oficial. Instale o Docker Desktop no Windows. 2022. Disponível em: https://docs.docker.com/desktop/install/windows-install/ . Acesso em: 18 out. 2022.
