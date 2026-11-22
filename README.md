# Phone Navigation App

[![Live Demo](https://img.shields.io/badge/Live_Demo-2563eb?style=for-the-badge&logo=vercel&logoColor=white)](https://phonenav.vercel.app)
[![JavaScript](https://img.shields.io/badge/JavaScript-71%25-f7df1e?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/docs/Web/JavaScript)
[![HTML](https://img.shields.io/badge/HTML-29%25-e34f26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/HTML)

A mobile navigation app built with HTML, CSS, and JavaScript. Search for a destination, follow a live route, and get spoken turn-by-turn directions in your browser.

**[Open the live app](https://phonenav.vercel.app)**

## Features

- Live GPS tracking
- Destination search with nearby suggestions
- OpenStreetMap-based interactive map
- Driving routes powered by OSRM
- Turn-by-turn text and voice instructions
- Distance, travel time, and speed information
- Automatic recalculation after leaving the route
- Destination pinning and map recenter controls
- Mobile-friendly full-screen interface
- Screen wake lock support while navigating

## Using the App

1. Open the app and allow location access.
2. Search for an address or place.
3. Select a result or tap the map to choose a destination.
4. Follow the route shown in the navigation panel.
5. Select **Recenter** to return to your live location or **End** to stop navigation.

## Built With

- HTML5
- CSS
- JavaScript
- [Leaflet](https://leafletjs.com/) for the map
- [OpenStreetMap](https://www.openstreetmap.org/) for map tiles
- [Photon](https://photon.komoot.io/) for location search
- [OSRM](https://project-osrm.org/) for route calculation
- Browser Geolocation, Speech Synthesis, and Wake Lock APIs

## Running Locally

Run the app through a local web server rather than opening the HTML file directly.

```bash
git clone https://github.com/htmlfan123/Phone-Navigation-App.git
cd Phone-Navigation-App
python -m http.server 8000
```

Visit <http://localhost:8000/phonenavfinal.html>.

Geolocation and wake lock features are best used over `localhost` or HTTPS. Browser support and permission settings vary by device.

## Project Structure

```text
Phone-Navigation-App/
├── phonenavfinal.html
├── js/
│   └── app.js
└── README.md
```

- `phonenavfinal.html` contains the page structure and interface styles.
- `js/app.js` contains the search, GPS, routing, and navigation logic.

## Browser Notes

- Location access is required for navigation.
- Voice instructions depend on the voices and speech support available in the browser and operating system.
- Screen wake lock support varies between browsers.
- Search, map, and routing features require an internet connection.

## Contributing

Issues and pull requests are welcome. Possible improvements include bug fixes, accessibility improvements, interface updates, and better GPS or route handling.
