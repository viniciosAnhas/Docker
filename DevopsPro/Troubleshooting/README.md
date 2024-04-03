<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">
O troubleshooting no Docker refere-se ao processo de identificar, diagnosticar e resolver problemas que possam surgir ao usar o Docker para construir, implantar e gerenciar contêineres.</p>

<p style="text-align: justify;">Veremos exmplos utilizando o <b>Docker info</b>, <b>Docker events</b>, <b>Docker log</b>, <b>Docker inspect</b>, <b>Docker top</b>, <b>Docker status</b> e <b>Docker exec</b>.</p>

<h1>Docker info</h1>

<p style="text-align: justify;">O comando Docker info fornece uma visão geral detalhada do ambiente Docker em execução no sistema. Aqui está um resumo das principais informações que podem ser obtidas com o comando Docker info.</p>

<ol>
  <li style="text-align: justify;">Informações do Docker Daemon</li>
  <ul>
    <li style="text-align: justify;">O comando docker info exibe informações sobre o Docker Daemon em execução, incluindo a versão do Docker, o número de contêineres em execução, o número de imagens disponíveis e o número de volumes em uso.</li>
  </ul>
  <li style="text-align: justify;">Informações do Sistema Operacional</li>
  <ul>
    <li style="text-align: justify;">O comando também fornece informações sobre o sistema operacional no qual o Docker está sendo executado, incluindo o nome e a versão do sistema operacional, a arquitetura do hardware e o tipo de processador.</li>
  </ul>
  <li style="text-align: justify;">Informações de Redes</li>
  <ul>
    <li style="text-align: justify;">São apresentadas informações sobre a configuração de rede do Docker, incluindo o número de redes disponíveis, o número de sub-redes, o número de contêineres conectados a redes específicas e detalhes sobre o driver de rede.</li>
  </ul>
</ol>

<p style="text-align: justify;">Em resumo, o comando docker info fornece uma visão geral abrangente do ambiente Docker em execução, incluindo informações sobre o Docker Daemon, sistema operacional, armazenamento, rede, segurança, kernel, hardware e configuração do cliente Docker. Essas informações são úteis para diagnóstico, solução de problemas e monitoramento do ambiente Docker.</p>

<h1>Docker events</h1>

<p style="text-align: justify;">O comando docker events é usado para monitorar eventos do Docker em tempo real. Aqui está um resumo sobre o docker events.</p>

<ol>
  <li style="text-align: justify;">Monitoramento em Tempo Real</li>
  <ul>
    <li style="text-align: justify;">O comando docker events permite que você monitore eventos do Docker em tempo real. Ele exibe eventos como criação, inicialização, parada e remoção de contêineres, redes e volumes.</li>
  </ul>
  <li style="text-align: justify;">Ampla Gama de Eventos</li>
  <ul>
    <li style="text-align: justify;">Uma variedade de eventos pode ser monitorada, incluindo eventos relacionados a contêineres (como criação, início, parada, morte, etc.), eventos relacionados a redes (como criação, conexão, desconexão, etc.) e eventos relacionados a volumes (como criação, montagem, desmontagem, etc.).</li>
  </ul>
  <li style="text-align: justify;">Informações Detalhadas</li>
  <ul>
    <li style="text-align: justify;">Cada evento exibido pelo docker events inclui informações detalhadas, como o tipo de evento, o ID do objeto afetado (por exemplo, ID do contêiner, ID da rede, etc.), o tipo de objeto (por exemplo, contêiner, rede, volume, etc.) e a hora em que o evento ocorreu.</li>
  </ul>
  <li style="text-align: justify;">Monitoramento de Mudanças de Estado</li>
  <ul>
    <li style="text-align: justify;">O docker events é útil para monitorar mudanças de estado em contêineres, redes e volumes. Por exemplo, você pode monitorar quando um novo contêiner é criado, quando um contêiner é iniciado ou quando um contêiner é removido.</li>
  </ul>
</ol>

<p style="text-align: justify;">Em resumo, o comando docker events é uma ferramenta útil para monitorar eventos do Docker em tempo real, fornecendo informações detalhadas sobre mudanças de estado e atividades no ambiente Docker. Ele é amplamente utilizado para monitoramento, automação, segurança e auditoria em ambientes Docker.</p>

<h1>Docker logs</h1>

<p style="text-align: justify;">O comando docker logs é utilizado para visualizar os logs de um contêiner específico no Docker. Aqui está um resumo sobre o docker logs:</p>

