<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>


<p style="text-align: justify;">Pra finalizar essa etapa, crie o comando pra criar o banco de dados MongoDB usando os requisitos abaixo:</p>

<ul>
  <li style="text-align: justify;">O usuário root do banco deve ser mongo_usr</li>
  <li style="text-align: justify;">A senha do usuário root deve ser mongo_pwd</li>
</ul>

<p style="text-align: justify;">Lembrando que a execução em container deve ser transparente pra quem está desenvolvendo. E que aqui você não precisa se preocupar com a perda dos dados do banco e nem nada disso, é apenas para desenvolvimento pontual.</p>

<p style="text-align: justify;">Coloque aqui embaixo o comando que a equipe deve usar pra criar um banco de dados MongoDB com esses requisitos:</p>

```bash
docker run -d --name mongodb -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME = mongo_usr -e MONGO_INITDB_ROOT_PASSWORD = mongo_pwd mongo
```