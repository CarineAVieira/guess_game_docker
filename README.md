
# Guess Game Docker

Aplicação do jogo de adivinhação desenvolvida em Flask e React, containerizada com Docker Compose.

## Tecnologias

- Python 3.12
- Flask
- React
- PostgreSQL 16
- NGINX
- Docker
- Docker Compose

## Arquitetura

A aplicação é composta pelos seguintes serviços:

- **postgres**: banco de dados PostgreSQL;
- **backend1**: primeira instância do backend Flask;
- **backend2**: segunda instância do backend Flask;
- **nginx**: servidor do frontend React e proxy reverso para o backend.

## Estrutura do projeto

```
.
├── frontend/
├── nginx/
├── Dockerfile.backend
├── Dockerfile.frontend
├── docker-compose.yml
├── requirements.txt
└── run.py
```

## Como executar

Clone o repositório:

```bash
git clone https://github.com/CarineAVieira/guess_game_docker.git
cd guess_game_docker
```

Execute a aplicação:

```bash
docker compose up --build
```

Acesse:

```
http://localhost:8080
```

Para finalizar:

```bash
docker compose down
```

## Como jogar

### Criar um novo jogo

1. Acesse:

```
http://localhost:8080
```

2. Digite uma frase secreta.

3. Clique em **Create**.

4. Guarde o **Game ID** gerado.

### Adivinhar a senha

1. Acesse novamente:

```
http://localhost:8080
```

2. Vá para a tela **Breaker**.

3. Informe o **Game ID**.

4. Faça suas tentativas até descobrir a senha.

## Funcionalidades

- criação de novos jogos;
- armazenamento da senha em Base64;
- comparação das tentativas;
- retorno de dicas ao jogador;
- persistência dos dados em PostgreSQL;
- balanceamento entre duas instâncias do backend utilizando NGINX.

## Serviços Docker

| Serviço | Porta |
|----------|------:|
| NGINX (Frontend) | 8080 |
| Backend Flask | 5000 (interna) |
| PostgreSQL | 5432 (interna) |

O backend não é acessado diretamente pelo navegador. As requisições são encaminhadas pelo NGINX utilizando o endpoint `/api`.

## Licença

MIT License.
