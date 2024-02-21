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