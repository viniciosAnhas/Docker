<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">O Docker Registry é um componente fundamental no ecossistema Docker, que é uma plataforma de contêineres. Ele serve como um repositório centralizado para armazenar e gerenciar imagens de contêineres Docker. Uma imagem de contêiner é uma unidade leve e independente que contém tudo o que é necessário para executar um aplicativo, incluindo o código, as bibliotecas e as dependências.</p>

<p style="text-align: justify;">
O Docker Registry permite que os desenvolvedores armazenem, compartilhem e distribuam suas imagens de contêineres de maneira eficiente. Existem dois tipos principais de Docker Registries:</p>

<ol>
  <li style="text-align: justify;"><b>Docker Hub</b>: Este é o registro público mantido pela Docker, Inc. Os desenvolvedores podem fazer o upload de suas imagens para o Docker Hub e compartilhá-las com a comunidade.</li>
  <li style="text-align: justify;"><b>Docker Registry Privado</b>: Empresas e organizações muitas vezes configuram seus próprios registros privados para armazenar imagens internas. Isso oferece mais controle sobre o acesso e a segurança das imagens de contêiner.</li>
</ol>

<p style="text-align: justify;">Os registros Docker armazenam diferentes versões de imagens, permitindo que os usuários acessem versões específicas de aplicativos. Além disso, o Docker Registry suporta recursos como controle de acesso, autenticação e criptografia, garantindo a segurança das imagens de contêineres durante o armazenamento e a transmissão.</p>

<p style="text-align: justify;">Para realizar o envio da imagem para o Docker Registry siga o passo a passo a seguir</p>

<p style="text-align: justify;">Abra o terminal ou prompt de comando e execute o seguinte comando <i>docker login -u seuUsuario</i>, substituindo <i>seuUsuario</i> pelo seu nome de usuário do Docker Hub.</p>

```bash
docker login -u seuUsuario
```

<p style="text-align: justify;">Construa a Imagem Docker, certifique-se de estar no diretório que contém o Dockerfile e os recursos necessários para a sua imagem. Execute o seguinte comando para construir a imagem. Substitua <i>nome-da-imagem</i> pelo nome desejado para a sua imagem e adicione opcionalmente uma tag (por exemplo, :latest).</p>

```bash
docker build -t <nome-da-imagem> .
```

<p style="text-align: justify;">Antes de enviar a imagem para o Docker Hub, é necessário adicionar a tag com o nome do seu repositório no Docker Hub.</p>

```bash
docker tag <nome-da-imagem> <seu-username>/<nome-da-imagem>
```

<p style="text-align: justify;">Faça o Push da Imagem para o Docker Hub use o seguinte comando para enviar a imagem</p>

```bash
docker push <seu-username>/<nome-da-imagem>
```

<p style="text-align: justify;">Isso enviará a imagem para o Docker Hub, tornando-a acessível a outras pessoas.</p>