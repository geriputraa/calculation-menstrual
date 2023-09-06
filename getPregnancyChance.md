# Function: getPregnancyChance

## Description

This function calculates the chance of pregnancy based on the menstrual cycle length and the current day of the menstrual cycle.

## Parameters

- `cycleLength` (number): Length of the menstrual cycle in days.
- `dayOfCycle` (number): Current day of the menstrual cycle.

## Returns

A string representing the pregnancy chance, either "high" or "low."

## Algorithm

1. Check if `cycleLength` or `dayOfCycle` is falsy (e.g., 0 or undefined). If either is falsy, return an empty string ("").
2. Calculate the length of the luteal phase, which is assumed to be 14 days.
3. Calculate the day of ovulation by subtracting the luteal phase length from the menstrual cycle length.
4. Calculate the difference in days between the day of ovulation and the current day of the cycle (`diffDay`).
5. If `diffDay` is between -2 and 4 (inclusive), return "high" (indicating a higher chance of pregnancy). Otherwise, return "low" (indicating a lower chance of pregnancy).

## Code

```javascript
/**
 * Calculate the chance of pregnancy based on cycle length and day of the cycle.
 * @param {number} cycleLength - Length of the menstrual cycle in days.
 * @param {number} dayOfCycle - Current day of the menstrual cycle.
 * @returns {string} - The pregnancy chance, either "high" or " low".
 */
export function getPregnancyChance(cycleLength, dayOfCycle) {
  if (!cycleLength || !dayOfCycle) {
    return "";
  }

  const lutealPhaseLength = 14;
  const ovulationDay = cycleLength - lutealPhaseLength;
  const diffDay = ovulationDay - dayOfCycle;

  if (diffDay >= -2 && diffDay <= 4) {
    return "high";
  }
  return "low";
}

/**
 * Example test case 1:
 * - cycleLength: 28
 * - dayOfCycle: 14
 * Expected result: "high"
 */
// console.log(getPregnancyChance(28, 14)); // Output: "high"

/**
 * Example test case 2:
 * - cycleLength: 30
 * - dayOfCycle: 24
 * Expected result: "low"
 */
// console.log(getPregnancyChance(30, 24)); // Output: "low"
```
