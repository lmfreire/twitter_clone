# ✅ To-Do List — Clone do Twitter com NestJS + Kafka

Organização das tarefas para desenvolver o projeto completo em NestJS com mensageria Kafka, cache com Redis, autenticação, testes e arquitetura modular.

---

## 📁 Estrutura Geral

- [ ] Criar projeto NestJS com `nest new`
- [ ] Configurar ESLint, Prettier, Husky (opcional)
- [ ] Definir ORM: TypeORM ou Prisma
- [ ] Criar estrutura modular baseada em domínios
- [ ] Criar e configurar `.env`
- [ ] Configurar Docker e `docker-compose.yml` com:
  - [ ] NestJS App
  - [ ] PostgreSQL
  - [ ] Kafka + Zookeeper
  - [ ] Redis

---

## 🔐 Autenticação (`auth`)

- [ ] Criar entidade `User` com senha hasheada
- [ ] DTOs: SignupDTO, LoginDTO
- [ ] Implementar JWT + refresh token (opcional)
- [ ] Criar `AuthGuard` e `@CurrentUser` decorator
- [ ] Endpoints:
  - [ ] `POST /auth/signup`
  - [ ] `POST /auth/login`

---

## 👤 Usuários (`users`)

- [ ] Criar CRUD de usuários
- [ ] Validar username e e-mail únicos
- [ ] Endpoints:
  - [ ] `GET /users/:id`
  - [ ] `PUT /users/:id`
  - [ ] `DELETE /users/:id` (opcional)

---

## 🐦 Tweets (`tweets`)

- [ ] Entidade `Tweet`: content, author, repost, timestamps
- [ ] Endpoints:
  - [ ] `POST /tweets`
  - [ ] `GET /tweets/:id`
  - [ ] `POST /tweets/:id/repost`
- [ ] Validar conteúdo (limite de caracteres)
- [ ] Emitir evento Kafka: `tweet.created`

---

## ❤️ Likes (`likes`)

- [ ] Entidade `Like`: user, tweet
- [ ] Endpoint:
  - [ ] `POST /tweets/:id/like` (like/unlike toggle)
- [ ] Emitir evento Kafka: `tweet.liked`

---

## 🔁 Reposts

- [ ] Permitir repost de tweets (reutilizar endpoint de criação)
- [ ] Linkar com `original_tweet_id`
- [ ] Impedir repost em loop (opcional)

---

## 🤝 Follows (`follows`)

- [ ] Entidade `Follow`: follower_id, following_id
- [ ] Endpoint:
  - [ ] `POST /users/:id/follow` (seguir/deixar de seguir)
- [ ] Emitir evento Kafka: `user.followed`

---

## 📰 Feed (`feed`)

- [ ] Endpoint: `GET /feed`
- [ ] Consultar últimos tweets de usuários seguidos
- [ ] Cache de feed com Redis
- [ ] Kafka consumer de:
  - [ ] `tweet.created` → atualizar feed

---

## 🔔 Notificações (`notifications`)

- [ ] Entidade `Notification`: recipient, type, payload
- [ ] Endpoint: `GET /notifications`
- [ ] Kafka consumers:
  - [ ] `user.followed` → notificar seguido
  - [ ] `tweet.liked` → notificar autor
  - [ ] `tweet.created` → notificar seguidores (opcional)
- [ ] Campo `read` para controle de leitura

---

## 💬 Mensageria Kafka

- [ ] Criar módulo `messaging/kafka`
- [ ] Configurar Kafka producer e consumer
- [ ] Padronizar payloads
- [ ] Assinar e produzir:
  - [ ] `tweet.created`
  - [ ] `tweet.liked`
  - [ ] `user.followed`

---

## 🧠 Common Module

- [ ] Criar `common` com:
  - [ ] Pipes de validação global
  - [ ] Exception filters
  - [ ] Interceptors
  - [ ] Custom decorators (`@Public`, `@CurrentUser`)
  - [ ] Middlewares (ex: logging, request ID)

---

## 🔐 Segurança

- [ ] Validar JWT em todas as rotas privadas
- [ ] Middleware de autorização (permissões básicas)
- [ ] Rate Limiting com `nestjs-rate-limiter`
- [ ] DTO validation com `class-validator`

---

## 🧪 Testes

- [ ] Configurar Jest com `@nestjs/testing`
- [ ] Unit tests:
  - [ ] AuthService
  - [ ] TweetService
  - [ ] KafkaService
- [ ] E2E tests com Supertest:
  - [ ] Signup/Login
  - [ ] Criar tweet, dar like, seguir
- [ ] Mock:
  - [ ] Kafka
  - [ ] Redis
  - [ ] JWT

---

## 📄 Documentação

- [ ] Integrar Swagger
- [ ] Criar exemplos com request/response para todos endpoints
- [ ] Documentar DTOs

---

## ☁️ Deployment

- [ ] Dockerfile da aplicação
- [ ] Finalizar `docker-compose.yml`
- [ ] Testar subida local (`docker compose up`)
- [ ] Variáveis `.env.production`

---

## 🔮 Funcionalidades Futuras (Backlog)

- [ ] Upload de imagens em tweets (S3 ou Disk)
- [ ] GraphQL + Subscriptions
- [ ] WebSocket para notificações em tempo real
- [ ] Frontend com React ou Angular
- [ ] Dark mode no frontend (hehe 😄)

---

## ✅ Finalização

- [ ] Revisar todos fluxos
- [ ] Validar consistência dos eventos Kafka
- [ ] Testar cache do feed
- [ ] Publicar no GitHub
- [ ] Gravar vídeo demo ou README com screenshots

---
