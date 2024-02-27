<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">As redes no Docker permitem a comunicação entre contêineres e a conexão de contêineres com a rede do host ou com redes externas. Aqui estão os principais pontos sobre redes no Docker:</p>

<ol>
  <li style="text-align: justify;">Isolamento de Rede</li>
  <ul>
    <li style="text-align: justify;">Cada contêiner Docker é executado em sua própria rede isolada por padrão, o que impede a comunicação direta entre contêineres, a menos que configurado explicitamente.</li>
  </ul>
  <li style="text-align: justify;">Modelo de Rede Bridge</li>
  <ul>
    <li style="text-align: justify;">O Docker usa um modelo de rede de bridge por padrão. Isso cria uma rede local onde cada contêiner recebe um endereço IP exclusivo e pode se comunicar com outros contêineres na mesma rede.</li>
  </ul>
  <li style="text-align: justify;">Exposição de Portas</li>
  <ul>
    <li style="text-align: justify;">Contêineres podem expor portas para permitir que outros contêineres ou serviços externos se conectem a eles. A exposição de portas é configurada no Dockerfile ou no comando <i>docker run</i>.</li>
  </ul>
  <li style="text-align: justify;">Comunicação entre Contêineres</li>
  <ul>
    <li style="text-align: justify;">Contêineres podem se comunicar entre si usando nomes de contêiner ou endereços IP, dependendo da rede configurada.</li>
  </ul>
  <li style="text-align: justify;">Redes Personalizadas</li>
  <ul>
    <li style="text-align: justify;">Além da rede de bridge padrão, é possível criar redes personalizadas para isolar grupos específicos de contêineres e controlar a comunicação entre eles.</li>
  </ul>
  <li style="text-align: justify;">Conexão com a Rede do Host</li>
  <ul>
    <li style="text-align: justify;">Contêineres podem ser conectados diretamente à rede do host para terem acesso direto aos recursos da máquina host.</li>
  </ul>
</ol>

<h1>Rede Bridge</h1>

<p style="text-align: justify;">A rede bridge no Docker é um modelo de rede padrão que facilita a comunicação entre contêineres em um mesmo host. Aqui estão os principais pontos sobre a rede bridge:</p>

<ol>
  <li style="text-align: justify;">Padrão de Rede</li>
  <ul>
    <li style="text-align: justify;">A rede bridge é o modelo de rede padrão para contêineres no Docker, criando uma rede local no host onde os contêineres podem se comunicar.</li>
  </ul>
  <li style="text-align: justify;">Endereços IP Únicos</li>
  <ul>
    <li style="text-align: justify;">Cada contêiner conectado à rede bridge recebe um endereço IP único dentro dessa rede, permitindo a comunicação entre eles por meio de suas respectivas interfaces de rede virtuais.</li>
  </ul>
  <li style="text-align: justify;">Isolamento por Padrão</li>
  <ul>
    <li style="text-align: justify;">Contêineres em uma rede bridge são isolados por padrão, o que significa que eles não podem se comunicar diretamente com contêineres fora dessa rede, a menos que explicitamente configurado.</li>
  </ul>
  <li style="text-align: justify;">DNS Interno</li>
  <ul>
    <li style="text-align: justify;">O Docker fornece um DNS interno para contêineres na rede bridge, permitindo que eles se comuniquem usando os nomes dos contêineres em vez de IPs.</li>
  </ul>
  <li style="text-align: justify;">Conexão a Redes Externas</li>
  <ul>
    <li style="text-align: justify;">Além de sua rede local, um contêiner na rede bridge pode ser conectado a redes externas para comunicação com recursos fora do host Docker.</li>
  </ul>
</ol>

<p style="text-align: justify;">Vamos ver a seguir na pratica como trabalhar com networks no docker, iremos utilizar o comando <i>docker network ls</i> para listar todas as network do docker.</p>

```bash
docker network ls
```

<p style="text-align: justify;">Quando executamos o comando vemos que possuimos tres redes, <b>none</b>, <b>host</b> e <b>bridge</b>. A rede none é justamente quando você isola o container e nao possui nenhuma conectividade de rede, a rede host é utilizada quando se conecta o container na rede local da sua maquina fisica, já a rede bridge funciona bem parecido com um switch de rede em que voce pode ligar diversos containers sendo assim possivel a comunicação entre eles.</p>

<p style="text-align: justify;">Por padrão todo container é executado na rede brigde, podemos usar o comando <i>docker container inspect nomedocontainer</i>, e verificar as networks.</p>

```bash
docker container inspct nomedocontainer
```

<p style="text-align: justify;">A criação de uma rede bridge no Docker envolve a configuração de uma rede local isolada, permitindo que contêineres na mesma rede comuniquem entre si. Utilize o comando <i>docker network create nomedarede</i> para cria a sua primeira rede.</p>

```bash
docker network create nomedarede
```

<p style="text-align: justify;">Iremos executar um container com essa rede que criamos a seguir, porem como vamos trabalher com rede que podemos acessar um container nessa mesma network iremos utilizar a resolução de nome utilizando a flag <b>--name</b>, veja o exemplo a seguir.</p>

