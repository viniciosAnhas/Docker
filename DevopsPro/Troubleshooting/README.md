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