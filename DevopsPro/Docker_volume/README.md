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