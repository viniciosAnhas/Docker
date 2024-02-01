<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>


<p style="text-align: justify;">Utilize o comando <i>docker build -t</i> para construir a imagem docker, passando como parametro o nome da imagem e o local que se encontra do Dockerfile</p>

```bash
docker build -t ubuntu-curl .
```

<p style="text-align: justify;">No caso acima, estamos criando uma imagem chamada ubuntu-curl e indicando que o arquivo Dockerfile esta localizado na pasta atual.</p>

<p style="text-align: justify;">Para verificar se a imagem foi criada com sucesso execute o comando <i>docker images</i>.</p>

```bash
docker images
```

<p style="text-align: justify;">Agora iremos criar o container dessa imagem que acabamos de criar.</p>

```bash
docker run -it ubuntu-curl /bin/bash
```

<p style="text-align: justify;">Lista de Argumentos para Dockerfile</p>

<ul>
  <li style="text-align: justify;"><b>FROM</b>: Inicializa o build de uma imagem a partir de uma imagem base;</li>
  <li style="text-align: justify;"><b>RUN</b>: Utilizado para executar comando de terminal;</li>
  <li style="text-align: justify;"><b>WORKDIR</b>: Define o seu diretorio corrente;</li>
  <li style="text-align: justify;"><b>COPY</b>: Copia arquivos ou diretorios e adiciona ao sistema de arquivos da imagem;</li>
  <li style="text-align: justify;"><b>ADD</b>: Copia arquivos, diretorios ou arquivos remotos e adiciona ao sistema de arquivos da imagem;</li>
  <li style="text-align: justify;"><b>LABEL</b>: Adiciona metadados a imagem;</li>
  <li style="text-align: justify;"><b>ENV</b>: Define variaveis de ambiente;</li>
  <li style="text-align: justify;"><b>VOLUME</b>: Define volumes que devem ser definidos;</li>
  <li style="text-align: justify;"><b>ARG</b>: Define um argumento pra ser usado no processo de construção;</li>
  <li style="text-align: justify;"><b>EXPOSE</b>: Define que o container precisa expor a porta em questão;</li>
  <li style="text-align: justify;"><b>USER</b>: Define o usuario que vai ser usado;</li>
  <li style="text-align: justify;"><b>CMD</b>: Define o comando e/ou os parametros padrão;</li>
  <li style="text-align: justify;"><b>ENTRYPOINT</b>: Ajuda a voce a configurar um container que pode ser executado como um executavel.</li>
</ul>