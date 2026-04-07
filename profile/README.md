**Symfonicat** is a JMS (JavaScript Management System) built on Symfony: admin, public runtime, webpack, Electron, and a FrankenPHP-oriented starter shell.

It's the web's perfect union of Symfony (Doctrine/PHP), Node.js/Webpack (JavaScript), and Bootstrap (SCSS). It is a heavily database driven system that handles domains, subdomains, routing, Electron applications, Webpack bundles, client-side routing, it's... well, it's awesome. It's better than anything that's out there - except for Drupal.

- if you don't like PHP, you can leave
- unless you like JavaScript more than PHP - you can stay
- Bootstrap people welcome, CSS3/SCSS/HTML5 are accepted here

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
