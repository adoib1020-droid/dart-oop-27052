# Dart OOP Assignment: Kigali Bus Card

**Name:** Abdalrahman Abdalkarim
**Student ID:** 27052

## Part 5

My prediction:
It will print:
1
5

Why:
- For `a` (Bag): `_items` starts at 0. Calling `a.add()` makes it 1. Then `a.items = -5` is ignored because the setter only accepts values >= 0. So `print(a.items)` prints 1.
- For `b` (BigBag): `BigBag` overrides `add()` to call `super.add()` twice, so each `b.add()` adds 2. Calling `b.add()` twice makes `_items` equal to 4. Then `b.items = b.items + 1` makes it 5. So `print(b.items)` prints 5.

Real output:
(to be added after running)

Was I right?
(to be added after running)