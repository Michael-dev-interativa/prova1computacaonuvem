# Prova 1 de Computação em Nuvem

Michael Barros de Souza Rocha
c7bcaaaa1e7bd93a82ca

## O que fiz

Executei uma página web em um contêiner Docker chamado atendimento.
Usei a imagem nginx:alpine e a porta 8082 do ambiente.

## Verificação do Contêiner

CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                     NAMES
32e261571e92   nginx:alpine   "/docker-entrypoint.…"   8 minutes ago   Up 8 minutes   0.0.0.0:8082->80/tcp, [::]:8082->80/tcp   atendimento

## Teste da Página 

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Atendimento</title>
</head>
<body>
  <h1>Atendimento disponível</h1>
</body>
</html>

## Explicação 

É uma imagem Docker do Nginx baseada no Alpine Linux.
Ela contém, de forma simplificada:Nginx instalado;
Alpine Linux como sistema-base;
configurações necessárias para executar o servidor web.
A imagem funciona como um molde. A partir dela, você pode criar vários contêineres.

Contêiner atendimento
O atendimento é uma instância em execução desse molde.
Por exemplo, se você executou algo como:
docker run --name atendimento -p 8082:80 nginx:alpine

Para que serviu 8082:80?
Esse é o mapeamento de portas:

8082:80
porta 80 do contêiner
porta 8082 da sua máquina

O Nginx, dentro do contêiner, normalmente escuta na porta 80.

Então o Docker fez uma ligação:

Seu computador                  Contêiner
    

localhost:8082                  Nginx :80    


Por isso, ao acessar:

http://localhost:8082

a requisição chega à porta 80 do Nginx dentro do contêiner.

Esse código:

<h1>Atendimento disponível</h1>

é uma página que o Nginx pode entregar. Se esse arquivo estiver colocado no diretório que o Nginx usa para servir arquivos.
