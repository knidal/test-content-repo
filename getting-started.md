---
title: Getting Started
---

# Getting Started

Welcome to the Acme Platform. This guide walks you through setting up your environment and running your first project.

## Prerequisites

Before you begin, make sure you have the following installed on your machine:

- Node.js 20 or later
- Docker Desktop
- Git 2.40+

You can verify your installations by running `node --version`, `docker --version`, and `git --version` in your terminal.

## Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/acme/platform.git
cd platform
npm install
```

The install step downloads all required packages and sets up local configuration files. This typically takes about two minutes on a fresh clone.

## Running Locally

Start the development server with:

```bash
npm run dev
```

The application will be available at `http://localhost:3000`. Hot reload is enabled by default, so any changes you make to source files will be reflected immediately in the browser.

## Troubleshooting

If the dev server fails to start, check that port 3000 is not already in use. You can specify an alternative port with:

```bash
PORT=3001 npm run dev
```

For Docker-related issues, ensure the Docker daemon is running and your user has permission to access the Docker socket.

## Next Steps

Once you have the platform running locally, read the [Architecture Overview](architecture/overview) to understand how the system is structured, and the [Authentication Guide](guides/authentication) to set up user login.
