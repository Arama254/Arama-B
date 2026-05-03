# 🧺 Arama — Laundry Management Tool

> A terminal-based C application that automates itemized pricing,
> Express surcharge calculation, and append-safe receipt logging
> for small laundry businesses. No spreadsheets. No internet. Just C.

---

## 📋 Description

Arama was built during **CS50 Week 1** as a practical application of
fundamental C programming concepts. It captures customer orders at the
point of service, calculates the correct total based on item counts and
service tier, and permanently logs every receipt to `laundry_log.txt`
in append mode — so no record is ever lost between sessions.

Designed for counter-based laundry operations that need a fast, reliable
paper-trail replacement without the overhead of a full POS system.

---

## ✨ Key Features

### 👕 Itemized Pricing Engine
Calculates a subtotal from three item types at fixed unit prices:

| Item    | Unit Price |
|---------|------------|
| Shirt   | $2.00 each |
| Pants   | $3.00 each |
| Dress   | $5.00 each |

### ⚡ Express Surcharge System
Applies a flat **$5.00 surcharge** to any order marked as Express
tier (`E`). Standard tier (`S`) orders pay the subtotal only.
Invalid tier codes are rejected — no silent defaults, no corrupt records.

### 📂 Append-Safe File Logging
Every completed order is written to `laundry_log.txt` using:
- `fopen` in `"a"` (append) mode — history is never overwritten
- `fflush` after every record — crash-safe, data hits disk immediately
- `fclose` at session end — OS file handle cleanly released

### 🔒 Input Validation
- `get_int` enforces whole-number item counts (no decimal entries)
- `get_string` return checked for `NULL` before any write
- Tier input normalized to uppercase (`e` → `E`, `s` → `S`)

### 🧾 Receipt Preview
Before saving, a full breakdown is printed to the terminal so the
cashier can verify the order — catching errors before they become
permanent log entries.

---

## 🛠️ Technical Foundation

| Layer         | Detail                                      |
|---------------|---------------------------------------------|
| Language      | C (C11 standard)                            |
| Input Library | `<cs50.h>` — safe, validated terminal input |
| File I/O      | Standard C `<stdio.h>` — `fprintf`, `fflush`, `fclose` |
| Concepts      | Loops, conditionals, constants, file persistence |
| Environment   | CS50 Week 1 — terminal / Linux              |

Arama was written to demonstrate that core CS50 Week 1 concepts —
variables, data types, conditionals, and loops — can power a real,
production-relevant business tool with minimal complexity.

---

## 🚀 Usage

### Compile
```bash
gcc -o arama arama.c -lcs50
