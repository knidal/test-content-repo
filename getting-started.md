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
