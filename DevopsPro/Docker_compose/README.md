<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">O Docker Compose é uma ferramenta que simplifica o gerenciamento de ambientes de múltiplos contêineres no Docker, permitindo a definição de configurações em arquivos YAML. Aqui estão os principais pontos sobre o Docker Compose:</p>

<ol>
  <li style="text-align: justify;">Definição em Arquivos YAML</li>
  <ul>
    <li style="text-align: justify;">O Docker Compose utiliza arquivos YAML para definir a configuração de serviços, redes e volumes em um ambiente Docker.</li>
  </ul>
  <li style="text-align: justify;">Orquestração Simples</li>
  <ul>
    <li style="text-align: justify;">Facilita a orquestração de contêineres, possibilitando a definição, execução e escalonamento de aplicações com vários contêineres.</li>
  </ul>
  <li style="text-align: justify;">Configuração Centralizada</li>
  <ul>
    <li style="text-align: justify;">Permite a configuração centralizada de múltiplos contêineres em um único arquivo, simplificando o gerenciamento e a replicação do ambiente.</li>
  </ul>
  <li style="text-align: justify;">Escala de Serviços</li>
  <ul>
    <li style="text-align: justify;">Oferece a capacidade de escalar serviços, especificando o número desejado de instâncias de um serviço específico.</li>
  </ul>
  <li style="text-align: justify;">Variáveis de Ambiente e Substituição de Variáveis</li>
  <ul>
    <li style="text-align: justify;">Suporta o uso de variáveis de ambiente no arquivo Compose, tornando a configuração mais flexível e adaptável a diferentes ambientes.</li>
  </ul>
  <li style="text-align: justify;">Facilita o Desenvolvimento Local</li>
  <ul>
    <li style="text-align: justify;">É especialmente útil para ambientes de desenvolvimento local, onde vários serviços precisam ser executados e coordenados.</li>
  </ul>
</ol>

<p style="text-align: justify;">Veja a seguir um exemplo de um arquivo docker compose.</p>

```yaml
version: "3"
services:
  nginx:
    container_name: nginx
    image: nginx
    ports:
      - "8080:80"
```

<ul>
  <li style="text-align: justify;"><b>version</b>: Especifica a versão da sintaxe do Docker Compose utilizada no arquivo. O valor "3" neste caso refere-se à versão específica da sintaxe do Docker Compose.</li>
  <li style="text-align: justify;"><b>services</b>: Indica o início da seção onde os serviços são definidos. Serviços são instâncias de contêineres que compõem o ambiente Docker orquestrado.</li>
  <li style="text-align: justify;"><b>nginx</b>: Nome do serviço. Neste exemplo, o serviço é chamado de "nginx". Este nome é usado para referenciar o serviço em outros lugares do arquivo e para identificar o contêiner correspondente.</li>
  <li style="text-align: justify;"><b>container_name</b>: Especifica um nome personalizado para o contêiner. Neste caso, o contêiner será nomeado como "nginx". Isso é opcional, e se não for fornecido, o Docker gerará automaticamente um nome baseado no serviço.</li>
  <li style="text-align: justify;"><b>image</b>: Especifica a imagem Docker usada para criar o contêiner do serviço. Neste caso, o serviço "nginx" será baseado na imagem oficial do Nginx disponível no Docker Hub.</li>
  <li style="text-align: justify;"><b>ports</b>: Define a exposição de portas entre o contêiner e o host. A opção "8080:80" indica que a porta 80 do contêiner será mapeada para a porta 8080 do host. Isso permite acessar o serviço Nginx no host pela porta 8080.</li>
</ul>

<p style="text-align: justify;">Para executarmos esse arquivo basta usar o comando <i>docker compose up -d</i>.</p>

```bash
docker compose up -d
```

<p style="text-align: justify;">Enquanto o <i>docker-compose down</i> é usado para parar e remover os contêineres</p>

```bash
docker compose down
```

<p style="text-align: justify;">É possivel colocar mais de um container dento do arquivo docker compose se caso for necessario.</p>

```yaml
version: "3"
services:
  nginx:
    container_name: nginx
    image: nginx
    ports:
      - "8080:80"
  nginx02:
    container_name: nginx02
    image: nginx
    ports:
      - "8181:80"
```

<h1>Variaveis de Ambiente</h1>

<p style="text-align: justify;">Variáveis de ambiente no Docker Compose são usadas para passar informações configuráveis para serviços e contêineres em um ambiente Docker. Elas são especialmente úteis para parametrizar configurações que podem variar dependendo do ambiente ou para facilitar a personalização de contêineres.</p>

<p style="text-align: justify;">Veja a seguir um exemplo de docker compose utilizando variaveis de ambiente.</p>

```yaml
version: "3"
services:
  postgre:
    container_name: postgresql
    image: postgres:12.17
    ports:
      - 5432:5432
    environment:
      POSTGRES_PASSWORD: 123
      POSTGRES_USER: compose
      POSTGRES_DB: compose_db
```

<p style="text-align: justify;">No exemplo acima colocamos tres variaveis de ambiente para o container do posgres, usuario, senha e nome do banco que iremos conectar.</p>

