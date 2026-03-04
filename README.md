# 📚 BookCart QA Portfolio

> Manual QA project built from scratch on [BookCart](https://bookcart.azurewebsites.net) — an open-source e-commerce book store built with .NET 8 and Angular 18.

This repository demonstrates a full QA workflow: requirements analysis, test planning, test case writing, test execution, and bug reporting — using **Jira**, **Zephyr Scale** and **GitHub**.

---

## 📌 Project Summary

| | |
|---|---|
| **App under test** | https://bookcart.azurewebsites.net |
| **Tech stack** | .NET 8 · Angular 18 · SQL Server |
| **Test management** | Jira + Zephyr Scale |
| **Project key** | `BOOK` |
| **Epics** | 5 |
| **User stories** | 18 |
| **Story points** | 66 |
| **Sprints** | 3 |
| **Test cases** | 29 (7 smoke · 20 regression · 2 edge-case) |
| **Bugs found** | 1 (High severity) |

---

## 🗂️ Repository Structure

```
bookcart-qa/
├── README.md
├── All test cases.xlsx          ← full test suite export from Zephyr Scale
├── test-cases/                  ← all 29 test cases in Markdown
│   ├── authentication/
│   ├── catalog/
│   ├── cart/
│   ├── orders/
│   ├── wishlist-profile/
│   └── edge-cases/
└── evidence/
    ├── jira/                    ← sprint board, roadmap, backlog screenshots
    ├── zephyr/                  ← test cycles, execution, test player screenshots
    └── bug-report/              ← defect report, reproduction video
```

---

## 🧩 Jira — Project Setup

The project was set up in Jira using a **Scrum** template with 5 epics, 18 user stories and 3 sprints.

### Epics

| Key | Epic |
|-----|------|
| BOOK-EP1 | User Registration & Authentication |
| BOOK-EP2 | Book Catalog & Search |
| BOOK-EP3 | Shopping Cart |
| BOOK-EP4 | Checkout & Orders |
| BOOK-EP5 | Wishlist & User Profile |

### Product Roadmap
![Product Roadmap](evidence/jira/Product%20Roadmap.png)

### Product Board
![Product Board](evidence/jira/Product%20board.png)

### Sprint 1 — Active Sprint
![Current Active Sprint](evidence/jira/Current%20Active%20Sprint.png)

### Sprint 2
![Other Sprint](evidence/jira/Other%20Sprint.png)

### Sprint 3
![Third Sprint](evidence/jira/Third%20sprint.png)

---

## 🧪 Zephyr Scale — Test Cases & Execution

Test cases were written in **Zephyr Scale**, organized into folders by module, and executed in test cycles mapped to each sprint.

### Test Case Folders
![Test Cases in Folders](evidence/zephyr/Test%20cases%20in%20Folders.png)

### Test Cycles Overview
![Test Cycles](evidence/zephyr/Test%20Cycles.png)

### Test Cycle — Player View
![Test Cycle Player](evidence/zephyr/Test%20Cycle%20-%20Player.png)

### Test Player — Execution
![Test Player](evidence/zephyr/Test%20Player.png)

---

## 📋 Test Case Summary

| ID | Summary | Module | Label | Priority |
|----|---------|--------|-------|----------|
| TC-001 | Register with all valid fields | Authentication | 🟡 smoke | High |
| TC-002 | Register with existing username | Authentication | 🔵 regression | High |
| TC-003 | Register with mismatched passwords | Authentication | 🔵 regression | High |
| TC-004 | Submit empty registration form | Authentication | 🔵 regression | High |
| TC-005 | Login with valid credentials | Authentication | 🟡 smoke | High |
| TC-006 | Login with invalid password | Authentication | 🔵 regression | High |
| TC-007 | Login with non-existent username | Authentication | 🔵 regression | Medium |
| TC-008 | Logout and verify session terminated | Authentication | 🔵 regression | Medium |
| TC-009 | Homepage displays book list | Catalog | 🟡 smoke | High |
| TC-010 | Category filter shows correct books | Catalog | 🔵 regression | High |
| TC-011 | Switch category updates book list | Catalog | 🔵 regression | Medium |
| TC-012 | Search for a known book title | Catalog | 🟡 smoke | High |
| TC-013 | Search returns empty state for no results | Catalog | 🔵 regression | Medium |
| TC-014 | Book detail page shows correct info | Catalog | 🟡 smoke | Medium |
| TC-015 | Add book to cart increments badge | Cart | 🟡 smoke | High |
| TC-016 | Add to cart while logged out redirects to login | Cart | 🔵 regression | High |
| TC-017 | Cart page shows books with correct total | Cart | 🔵 regression | High |
| TC-018 | Remove book from cart updates total | Cart | 🔵 regression | High |
| TC-019 | Increase quantity updates total | Cart | 🔵 regression | Medium |
| TC-020 | Place order clears cart and saves order | Orders | 🟡 smoke | Critical |
| TC-021 | Place order with empty cart shows error | Orders | 🔵 regression | High |
| TC-022 | Order history shows past orders | Orders | 🔵 regression | High |
| TC-023 | Order detail shows correct items | Orders | 🔵 regression | Medium |
| TC-024 | Add book to wishlist | Wishlist | 🔵 regression | Medium |
| TC-025 | Move book from wishlist to cart | Wishlist | 🔵 regression | Medium |
| TC-026 | Change password with correct current password | Profile | 🔵 regression | Medium |
| TC-027 | Change password with wrong current password | Profile | 🔵 regression | Medium |
| TC-028 | Register with maximum length username | Edge Cases | 🟠 edge-case | Medium |
| TC-029 | Navigate to /login while already authenticated | Edge Cases | 🟠 edge-case | Medium |

---

## 🐛 Bug Report

**1 defect identified** during Sprint 2 test execution.

| Field | Detail |
|-------|--------|
| **ID** | BOOK-BUG-001 |
| **Summary** | No error message displayed on failed login |
| **Severity** | High |
| **Affects** | TC-006, TC-007 |
| **Steps** | Enter invalid credentials → click Login |
| **Expected** | Error message: "Invalid username or password" |
| **Actual** | Page shows no feedback — silent failure |

### Defect Report
![Defect Report](evidence/bug-report/Defect%20report.png)

### Bug Reproduction Video
> 📹 See [`evidence/bug-report/Bug Reproduction steps`](evidence/bug-report/Bug%20Reproduction%20steps) for the full reproduction recording.

---

## 🏷️ Labels

| Label | Description |
|-------|-------------|
| 🟡 `smoke` | Core happy-path flows. Run first. If any fail the module is blocked. |
| 🔵 `regression` | Negative tests, validations and secondary flows. Run after smoke passes. |
| 🟠 `edge-case` | Boundary and unexpected behavior scenarios. Run last. |

---

## 📁 Zephyr Folder Structure

```
BookCart/
├── Authentication/
│   ├── Registration       → TC-001 to TC-004
│   └── Login              → TC-005 to TC-008
├── Catalog/
│   ├── Browse             → TC-009, TC-010, TC-011, TC-014
│   └── Search             → TC-012, TC-013
├── Cart/
│   ├── Add-Remove         → TC-015, TC-016, TC-018
│   └── View               → TC-017, TC-019
├── Orders/
│   ├── Checkout           → TC-020, TC-021
│   └── History            → TC-022, TC-023
├── Wishlist               → TC-024, TC-025
├── Profile                → TC-026, TC-027
└── EdgeCases/
    └── Authentication     → TC-028, TC-029
```

---

## 🔗 Links

- **App under test:** https://bookcart.azurewebsites.net
- **Source code:** https://github.com/AnkitSharma-007/BookCart
- **Jira project:** [add your Jira link here]