```bash
docker run --name ngninx --network nomedarede -d nginx
```

<p style="text-align: justify;">Também é possivel criar uma nova network passando os parameetros de subnet e de gateway, utilize o comando a seguir.</p>

```bash
docker network create --subnet=10.0.0.0/16 --gateway=10.0.0.1 novaredee
```

<p style="text-align: justify;">Em resumo, a criação de uma rede bridge no Docker envolve a criação de uma rede local isolada, a conexão de contêineres a essa rede. Isso facilita a comunicação eficiente entre contêineres e fornece um ambiente isolado para aplicações em execução.</p>

<h1>Rede Host</h1>

<p style="text-align: justify;">
A rede host no Docker é um modelo de rede que permite que um contêiner compartilhe diretamente o namespace de rede do host. Isso elimina o isolamento de rede entre o host e o contêiner, proporcionando vantagens em termos de desempenho. Aqui está um resumo sobre a rede host no Docker:</p>

<ol>
  <li style="text-align: justify;">Compartilhamento do Namespace de Rede</li>
  <ul>
    <li style="text-align: justify;">Na rede host, o contêiner compartilha diretamente o namespace de rede do host, o que significa que ele usa a pilha de rede do host, incluindo interfaces, endereços IP e portas.</li>
  </ul>
  <li style="text-align: justify;">Desempenho Aprimorado</li>
  <ul>
    <li style="text-align: justify;">Por não introduzir uma camada adicional de virtualização da rede, a rede host pode oferecer melhor desempenho em comparação com outros modelos de rede, como bridge.</li>
  </ul>
  <li style="text-align: justify;">Mesma Rede do Host</li>
  <ul>
    <li style="text-align: justify;">O contêiner na rede host utiliza a mesma rede que o host, tornando-o acessível diretamente na mesma rede local.</li>
  </ul>
  <li style="text-align: justify;">Exposição Direta de Portas</li>
  <ul>
    <li style="text-align: justify;">Ao contrário de outros modelos de rede, como bridge, a rede host não requer a exposição de portas para permitir a comunicação com serviços dentro do contêiner. Os serviços são acessíveis diretamente nas mesmas portas do host.</li>
  </ul>
  <li style="text-align: justify;">Conexão com Redes Externas</li>
  <ul>
    <li style="text-align: justify;">Contêineres na rede host podem se comunicar diretamente com recursos fora do host, conectando-se a redes externas, se necessário.</li>
  </ul>
</ol>

<p style="text-align: justify;">Veja o exemplo a seguir utilizando a rede host.</p>

```bash
docker run --network=host -d meucontainer
```

<p style="text-align: justify;">A escolha entre redes bridge e host depende dos requisitos específicos da aplicação. A rede host é mais adequada quando o desempenho é crucial, e a aplicação precisa de acesso direto aos recursos da máquina host. No entanto, a falta de isolamento de rede pode ser uma consideração importante em termos de segurança e gerenciamento de recursos em ambientes específicos.</p>

<h1>Rede None</h1>

<p style="text-align: justify;">A rede "none" no Docker é um modelo de rede que isola completamente um contêiner da rede. Isso significa que o contêiner não possui interfaces de rede e não pode se comunicar com a rede do host ou outros contêineres. Aqui estão os principais pontos sobre a rede "none" no Docker:</p>

<ol>
  <li style="text-align: justify;">Isolamento Completo</li>
  <ul>
    <li style="text-align: justify;">A rede "none" isola totalmente o contêiner da rede, removendo todas as interfaces de rede do contêiner.</li>
  </ul>
  <li style="text-align: justify;">Sem Acesso à Rede do Host</li>
  <ul>
    <li style="text-align: justify;">Contêineres na rede "none" não têm acesso à rede do host. Eles não podem se comunicar com outros contêineres ou serviços no host.</li>
  </ul>
  <li style="text-align: justify;">Sem Exposição de Portas</li>
  <ul>
    <li style="text-align: justify;">Contêineres na rede "none" não podem expor portas para se comunicarem com serviços externos. Eles ficam isolados da rede e dos serviços externos.</li>
  </ul>
  <li style="text-align: justify;">Utilizado para Ambientes Isolados</li>
  <ul>
    <li style="text-align: justify;">A rede "none" é útil em cenários em que é necessário um isolamento total da rede, como para contêineres que executam tarefas específicas sem a necessidade de conectividade de rede.</li>
  </ul>
  <li style="text-align: justify;">Sem DNS Interno</li>
  <ul>
    <li style="text-align: justify;">Contêineres na rede "none" não têm DNS interno, o que significa que a resolução de nomes pode ser desafiadora sem uma configuração adicional.</li>
  </ul>
</ol>

<p style="text-align: justify;">Veja o exemplo a seguir utilizando a rede none.</p>

```bash
docker run --network=none -d meucontainer
```

<p style="text-align: justify;">Em resumo, a rede "none" no Docker fornece isolamento total do contêiner em termos de conectividade de rede. É útil em situações em que a rede é desnecessária ou quando a segurança e o isolamento são prioridades. No entanto, seu uso é limitado a casos específicos devido à falta de conectividade de rede.</p>