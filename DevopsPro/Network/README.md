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