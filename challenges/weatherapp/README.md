# Develop a Weather App

## 1. Problem Description

Build a **Weather Application** that fetches real-time weather data and displays current conditions and forecasts for any location. The system should provide an intuitive interface for users to search locations, view detailed weather information, and see multi-day forecasts.

### Core Requirements:
- **Frontend**: User interface for location search and weather display
- **Backend**: RESTful API (.NET Core, Python Flask, or Node.js Express) for weather data aggregation
- **External API Integration**: Connect to weather data provider (OpenWeatherMap, WeatherAPI, or similar)
- **Data Caching**: Cache weather data to reduce API calls and improve performance
- **Responsive Design**: Mobile-friendly interface with weather icons and visual indicators

### User Stories:
1. As a user, I can search for weather by city name or zip code
2. As a user, I can view current weather conditions (temperature, humidity, wind speed)
3. As a user, I can see a 5-day weather forecast
4. As a user, I can view weather details with appropriate icons and visual indicators
5. As a user, I can save favorite locations for quick access
6. As a user, I can toggle between Celsius and Fahrenheit temperature units

## 2. Hints

### Technical Implementation Hints:
- **Weather API Options**: 
  - [OpenWeatherMap](https://openweathermap.org/api) (Free tier: 1000 calls/day)
  - [WeatherAPI.com](https://www.weatherapi.com/) (Free tier: 1M calls/month)
  - [OpenMeteo](https://open-meteo.com/) (Free, no API key required)
- **Data Structure**: Weather object with temperature, description, humidity, wind, pressure, icon
- **Caching Strategy**: Cache weather data for 10-15 minutes per location
- **Error Handling**: Handle network errors, invalid locations, API limits gracefully
- **Icons**: Use weather icon libraries or emoji for weather conditions

### Quick Start Tips:
- Start with a simple location search and current weather display
- Use environment variables for API keys (never commit them!)
- Implement caching early to avoid hitting API rate limits during testing
- Focus on one weather API provider to keep it simple
- Use mock data initially to build UI without API calls
- Display "feels like" temperature for better user experience

### API Integration Example:
```javascript
// Example: OpenWeatherMap API call
const API_KEY = process.env.WEATHER_API_KEY;
const city = "London";
const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${API_KEY}&units=metric`;
```

### Agent Mode Note:
If you are using the Agent mode and notice that the agent is working in the wrong directory, try to add the following line to your prompt:
```markdown
Work in the directory backend. When run terminal remember to change the right directory, for example: `cd challenges/weatherapp/backend && <command>`.
```
Change the directory to `frontend` when working on the frontend part.

## 3. Time Needed

**Estimated Duration: 45-60 minutes**

### Time Breakdown:
- **Setup** (10-15 minutes): Project structure, API key setup, dependencies
- **API Integration** (10-15 minutes): Connect to weather API, fetch data, error handling
- **Backend Endpoints** (10-15 minutes): Create search endpoint, implement caching
- **Frontend UI** (15-20 minutes): Search form, weather display, forecast cards
- **Testing & Polish** (5-10 minutes): Test different locations, add icons, improve styling

## 4. Extra Features (Bonus Challenges)

Quick additions for teams that finish early:

### Easy Additions (5-10 minutes each):
- **Geolocation**: Auto-detect user's location using browser geolocation API
- **Recent Searches**: Show list of recently searched locations
- **Loading States**: Add loading spinners while fetching data
- **Weather Alerts**: Display severe weather warnings if available

### Medium Additions (10-15 minutes each):
- **Hourly Forecast**: Show hour-by-hour forecast for the next 24 hours
- **Weather Maps**: Integrate weather maps (radar, satellite, temperature)
- **Historical Data**: Show historical average temperatures for comparison
- **Air Quality Index**: Display air quality information
- **UV Index**: Show UV index with safety recommendations

### Advanced Additions (15-25 minutes each):
- **Multiple Locations Dashboard**: Compare weather across multiple cities
- **Weather Notifications**: Browser notifications for weather changes
- **Data Visualization**: Charts showing temperature trends over time
- **PWA Features**: Make the app installable as Progressive Web App
- **Dark Mode**: Theme toggle based on day/night at location

### Why Perfect for 1-Hour Challenge:
- **Real-World API Integration**: Practice working with external APIs
- **Asynchronous Operations**: Learn to handle async/await and promises
- **Caching Strategy**: Understand performance optimization
- **Error Handling**: Deal with network errors and edge cases
- **User Experience**: Focus on responsive design and loading states
- **Practical Utility**: Build something people actually use daily

### Success Criteria:
- ✅ Can search for weather by location
- ✅ Displays current weather conditions accurately
- ✅ Shows multi-day forecast
- ✅ Handles errors gracefully (invalid location, network issues)
- ✅ Weather data is cached to reduce API calls
- ✅ UI is responsive and shows weather icons
- ✅ Temperature unit toggle works (C°/F°)

### Testing Checklist:
- ✅ Test with various city names
- ✅ Test with invalid location names
- ✅ Test with network disconnected
- ✅ Verify caching is working (check network calls)
- ✅ Test on mobile viewport
- ✅ Verify all weather icons display correctly

This challenge combines external API integration, caching strategies, and responsive UI design - perfect for learning how to build data-driven applications that interact with third-party services!

## 5. Additional Resources

### Weather API Documentation:
- [OpenWeatherMap API Docs](https://openweathermap.org/api)
- [WeatherAPI.com Docs](https://www.weatherapi.com/docs/)
- [OpenMeteo API Docs](https://open-meteo.com/en/docs)

### Weather Icons:
- [Weather Icons Font](https://erikflowers.github.io/weather-icons/)
- [OpenWeatherMap Icons](https://openweathermap.org/weather-conditions)
- Or use emoji: ☀️ ⛅ ☁️ 🌧️ ⛈️ 🌨️ 🌩️

### Best Practices:
- Never commit API keys - use environment variables
- Implement rate limiting to avoid exceeding API quotas
- Cache aggressively but set appropriate TTL (10-15 minutes)
- Show user-friendly error messages
- Display timestamp of last data update