<ol>
  <li style="text-align: justify;">Visualização de Logs</li>
  <ul>
    <li style="text-align: justify;">O comando docker logs é usado para visualizar os logs gerados por um contêiner em tempo real ou em um determinado período de tempo.</li>
  </ul>
  <li style="text-align: justify;">Logs Multilinha</li>
  <ul>
    <li style="text-align: justify;">Os logs gerados por um contêiner podem ser multilinha, o que significa que uma única mensagem de log pode ser dividida em várias linhas. O comando docker logs exibe essas mensagens multilinha de forma legível.</li>
  </ul>
  <li style="text-align: justify;">Identificação de Problemas</li>
  <ul>
    <li style="text-align: justify;">A visualização dos logs de um contêiner é útil para identificar problemas de execução, erros de aplicativos, mensagens de depuração e eventos significativos.</li>
  </ul>
  <li style="text-align: justify;">Monitoramento de Saúde</li>
  <ul>
    <li style="text-align: justify;">Os logs de um contêiner podem fornecer informações sobre a saúde e o status do aplicativo em execução dentro do contêiner. O monitoramento regular dos logs pode ajudar a identificar problemas de desempenho ou de disponibilidade.</li>
  </ul>
</ol>

<p style="text-align: justify;">Você pode visualizar os logs de um contêiner especificando seu nome ou ID como argumento para o comando docker logs.</p>

```bash
docker logs [nome_do_contêiner ou ID_do_contêiner]
```

<p style="text-align: justify;">Você pode filtrar os logs por diferentes critérios, como nível de log (por exemplo, erro, aviso, informação), data/hora ou padrões de texto específicos.</p>

```bash
docker logs --since="2022-01-01" [nome_do_contêiner ou ID_do_contêiner]
```

<p style="text-align: justify;">Os logs de um contêiner podem ser redirecionados para um arquivo local para análise posterior ou armazenamento. Isso pode ser feito usando redirecionamento de saída.</p>

```bash
docker logs [nome_do_contêiner ou ID_do_contêiner] > logs.txt
```

<p style="text-align: justify;">O comando docker logs é uma ferramenta útil para visualizar e analisar os logs de contêineres no Docker, permitindo que os usuários obtenham informações sobre o funcionamento e o estado dos aplicativos em execução dentro dos contêineres. Ele é amplamente utilizado para solução de problemas, monitoramento e manutenção de ambientes Docker.</p>

<h1>Docker inspect</h1>

<p style="text-align: justify;">O comando docker inspect é utilizado para obter informações detalhadas sobre um ou mais objetos Docker, como contêineres, imagens, volumes, redes e plugins. Aqui está um resumo sobre o docker inspect.</p>

<ol>
  <li style="text-align: justify;">Informações Detalhadas</li>
  <ul>
    <li style="text-align: justify;">O comando docker inspect fornece informações detalhadas sobre um objeto Docker específico. Isso inclui metadados, configurações, estados e outras propriedades do objeto.</li>
  </ul>
  <li style="text-align: justify;">Formato JSON</li>
  <ul>
    <li style="text-align: justify;">As informações retornadas pelo docker inspect são formatadas em JSON, o que permite fácil análise e processamento programático dos dados.</li>
  </ul>
  <li style="text-align: justify;">Objetos Suportados</li>
  <ul>
    <li style="text-align: justify;">O docker inspect pode ser usado para inspecionar diversos tipos de objetos Docker, incluindo contêineres, imagens, volumes, redes e plugins.</li>
  </ul>
  <li style="text-align: justify;">Detalhes de Configuração</li>
  <ul>
    <li style="text-align: justify;">Para contêineres, por exemplo, o comando docker inspect fornece informações sobre a configuração do contêiner, como variáveis de ambiente, comandos de inicialização, configurações de rede e montagens de volumes.</li>
  </ul>
</ol>

<p style="text-align: justify;">Você pode inspecionar um objeto Docker especificando seu nome ou ID como argumento para o comando docker inspect.
</p>

```bash
docker inspect [nome_do_objeto ou ID_do_objeto]
```

<p style="text-align: justify;">O comando docker inspect é uma ferramenta poderosa para obter informações detalhadas sobre objetos Docker e é amplamente utilizado para solução de problemas, automação, análise de configurações e melhorias de segurança. Ele fornece uma visão profunda do ambiente Docker, permitindo que os usuários compreendam e controlem melhor seus recursos e configurações.</p>

<h1>Docker top</h1>

<p style="text-align: justify;">O comando docker top é usado para exibir os processos em execução dentro de um contêiner Docker. Aqui está um resumo sobre o docker top.</p>

<ol>
  <li style="text-align: justify;">Exibição de Processos</li>
  <ul>
    <li style="text-align: justify;">O docker top mostra os processos em execução dentro de um contêiner Docker, semelhante ao comando top no Linux.</li>
  </ul>
  <li style="text-align: justify;">Visão Geral dos Processos</li>
  <ul>
    <li style="text-align: justify;">O comando exibe uma visão geral dos processos dentro do contêiner, incluindo informações como PID (Identificador do Processo), nome do usuário, tempo de CPU consumido, tempo de execução e o comando sendo executado.</li>
  </ul>
  <li style="text-align: justify;">Identificação de Problemas</li>
  <ul>
    <li style="text-align: justify;">O comando pode ser usado para diagnosticar problemas dentro de um contêiner, identificando processos em execução que podem estar consumindo recursos excessivos ou causando problemas de desempenho.</li>
  </ul>
  <li style="text-align: justify;">Monitoramento de Atividades</li>
  <ul>
    <li style="text-align: justify;">O docker top é útil para monitorar as atividades em tempo real dentro de um contêiner, permitindo que os usuários identifiquem processos em execução, recursos consumidos e atividades de sistema.</li>
  </ul>
