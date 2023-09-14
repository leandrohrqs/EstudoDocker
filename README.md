<h1 align="center">Estudo Docker</h1>

## O que são containers

- É um pacote de código que pode executar uma ação, por exemplo, rodar uma aplicação de Node.js, PHP, Python e etc.

- Containers utilizam imagens para poderem ser executados

- Múltiplos containers podem rodar juntos, por exemplo: um para PHP e outro para MySQL

## Container x Imagem

- Container: É o Docker rodando alguma imagem, consequentemente executando algum código proposto por ela

- O fluxo é: programamos uma imagem e a executamos por meio de um container

## Onde encontrar imagens?

- No próprio repositório do Docker: [Docker Hub](https://hub.docker.com)

- Vamos executar uma imagem em um container com o comando: `docker run <imagem>`

## Verificando containers executados

- O comando `docker ps` exibe quais containers estão sendo executados no momento

- Utilizando a flag `-a`, temos todos os containers já executados na máquina

- Este comando é útil para entender o que está sendo executado e acontece no nosso ambiente

## Executar container com interação

- Podemos rodar um container e deixa-lo executando no terminal

- Utilizando a flag: `-it`

## Container X VM (Virtual Machine)

- Container é uma aplicação que serve para um determinado fim, não possui sistema operacional, seu tamanho é de alguns mbs;

- VM possui sistema operacional próprio, tamanho de gbs, pode executar diversas funções ao mesmo tempo;

- Containers acabam gastando menos recursos para serem executados, por causa do seu uso específico;

- VMs gastam mais recursos, porém podem exercer mais funções;

## Executando container em background

![Alt text](img/exec-cont-back.png)

## Expor portas

![Alt text](img/expor-portas.png)

## Parando containers

- Utilize: `docker stop <id ou nome-do-container>`

## Iniciando containers

- Utilize: `docker start <id ou nome-do-container>`

## Dando nome a um container

- Utilize a flag `--name nome-do-container`

## Verificando os logs

- Utilize: `docker logs <id>`

## Removendo um container

- Utilize: `docker rm <id>`

- Caso o container esteja rodando, é só utilizar: `docker rm <id> -f`

## O que são imagens

![Alt text](img/oq-sao-imagens.png)

## Como escolher uma imagem

- Podemos fazer download das imagens em: https://hub.docker.com;

- Porém qualquer um pode fazer upload de uma imagem, isso é um problema;

- Devemos então nos atentar as imagens oficiais;

- Outro parâmetro interessante é a quantidade de downloads e a quantidade de stars;

# Como criar uma imagem

- Para criar uma imagem vamos precisar de um arquivo Dockerfile em uma pasta que ficará o projeto;

- Este arquivo vai precisar de algumas instruções para poder ser executado;

`FROM`: imagem base;

`WORKDIR`: diretório da aplicação;

`EXPOSE`: porta da aplicação;

`COPY`: quais arquivos precisam ser copiados;

## Executando uma imagem

- Para executar precisamos usar o build: `docker build <diretório-da-imagem>`

- Depois vamos utilizar o: `docker run <>imagem`

## Alterando uma imagem

- Sempre que alterar uma imagem, é necessário fazer o build novamente.

- Para o docker, será uma imagem nova

- Após fazer o build, vamos executá-la por outro id único criada com o docker run;

## Camadas das imagens

- As imagens do docker são divididas em layers (camadas)

- Cada instrução no Dockerfile representa uma layer;

- Quando algo é atualizado apenas as layers depois da linha atualizada são refeitas;

- O resto permanece em cache, tornando o build mais rápido

## Fazendo download de imagens

- Podemos fazer o download de alguma imagem do hub e deixá-la disponível em nosso ambiente;

- Vamos utilizar o comando `docker pull <imagem>`;

- Desta maneira, caso se use em outro container, a imagem já estará pronta para ser utilizada;

## Múltiplas aplicações, mesmo container

- Podemos inicializar vários containers com a mesma imagem;

- As aplicações funcionarão em paralelo;

- Para testar isso, podemos determinar uma porta diferente para cada uma, e rodar no modo detached;

## Alterando o nome da imagem e tag

- Podemos nomear a imagem que criamos;

- Vamos utilizar o comando `docker tag <nome>` para isso;

- Também podemos modificar a tag, que seria como uma versão da imagem, semelhante ao git;

- Para inserir a tag utilizamos: `docker tag <nome>:<tag>`

## Iniciando imagem com um nome

- Podemos nomear a imagem já na sua criação;

- Vamos utilizar a flag `-t`;

- É possível inserir o nome e a tag, na sintaxe: `nome:tag`

- Isso torna o processo de nomeação mais simples;

## Comando start interativo

- A flag `-it` pode ser utilizada com o comando start também com a flag `-i`;

## Removendo imagens

- Para remover imagem deve utilizar: `docker rmi <imagem>`

- Para forçar a remoção utilize a flag `-f`: `docker rmi -f <imagem>`

## Removendo imagens e containers

- Com o comando: `docker system prune`

- Podemos remover imagens, containers e networks não utilizados;

- O sistema irá pedir uma confirmação para realizar a ação

## Removendo container após a utilização

- Um container pode ser automaticamente deletado após usa utilização

- Para isso vamos utilizar a flag `--rm`;

- O comando seria `docker run --rm <container>`

## Copiando arquivos do container

- Para fazer isso utilizamos: `docker cp`;

- Pode ser utilizado para copiar um arquivo de um diretório para um container;

- Ou de um container para um diretório determinado;

- Exemplo: `docker cp node_diferente:/app/app.js ./copia/`

## Verificando informações de processamento

- Para verificar dados de execução de um container utilizamos: `docker top <container>`

## Verificando dados de um container

- Para verificar diversas informações como: id, data de criação, imagem e muito mais;

- Utilizamos o comando: `docker inspect <container>`

## Verificando processamento do Docker

- Para verificar os processos que estão sendo executados em um container, utilizamos o comando: `docker stats`

## Enviando imagens para o Hub

- Para enviar uma imagem para o hub, devemos utilizar o: `docker push <imagem>`

- Porem antes deve ser criado o repositório para a imagem.

## Atualizando imagens no Hub

- Para atualizar uma imagem primeiro deve ser feito o build

- Troncando a tag da imagem para a versão atualizada

- Depois vamos fazer um push novamente para o repositório;

- Assim todas as versões estarão disponíveis para serem utilizadas
