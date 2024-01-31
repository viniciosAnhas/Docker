<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>


<p>Utilize o comando <i>docker build -t</i> para construir a imagem docker, passando como parametro o nome da imagem e o local que se encontra do Dockerfile</p>

```docker
docker build -t ubuntu-curl .
```

<p>No caso acima, estamos criando uma imagem chamada ubuntu-curl e indicando que o arquivo Dockerfile esta localizado na pasta atual.</p>

<p>Para verificar se a imagem foi criada com sucesso execute o comando <i>docker images</i>.</p>

```docker
docker images
```

<p>Agora iremos criar o container dessa imagem que acabamos de criar.</p>

```docker
docker run -it ubuntu-curl /bin/bash
```

<p>Lista de Argumentos para Dockerfile</p>

<ul>
  <li><b>FROM</b>: Inicializa o build de uma imagem a partir de uma imagem base;</li>
  <li><b>RUN</b>: Utilizado para executar comando de terminal;</li>
  <li><b>WORKDIR</b>: Define o seu diretorio corrente;</li>
  <li><b>COPY</b>: Copia arquivos ou diretorios e adiciona ao sistema de arquivos da imagem;</li>
  <li><b>ADD</b>: Copia arquivos, diretorios ou arquivos remotos e adiciona ao sistema de arquivos da imagem;</li>
  <li><b>LABEL</b>: Adiciona metadados a imagem;</li>
  <li><b>ENV</b>: Define variaveis de ambiente;</li>
  <li><b>VOLUME</b>: Define volumes que devem ser definidos;</li>
  <li><b>ARG</b>: Define um argumento pra ser usado no processo de construção;</li>
  <li><b>EXPOSE</b>: Define que o container precisa expor a porta em questão;</li>
  <li><b>USER</b>: Define o usuario que vai ser usado;</li>
  <li><b>CMD</b>: Define o comando e/ou os parametros padrão;</li>
  <li><b>ENTRYPOINT</b>: Ajuda a voce a configurar um container que pode ser executado como um executavel.</li>
</ul>