# E-commerce Frontend (Next.js)

A minimal Next.js 14 ecommerce frontend with App Router, TypeScript, and Tailwind CSS.

## 🎯 About This Repository

This repository is part of the **ecommerce-polyrepo** project - a polyrepo setup designed for testing the [Propel](https://propel.us) code review feature across multiple microservices.

### Role in Microservices Architecture

The Frontend serves as the **user interface** that connects to the API Gateway:

```
┌─────────────────┐
│    Frontend     │
│    (Next.js)    │
│   [THIS REPO]   │
└────────┬────────┘
         │ HTTP/REST
         ▼
  ┌──────────────┐
  │ API Gateway  │
  │   (Go/Gin)   │
  └──────────────┘
         │
         ▼
   Backend Services
   (User, Listing,
    Inventory)
```

### Quick Start (Standalone Testing)

To test this frontend independently:

```bash
# 1. Install dependencies
npm install

# 2. Set up environment
cp .env.example .env.local
# Edit .env.local to point to API Gateway
# NEXT_PUBLIC_API_URL=http://localhost:8080

# 3. Run development server
npm run dev

# 4. Open browser
open http://localhost:3000

# 5. Build for production (optional)
npm run build
npm start
```

**Note:** This frontend requires the API Gateway to be running for backend data. For local development with mock data, the API client in `src/lib/api.ts` handles graceful fallbacks. See the [parent polyrepo](https://github.com/jasonyuezhang/ecommerce-polyrepo) for orchestrated setup.

---

## Tech Stack

- Next.js 14 (App Router)
- React 18
- TypeScript
- Tailwind CSS

## Getting Started

1. Install dependencies:
   ```bash
   npm install
   ```

2. Copy environment variables:
   ```bash
   cp .env.example .env.local
   ```

3. Run the development server:
   ```bash
   npm run dev
   ```

4. Open [http://localhost:3000](http://localhost:3000)

## Project Structure

```
src/
  app/
    layout.tsx      # Root layout
    page.tsx        # Home page
    products/
      page.tsx      # Product listing
      [id]/
        page.tsx    # Product detail
  components/
    Header.tsx      # Navigation header
    ProductCard.tsx # Product card component
  lib/
    api.ts          # API client
```

## Environment Variables

- `NEXT_PUBLIC_API_URL` - Backend API URL (default: http://localhost:8080)
