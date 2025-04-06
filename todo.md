# ✅ To-Do List — Clone do Twitter com NestJS + Kafka

Organização das tarefas para desenvolver o projeto completo em NestJS com mensageria Kafka e arquitetura modular.

---

## 🔹 1. Inicialização do Projeto

- [ ] Criar projeto NestJS com `nest new`
- [ ] Configurar ESLint, Prettier e Husky (opcional)
- [ ] Criar estrutura de pastas modular
- [ ] Criar e configurar `.env`
- [ ] Criar `docker-compose.yml` com:
  - [ ] NestJS App
  - [ ] PostgreSQL
  - [ ] Redis
  - [ ] Kafka + Zookeeper

---

## 🔹 2. Módulo de Autenticação (`auth`)

- [ ] Criar DTOs de login e signup
- [ ] Implementar JWT (sign e verify)
- [ ] Criar serviço de autenticação
- [ ] Criar guards e decorators (`@CurrentUser`)
- [ ] Endpoints:
  - [ ] `POST /auth/signup`
  - [ ] `POST /auth/login`

---

## 🔹 3. Módulo de Usuário (`users`)

- [ ] Criar entidade `User`
- [ ] Implementar repositório e service
- [ ] Endpoint:
  - [ ] `GET /users/:id`

---

## 🔹 4. Módulo de Tweets (`tweets`)

- [ ] Criar entidade `Tweet`
- [ ] Implementar lógica de criação e busca
- [ ] Endpoints:
  - [ ] `POST /tweets`
  - [ ] `GET /tweets/:id`
  - [ ] `POST /tweets/:id/repost`

---

## 🔹 5. Módulo de Likes (`likes`)

- [ ] Criar entidade `Like`
- [ ] Endpoint:
  - [ ] `POST /tweets/:id/like`
- [ ] Emitir evento Kafka `tweet.liked`

---

## 🔹 6. Módulo de Follows (`follows`)

- [ ] Criar entidade `Follow`
- [ ] Endpoint:
  - [ ] `POST /users/:id/follow`
- [ ] Emitir evento Kafka `user.followed`

---

## 🔹 7. Módulo de Feed (`feed`)

- [ ] Implementar lógica para feed personalizado
- [ ] Endpoint:
  - [ ] `GET /feed`
- [ ] Kafka Consumer:
  - [ ] `tweet.created` → atualizar feeds dos seguidores

---

## 🔹 8. Módulo de Notificações (`notifications`)

- [ ] Criar entidade `Notification`
- [ ] Endpoint:
  - [ ] `GET /notifications`
- [ ] Kafka Consumers:
  - [ ] `user.followed`
  - [ ] `tweet.liked`
  - [ ] `tweet.created` (opcional)

---

## 🔹 9. Integrações Técnicas

- [ ] Configurar Kafka Producers e Consumers
- [ ] Implementar Redis para cache de feed (opcional)
- [ ] Implementar rate limit com `nestjs-rate-limiter`
- [ ] Adicionar Swagger (`@nestjs/swagger`)

---

## 🔹 10. Testes

- [ ] Criar testes unitários (Jest)
- [ ] Criar testes E2E (Supertest)
- [ ] Mock de:
  - [ ] Redis
  - [ ] Kafka
  - [ ] JWT

---

## 🔹 11. Deployment

- [ ] Criar Dockerfile para app NestJS
- [ ] Finalizar `docker-compose.yml`
- [ ] Testar ambientes localmente
- [ ] Adicionar `.env.production`

---

## 🔹 12. Extras ✨

- [ ] Criar README.md com instruções
- [ ] Gerar seeds com `faker`
- [ ] Criar cron job para limpar notificações antigas (opcional)
- [ ] Implementar WebSocket para notificações em tempo real (opcional)

---

## 🏁 Finalização

- [ ] Testar todos os fluxos com usuários reais
- [ ] Validar consumo Kafka
- [ ] Verificar segurança geral
- [ ] Publicar projeto no GitHub com README + vídeo/demo

---
