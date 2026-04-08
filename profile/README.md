`Symfonicat` is a JMS (JavaScript Management System) built on Symfony. `symfonicat/core` is the full application package: the admin runtime, database-driven Webpack Encore front end, Electron support, and the FrankenPHP-oriented back end all live here.

It ships with a Docker stack to get running quickly: FrankenPHP, PostgreSQL, Mercure Hub, and Redis, already wired for Symfony.

It is the web's union of Symfony, Doctrine, PHP, Node.js, Webpack Encore, Stimulus, Bootstrap, SCSS, and Twig. It is a heavily database-driven system that handles domains, subdomains, routing, catch-all client-side routing, Electron applications, and Webpack bundles from one admin-managed shell.

It supports what Webpack Encore supports, so that includes React, Angular, TypeScript, ES modules, Turbo, source maps, integrity hashes, Babel, and Sass. Encore imports the included Bootstrap library in SCSS and builds it into a bundle, while still allowing additional per-bundle SCSS for more targeted theme assets.

- if you don't like PHP, you can leave
- unless you just like JavaScript more than PHP, then you can stay
- Bootstrap, Twig, CSS3, SCSS, and HTML5 people are welcome here

It's Symfony in a beautiful swirl of JavaScript functionality, modularity, and simplicity.

## Ships

- the full `symfonicat/core` Symfony application
- the public frontend runtime for `/` and `/{path}`
- the separate `/admin` runtime and CRUD surface
- the Webpack Encore data interface driven by `symfonicat:data:webpack`
- shared assets under `assets` and build output under `public/build`
- the Electron runtime and related console commands
- FrankenPHP-oriented Docker and Caddy infrastructure in this repository

## Stack

- Symfony 8, Doctrine, and PHP
- Node.js, Webpack Encore, Stimulus, and Turbo
- Bootstrap, SCSS, Twig, and HTML5
- FrankenPHP and Caddy
- PostgreSQL, Mercure, and Redis

## Entities

- `Domain`: top-level domain management, including redirects and domain-level runtime context
- `Project`: subdomain-backed runtime shells keyed by slug; projects can be attached to multiple domains and prepared for Electron output
- `Module`: micro-bundles assignable to `Domain` or `Project` entities that bootstrap after the main domain or project runtime
- `RoutingRule`: minimal routing rules that can map the first path segment to a specific `Domain`
- `Admin`: a separate admin auth model owned by Symfonicat for the `/admin` area

## Philosophy

- only supports one subdomain layer
- a subdomain (`Project`) is usually a second-tier section of a site, so Symfonicat treats it as a first-class runtime shell
- `Project` entities exist in the database for Symfony-native referencing, modularity, extension, and tracking
- `Project` entities can be prepared for Electron applications
- when a `Project` is active, the public runtime uses a catch-all route so the rest of the URL can be client-side routed
- if no `Project` is active, the `Domain` runtime is loaded
- if you are on a `Domain` and there is a path, Symfony handles it
- if you are on a `Domain`, there is a path, and a matching `RoutingRule` exists for the first path segment, Symfonicat can redirect to the correct `Domain` and let Symfony continue from there

## Install

```bash
composer create-project symfonicat/core symfonicat
cd symfonicat
docker compose up -d
npm install
npm run dev
docker exec php bin/console symfonicat:admin:create <email> <password>
```
- seeds a `localhost` domain row
- seeds and enables the `analytics` module for `localhost`

## Useful commands

- `bin/console symfonicat:admin:create <email> <password>`
- `bin/console symfonicat:admin:delete <email>`
- `bin/console symfonicat:data:webpack`
- `bin/console symfonicat:data:electron`
- `bin/console symfonicat:electron:prepare`
- `bin/console symfonicat:electron:dev`
- `bin/console symfonicat:electron:build`
- `bin/console symfonicat:electron:package`
- `bin/console symfonicat:public-suffix:refresh`
