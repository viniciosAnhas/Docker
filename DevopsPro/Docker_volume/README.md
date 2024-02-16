<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">No Docker, volumes são recursos que possibilitam a persistência e o compartilhamento de dados entre contêineres e o host. Eles oferecem uma maneira flexível de lidar com o armazenamento de dados, permitindo que informações cruciais sejam mantidas independentemente do ciclo de vida de um contêiner específico. Alguns pontos-chave sobre volumes no Docker incluem:</p>

<ol>
  <li style="text-align: justify;"><b>Persistência de Dados</b></li>
  <ul>
    <li style="text-align: justify;">Volumes permitem que dados sejam mantidos mesmo quando um contêiner é removido, proporcionando persistência além do ciclo de vida do contêiner.</li>
  </ul>
  <li style="text-align: justify;"><b>Compartilhamento de Dados</b></li>
  <ul>
    <li style="text-align: justify;">Volumes facilitam o compartilhamento de dados entre contêineres, permitindo que diferentes contêineres acessem e compartilhem informações.</li>
  </ul>
  <li style="text-align: justify;"><b>Independência do Sistema de Arquivos do Contêiner</b></li>
  <ul>
    <li style="text-align: justify;">Dados armazenados em volumes não fazem parte do sistema de arquivos do contêiner, o que significa que são mais flexíveis e podem ser compartilhados entre contêineres.</li>
  </ul>
  <li style="text-align: justify;"><b>Backup e Restauração Facilitados</b></li>
  <ul>
    <li style="text-align: justify;">A gestão de volumes simplifica operações de backup e restauração de dados, fornecendo uma maneira robusta de preservar informações importantes.</li>
  </ul>
  <li style="text-align: justify;"><b>Backup e Restauração Facilitados</b></li>
  <ul>
    <li style="text-align: justify;">A gestão de volumes simplifica operações de backup e restauração de dados, fornecendo uma maneira robusta de preservar informações importantes.</li>
  </ul>
</ol>

<h1>Bind mount</h1>

<p style="text-align: justify;">Bind mount no Docker refere-se a uma técnica que permite montar um diretório ou arquivo específico do sistema de arquivos do host diretamente dentro de um contêiner. Isso estabelece uma conexão entre o sistema de arquivos do host e o sistema de arquivos do contêiner, compartilhando dados em tempo real. Aqui estão os principais pontos sobre bind mount:</p>

<ol>
  <li style="text-align: justify;"><b>Montagem de Diretórios ou Arquivos</b></li>
  <ul>
    <li style="text-align: justify;">O bind mount permite montar diretórios ou arquivos específicos do host diretamente no contêiner.</li>
  </ul>
  <li style="text-align: justify;"><b>Persistência de Dados</b></li>
  <ul>
    <li style="text-align: justify;">Diferentemente dos volumes do Docker, que são gerenciados pelo Docker e armazenam dados independentemente do ciclo de vida do contêiner, os bind mounts estão diretamente vinculados ao sistema de arquivos do host, proporcionando persistência de dados no host.</li>
  </ul>
  <li style="text-align: justify;"><b>Atualizações em Tempo Real</b></li>
  <ul>
    <li style="text-align: justify;">Alterações feitas no diretório ou arquivo do host refletem imediatamente no contêiner e vice-versa. Isso é útil para desenvolvimento, depuração e situações em que as alterações precisam ser refletidas instantaneamente em ambas as direções.</li>
  </ul>
</ol>

<p style="text-align: justify;">Vamos ver um exemplo de Bind mount.</p>

```bash
docker run -v /caminho/no/host:/caminho/no/contêiner imagem-do-contêiner
```

<h1>Docker Volume</h1>

<p style="text-align: justify;">Os volumes gerenciados no Docker referem-se a uma forma mais integrada e controlada de lidar com o armazenamento de dados persistente. Eles são criados e gerenciados pelo próprio Docker, proporcionando maior automação e abstrações simplificadas em comparação com bind mounts. Aqui estão os principais pontos sobre volumes gerenciados:</p>

