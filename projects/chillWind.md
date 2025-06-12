---
layout: project
type: project
image: img/WindChillChart.jpg
title: "Wind Chill"
date: 2025
published: true
labels:
  - Typescript
  - GitHub
summary: "A Relatively simple project about thresholds of Hypothermia made during ICS 314 quiz."
---

<img src="/img/WindChillChart.jpg" alt="Wind Chill Chart" width="300" height="200">

## About

This is a typescript project involving the Wind Chill formula with variables ivolving temperature in Fahrenheit [T] and Wind Speed [V] in miles per hour.

Wind Chill is feels like of how cold it actually is on the skin whenever the wind is blowing on said skin.

We use this formula Wind_Chill (in Fahrenheit) = 35.74 + 0.6215 * T - (35.75 * V)^0.16 + 0.4275 * T * V^16 to find the temperature it feels like on the skin.

Finally we use thresholds indicated in the image above to determine danger level of Hypothermia.

## Code

This function uses the formula listed above requiring two parameters
The two parameter are tempF (Fahrenheit) and windSpeed (Miles/Hour)
This formula is only active when tempF is less than 50 and windSpeed is greater that 3 miles an hour

```typescript
function windChill(tempF: number, windSpeed: number): string {
  let windChill: number;
  if (tempF <= 50 && windSpeed > 3) {
    windChill = 35.74 +
      0.6215 * tempF -
      35.75 * Math.pow(windSpeed, 0.16) +
      0.4275 * tempF * Math.pow(windSpeed, 0.16);
    windChill = Math.round(windChill * 10) / 10
  } else {
    windChill = tempF;
  }
```

The rest of the code is simply a blanket of if statements that give out various messages.
Dependent on the value of windChill, from least to most severe

```typescript
let level: string;
let effects: string;

  if (windChill > 32) {
    level = "no risk";
    effects = "minumum danger of frostbite.";
  } else if (windChill > 16) {
    level = "caution";
    effects = "Increased risk of hypothermia over prolonged exposure.";
  } else if (windChill > 0) {
    level = "moderate";
    effects = "Frostbite possible on exposed skin within 30–45 minutes.";
  } else if (windChill > -20) {
    level = "High";
    effects = "Frostbite possible within 10–30 minutes.";
  } else if (windChill > -40) {
    level = "Very High";
    effects = "Frostbite likely within 5–10 minutes.";
  } else {
    level = "Extreme Danger";
    effects = "Frostbite possible in less than 5 minutes. Exposed skin freezes rapidly.";
  }

  return `Wind Chill: ${windChill}°F – ${level} – ${effects}`;

}
```

Here are some test cases used with expected results

```typescript
console.log(windChill(40, 10));  // Wind Chill: 33.6°F - No Risk - Minimal danger of frostbite.
console.log(windChill(30, 25));  // Wind Chill: 16.0°F - Caution - Increased risk of hypothermia over prolonged exposure.
console.log(windChill(20, 35)); // Wind Chill: 0.1°F - Moderate - Frostbite possible on exposed skin within 30-45 minutes.
console.log(windChill(5, 30));  // Wind Chill: -19.1°F - High - Frostbite possible within 10-30 minutes.
console.log(windChill(-10, 30));  // Wind Chill: -39.4°F - Very High - Frostbite likely within 5-10 minutes.
console.log(windChill(-15, 35));  // Wind Chill: -48.1°F - Extreme Danger - Frostbite possible in less than 5 minutes. Exposed skin freezes rapidly..
```



[Run This Code on TypeScript](https://tinyurl.com/3cxr7z9)
