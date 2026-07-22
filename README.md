# ⚽ Football Ticket Booking System — Database Design & SQL

A relational database project that models a football ticket booking platform — covering fan registrations, tournament match listings, and ticket booking transactions. Built as part of a database design assignment, this project demonstrates ERD design, referential integrity, and intermediate-to-advanced SQL querying.

---

## 📌 Project Overview

The **Football Ticket Booking System** manages three core entities:

- **Users** — Football fans and ticket managers who use the platform
- **Matches** — Tournament fixtures, categories, and base ticket pricing
- **Bookings** — Individual ticket purchase transactions linking users to matches

The schema is designed around real-world business logic: a fan can book tickets for multiple matches, a match can have thousands of bookings, and each booking captures seat allocation, payment status, and final cost.

---

## 🗂️ Entity Relationship Diagram (ERD)

**View the ERD here:** [Add your Draw.io / Lucidchart public link]

### Relationships

| Relationship | Description |
|---|---|
| **One-to-Many** | One `User` → Many `Bookings` (a fan can purchase tickets for multiple matches) |
| **Many-to-One** | Many `Bookings` → One `Match` (a popular match can have thousands of bookings) |
| **One-to-One (logical)** | Each `Booking` row maps exactly one user to one match for a specific seat |

---

## 🧱 Database Schema

### 1. Users Table

| Column | Type | Description |
|---|---|---|
| `user_id` | PK | Unique identifier for each user |
| `full_name` | VARCHAR | First and last name |
| `email` | VARCHAR | Login email address |
| `role` | VARCHAR | `Ticket Manager` or `Football Fan` |
| `phone_number` | VARCHAR | Contact number (nullable) |

### 2. Matches Table

| Column | Type | Description |
|---|---|---|
| `match_id` | PK | Unique identifier for each match |
| `fixture` | VARCHAR | Competing teams (e.g., `Real Madrid vs Barcelona`) |
| `tournament_category` | VARCHAR | League/cup name |
| `base_ticket_price` | DECIMAL | Standard entry seat price |
| `match_status` | VARCHAR | `Available`, `Selling Fast`, `Sold Out`, `Postponed` |

### 3. Bookings Table

| Column | Type | Description |
|---|---|---|
| `booking_id` | PK | Unique booking transaction number |
| `user_id` | FK → Users | The user who made the booking |
| `match_id` | FK → Matches | The match being attended |
| `seat_number` | VARCHAR | Allocated seat (e.g., `A-12`), nullable |
| `payment_status` | VARCHAR | `Pending`, `Confirmed`, `Cancelled`, `Refunded` |
| `total_cost` | DECIMAL | Final invoice price |

---

## ✨ Key Features

- ✅ Normalized relational schema with clearly defined **Primary Keys** and **Foreign Keys**
- ✅ Referential integrity enforced between Users, Matches, and Bookings
- ✅ Realistic sample dataset covering multiple fixtures, users, and booking states
- ✅ SQL queries demonstrating:
  - **JOIN variants** — `INNER JOIN`, `LEFT JOIN`
  - **Aggregations** — `AVG`, `COUNT` with `HAVING`
  - **Subqueries** — filtering rows against computed aggregate values
  - **Pattern matching** — `LIKE`, `ILIKE` for case-insensitive search
  - **NULL handling** — `IS NULL`, `COALESCE` for graceful fallback values
  - **Pagination** — `LIMIT` / `OFFSET`

---

## 🔍 SQL Query Highlights

| # | Query | Concepts Used |
|---|---|---|
| 1 | Available Champions League matches | `WHERE`, filtering |
| 2 | Search users by name pattern | `LIKE`, `ILIKE` |
| 3 | Bookings with missing payment status | `IS NULL`, `COALESCE` |
| 4 | Booking details with user & fixture info | `INNER JOIN` |
| 5 | All users including those with no bookings | `LEFT JOIN` |
| 6 | Bookings above average total cost | Subquery, `AVG` |
| 7 | Top 2 most expensive matches (skip highest) | `ORDER BY`, `LIMIT`, `OFFSET` |

Full query definitions and expected outputs are available in [`QUERY.sql`](./QUERY.sql).

---

## 🛠️ Tech Stack

- **Database:** SQL (PostgreSQL compatible)
- **Design Tool:** Draw.io  (ERD)

---

## 📁 Repository Structure

```
football-ticket-booking-system/
├──  erd-diagram.png
|__ sample_data.sql     # Sample data inserts. All SQL queries with comments
└── README.md

```
✅ ERD Link: https://drawsql.app/teams/rabbani08/diagrams/football-ticket-booking-system
---


## 🎓 Learning Outcomes

- Designing ERDs with correct cardinality (1:1, 1:N, N:1)
- Enforcing data integrity with Primary and Foreign Keys
- Writing multi-table SQL joins and subqueries
- Handling NULLs and missing data gracefully
- Applying aggregation and pagination in real-world query scenarios

---

## 👤 Author

**MD Golam RABBANI**
[LinkedIn](https://www.linkedin.com/in/mdgolamrabbani1/) · [GitHub](https://github.com/rabbani37) · [Email](mrabbbani08@gmail.com)

---

## 📄 License

This project is submitted as part of an academic assignment and is shared for learning and portfolio purposes.
