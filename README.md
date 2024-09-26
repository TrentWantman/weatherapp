# Weather App Documentation

## Overview

The **Weather App** is a JavaScript-based web application that uses the **OpenWeatherMap API** to fetch and display weather data for any city. It shows the current weather conditions, an hourly forecast, and a 7-day forecast. The app also includes geolocation functionality to show weather based on the user's current location.

![Weather App Demo](src/assets/weatherapp-example.gif)


---
## Detailed Explanation of Files and Functions

### 1. `index.js`

This file handles all the core logic of the application, including fetching data from the OpenWeatherMap API and displaying it on the screen.

#### Functions:

- **`gps()`**  
  - **Purpose**: Uses the browser's Geolocation API to retrieve the user's current latitude and longitude.  
  - **Details**: This function checks if geolocation is available in the browser. If it is, it retrieves the coordinates and calls `fetchForecastData(lat, lon)` to get weather data based on the location.

- **`makeRequest(city)`**  
  - **Purpose**: Fetches weather data for a specific city.  
  - **Details**: This function takes the city name as a parameter, constructs a request URL using the OpenWeatherMap API, and calls `fetchData()` to retrieve weather data.

- **`fetchData(city)`**  
  - **Purpose**: Retrieves current weather data for the provided city.  
  - **Details**: It uses the OpenWeatherMap API’s `weather` endpoint to get real-time weather information like temperature, weather conditions, and location data. The fetched data is then passed to `displayWeather()`.

- **`fetchForecastData(lat, lon)`**  
  - **Purpose**: Fetches the 7-day weather forecast based on latitude and longitude.  
  - **Details**: This function uses the OpenWeatherMap API’s `forecast` endpoint to retrieve the weather forecast for the next 7 days. It takes the latitude and longitude as parameters and fetches the data.

- **`displayWeather(cityData, forecastData)`**  
  - **Purpose**: Updates the DOM with the weather information.  
  - **Details**: This function processes the fetched weather data and populates the webpage with the current weather, hourly forecast, and 7-day forecast. It uses the JSON response to extract relevant weather details such as temperature, humidity, wind speed, and weather icons.

- **`formatDateTime()`**  
  - **Purpose**: Formats the time and date for display on the webpage.  
  - **Details**: Converts Unix timestamps to human-readable dates and times, which are used in displaying forecast times and dates in the app.

---

### 2. `key.js`

This file stores the OpenWeatherMap API key, which is used for making API requests.

#### Variables:

- **`API_KEY`**  
  - **Purpose**: Holds the OpenWeatherMap API key.  
  - **Details**: Replace `'your_api_key'` with the actual API key from OpenWeatherMap to enable API requests.

---

### 3. `style.css`
This file defines the styling of the application using Tailwind CSS. Tailwind is a utility-first CSS framework that makes it easy to design responsive and modern web applications.

#### Key Classes:
- **`container`**: Defines the main layout container for the app.
- **`text-center`**: Centers the text inside weather elements like city name, temperature, and weather conditions.
- **`grid`**: Used for creating the grid layout for displaying the hourly and 7-day forecast.
- **`bg-gray-200`**: Adds a light gray background to various elements.
- **Responsive classes**: Includes Tailwind’s responsive design utilities like `sm:text-sm`, `md:text-lg` to ensure proper display on different screen sizes.

---

### 4. `webpack.config.js`
This file configures Webpack, a tool that bundles JavaScript and CSS files for the application.

#### Key Sections:
- **entry**  
  - **Purpose**: Defines the entry point of the application.  
  - **Details**: The `src/index.js` file is specified as the entry point, meaning Webpack will begin bundling from this file.

- **output**  
  - **Purpose**: Defines where the bundled files will be saved.  
  - **Details**: The bundled files will be outputted to the `dist/` folder as `bundle.js`.

- **module**  
  - **Purpose**: Specifies rules for processing different file types.  
  - **Details**: Uses the `css-loader` and `postcss-loader` to process CSS files, including Tailwind CSS.

---

### 5. `postcss.config.js`
This file configures PostCSS, a tool that transforms CSS files with JavaScript plugins. It processes the CSS to ensure browser compatibility and includes Tailwind CSS.

#### Plugins:
- **`tailwindcss`**: Enables Tailwind CSS utility classes in the project.
- **`autoprefixer`**: Automatically adds browser-specific prefixes to CSS properties, ensuring compatibility across different browsers.

---

### 6. `tailwind.config.js`
This file customizes the Tailwind CSS framework for the project. It defines which parts of the project should be scanned for class names and customizes the theme used in the app.

#### Key Sections:
- **content**  
  - **Purpose**: Defines the files where Tailwind should look for class names.  
  - **Details**: The `src/` directory is scanned by Tailwind, ensuring that only the necessary CSS classes are included in the final build.

- **theme**  
  - **Purpose**: Extends the default Tailwind theme.  
  - **Details**: Allows for customization of colors, spacing, and other design elements.

---

### 7. `.eslintrc.json`
This file configures ESLint, a static analysis tool that helps enforce coding standards and identifies potential errors in the JavaScript code.

#### Key Rules:
- **`quotes`**: Enforces single quotes for strings in JavaScript.
- **`no-unused-vars`**: Prevents unused variables in the code.
- **`no-console`**: Allows `console.log` for debugging purposes during development but can be disabled for production.

---

### 8. `package.json`
This file contains metadata about the project and manages its dependencies and scripts.

#### Key Sections:
- **dependencies**: Lists the external libraries and packages the project depends on:
  - **Tailwind CSS**: Utility-first CSS framework.
  - **Webpack**: Module bundler for JavaScript and CSS.
  - **ESLint**: Linting tool to ensure code quality.

- **scripts**: Defines commands for building and running the project:
  - **`build`**: Runs Webpack to bundle the project.
  - **`watch`**: Watches for changes in files and automatically rebuilds the project when changes are detected.
 
---

## Features
- **Geolocation Support**: Automatically fetches and displays weather data based on the user’s current location.
- **City Search**: Allows users to search for and display weather information for any city in the world.
- **7-Day Forecast**: Displays a detailed 7-day weather forecast for the selected city or location.
- **Responsive Design**: The app uses Tailwind CSS to provide a mobile-friendly, responsive design.

---

## How to Use

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>

2. **Install Dependencies**: Navigate to the project directory and run:
   ```bash
   npm install

3. **Add OpenWeatherMap API Key**: In the file `key.js`, replace `'your_api_key'` with your actual API key from OpenWeatherMap.

4. **Build and Serve the Application**: Build the project using Webpack:
   ```bash
   npm run build
   npm run watch

5. **Open the App**: Open the index.html file in your browser to view the weather app.
