# Function: getOvulationStatus

## Description

### `getOvulationStatus`

This function calculates the ovulation status based on the menstrual cycle's length and the current day of the cycle.

### Parameters

- `cycleLength` (number): The length of the menstrual cycle, typically measured in days.
- `dayOfCycle` (number): The current day of the menstrual cycle.

### Return Value

A string representing the ovulation status.

### Ovulation Status Messages

The function returns one of the following messages based on the calculated difference between the ovulation day and the current day of the cycle:

- "Finished": When the difference between the ovulation day and the current day is less than -2 days.
- "Possible": When the difference is less than 0 days.
- "Today": When the difference is 0 days.
- "Tomorrow": When the difference is 1 day.
- "In X Days": When the difference is greater than 1, it provides the number of days until ovulation.

## Code Implementation

```javascript
/**
 * Calculate ovulation status based on cycle length and day of the cycle.
 * @param {number} cycleLength - The length of the menstrual cycle.
 * @param {number} dayOfCycle - The current day of the menstrual cycle.
 * @returns {string} - Ovulation status message.
 */
function getOvulationStatus(cycleLength, dayOfCycle) {
  if (!cycleLength || !dayOfCycle) {
    return "";
  }

  // Define the length of the luteal phase (constant value).
  const lutealPhaseLength = 14;

  // Calculate the day of ovulation.
  const ovulationDay = cycleLength - lutealPhaseLength;

  // Calculate the difference between ovulation day and current day.
  const diffDay = ovulationDay - dayOfCycle;

  if (diffDay < -2) {
    return "Finished";
  }
  if (diffDay < 0) {
    return "Possible";
  }
  if (diffDay === 0) {
    return "Today";
  }
  if (diffDay === 1) {
    return "Tomorrow";
  }

  return `In ${diffDay} Days`;
}
```

### Example Test

To demonstrate the usage of the getOvulationStatus function, we provide an example test:

```javascript
const cycleLength = 28;
const dayOfCycle = 15;
const result = getOvulationStatus(cycleLength, dayOfCycle);
```

### Result Examples

- If cycleLength is 28 and dayOfCycle is 15, the result will be "Possible".
- If cycleLength is 28 and dayOfCycle is 28, the result will be "In 14 Days".
- If cycleLength is 28 and dayOfCycle is 31, the result will be "Finished".
