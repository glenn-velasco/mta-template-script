# MTA:SA Server Template Setup Guide

This repository provides a modular, modern boilerplate for building Multi Theft Auto: San Andreas (MTA:SA) gamemodes using MySQL and Node.js/Prisma.

---

## 📋 Prerequisites

Before starting, ensure you have installed:

1. **MTA:SA Official Server Files:** Download from [multitheftauto.com](https://multitheftauto.com/).
2. **Git Tooling / Code Editor (Choose one):**
   * [Git SCM](https://git-scm.com/)
   * [GitHub Desktop](https://desktop.github.com/)
   * [Visual Studio Code](https://code.visualstudio.com/)
3. **Node.js Runtime & Package Manager (Choose one):**
   * `npm` (Included with Node.js)
   * `pnpm`
   * `yarn`
   * `bun`
4. **Database:** Local or remote MySQL instance.

---

## 🛠️ Part 1: MTA Server Setup (`mods/deathmatch`)

### Step 1: Download & Extract MTA Binaries
1. Download the **MTA:SA Server** package from [multitheftauto.com](https://multitheftauto.com/).
2. Extract the server files into your desired project directory (e.g., `D:\mtaserver\`).

### Step 2: Unpack Template into `mods/deathmatch`
Open your terminal or command prompt and navigate into the `mods/deathmatch` directory:

```powershell
cd server/mods/deathmatch

```

Unpack the template directly into the `deathmatch` folder:

```bash
npx degit glenn-velasco/mta-template-script . --force

```

### Step 3: Local Configuration Overrides (Optional)

`mtaserver.conf` and `acl.xml` are included directly with the template.

If you need machine-specific setting overrides (such as custom testing ports or developer server names), create a `local.conf` file in `mods/deathmatch/`. MTA will automatically merge `local.conf` on top of `mtaserver.conf` without affecting Git tracking.

---

## 🗄️ Part 2: Prisma & Backend Setup (`js/prisma`)

### Step 1: Navigate to the Prisma Directory

From `mods/deathmatch`, navigate into your Node/Prisma folder:

```powershell
cd js/prisma
```

### Step 2: Configure Environment Variables

Duplicate the `.env.example` file to create your local `.env` file.

```bash
# Using windows cmd
copy .env.example .env

# Using powershell
Copy-Item .env.example .env
```

Open `.env` in your code editor and update your MySQL connection string:

```env
DATABASE_URL="mysql://johndoe:randompassword@localhost:3306/mydb"
DATABASE_USER="johndoe"
DATABASE_PASSWORD="randompassword"
DATABASE_NAME="mydb"
DATABASE_HOST="localhost"
DATABASE_PORT=3306
```

### Step 3: Install Dependencies

Install the required packages using your preferred package manager:

```bash
# Using npm
npm install

# Using pnpm
pnpm install

# Using yarn
yarn install

# Using bun
bun install

```

### Step 4: Run Prisma Database Setup

Generate the Prisma client and execute migrations to create your database tables:

```bash
# 1. Generate Prisma Client
npx prisma generate

# 2. Apply migrations to construct local MySQL tables
npx prisma migrate dev

```

---

## 🚀 Part 3: Launching the Server

1. Ensure your local MySQL server is running.
2. Return to the root MTA server directory.
3. Launch `MTA Server.exe`.

---
