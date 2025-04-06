# 📱 Clone do Twitter com NestJS + Kafka

## 📌 Resumo do Projeto

Um backend inspirado no Twitter, construído com NestJS e Kafka, que demonstra arquitetura escalável, integração com mensageria, cache, segurança e testes.

---

## 🚀 Tecnologias Utilizadas

- **NestJS** (core framework)
- **PostgreSQL** (relacional)
- **TypeORM ou Prisma**
- **Kafka** (mensageria)
- **Redis** (cache e pub/sub)
- **JWT** (autenticação)
- **Docker** (ambientes)
- **Swagger** (documentação)
- **Jest + Supertest** (testes)

---

## 🎯 Funcionalidades

- CRUD de usuários
- Autenticação JWT
- Postagem de tweets
- Likes e reposts
- Seguir usuários
- Feed personalizado (tweets de quem você segue)
- Notificações assíncronas
- Integração com Kafka para feed e notificações

---

## 🧱 Arquitetura Modular

Estrutura de diretórios do projeto NestJS:

    src/
    ├── auth/                # Módulo de autenticação (JWT, login, signup)
    ├── users/               # Gerenciamento de usuários e perfis
    ├── tweets/              # Tweets e reposts
    ├── likes/               # Likes nos tweets
    ├── follows/             # Seguidores e seguidos
    ├── feed/                # Geração do feed do usuário
    ├── notifications/       # Notificações baseadas em eventos
    ├── messaging/
    │   ├── kafka/           # Configuração do Kafka
    │   ├── producers/       # Produtores de eventos
    │   └── consumers/       # Consumidores de eventos
    ├── common/              # Pipes, guards, interceptors, filters
    └── main.ts              # Entry point da aplicação


---

## 🗃️ Estrutura do Banco de Dados

### Tabela: `users`

- `id` (PK)
- `username`
- `email`
- `password`
- `created_at`

### Tabela: `tweets`

- `id` (PK)
- `author_id` (FK → users)
- `content`
- `is_repost` (boolean)
- `original_tweet_id` (nullable, FK → tweets)
- `created_at`

### Tabela: `likes`

- `id` (PK)
- `user_id` (FK → users)
- `tweet_id` (FK → tweets)

### Tabela: `follows`

- `id` (PK)
- `follower_id` (FK → users)
- `following_id` (FK → users)

### Tabela: `notifications`

- `id` (PK)
- `recipient_id` (FK → users)
- `type` (ENUM: `"FOLLOW"`, `"LIKE"`, `"NEW_TWEET"`)
- `payload` (JSON)
- `read` (boolean)
- `created_at`

---

## 🔁 Fluxos com Kafka

### Evento: `user.followed`

- Produzido quando alguém segue outro usuário
- Consumer atualiza o feed e cria notificação

### Evento: `tweet.created`

- Produzido ao criar um tweet
- Consumer atualiza feeds dos seguidores

### Evento: `tweet.liked`

- Produzido ao curtir um tweet
- Cria notificação para o autor do tweet

---

## 🔐 Segurança

- Autenticação JWT
- Middleware de autorização
- Rate limiting com Nest RateLimiter
- DTO validation com `class-validator`

---

## ⚙️ Rotas da API

| Método | Endpoint | Descrição                         |
|--------|----------|-----------------------------------|
| POST   | /auth/signup       | Cadastrar novo usuário          |
| POST   | /auth/login        | Login com JWT                  |
| GET    | /users/:id         | Buscar perfil de um usuário    |
| POST   | /tweets            | Criar novo tweet               |
| GET    | /tweets/:id        | Ver um tweet                   |
| POST   | /tweets/:id/like   | Curtir um tweet                |
| POST   | /tweets/:id/repost | Repostar um tweet              |
| POST   | /users/:id/follow  | Seguir um usuário              |
| GET    | /feed              | Feed personalizado do usuário  |
| GET    | /notifications     | Ver notificações               |

---

## 🧪 Testes

- Testes unitários com Jest
- Testes E2E com Supertest
- Mock de serviços externos (Kafka, Redis)

---

## ☁️ Deployment com Docker Compose

Serviços incluídos no `docker-compose.yml`:

- NestJS App
- Kafka + Zookeeper
- PostgreSQL
- Redis

---

## 💡 Extensões Futuras

- Upload de imagens nos tweets
- API GraphQL com Subscriptions
- Integração com WebSocket para notificações em tempo real
- Interface frontend com React ou Angular

---


