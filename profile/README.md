**`Symfonicat`** is a JMS (JavaScript Management System) built on Symfony: an admin portion to manage everything, database-driven Webpack Encore front end, Electron support, and a FrankenPHP-oriented back end. It ships with a Docker setup to get up and running in no time: FrankenPHP, PostgreSQL, Mercure Hub, and Redis, completely configured for Symfony.

It's the web's perfect union of Symfony (Doctrine/PHP), Node.js/Webpack Encore/Stimulus (JavaScript), and Bootstrap (SCSS). It is a heavily database driven system that handles domains, subdomains, routing, catch-all client-side routing, Electron applications, Webpack bundles, it's... well, it's awesome. It's a better shell than anything that's out there - except for Drupal.

It supports what Webpack Encore supports, so that includes React, Angular, TypeScript, ES6 modules, Turbo Frames, everything JavaScript/source maps/integrity hashes/Babel/Sass. Encore imports the included Bootstrap library in SCSS and prints it out in a bundle, but can print additional per-bundle SCSS as well - making a really smooth system for including theme assets strategically.

- if you don't like PHP, you can leave
- unless you just like JavaScript more than PHP - you can stay
- Bootstrap and Twig people welcome, CSS3/SCSS/HTML5 are accepted here

it's Symfony in a beautiful swirl or JS functionality, modularity, and simplicity

### Entities

- **`Domain`**: top level domain management, supports redirects
- **`Project`**: has a slug that matches to a subdomain like `project.example.com`. It's automatically configured to load a bundle that exists in the filesystem. **`Project`** entities can be assigned to multiple **`Domain`** entities for modularity like `user.*.com`
- **`Module`**: micro-bundles assignable to **`Domain`** or **`Project`** entities that bootstrap after the main **`Domain`** or **`Project`** bundles
- **`RoutingRule`**: minimal routing rules that can assign 0 index path arguments to specific **`Domain`** entities, to assert that one Symfony path argument is for one **`Domain`**

### Philosophy

- only supports one subdomain
- a subdomain **`(Project)`** is usually a second-tier section of any given site so why not have them each be a bundle?
- **`Project`** entities can all be exported to Electron apps
- they exist in the database as entities for Symfony-supported referencing, modularity, extension, and tracking
- there is a catch-all route for when a **`Project`** is present, so no matter what URL you load it's client-side routed
- if no **`Project`** is present, the **`Domain`** bundle is loaded
- if you're on a **`Domain`** and there's a path, then Symfony handles it
- if you're on a **`Domain`** and there's a path and a **`RoutingRule`** for the first path argument, it redirects to the correct **`Domain`** and Symfony handles it

### Install

```bash
composer create-project symfonicat/core symfonicat
cd symfonicat
docker compose up -d
npm install
npm run dev
docker exec php bin/console symfonicat:admin:create <username> <password>
```
