# Loshon

### Introduction

Loshon is a block-based note-taking (inspired by notion obviously, I'm obssessed with how notion does things). It consists of NextJS for the Web frontend and API written using Golang.

_Currently, I am not sure the direction of this application so I've been doing whatever I feel like implementing_

Here's the entire tech stack:

- NextJS
- ShadCN UI
- TailwindCSS
- Golang
- GORM
- PostgreSQL
- Clerk (for authentication)
- AgoliaSearch (for advanced searching)
- Edge store (for file storage)

For deployment:

- Vercel
- Render.com

### Features

Loshon has basic features a modern note-taking application should have:

- Notes are organized in a tree-like manner which allow nested child documents
- Block editor with customizable formatting
- Archiving and Restoring notes
- Publishing notes
- Quick and robust searching using AgoliaSearch

### Local development guide

> **PRESIQUITES: make sure you have the node version >= 20.17.0 and golang 1.23 installed**

Clone this repo (or you can clone seperate subrepo for api and web)

```shell
git clone git@github.com:DustinDust/loshon.git
```

Install the required modules

```bash
# in ./lo-shon
npm install

# in ./loshon-go
go mod download
```

Setup the database. Make sure you have your postgresql database already created

```bash
# in ./loshon-go
make migrate.up DB_CONN="..."
```

Sign up for [Agolia](https://www.algolia.com/) and [Clerk](https://clerk.com/) (if you haven't already)

Provide required environment variables in

```bash
# ./loshon-go/.env.development
CLERK_PUBLISHABLE_KEY =
CLERK_SECRET_KEY =
POSTGRES_URL =
ANGOLIA_APP_ID =
ANGOLIA_API_KEY =
PORT = 8081

# ./lo-shon/.env.local
CLERK_SECRET_KEY=
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
NEXT_PUBLIC_AGOLIA_APP_ID=
NEXT_PUBLIC_AGOLIA_API_KEY=
EDGE_STORE_ACCESS_KEY=
EDGE_STORE_SECRET_KEY=

NEXT_PUBLIC_API_BASE_URL=http://localhost:8080/api⏎ #  ur backend url
```

Run the application for local developemnt

```bash
# ./lo-shon
npm run dev

# ./loshon-go
make
```

### TODO LIST

- [ ] Add test
- [x] Dockerize
- [ ] Move infra to AWS

For individual features to-do list/issues, visit each repos' issues tabs
