# Kamride

> Plateforme web de covoiturage interurbain au Cameroun : relier des conducteurs ayant des places libres à des passagers, avec identité vérifiée et paiement Mobile Money sécurisé.

![Laravel](https://img.shields.io/badge/Laravel-13-FF2D20?logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-%E2%89%A5%208.3-777BB4?logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-MariaDB-4479A1?logo=mysql&logoColor=white)

## Sommaire

- [Contexte](#contexte)
- [Fonctionnalités](#fonctionnalités)
- [Stack technique](#stack-technique)
- [Prérequis](#prérequis)
- [Installation](#installation)
- [Commandes utiles](#commandes-utiles)
- [Structure du projet](#structure-du-projet)
- [Workflow de contribution](#workflow-de-contribution)
- [Feuille de route](#feuille-de-route)
- [Équipe](#équipe)
- [Licence](#licence)

## Contexte

Kamride propose une alternative plus sûre et plus transparente aux trajets informels, et plus flexible que les agences de bus, sur les principaux axes interurbains du Cameroun (par exemple Douala–Yaoundé, Yaoundé–Bafoussam, Douala–Kribi).

Le cahier de cadrage complet se trouve dans [`docs/cadrage/`](docs/cadrage/).

## Fonctionnalités

| Espace | Fonctionnalités |
|---|---|
| **Passager** | Recherche de trajets, réservation, paiement Mobile Money sécurisé (séquestre), suivi du trajet, avis |
| **Conducteur** | Publication d'annonces, vérification d'identité (permis, carte grise, assurance), gestion des réservations, portefeuille |
| **Administration** | Validation des identités, modération, suivi financier et commissions, gestion des alertes |

## Stack technique

- **Backend / web** : Laravel 13 (PHP 8.3 minimum)
- **Base de données** : MySQL / MariaDB
- **Front** : Blade + Vite
- **Versionnement** : Git / GitHub

## Prérequis

- PHP **8.3 ou plus** avec les extensions : `curl`, `fileinfo`, `mbstring`, `openssl`, `pdo_mysql`, `zip`, `gd`, `intl`
- [Composer](https://getcomposer.org/)
- MySQL ou MariaDB (XAMPP convient)
- [Node.js](https://nodejs.org/) et npm
- Git

Vérifie ta version de PHP avec `php -v`.

## Installation

```bash
# 1. Cloner le dépôt
git clone https://github.com/Abd130658/Kamride.git
cd kamride

# 2. Installer les dépendances PHP
composer install

```

**5. Configurer la base de données.** Crée une base vide (par exemple `kamride`, interclassement `utf8mb4_unicode_ci`) puis adapte ces lignes dans ton fichier `.env` :

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=kamride
DB_USERNAME=
DB_PASSWORD=
```

```bash
# 6. Créer les tables
php artisan migrate

# 7. Installer et compiler les ressources front
npm install
npm run dev
```

Dans un second terminal, lance le serveur de développement :

```bash
php artisan serve
```

L'application est disponible sur <http://127.0.0.1:8000>.

> Le fichier `.env` est propre à chaque développeur : il ne doit **jamais** être commité.

## Commandes utiles

| Commande | Rôle |
|---|---|
| `php artisan serve` | Lancer le serveur local |
| `php artisan migrate` | Appliquer les migrations |
| `php artisan migrate:fresh --seed` | Réinitialiser la base avec les données de test |
| `php artisan make:model Nom -mfc` | Créer un modèle avec migration, factory et contrôleur |
| `php artisan test` | Lancer les tests |
| `./vendor/bin/pint` | Formater le code selon le style Laravel |
| `npm run build` | Compiler les ressources pour la production |

## Structure du projet

```
app/            Logique métier (modèles, contrôleurs, services)
config/         Configuration de l'application
database/       Migrations, factories, seeders
resources/      Vues Blade, CSS, JS
routes/         Définition des routes (web.php, ...)
tests/          Tests automatisés
docs/           Cadrage, schémas UML, architecture
```

La structure de la base de données se partage uniquement via les **migrations** (et les **seeders** pour les données de test), jamais par des exports SQL.

## Workflow de contribution

1. Se placer sur `develop` et récupérer les dernières modifications : `git checkout develop && git pull`
2. Créer une branche : `git checkout -b feature/<module>-<description>` (ex. `feature/auth-otp`)
3. Commiter avec des messages clairs (`feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`)
4. Pousser la branche et ouvrir une Pull Request vers `develop`
5. Faire relire la PR par au moins un autre membre avant de fusionner

`main` contient uniquement du code stable. Personne ne pousse directement dessus.

### Règles de sécurité

- Ne jamais commiter `.env`, des clés d'API (Mobile Money, SMS, etc.) ou des mots de passe.
- Ne jamais commiter de données réelles d'utilisateurs (pièces d'identité, permis, etc.).

## Feuille de route

- [ ] **Phase 1** : Cadrage et analyse (cahier des charges, UML, maquettes)
- [ ] **Phase 2** : Architecture et conception (modèle de données, API, hébergement)
- [ ] **Phase 3** : Développement (espaces passager, conducteur, administration)
- [ ] **Phase 4** : Tests, validation et déploiement

## Équipe

| Nom | Rôle |
|---|---|
| _À compléter_ | _À compléter_ |

## Licence

_À définir._
