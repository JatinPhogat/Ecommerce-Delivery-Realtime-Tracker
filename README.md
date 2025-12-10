# E-commerce Delivery Real-Time Tracker

A real-time delivery tracking application built with the MERN stack, Socket.io, Tailwind CSS, and Leaflet. This project tracks delivery personnel locations in real-time, displays them on an interactive map, and calculates distance and ETA for deliveries.

---

## Features

* Live location tracking of all connected users in real-time
* User permission prompt before accessing geolocation
* Distance between users in kilometers
* ETA (Estimated Travel Time) between users
* UI with Tailwind CSS
* Socket.io powered real-time communication

---

## Tech Stack

* **Frontend**: React, Tailwind CSS, React-Leaflet, Socket.io-client
* **Backend**: Node.js, Express, Socket.io
* **Database**: MongoDB (optional for user sessions)
* **APIs**: Google Distance Matrix API or OpenRouteService (for distance & ETA)

---

## Prerequisites

* Node.js >= 14
* MongoDB URI (local or Atlas)
* Distance Matrix API Key (Google or OpenRouteService)

---

## 🔧 Installation & Setup

### 1. Install Backend Dependencies

```bash
cd server
npm install
```

### 2. Install Frontend Dependencies

```bash
cd client
npm install
```

### 3. Environment Variables

Create a `.env` file in the server directory:

```env
PORT=4000
MONGO_URI=your_mongodb_uri
ORS_API_KEY=your_openrouteservice_api_key
```

### 4. Run the Development Servers

**Terminal 1 - Start Backend Server:**

```bash
cd server
npm start
```

Server will run on: `http://localhost:4000`

**Terminal 2 - Start Frontend:**

```bash
cd client
npm start
```

Client will run on: `http://localhost:3000`

### 5. Access the Application

Open your browser and visit: **`http://localhost:3000`**

The frontend connects to the backend at `http://localhost:4000`

---

## 🛠️ Project Structure

```
ecommerce-delivery-tracker/
├── client/                  # React Frontend
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/      # Map, Sidebar, UserCard
│   │   ├── socket.js        # Socket.io client setup
│   │   ├── App.jsx
│   │   ├── index.js
│   │   └── styles.css
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── package.json
│   └── README.md
├── server/                 # Express Backend
│   ├── controllers/
│   │   └── locationController.js
│   ├── models/
│   │   └── User.js
│   ├── routes/
│   │   └── locationRoutes.js
│   ├── socketHandlers.js
│   ├── server.js
│   ├── package.json
│   └── README.md
├── .env
└── README.md
```

---

## 🔁 Socket Event Flow

### Client

* Connects via Socket.io
* Requests user location via `navigator.geolocation`
* Emits `location-update` with `{ lat, lng }`
* Receives updates from server about all users with `distance`, `eta`

### Server

* Listens for `location-update`
* Stores/updates user coordinates
* Calculates distance & ETA using external API
* Broadcasts updated location + distance to all connected clients

---

##  APIs Used

### Google Distance Matrix API

* Endpoint: `https://maps.googleapis.com/maps/api/distancematrix/json`
* Input: origin & destination lat/lng
* Output: distance in km, duration in minutes

*Alternative*: OpenRouteService API (Free tier)

---

##  UI/UX Guidelines

* Use `react-leaflet` for map rendering
* On permission deny, show a modal/toast explaining the need for location
* On map: user’s marker + popup with name, distance & ETA
* Sidebar showing all active users and their distances
* Mobile responsive: collapsible sidebar, map full screen on small viewports

---

##  Testing

* Run locally with 2 browser tabs or devices
* One user accepts location, other denies (check both flows)
* Validate socket connections, distance calculations, and map markers
