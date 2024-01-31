FROM ubuntu

LABEL criador = Vinicios \
    versao = 1.0

ENV VALOR_DOCKER_IDADE = "27"
ARG ARG_ECHO="echo executador"
ARG ARG_USER="viniciosanhas"

RUN apt update && \
    apt install -y curl && \
    apt install -y nginx

RUN echo $ARG_ECHO > echo.txt

WORKDIR /app
RUN mkdir volume
VOLUME /app/volume

COPY README.md .
ADD https://www.google.com.br/ pagina.html
ADD arquivo.tar.gz ./

EXPOSE 80

RUN useradd $ARG_USER
USER $ARG_USER

ENTRYPOINT [ "echo", "Hello World" ]

CMD ["combinando com o ENTRYPOINT"]