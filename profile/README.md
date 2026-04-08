**Symfonicat** is a JMS (JavaScript Management System) built on Symfony: an admin section, public runtime, Webpack Encore, Electron, and a FrankenPHP-oriented back end.

It's the web's perfect union of Symfony (Doctrine/PHP), Node.js/Webpack Encore/Stimulus (JavaScript), and Bootstrap (SCSS). It is a heavily database driven system that handles domains, subdomains, routing, catch-all client-side routing, Electron applications, Webpack bundles, it's... well, it's awesome. It's better than anything that's out there - except for Drupal.

It supports what Webpack Encore supports, so that includes React, Angular, TypeScript, ES6 modules, all of it. Encore imports the included Bootstrap theme in SCSS and prints it out in a bundle, but can print out per-bundle SCSS as well - making a really smooth system for including theme assets strategically.

- if you don't like PHP, you can leave
- unless you just like JavaScript more than PHP - you can stay
- Bootstrap and Twig people welcome, CSS3/SCSS/HTML5 are accepted here

it's Symfony in a beautiful swirl or JS functionality, modularity, and simplicity

### Install

```bash
composer create-project symfonicat/core symfonicat
cd symfonicat
docker compose up -d
npm install
npm run dev
docker exec php bin/console symfonicat:admin:create <username> <password>
```
