<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>


<p style="text-align: justify;">Você está dando os primeiros passos no uso de containers. E a melhor forma de iniciar no mundo de containers é usar em ambiente de desenvolvimento.</p>

<p style="text-align: justify;">Sua missão é ajudar a equipe de desenvolvimento a ter mais autonomia no desenvolvimento de projetos. E uma das reclamações da equipe é o setup local. </p>

<p style="text-align: justify;">Crie um comando para criar um banco de dados PostgreSQL no ambiente do desenvolvedor de uma forma que cumpra os seguintes requisitos:</p>

<ul>
  <li style="text-align: justify;">O nome do banco de dados deve ser curso_docker</li>
  <li style="text-align: justify;">O usuário de acesso ao banco deve ser docker_usr</li>
  <li style="text-align: justify;">A senha do usuário deve ser docker_pwd</li>
</ul>

<p style="text-align: justify;">Lembrando que a execução em container deve ser transparente pra quem está desenvolvendo. E que aqui você não precisa se preocupar com a perda dos dados do banco e nem nada disso, é apenas para desenvolvimento pontual.</p>

<p style="text-align: justify;">Coloque aqui embaixo o comando que a equipe deve usar pra criar um banco de dados PostgreSQL com esses requisitos.</p>

```bash
docker run -d --name postgresql -p 5432:5432 -e POSTGRES_DB = curso_docker -e POSTGRES_USER = docker_usr -e POSTGRES_PASSWORD = docker_pwd postgres
```