<ol>
  <li style="text-align: justify;"><b>Criação e Gerenciamento Automático</b></li>
  <ul>
    <li style="text-align: justify;">Os volumes gerenciados são criados e gerenciados automaticamente pelo Docker. Não há necessidade de criar diretórios no host ou especificar caminhos absolutos.</li>
  </ul>
  <li style="text-align: justify;"><b>Independência do Ciclo de Vida do Contêiner</b></li>
  <ul>
    <li style="text-align: justify;">Assim como bind mounts, os volumes gerenciados são independentes do ciclo de vida dos contêineres. Eles persistem mesmo após a remoção do contêiner que os utilizou.</li>
  </ul>
  <li style="text-align: justify;"><b>Nomes Amigáveis</b></li>
  <ul>
    <li style="text-align: justify;">Os volumes gerenciados podem ser referenciados por nomes amigáveis em vez de caminhos no sistema de arquivos do host. Isso torna mais fácil e legível trabalhar com volumes em ambientes distribuídos.</li>
  </ul>
  <li style="text-align: justify;"><b>Segurança e Controle</b></li>
  <ul>
    <li style="text-align: justify;">Os volumes gerenciados oferecem maior controle sobre permissões e configurações de segurança em comparação com bind mounts, uma vez que são gerenciados pela própria infraestrutura do Docker.</li>
  </ul>
</ol>

<p style="text-align: justify;">Veja a seguir um exmplo de utilização do Docker Volume, iremos utilizar o comando <i>docker volume create</i> para criar o nosso volume.</p>

```bash
docker volume create primeiro-volume
```

<p style="text-align: justify;">Para visualizar os volumes criados basta usar o comando <i>docker volume ls</i>.</p>

```bash
docker volume ls
```

<p style="text-align: justify;">Iremos mapear o volume criado com um container.</p>

```bash
docker run -it --mount type=volume,source=primeiro-volume,target=/app ubuntu /bin/bash
```

<p style="text-align: justify;">Utilize o comando <i>docker volume rm</i> para excluir o volume.</p>

```bash
docker volume rm primeiro-volume
```

<p style="text-align: justify;">É possivel acessar o diretorio do volume utilizando o comando <i>docker volume inspect</i>, porem caso você esteja usando Windows ou Mac, você ira percebr que esse diretorio nao existe na sua maquina, já que o Docker funciona em virtualização nesses dois sistemas operacionais.</p>

```bash
docker volume inspect primeiro-volume
```

<p style="text-align: justify;">Podemos utilizar o volume em um Dockerfile, podendo assim criar imagens personalizadas, veja o exemplo a seguir.</p>

```Dockerfile
FROM ubuntu

VOLUME /app
WORKDIR /app
```

<p style="text-align: justify;">Para que possamos utilizar essa imagem utilize o seguinte comando.</p>

```bash
docker run -it -v primeiro-volume:/app ubuntu-volume
```

<h1>Storage tmpfs</h1>

<p style="text-align: justify;">O tmpfs no Docker refere-se a uma opção de armazenamento temporário em memória que pode ser montada em um contêiner. Aqui estão os pontos-chave sobre o tmpfs no Docker:</p>

<ol>
  <li style="text-align: justify;"><b>Armazenamento em Memória</b></li>
  <ul>
    <li style="text-align: justify;">tmpfs é uma opção de armazenamento baseada em memória RAM, permitindo a criação de sistemas de arquivos temporários diretamente na memória do sistema.</li>
  </ul>
  <li style="text-align: justify;"><b>Temporário e Volátil</b></li>
  <ul>
    <li style="text-align: justify;">Diferentemente de volumes persistentes, o tmpfs é temporário e volátil. Os dados armazenados são perdidos quando o contêiner é removido ou o sistema é reiniciado.</li>
  </ul>
  <li style="text-align: justify;"><b>Útil para Dados Temporários</b></li>
  <ul>
    <li style="text-align: justify;">tmpfs é útil para armazenar dados temporários ou arquivos que não precisam ser persistentes entre execuções de contêineres.</li>
  </ul>
</ol>

<p style="text-align: justify;">Veja agora um exemplo utilizando o tmpfs.</p>

```bash
docker run -it --mount type=tmpfs,target=/app ubuntu /bin/bash
```