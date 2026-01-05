# Aptitude Questions & Solutions

This document contains step-by-step solutions to the aptitude questions covering topics such as Exponents, Logical Reasoning, Functional Equations, Permutations, Number Theory, Geometry, and Algebra.

---

## 1. Exponents
**Question:** If `7^x - 7^(x-2) = 48 * 7^6`, what is the value of `x`?

**Solution:**
1. **Factor out the smallest power:**
   On the left side, factor out `7^(x-2)`:
   > `7^(x-2) * (7^2 - 1) = 48 * 7^6`

2. **Simplify:**
   Calculate `7^2 - 1`:
   > `7^(x-2) * (49 - 1) = 48 * 7^6`
   > `7^(x-2) * 48 = 48 * 7^6`

3. **Cancel common terms:**
   Divide both sides by 48:
   > `7^(x-2) = 7^6`

4. **Solve for x:**
   Since the bases are the same, equate the exponents:
   > `x - 2 = 6`
   > `x = 8`

**Answer:** `x = 8`

---

## 2. Logical Reasoning (Climbing Problem)
**Question:** A tortoise currently at the bottom of a 65-meter hill is trying to climb it. Every hour, the tortoise climbs five meters and slips down three meters. How long would it take for the tortoise to reach the top of the hill?

**Solution:**
1. **Calculate effective speed:**
   Every hour, the tortoise climbs 5m and slips 3m.
   > Net gain per hour = `5 - 3 = 2` meters.

2. **Account for the final stretch:**
   *Note: This is a trick question.* In the final hour, the tortoise will climb 5 meters and reach the top. Once it reaches the top, it does not slip back down.
   Subtract the final 5 meters from the total distance:
   > `65m - 5m = 60m`

3. **Calculate time for the first 60 meters:**
   > `Time = Distance / Net Speed`
   > `60m / 2 m/hr = 30 hours`

4. **Add the final hour:**
   After 30 hours, the tortoise is at 60 meters. In the 31st hour, it climbs 5 meters to reach 65 meters.
   > Total Time = `30 + 1 = 31` hours.

**Answer:** 31 hours

---

## 3. Functional Equations
**Question:** `f(x+y) = f(x) + f(y)` for all positive integer values of `x` and `y`. If `f(2) = 4`, what is the value of `f(3)`?

**Solution:**
1. **Find f(1):**
   We know that `f(2) = f(1+1)`.
   According to the rule: `f(1+1) = f(1) + f(1) = 2f(1)`.
   Given `f(2) = 4`:
   > `2f(1) = 4` → `f(1) = 2`

2. **Calculate f(3):**
   We can express 3 as `2 + 1`.
   > `f(3) = f(2+1) = f(2) + f(1)`

   Substitute the known values (`f(2)=4` and `f(1)=2`):
   > `f(3) = 4 + 2 = 6`

**Answer:** 6

---

## 4. Permutations & Combinations
**Question:** In how many different ways can 3 identical green shirts and 3 identical red shirts be distributed among 6 children such that each child receives a shirt?

**Solution:**
1. **Analyze the setup:**
   We have 6 distinct children (positions) and a set of 6 shirts where 3 are Green (G) and 3 are Red (R).
   This is equivalent to finding the number of distinct permutations of the letters: **G, G, G, R, R, R**.

2. **Apply the permutation formula for repeated items:**
   Formula: `n! / (p! * q!)` where `n` is total items, and `p, q` are the counts of identical items.
   > Ways = `6! / (3! * 3!)`

3. **Calculate:**
   > `720 / (6 * 6)`
   > `720 / 36 = 20`

**Answer:** 20 ways

---

## 5. Number Theory (LCM)
**Question:** What could be the values of integers from 180 to 300, inclusive, that leave the remainder 2 when divided by 15 and by 9?

**Solution:**
1. **Find the LCM:**
   The number leaves the same remainder (2) for both divisors. The number must be in the form:
   > `N = LCM(15, 9) * k + 2`
   
   LCM of 15 and 9 is **45**.
   So, `N = 45k + 2`.

2. **Find values within range [180, 300]:**
   Test integer values for `k`:
   * If `k = 4`: `45(4) + 2 = 180 + 2 = 182` (Valid)
   * If `k = 5`: `45(5) + 2 = 225 + 2 = 227` (Valid)
   * If `k = 6`: `45(6) + 2 = 270 + 2 = 272` (Valid)
   * If `k = 7`: `45(7) + 2 = 315 + 2 = 317` (Too high)

**Answer:** 182, 227, 272

---

## 6. Geometry & Percentages
**Question:** The diameter of a circle is increased by 50%. By what percentage does the area increase?

