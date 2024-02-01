<div align="center">
  <div>
    <img height = "150" width = "150" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original-wordmark.svg" />
  </div>
</div>

<p style="text-align: justify;">O multistage build no Docker é uma técnica que permite otimizar o processo de construção de imagens, reduzindo o tamanho final da imagem resultante. Essa abordagem envolve a criação de múltiplos estágios (fases) dentro de um único Dockerfile, cada um servindo a um propósito específico durante o processo de construção.</p>

<p style="text-align: justify;">A ideia fundamental do multistage build é separar as etapas de desenvolvimento e compilação das etapas de produção. O Dockerfile inclui várias instruções FROM, onde cada FROM representa um estágio diferente. Cada estágio pode ter sua própria base e realizar tarefas específicas, como compilar código, copiar artefatos e configurar o ambiente.</p>

<p style="text-align: justify;">Principais pontos do multistage build:</p>

<ol>
  <li style="text-align: justify;"><b>Estágios Múltiplos</b></li>
  <ul>
    <li style="text-align: justify;">O Dockerfile inclui várias instruções FROM, cada uma representando um estágio distinto.</li>
  </ul>

  <li style="text-align: justify;"><b>Redução do Tamanho da Imagem</b></li>
  <ul>
    <li style="text-align: justify;">A principal vantagem é a redução do tamanho final da imagem, pois apenas os artefatos necessários para a execução do aplicativo são incluídos no estágio final.</li>
  </ul>

  <li style="text-align: justify;"><b>Separação de Ambientes de Desenvolvimento e Produção</b></li>
  <ul>
    <li style="text-align: justify;">Os estágios iniciais podem conter dependências e ferramentas de compilação necessárias apenas durante o desenvolvimento, enquanto o estágio final contém apenas o que é essencial para a execução do aplicativo em produção.</li>
  </ul>

  <li style="text-align: justify;"><b>Estrutura Modular</b></li>
  <ul>
    <li style="text-align: justify;">Facilita a criação de imagens mais modulares e compreensíveis, dividindo o processo de construção em etapas lógicas e isoladas.</li>
  </ul>
</ol>

<p style="text-align: justify;">Veja a seguir um exemplo de Dockerfile utilizando multistage</p>

```Dockerfile
FROM golang:1.18.10 as build

WORKDIR /build
COPY . .

RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main .

FROM alpine:3.18.4 as app

WORKDIR /app
COPY --from=build /build/main .
CMD [ "./main" ]
```

<ol>
  <li style="text-align: justify;"><b>Estágio de Construção (build)</b></li>
  <ul>
    <li style="text-align: justify;"><b>FROM golang:1.18.10 as build</b>: Este é o primeiro estágio, onde a imagem base é o ambiente Go. O alias <b>build</b> é usado para se referir a este estágio posteriormente.</li>
    <li style="text-align: justify;"><b>WORKDIR /build</b>: Define o diretório de trabalho como <b>/build</b></li>
    <li style="text-align: justify;"><b>COPY . .</b>: Copia todos os arquivos do contexto de construção para o diretório de trabalho no contêiner.</li>
    <li style="text-align: justify;"><b>RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main .</b>: Compila o código Go, criando um executável chamado <b>main</b>. As opções fornecidas desativam o uso do CGO, definem o sistema operacional como Linux e especificam o nome do executável.</li>
  </ul>
  <li style="text-align: justify;"><b>Estágio de Produção (app):</b></li>
  <ul>
    <li style="text-align: justify;"><b>FROM alpine:3.18.4 as app</b>: Este é o segundo estágio, usando uma imagem Alpine Linux leve como base. O alias <b>app</b> é usado para referenciar este estágio.</li>
    <li style="text-align: justify;"><b>WORKDIR /app</b>: Define o diretório de trabalho como <b>/app</b>.</li>
    <li style="text-align: justify;"><b>COPY --from=build /build/main .</b>: Copia o executável <b>main</b> do estágio de construção (<b>build</b>) para o diretório de trabalho no segundo estágio (<b>app</b>).</li>
    <li style="text-align: justify;"><b>CMD [ "./main" ]</b>: Define o comando padrão a ser executado quando um contêiner baseado nesta imagem for iniciado. Neste caso, executa o executável <b>main</b>.</li>
  </ul>
</ol>

<p style="text-align: justify;">Este Dockerfile utiliza o multistage build para separar as etapas de construção e produção, resultando em uma imagem final mais leve, que contém apenas o executável compilado e os recursos essenciais para a execução da aplicação Go. A primeira fase é responsável pela compilação, enquanto a segunda é destinada à execução da aplicação em um ambiente mais leve.</p>