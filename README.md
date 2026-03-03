# Digital Key Store Database

This repository contains a set of SQL scripts defining a relational database for managing
**digital license keys**.

---

## About the database

The schema implements core functionality for selling, reserving, and distributing
software/gaming license keys. Key concepts include:

- **User accounts** with statuses (active/locked/logically deleted)
- **Products** representing software or services identified by SKU, platform, region, etc.
- **License keys** tied to products, with statuses like available, reserved, or issued.
- **Shopping cart & cart items** allowing users to build orders before purchase.
- **Orders and entitlements** tracking purchases and resulting license assignments.
- **Sharing groups** providing controlled access to keys among groups of users.

Several supporting objects enforce business rules via
`CHECK` constraints, unique indexes, and primary key constraints.

---

## Graphic model

<img width="1920" height="1080" alt="Blue Green Professional Flowchart Template Brainstorm (6)" src="https://github.com/user-attachments/assets/cf350ff8-e427-4232-aef7-59d95affd258" />

---

## What you can do

- **Install** the database by running `1_create.txt`.
- **Populate** it with sample data from `2_inserts.txt`.
- **Add foreign keys** using `3_foreign_keys.txt`.
- **View definitions, stored procedures, functions, and triggers** are provided in
  the corresponding files.
- **Browse** the structure to understand relationships: users → carts → orders → entitlements,
  etc.

  ---

## Limitations & notes

- The current schema assumes a single-currency store (`PLN`) and uses hardcoded locale
  conventions (e.g. `price_gross_pln`).
- There is no authentication or application layer; this is purely a data model.
- Some enums are small and might require expansion (e.g. order statuses, group roles).
- Triggers and stored procedures contain basic examples but are not exhaustive.
- All temporal fields use `DATETIME` or `DATE` without timezone support.

---

## Future enhancements

- **Localization support**: abstract currency/region fields and add multi-language
  descriptions for products.
- **Multi-currency/pricing tiers** for international stores.
- **Inventory management**: track stock counts, provider integration.
- **User roles/permissions** beyond simple statuses (admin/moderator).
- **Audit logging**: record changes to sensitive tables.
- **Performance tuning**: add more indexes or partition large tables.
- **API layer**: expose data via REST/GraphQL for integration with web frontends.
- **Testing harness**: include sample data scripts and unit tests for procedures.

Feel free to adapt the schema for other digital goods, embed it in your own

application, or use it as a learning resource for database design.