</ol>

<p style="text-align: justify;">Você pode listar os processos de um contêiner específico, especificando seu nome ou ID como argumento para o comando docker top.</p>

```bash
docker top [nome_do_contêiner ou ID_do_contêiner]
```

<p style="text-align: justify;">O comando docker top é uma ferramenta útil para visualizar os processos em execução dentro de contêineres Docker e é frequentemente usado para monitoramento em tempo real, diagnóstico de problemas e análise de desempenho. Ele fornece uma visão instantânea das atividades dentro de um contêiner, permitindo que os usuários compreendam melhor o que está acontecendo dentro do ambiente de contêineres.</p>

<h1>Docker stats</h1>

<p style="text-align: justify;">O comando docker stats é utilizado para exibir estatísticas de uso de recursos de contêineres em tempo real. Aqui está um resumo sobre o docker stats.</p>

<ol>
  <li style="text-align: justify;">Monitoramento de Recursos</li>
  <ul>
    <li style="text-align: justify;">O docker stats exibe estatísticas em tempo real sobre o uso de CPU, memória, rede e E/S (entrada/saída) de contêineres Docker em execução.</li>
  </ul>
  <li style="text-align: justify;">Visão Geral de Recursos</li>
  <ul>
    <li style="text-align: justify;">O comando fornece uma visão geral dos recursos utilizados por um contêiner, incluindo o uso atual, uso médio, limite e percentual de uso em relação aos recursos disponíveis.</li>
  </ul>
  <li style="text-align: justify;">Identificação de Problemas</li>
  <ul>
    <li style="text-align: justify;">O docker stats é útil para identificar problemas de desempenho ou gargalos de recursos, permitindo que os usuários identifiquem rapidamente contêineres que estão consumindo recursos excessivos.</li>
  </ul>
</ol>

<p style="text-align: justify;">Você pode exibir estatísticas para um contêiner específico especificando seu nome ou ID como argumento para o comando docker stats.</p>

```bash
docker stats [nome_do_contêiner ou ID_do_contêiner]
```

<p style="text-align: justify;">O comando docker stats é uma ferramenta valiosa para monitoramento de recursos em tempo real em contêineres Docker. Ele fornece uma visão detalhada e atualizada do uso de recursos, permitindo que os usuários identifiquem rapidamente problemas de desempenho e façam ajustes conforme necessário.</p>

<h1>Docker exec</h1>

<p style="text-align: justify;">O comando docker exec é usado para executar comandos dentro de um contêiner Docker em execução. Aqui está um resumo sobre o docker exec.</p>

<ol>
  <li style="text-align: justify;">Execução de Comandos</li>
  <ul>
    <li style="text-align: justify;">O docker exec permite executar comandos dentro de um contêiner Docker em execução, sem a necessidade de abrir uma nova sessão de shell no contêiner.</li>
  </ul>
  <li style="text-align: justify;">Execução de Comandos em Contêineres em Execução.</li>
  <ul>
    <li style="text-align: justify;">O docker exec só pode ser usado em contêineres que estão em execução. Se um contêiner estiver parado, você precisará iniciar antes de poder executar comandos dentro dele.</li>
  </ul>
  <li style="text-align: justify;">Comunicação com Contêineres em Rede</li>
  <ul>
    <li style="text-align: justify;">O docker exec pode ser usado para executar comandos em contêineres conectados à mesma rede Docker, facilitando a comunicação entre contêineres.</li>
  </ul>
  <li style="text-align: justify;">Execução de Comandos em Contêineres em Produção</li>
  <ul>
    <li style="text-align: justify;">O docker exec pode ser usado em ambientes de produção para executar comandos de manutenção ou depuração em contêineres sem interromper os serviços em execução.</li>
  </ul>
</ol>

<p style="text-align: justify;">Você pode especificar o nome ou o ID do contêiner como argumento para o comando docker exec.</p>

```bash
docker exec [nome_do_contêiner ou ID_do_contêiner] [comando]
```

<p style="text-align: justify;">Você pode executar comandos dentro do contêiner como um usuário específico, especificando a opção -u.</p>

```bash
docker exec -u [usuário] [nome_do_contêiner ou ID_do_contêiner] [comando]
```

<p style="text-align: justify;">O comando docker exec é uma ferramenta essencial para interagir com contêineres Docker em execução, permitindo a execução de comandos, depuração e manutenção dentro do ambiente do contêiner de forma conveniente e eficiente.</p>