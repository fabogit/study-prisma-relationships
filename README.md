# study-prisma-relationships

> A relational database modeling laboratory demonstrating one-to-one, one-to-many, many-to-many, and self-referential schema patterns using Prisma ORM and SQLite.

**Inception (First Commit):** `2023-01-07` • **Batch / Horizon:** `batch-2023` • **Architecture Domain:** `Relational Data Modeling / Prisma ORM`

---

## 📌 Architecture & Overview

`prisma-relationships` is an interactive engineering laboratory deconstructing relational database modeling using Prisma ORM. Rather than exposing an HTTP server, it provides executable TypeScript scripts powered by `tsx` and `@faker-js/faker` to demonstrate data insertion, relation traversal, and nested schema queries across standard relational patterns.

The laboratory isolates the four foundational relational patterns of relational database theory:

```
+-------------------------------------------------------------------------+
|                          prisma-relationships                           |
|                                                                         |
|  1. ONE-TO-ONE (1:1)                                                    |
|     +--------+              +---------+                                 |
|     |  User  |<------------>| Profile |  (Unique foreign key: userId)   |
|     +---+----+              +---------+                                 |
|         |                                                               |
|  2. ONE-TO-MANY (1:N)                                                   |
|         |                   +---------+                                 |
|         +------------------>|  Order  |  (Multiple orders per user)     |
|                             +----+----+                                 |
|                                  |                                      |
|  3. MANY-TO-MANY (M:N)           |                                      |
|                             +----+----+     +----------+                |
|                             | Product |<--->| Category |                |
|                             +----+----+     +-----+----+                |
|                                  |                |                     |
|  4. SELF-REFERENTIAL (1:N)       |                v                     |
|                                  |          +----------+                |
|                                  |          | Sub-Cat  |                |
|                                  v          +----------+                |
|                             (Many-to-Many Order <-> Product)            |
+-------------------------------------------------------------------------+
```

* **Context:** Hands-on reference laboratory created to explore and validate declarative relationship mappings, foreign key constraints, and cascading rules in Prisma ORM.
* **Key Patterns:**
  * **One-to-One (1:1):** Decoupling authentication (`User`) from personal profile data (`Profile`) using unique foreign key constraints.
  * **One-to-Many (1:N):** Relational linking between customer entities (`User`) and historical purchase records (`Order`).
  * **Many-to-Many (M:N):** Implicit join table modeling between `Product` and `Category`, as well as `Order` and `Product`.
  * **Self-Referential Tree Hierarchy:** Parent-child category nesting modeling e-commerce taxonomies via unary relationships (`CategoryToCategory`).

---

## 🛠 Tech Stack

* **ORM & Database:** Prisma ORM 4.4.0 (`@prisma/client`, `prisma`), SQLite
* **Execution & Language:** Node.js (>= 18), TypeScript 4.8.4, `tsx` 3.10.3 (ESM runtime)
* **Data Synthesis:** `@faker-js/faker` 7.6.0

---

## ✨ Features & Endpoints

* **Executable Scenario Scripts:** Discrete command-line entry points illustrating each relationship pattern with live query results.
* **Automated Mock Data Generation:** Realistic synthetic user names, descriptions, and catalog items generated via Faker.js.
* **Migration Audit Trail:** Versioned SQL DDL migrations located in `prisma/migrations/`.
* **Prisma Studio Compatibility:** Visual inspection of relational graph structures via `npx prisma studio`.

### Executable Demonstrations

| Command | Script Path | Relationship Pattern | Description |
|---|---|---|---|
| `npm run 1` | `src/1-one-to-one.ts` | One-to-One (`1:1`) | Creates `User` and links unique `Profile` record. |
| `npm run 2` | `src/2-one-to-many.ts` | One-to-Many (`1:N`) | Populates `User` and creates associated `Order` records. |
| `npm run 3` | `src/3-many-to-many.ts` | Many-to-Many (`M:N`) | Associates `Product` items across multiple `Category` tags. |
| `npm run 4` | `src/4-many-to-many.ts` | Complex Relational Graph | Demonstrates self-referential categories and multi-order joins. |

---

## 🚀 Getting Started

### Prerequisites

* Node.js `>= 18.0.0`
* npm `>= 8.0.0`

### Installation

```bash
# Clone the repository
git clone https://github.com/fabogit/study-prisma-relationships.git
cd study-prisma-relationships

# Install dependencies
npm install
```

### Environment Configuration

Configure your SQLite database file path in `.env`:

```env
DATABASE_URL="file:./dev.db"
```

### Database Migration & Client Generation

```bash
# Apply migrations to local SQLite database
npx prisma migrate dev

# Generate Prisma Client types
npx prisma generate
```

### Running Relationship Demonstrations

```bash
# Run One-to-One demonstration
npm run 1

# Run One-to-Many demonstration
npm run 2

# Run Many-to-Many demonstration
npm run 3

# Run Self-Referential hierarchy demonstration
npm run 4
```

### Inspecting Data Graph Visually

```bash
# Launch interactive web visualizer
npx prisma studio
```

---

## 📄 License & Author

Developed by [@fabogit](https://github.com/fabogit).
