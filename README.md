# Projeto Jogo - Guess Game

Este documento fornece as instruções e orientações necessárias para executar a estrutura Docker (utilizando Docker Compose) que suporta o jogo Guess Game.

## Requisitos

O projeto faz uso de Docker e Docker Compose para gerenciar e executar os containers.
É necessário que ambas as ferramentas estejam instaladas para o prosseguimento.

###Instalação do Docker e Docker Compose

-Seguem os links contendo as orientações necessárias: [Instalar Docker](https://docs.docker.com/get-docker/) e [Instalar Docker Compose](https://docs.docker.com/compose/install/)

## Projeto

1.Realize o clone do repositório:

   ```bash
   git clone https://github.com/leoff15/trabalhopratico1-docker.git
   cd trabalhopratico1-docker
   ```

2.Construa e inicie os containers pelo docker compose pelo comando abaixo; ele cria todas as imagens necessárias e inicializa os serviços. Após isso basta acessar http://localhost para visualizar e acessar o projeto (game).

   ```bash
   docker compose up --build
   ```

## Finalização do projeto

Deve-se remover os volumes associados e limpar os dados persistentes:

```bash
docker compose down --volumes
```
Para a remoção total de imagens e dados armazenados, deve-se executar os comandos abaixo:

```bash
#Exclusão de volumes
docker compose down --volumes

#Exclusão de imagens
docker rmi $(docker images -aq)

#Limpeza do sistema
docker system prune -a -f

---

## Informações do projeto

#### Docker Compose
O Docker Compose foi utilizado para a orquestração de containers backend, frontend e banco de dados, garantindo a automatização da execução dos mesmos.

#### Backend
- Desenvolvido em Python com o framework Flask.
- Integração com o banco de dados PostgreSQL.

#### Frontend
- Construído em React (Node.v18).
- Hospedado no ervidor NGINX, que também atua como proxy reverso para o backend.

#### PostgreSQL
- Configurado para armazenar de forma segura os dados.

### Lógica do Jogo

Papeis no jogo:

1. **Criador**:
   - Define a frase secreta e inicia um novo jogo.
2. **Quebrador**:
   - Recebe o identificador do jogo e tenta adivinhar a frase secreta.

Cada jogo possui um identificador único `game_id`, para associar as tentativas ao jogo correto no backend.

---

## Como Jogar

1. **Criar um Novo Jogo:**

   - Acesse [http://localhost](http://localhost).
   - Insira uma frase secreta no campo indicado e envie.
   - Guarde o **game_id** gerado para compartilhar com o Quebrador.

2. **Adivinhar a Frase:**

   - Navegue até [http://localhost](http://localhost).
   - Acesse a página **Breaker** (Quebrador).
   - Insira o **game_id** fornecido pelo Criador.
   - Realize as tentativas para desvendar a frase secreta.


## Aluno

- Nome: Leonardo Miranda Gregório
- Matrícula: 226039
- E-mail: leomiranda95@hotmail.com / 937748@sga.pucminas.br
