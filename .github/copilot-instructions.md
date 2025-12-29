# Weather App Development Guidelines

## Architecture Overview

This is a client-side weather application built with vanilla JavaScript, HTML, and CSS. The app fetches weather data from a public API (e.g., OpenWeatherMap) and displays current conditions and forecasts in a responsive interface.

Key components:
- `inde.html`: Main HTML structure (note: likely intended as `index.html`)
- `script.js`: JavaScript for API interactions, data processing, and DOM manipulation
- `style.css`: CSS for responsive design, theming, and animations

Data flow: User inputs location → API fetch → Parse JSON response → Update DOM elements → Apply CSS styling

## Development Workflow

- Edit files directly in VS Code
- Open `inde.html` in a web browser to test functionality
- Use browser developer tools for debugging JavaScript and inspecting DOM changes
- No build process required - pure client-side application

## API Integration Pattern

Use the OpenWeatherMap API for weather data. Standard pattern:

```javascript
const apiKey = 'your_api_key_here';
const city = 'London';

fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`)
  .then(response => response.json())
  .then(data => {
    // Extract relevant data: data.main.temp, data.weather[0].description, etc.
    updateWeatherDisplay(data);
  })
  .catch(error => console.error('Error fetching weather:', error));
```

Handle API responses consistently: check response.ok, parse JSON, update UI, handle errors.

## Coding Conventions

- Use modern ES6+ features: arrow functions, template literals, async/await
- Structure JavaScript with event listeners for user interactions (e.g., search button clicks)
- Use semantic HTML: `<main>`, `<section>`, `<article>` for weather display areas
- Implement responsive design with CSS Flexbox/Grid
- Add loading states and error messages for better UX

## File Organization

Keep all assets in the root directory. No subfolders needed for this simple app structure.

## Common Patterns

- Store API key securely (consider environment variables for production)
- Use metric units by default (`units=metric` in API calls)
- Display weather icons based on `data.weather[0].icon` codes
- Implement geolocation API for automatic location detection: `navigator.geolocation.getCurrentPosition()`