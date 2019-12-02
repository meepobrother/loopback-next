---
lang: en
title: 'Migrating built-in authentication and authorization'
keywords: LoopBack 4.0, LoopBack 4, LoopBack 3, Migration
sidebar: lb4_sidebar
permalink: /doc/en/lb4/migration-auth-built-in.html
---

## Migrate the authentication flow

### Request access tokens via login

1. Implement the following functions

- User service

  - https://github.com/strongloop/loopback4-example-shopping/blob/master/packages/shopping/src/services/user-service.ts

- Token service

  - https://github.com/strongloop/loopback4-example-shopping/blob/master/packages/shopping/src/services/jwt-service.ts

- Login method

  - https://github.com/strongloop/loopback4-example-shopping/blob/master/packages/shopping/src/controllers/user.controller.ts#L204

2. Reuse the `User` database from LB3

- Datasource for the User database
- UserCredentialsRepository

  - https://github.com/strongloop/loopback4-example-shopping/blob/master/packages/shopping/src/repositories/user-credentials.repository.ts

### Protect API calls with access tokens

- JWT strategy

  - https://github.com/strongloop/loopback4-example-shopping/blob/master/packages/shopping/src/authentication-strategies/jwt-strategy.ts

## Migrate the authorization flow

### Migrate ACLs

1. Decorate protected methods with `@authorize`

- https://github.com/strongloop/loopback4-example-shopping/blob/11c48ef222a7960cb266bd88878c0eb9f8138127/packages/shopping/src/controllers/user-order.controller.ts#L48

2. Implement an Authorizer

- https://github.com/strongloop/loopback4-example-shopping/blob/master/packages/shopping/src/services/authorizor.ts
