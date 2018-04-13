---
title: Authentication
description: This tutorial will show you how to use Auth0 to add authorization to your Relay API.
---

<%= include('../../../_includes/_api_auth_intro') %>

<%= include('../_includes/_api_create_new') %>

<%= include('../_includes/_api_auth_preamble') %>

## Validate Access Tokens

### Install dependencies

Add **express-jwt** and **express-graphql** as dependencies.

${snippet(meta.snippets.dependencies)}

### Configuration

Configure the **express-jwt** middleware to use the remote JWKS for your Auth0 account.

${snippet(meta.snippets.setup)}

## Protect API Endpoints

<%= include('../_includes/_api_endpoints') %>

In your Relay app, you serve a GraphQL object from a single endpoint, which is typically at `/graphql`. You can protect this endpoint globally with the `express-jwt` middleware.

${snippet(meta.snippets.use)}

### Send an Access Token from your front end

When you send a request to the GraphQL endpoint, you need to include the user's Access Token as an `Authorization` header. This can be done by tapping into Relay's network layer and extending requests to include a header.

${snippet(meta.snippets.frontend)}