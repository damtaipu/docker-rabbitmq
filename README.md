## Servidor RabbitMQ com Docker


Arquivo .yml para ser executado com docker compose em intancia Linux Ubuntu.

O arquivo faz referencia a imagem oficial do RabbitMQ no dockerHub. Uma vez executado faz subir um servidor RabbitMQ preconfigurado em uma máquina com OS Ubuntu.

### Etapas para execução:
#### 1º Etapa: Instalando o docker no Ubuntu (se ainda não tem)
Os item abaixo estão de acordo com a publicação oficial o site do [Docker](https://docs.docker.com/engine/install/ubuntu/):

- Atualize o apt-get e instale os pacotes para permitir apto uso de um repositório por HTTPS:

```
$ sudo apt-get update
$ sudo apt-get install ca-certificates curl gnupg
```
 - Adicione a chave GPG oficial do Docker:
```
$ sudo install -m 0755 -d /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
$ sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
 - Use o comando abaixo para configurar o repositório:

```
$ echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

 - Atualize mais uma vez o apt-get:
```
$ sudo apt-get update
```
 - E por fim, Instale o Docker Engine, o containerd e o Docker Compose:
```
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

#### 2º Etapa: Executar o arquivo .yml
No diretório que vc salvou o arquivo .yml execute o comando:
```
docker-compose up
```
O Docker irá baixar a imagem e criar o container com o RabbitMQ já pré-configurado. Para entender melhor o arquivo yml e outros detalhes segue o [link](https://joaopaulodunder.wordpress.com/2019/03/03/rodando-rabbitmq-usando-docker-compose-com-usuario-fora-do-localhost/)