# Medusa Nuxt Store

![Project Cover Image](https://res.cloudinary.com/craigsims808/image/upload/v1708526494/articles/medusa-nuxt/gh-cover_vm1nlg.png)

## Project Description

This is an ecommerce store built using Medusa as a headless commerce engine and Nuxt.js as the frontend framework.

<!-- Live Demo -->

## Source Code

[Medusa Nuxt Store v1.0.0](https://github.com/Marktawa/medusa-nuxt/releases/tag/v1.0.0)

## Article Link

[Build an ecommerce store using Nuxt and Medusa from scratch](https://github.com/Marktawa/medusa-nuxt-article)

## Prerequisites

To follow along you will need:
- Basic understanding of HTML, CSS, and JavaScript
- Basic understanding of Node.js and npm
- Basic understanding of the command line
- Knowledge of Vue and Nuxt is a bonus but not a requirement.
- Knowledge of Medusa is a bonus but not a requirement.

In addition to knowing these tools, your computer system should have the following packages installed:
- [Node.js](https://nodejs.org/en/download/) (v16 and above) 
- [PostgreSQL](https://www.postgresql.org/download/). Alternatively, you can create a free PostgreSQL database with a [Neon](https://console.neon.tech/signup) account. This tutorial will use a database created using Neon.
- yarn (optional)
- git (optional)

## Getting Started

Clone the repo.
```bash
git clone https://github.com/Marktawa/medusa-nuxt
```
Change directory.
```bash
cd medusa-nuxt
```

## Medusa Setup

Install Medusa CLI.
```bash
npm install @medusajs/medusa-cli -g
```

Install dependencies.
```bash
cd my-medusa-store
npm install
```

### Configure Database - Local PostgreSQL DB

Access the PostgreSQL console to create a new user and database for the Medusa server.

```bash
sudo -u postgres psql
```

To create a new user named `medusa_admin` run this command:

```sql
CREATE USER medusa_admin WITH PASSWORD 'medusa_admin_password';
```

Now, create a new database named `medusa_db` and make `medusa_admin` the owner.

```sql
CREATE DATABASE medusa_db OWNER medusa_admin;
```

Last, grant all privileges to `medusa_admin` and exit the PostgreSQL console.

```sql
GRANT ALL PRIVILEGES ON DATABASE medusa_db TO medusa_admin;
```

```sql
exit
```

Add the connection string as the `DATABASE_URL` to your environment variables. Inside `my-medusa-store` create a `.env` file and add the following:

```
DATABASE_URL=postgres://medusa_admin:medusa_admin_password@localhost:5432/medusa_db
```

### Seed Database

Run migrations and seed data to the database by running the following command:

```bash
medusa seed --seed-file="./data/seed.json"
```

### Start your Medusa backend

```bash
medusa develop
```

The Medusa server will start running on port `9000`.

Test your server:
```bash
curl localhost:9000/store/products
```

Open up your browser and visit [`localhost:7001`](http://localhost:7001) to see the Medusa Admin Dashboard. Use the Email `admin@medusa-test.com` and password `supersecret` to log in.

## Nuxt Setup

Open up a new terminal session and open up the main project folder, `my-store`. 

Install dependencies.
```bash
cd my-nuxt-storefront
npm install
```

Run Nuxt app.
```bash
npm run dev
```

Visit [localhost:3000](http://localhost:3000) in your browser to view the Nuxt app.

## Author

[Mark Munyaka](https://markmunyaka.com)

GitHub: [@Marktawa](https://github.com/Marktawa)
Twitter: [@McMunyaka](https://twitter.com/McMunyaka)

## Sponsor

Support my passion for sharing development knowledge by making a donation to my [**Buy Me a Coffee**](https://www.buymeacoffee.com/markmunyaka) account. Your contribution helps me create valuable content and resources. Thank you for your support!

[![Buy Me A Coffee Banner](https://res.cloudinary.com/craigsims808/image/upload/v1708089939/articles/test/buymeacoffee_lqmwjn.png)](https://www.buymeacoffee.com/markmunyaka)

[Buy Me A Coffee](https://www.buymeacoffee.com/markmunyaka)
