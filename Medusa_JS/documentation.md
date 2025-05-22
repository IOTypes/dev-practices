
# 🚀 Medusa: Quick Overview

Medusa is an ecommerce platform with a built-in framework for customization that allows you to build custom commerce applications without reinventing core commerce logic. The framework and modules can be used to build advanced B2B or DTC ecommerce stores, marketplaces, PoS systems, service businesses, or any product that needs foundational commerce primitives. All commerce modules are open-source and freely available on npm.

---

## 🧰 Core Tools

1. **Commerce Modules** – Inventory, cart, orders, payments, etc.  
2. **Custom Framework** – Build custom APIs, business logic, automations, and integrations.  
3. **Admin Dashboard** – Manage and configure store operations.

---

## 🎯 Why Use Medusa?

Built for businesses with unique needs. Unlike rigid platforms, Medusa prioritizes extensibility and developer freedom, allowing custom features without hacky workarounds.

---

## 👥 Who’s It For?

- Startups to enterprises  
- Any tech team with at least one developer  
- Ideal for D2C, B2B, Marketplaces, POS, OMS, and platform builds

---

## 🚀 Create Medusa Application

A Medusa application is made up of a Node.js server and an admin dashboard.

### ⚙️ Install Medusa

#### ✅ Prerequisites

- Node.js v20+  
- Git  
- PostgreSQL

To create a Medusa application, run:

```bash
npx create-medusa-app@latest my-medusa-store
```

Where `my-medusa-store` is the name of the project directory and PostgreSQL database.

You’ll be prompted to optionally install the Next.js Starter Storefront. The app and storefront are placed in separate directories.

---

### 🖥 After Installation

- Medusa app runs at: `http://localhost:9000`  
- Admin dashboard: `http://localhost:9000/app`  
- Next.js Storefront (if installed): `http://localhost:8000`

---

### 🧪 Run in Development

```bash
npm run dev
```

---

### 👤 Create Admin User (CLI)

```bash
npx medusa user -e admin@medusajs.com -p supersecret
```

Replace with your own email/password. Use to log in at `/app`.

---

## 🗂 Project Structure

```
src/
├── admin/        # Admin dashboard custom widgets and UI
├── api/          # Custom API routes
├── jobs/         # Scheduled background jobs
├── links/        # Module associations
├── modules/      # Custom business logic
├── scripts/      # CLI scripts
├── subscribers/  # Event listeners
├── workflows/    # Custom executable flows

medusa-config.ts  # DB and other configurations
.medusa/          # Auto-generated files (DO NOT EDIT or COMMIT)
```

---

## 🏗 Medusa Architecture

Medusa is a **headless commerce platform**. Storefronts, dashboards, and clients interact with it via API routes.

### 🔁 Request Flow Layers

1. **API Routes (HTTP Layer)**  
   - Based on Express.js  
   - Can connect to Redis for session management  

2. **Workflows**  
   - API routes invoke workflows for business logic  

3. **Modules**  
   - Workflows delegate to domain-specific modules  

4. **Data Store**  
   - Modules interact with PostgreSQL  

**Flow:**  
`Client → API → Workflow → Module → DB`

---

## 🗃 Database Layer

- All modules use a shared PostgreSQL DB  
- Database interaction is abstracted by modules

---

## 🔌 Third-Party Integrations

Medusa integrates external services through:

### 1. Commerce Modules  
For commerce features (e.g., Stripe for payments, ShipStation for fulfillment)

### 2. Infrastructure Modules  
For internal system services:

- **Cache Module** – e.g., Redis, Memcached  
- **Event Module** – Pub/Sub system (e.g., Redis)  
- **File Module** – e.g., AWS S3 for file storage  
- **Locking Module** – e.g., Redis to avoid race conditions  
- **Notification Module** – e.g., SendGrid for email  
- **Workflow Engine Module** – e.g., Redis for orchestration

🛠 You can replace any of these services with your preferred tools.

---

## 🏗 Build Medusa Application

To build a production-ready app:

```bash
npx medusa build
```

This:

- Compiles TypeScript  
- Outputs to `.medusa` directory  
- Creates standalone app (no source files needed)

### 📁 Build Output

```
.medusa/
└── server/
    └── public/admin/   # Admin dashboard build
```

---

## ▶️ Start Built Medusa Application

1. Change to `.medusa/server`  
2. Install dependencies  
3. Copy `.env` from root  
4. Set `NODE_ENV=production`  
5. Start the app:

```bash
npm run start
```

---

## 🚀 Medusa Deployment Overview

### 🧩 Project Structure

- Medusa Application (Server + Admin Dashboard)  
- Storefront (e.g., built with Next.js)

**Deploy Medusa first** – the storefront depends on its API.

---

### 🌐 Deploying the Medusa Application

Use any Node.js-compatible host:  
- Railway  
- DigitalOcean  
- AWS  
- Heroku

Must connect to:
- PostgreSQL  
- Redis  
- Optional integrations (Stripe, S3, etc.)

**Tip:** Use hosting providers like Railway or DigitalOcean for hosting DB + Redis + App together.

---

### 🌍 Deploying the Storefront

Deployed separately using:
- Vercel  
- Netlify  
- Any frontend platform

---

## ✅ Summary

Medusa is a **headless, open-source commerce platform** designed for:

- Flexibility  
- Modularity  
- Extensibility  

### Key Architecture

- **API Routes**: Express.js  
- **Workflows**: Business logic  
- **Modules**: Resource management  
- **PostgreSQL**: Data storage  
- **Plugins**: Extend with 3rd-party services

### 3rd-Party Integration

- **Commerce Modules**: Stripe, ShipStation, etc.  
- **Infrastructure Modules**: Redis (cache, pub/sub), AWS S3 (files), etc.

### Build & Deploy

- `npx medusa build` → outputs compiled app in `.medusa/`  
- Start production app from `.medusa/server`  
- Set environment variables correctly  
- Host backend on Node-compatible providers  
- Host storefront separately on frontend platforms

Optionally use **Medusa Cloud** for managed deployments.