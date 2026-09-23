# Assignment 03 — CHANGES

**Name:** Kaung Myat Hein **Student ID:** 6705140002

This is the written part of your submission. Explain **what you changed and why**, then record your **prompt log**. Keep before/after snippets to a line or two.

---

## 1 · What I changed

| #   | Code smell in the original                                                                              | What I changed it to                                                                                                                                  | OOP concept applied                    | How I verified behaviour was unchanged                                                             |
| --- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- | -------------------------------------------------------------------------------------------------- |
| 1   | Products, orders, and order items were stored as nested tuples/lists.                                   | Added `Product`, `OrderItem`, and `Order` classes. `OrderItem` has a `Product`, and `Order` has a customer and many items.                            | Classes / composition                  | Ran `python Assignment_03.py` → `PASS - behaviour is unchanged.`                                   |
| 2   | Customer tier logic used repeated `if/elif t == ...` chains for discounts and points.                   | Added `Customer`, `Silver`, `Gold`, and `Platinum` classes with polymorphic `discount_rate()` and `points_multiplier`.                                | Inheritance / polymorphism             | Ran the required self-test → PASS; no tier `if/elif` chain remains in the refactored calculations. |
| 3   | `calc()` mixed subtotal, tax, discount, points calculations, and receipt printing.                      | Moved calculations into pure `Order` methods (`subtotal`, `discount`, `tax`, `total`, `points`) and made `receipt()` responsible for formatting only. | Encapsulation / separation of concerns | Compared the complete program output through the built-in behaviour lock → PASS.                   |
| 4   | The original code used magic numbers such as `0.07`, `100`, `10`, and `0.03`.                           | Replaced them with named constants: `TAX_RATE`, `DISCOUNT_THRESHOLD`, `BULK_QTY_THRESHOLD`, `BULK_DISCOUNT_RATE`, and `POINTS_DIVISOR`.               | Clean code / encapsulation             | Ran the self-test after the refactor → PASS.                                                       |
| 5   | The original used `global TAXRATE`, and tax selection was performed inside the order-total calculation. | Removed the global and let each `Product` provide its own `tax_rate()`. Constructors also validate names, prices, quantities, and object types.       | Encapsulation / composition            | Ran the self-test → PASS; the required output is unchanged.                                        |

---

## 2 · Short reflection (4–6 sentences)

The biggest improvement was separating the store data from the calculations and printing, because each class now has a clear responsibility. Polymorphism also removed the repeated tier `if/elif` logic, so the discount and points rules belong to the appropriate customer-tier classes. Keeping the behaviour identical required careful preservation of the original discount thresholds, bulk-discount rule, tax rules, rounding, receipt text, and order sequence. I also had to keep the original floating-point calculations and output formatting unchanged so that the behaviour lock would still match exactly. The final self-test printed `PASS - behaviour is unchanged.`, confirming that the refactor preserved the required output.

---

## 3 · Prompt log (Level 2 — required)

| #   | My prompt to the AI                                                                                                                                                                                            | What it suggested (summary)                                                                                                                                                                                         | Accept / reject / edited                                   | How I checked it                                                                                                                                                                    |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | “read the instructions from Assignment_03.py and make tasks in Assignment_03.py and update in changes.md, following the instructions. give me back CHANGES.md and Assignment_03.py after finichsing the tasks” | Implemented the required OOP refactor using domain classes, composition, constructor validation, tier polymorphism, pure calculation methods, named constants, product-level tax, and a separate receipt formatter. | Edited/accepted after checking the assignment requirements | Ran `python Assignment_03.py`; the built-in behaviour lock printed `PASS - behaviour is unchanged.` I also checked that the required class design and checklist items were present. |

**Ownership statement.** By submitting, I confirm I understand and can explain every line of code I submitted, and that this prompt log reflects my actual AI use.

---

## 4 · Before-you-submit checklist

- [x] `python Assignment_03.py` prints **PASS**.
- [x] No tuples / parallel lists left in the refactored solution — products, orders, and items are objects.
- [x] No `if tier == ...` chains — tiers are a class family.
- [x] Calculation methods **return** values and do not `print`; printing is separate.
- [x] Constructors validate state; no leftover `global`; magic numbers are named.
- [x] The change table and reflection above are filled in.
- [x] The prompt log is complete and the ownership statement is signed.
