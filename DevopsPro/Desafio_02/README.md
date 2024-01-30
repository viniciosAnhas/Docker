<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>


<p>Agora que a equipe tem como criar o banco de dados Postgre, crie o comando pra criar o banco de dados MySQL usando os requisitos abaixo:</p>

<ul>
  <li>O nome do banco de dados deve ser docker_db</li>
  <li>O usuário de acesso ao banco deve ser docker_usr</li>
  <li>A senha do usuário deve ser docker_pwd</li>
</ul>

<p>Lembrando que a execução em container deve ser transparente pra quem está desenvolvendo. E que aqui você não precisa se preocupar com a perda dos dados do banco e nem nada disso, é apenas para desenvolvimento pontual..</p>

<p>Coloque aqui embaixo o comando que a equipe deve usar pra criar um banco de dados MySQL com esses requisitos:</p>

```docker
docker run -d --name mysql -p 3306:3306 -e MYSQL_DATABASE = docker_db -e MYSQL_USER = docker_usr -e MYSQL_PASSWORD = docker_pwd mysql
```