**Solution:**
1. **Relationship between Diameter and Area:**
   Area is proportional to the square of the diameter (`Area ∝ d^2`).

2. **Calculate Increase:**
   Let initial diameter = `d`.
   New diameter = `1.5d` (since it increased by 50%).
   New Area ∝ `(1.5d)^2 = 2.25d^2`.

3. **Find Percentage Change:**
   The new area is **2.25** times the original area.
   Change = `2.25 - 1 = 1.25`.
   Percentage = `1.25 * 100% = 125%`.

**Answer:** 125%

---

## 7. Algebra (Radicals)
**Question:** If `sqrt(sqrt(sqrt(3x))) = 4th_root(2x)`, what is the value of `x`, assuming `x > 0`?

**Solution:**
1. **Convert radicals to exponents:**
   * LHS: `sqrt(sqrt(sqrt(3x)))` is `(3x)^(1/2 * 1/2 * 1/2) = (3x)^(1/8)`
   * RHS: `4th_root(2x)` is `(2x)^(1/4)`

2. **Equate and solve:**
   > `(3x)^(1/8) = (2x)^(1/4)`

   Raise both sides to the power of 8 to eliminate fractions:
   > `3x = ((2x)^(1/4))^8`
   > `3x = (2x)^2`
   > `3x = 4x^2`

3. **Isolate x:**
   Divide by `x` (since `x > 0`):
   > `3 = 4x`
   > `x = 3 / 4`

**Answer:** 0.75 (or 3/4)

---

## 8. Averages (Mixtures)
**Question:** If a group of students having an average age of 16 years joined a class, the average age of all the students in the class reduces from 18 years to 17 years. What is the ratio of the number of students who joined the class to the number of students who were initially in the class?

**Solution:**
1. **Set up the equation:**
   * Let `N1` = initial students (Avg age 18).
   * Let `N2` = new students (Avg age 16).
   * Final Avg = 17.
   
   > `(18*N1 + 16*N2) / (N1 + N2) = 17`

2. **Solve:**
   > `18*N1 + 16*N2 = 17(N1 + N2)`
   > `18*N1 + 16*N2 = 17*N1 + 17*N2`
   > `18*N1 - 17*N1 = 17*N2 - 16*N2`
   > `N1 = N2`

3. **Find Ratio:**
   The ratio of joined (`N2`) to initial (`N1`) is **1:1**.

**Answer:** 1:1

---

## 9. Number Theory (Digits)
**Question:** If `x` represents the sum of all the positive three-digit numbers that can be constructed using each of the distinct nonzero digits `a`, `b`, and `c` exactly once, what is the largest integer by which `x` must be divisible?

**Solution:**
1. **Form the numbers:**
   The distinct 3-digit numbers formed by `a, b, c` are: `abc, acb, bac, bca, cab, cba`.

2. **Sum them up:**
   In each position (hundreds, tens, units), each digit appears exactly twice (`2*a`, `2*b`, `2*c`).
   > Sum = `2(a+b+c) * 100 + 2(a+b+c) * 10 + 2(a+b+c) * 1`
   > Sum `x` = `(a+b+c) * (200 + 20 + 2)`
   > `x = 222 * (a+b+c)`

3. **Find largest mandatory divisor:**
   `x` is always a multiple of 222.
   The term `(a+b+c)` varies depending on the digits chosen. Since consecutive sums (like 6 and 7) are coprime, there is no other guaranteed factor shared by all possible outcomes.
   Thus, **222** is the largest guaranteed divisor.

**Answer:** 222

---

## 10. Sophie Germain Primes
**Question:** A “Sophie Germain” prime is any positive prime number `p` for which `2p + 1` is also prime. The product of all the possible units digits of Sophie Germain primes greater than 5 is?

**Solution:**
1. **Identify valid unit digits for primes > 5:**
   A prime number greater than 5 can only end in 1, 3, 7, or 9.

2. **Test each digit:**
   * **Ends in 1:** If `p = ...1`, then `2p+1 = ...3` (Possible, e.g., p=11 → 23).
   * **Ends in 3:** If `p = ...3`, then `2p+1 = ...7` (Possible, e.g., p=23 → 47).
   * **Ends in 7:** If `p = ...7`, then `2p+1 = ...5` (Impossible; divisible by 5).
   * **Ends in 9:** If `p = ...9`, then `2p+1 = ...9` (Possible, e.g., p=29 → 59).

3. **Calculate Product:**
   The possible unit digits are 1, 3, and 9.
   > Product = `1 * 3 * 9 = 27`.

**Answer:** 27