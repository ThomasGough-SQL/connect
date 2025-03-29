# 🛫 Social Network & Affiliation Schema

This project defines a relational database schema for a **user connection and affiliation system**. It models users, companies, institutes, and the relationships between them, such as follows and affiliations.

## 📦 Schema Overview

The database includes the following tables:

| Table                     | Purpose                                                       |
|---------------------------|---------------------------------------------------------------|
| `users`                  | Stores user profile information                               |
| `companies`              | Represents companies that users can follow or be linked to    |
| `institutes`             | Represents educational institutions users can follow or attend|
| `following`              | Tracks users following companies                              |
| `user_following`         | Tracks users following other users                            |
| `institute_following`    | Tracks users following institutes                             |
| `user_company`           | Maps users to companies they are affiliated with              |
| `user_institute`         | Maps users to institutes they are affiliated with             |
| `user_company_following` | Tracks companies a user is following                          |
| `affiliation`            | Additional mapping between users and institutes               |

## 🧪 Example Query

List all users and the companies they follow:
```sql
SELECT 
    users.first_name || ' ' || users.last_name AS user_name,
    companies.name AS company_followed
FROM user_company_following
JOIN users ON user_company_following.user_id = users.id
JOIN companies ON user_company_following.company_id = companies.id;
```

## ⚙️ Setup Instructions

1. Create a new SQLite database:
   ```bash
   sqlite3 social_network.db < schema.sql
   ```

2. Run `.tables` in SQLite to verify all tables are created:
   ```bash
   sqlite3 social_network.db
   .tables
   ```

3. (Optional) Populate tables with test data and run queries.

## 🧠 Notes

- The schema uses **foreign keys** to maintain relational integrity.
- `AUTOINCREMENT` is used for unique ID generation.
- Designed to be SQLite-compatible, but can be adapted for MySQL/PostgreSQL easily.

## 🙋 Author

Built by **Thomas John Gough** (aka `@Readyray7513`) as part of ongoing full-stack and data development learning.
