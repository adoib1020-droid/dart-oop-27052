# Dart OOP Assignment: Kigali Bus Card

**Name:** Abdalrahman Abdalkarim  
**Student ID:** 27052

## My numbers
- D = 52, L = 2
- Starting balance = 1520 RWF
- Bus fare = 252 RWF
- Student discount = 12%

## Output of main.dart
```text
Error: name too short
Owner: Abdalrahman | Balance: 1520 RWF
Owner: Abdalrahman Abdalkarim | Balance: 1520 RWF
Error: top-up must be 500 to 50000 RWF
Topped up 2000 RWF
Paid 252 RWF
Paid 252 RWF
Owner: Abdalrahman Abdalkarim | Balance: 3016 RWF
Student discount: 30 RWF
Paid 222 RWF
Owner: Abdalrahman Abdalkarim | Balance: 1298 RWF
Student card: 12% off
```

## Part 1: Why no setter for balance?
If there was a setter, any code could change the balance directly, for example `card.balance = 999999`, and skip the rules. Without a setter, the balance can only change through `topUp` and `pay`, which check the amount first. This keeps the money safe.

## Part 2: What does ~/ do?
`~/` is integer division. It divides and removes the decimal part. `print(237 * 17 / 100);` prints `40.29` (a double), but `print(237 * 17 ~/ 100);` prints `40` (an int). I use it so the discount is a whole number of RWF.

## Part 4: Bug table
| Bug | The line | Why it is wrong (your words) | Your fix |
|---|---|---|---|
| 1 | `String _brand;` and `int _battery;` | The fields have no starting value, and Dart does not allow that for non-nullable fields. | `String _brand = '';` and `int _battery = 0;` |
| 2 | `SmartPhone(String brand, int battery, String system) {` | The constructor does not call the parent constructor, so Phone is not built. | Added `: super(brand, battery)` |
| 3 | `@override void restart()` | `@override` only works if the parent has that method, and Phone has no `restart`. | Removed `@override` |
| 4 | `p.battery = 100;` | There is no setter for battery, so I cannot assign a value to it. | Added `set battery(int value)` that accepts only 0 to 100 |
| 5 | `print(p.battery());` | `battery` is a getter, not a method, so it must not have `()`. | `print(p.battery);` |
| Not a bug | `Phone p = new Phone('Tecno', 50);` | `new` is old style but it is still allowed in Dart, so the line works. | (none) |

## Part 5
My prediction:
It will print:
1
5

Why:
- For `a` (Bag): `_items` starts at 0. `a.add()` makes it 1. `a.items = -5` is ignored because the setter only accepts values >= 0. So it prints 1.
- For `b` (BigBag): each `b.add()` calls `super.add()` twice, so it adds 2. Two calls make 4. Then `b.items = b.items + 1` makes 5. So it prints 5.

Real output:
1
5

Was I right?
Yes, my prediction was right.