<p style="text-align: justify;">Tambem é possivel colocra as variaveis de ambiente em um arquivo <b>.env</b> para facilitar as manutenções futuras.</p>

```yaml
version: "3"
services:
  postgre:
    container_name: postgresql
    image: postgres:12.17
    ports:
      - 5432:5432
    env_file:
      - .env
```
<p style="text-align: justify;">Crie um arquivo <b>.env</b> no mesmo diretorio do arquivo <b>compose.yaml</b> e coloque as variaveis no arquivo.</p>

```env
POSTGRES_PASSWORD: 123
POSTGRES_USER: compose
POSTGRES_DB: compose_db
```

<h1>Volume Bind Mount</h1>

<p style="text-align: justify;">
O volume "bind mount" no Docker Compose é uma técnica que permite montar diretórios ou arquivos de um sistema de arquivos do host diretamente em um contêiner. Essa abordagem é útil para compartilhar dados entre o host e o contêiner de maneira flexível.</p>

<p style="text-align: justify;">Veja um exemplo utilizando o Bind Mount com docker compose.</p>

```yaml
version: "3"
services:
  postgre:
    container_name: postgresql
    image: postgres:12.17
    ports:
      - 5432:5432
    env_file:
      - .env
    volumes:
      - C:\Users\HxTos\Documents\Git\Docker\DevopsPro\Docker_compose\bind_mount\postgre_vol:/var/lib/postgresql/data
```

<p style="text-align: justify;">Criamos um diretorio chamado postgre_vol para armazenar os registros do container como exemplo.</p>

<h1>Docker Volume</h1>

<p style="text-align: justify;">Os volumes no Docker Compose são uma maneira de gerenciar armazenamento persistente para serviços e contêineres. Eles fornecem uma solução para o armazenamento de dados que precisa sobreviver ao ciclo de vida dos contêineres.</p>

<p style="text-align: justify;">Veja um exemplo utilizando o docker volume com docker compose.</p>

```yaml
version: "3"
services:
  postgre:
    container_name: postgresql
    image: postgres:12.17
    ports:
      - 5432:5432
    env_file:
      - .env
    volumes:
      - postgre_docker_vol:/var/lib/postgresql/data
volumes:
  postgre_docker_vol:
    name: postgre_volume
```

<p style="text-align: justify;">Veja que o caminho do <b>volumes</b> no service é alterado, ao invez de apontar para um diretorio local da maquina, será apontado para o volume gerenciado pelo docker, para verficar se o volume foi criado basta utilizar o comando <i>docker volume ls</i>.</p>

<p style="text-align: justify;">Caso você ja tenha um volume criado basta usar a flag <i>external: true</i> para especificar que esse volme foi criado separadamente do container utilizando o docker compose.</p>

```yaml
version: "3"
services:
  postgre:
    container_name: postgresql
    image: postgres:12.17
    ports:
      - 5432:5432
    env_file:
      - .env
    volumes:
      - postgre_docker_vol:/var/lib/postgresql/data
volumes:
  postgre_docker_vol:
    name: volume_db_postgres
    external: true
```

<h1>Docker Network Bridge</h1>

<p style="text-align: justify;">A rede bridge no Docker Compose refere-se ao modelo de rede padrão utilizado para conectar contêineres na mesma máquina host. Ela cria uma rede local isolada que facilita a comunicação entre os contêineres. </p>

<p style="text-align: justify;">Veja um exemplo utilizando a rede bridge com docker compose.</p>

```yaml
version: "3"
services:
  postgre:
    container_name: postgresql
    image: postgres:12.17
    ports:
      - 5432:5432
    env_file:
      - .env
    volumes:
      - postgre_docker_vol:/var/lib/postgresql/data
    networks:
      - db_net
volumes:
  postgre_docker_vol:
    name: postgre_volume
networks:
  db_net:
    name: db_network
    driver: bridge
```

<p style="text-align: justify;">Caso o seu arquivo compose possua mais do que um service é necessario especificar a network para todos.</p>

```yaml
version: "3"
services:
  postgre:
    container_name: postgresql
    image: postgres:12.17
    ports:
      - 5432:5432
    env_file:
      - .env
    volumes:
      - postgre_docker_vol:/var/lib/postgresql/data
    networks:
      - db_net
  nginx:
    container_name: nginx
    image: nginx
    ports:
      - 8080:80
    networks:
      - db_net
volumes:
  postgre_docker_vol:
    name: postgre_volume
networks:
  db_net:
    name: db_network
    driver: bridge
```

<p style="text-align: justify;">Da mesma maneira que vimos no volume, se caso ja possuimos um volume criado e precisamos usar esse volume, precisamos usar a flag <b>external</b>, com a network e a mesma coisa, veja um exemplo.</p>

```yaml
version: "3"
services:
  postgre:
    container_name: postgresql
    image: postgres:12.17
    ports:
      - 5432:5432
    env_file:
      - .env
    volumes:
      - postgre_docker_vol:/var/lib/postgresql/data
    networks:
      - db_net
volumes:
  postgre_docker_vol:
    name: postgre_volume
networks:
  db_net:
    name: db_network_bridge
    external: true
    driver: bridge
```