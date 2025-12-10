# 🚚 E-commerce Delivery Real-Time Tracker

A modern, full-stack real-time delivery tracking application that enables live location monitoring on an interactive map. Built with the MERN stack, this application provides seamless tracking of delivery personnel with distance and ETA calculations.

![Tech Stack](https://img.shields.io/badge/Stack-MERN-green)
![Socket.io](https://img.shields.io/badge/Real--time-Socket.io-blue)
![License](https://img.shields.io/badge/License-Open%20Source-brightgreen)

---

## Features

- **Real-Time Location Tracking** - Track multiple users simultaneously with instant updates
- **Interactive Map Interface** - Powered by Leaflet with satellite imagery
- **Distance & ETA Calculation** - Automatic calculation between delivery points
- **Room-Based System** - Create and join delivery tracking rooms
- **Responsive Design** - Works seamlessly on desktop and mobile devices
- **Live Route Visualization** - See the actual route between locations
- **User-Friendly UI** - Clean interface with Tailwind CSS

---

## Tech Stack

### Frontend
- **React** - UI library for building interactive interfaces
- **Tailwind CSS** - Utility-first CSS framework
- **React-Leaflet** - Map rendering and interaction
- **Socket.io Client** - Real-time bidirectional communication
- **Axios** - HTTP client for API requests
- **Lottie React** - Animation library

### Backend
- **Node.js** - JavaScript runtime environment
- **Express.js** - Web application framework
- **Socket.io** - Real-time event-driven communication
- **Mongoose** - MongoDB object modeling (optional)
- **Axios** - External API integration

### External Services
- **OpenRouteService API** - Distance, duration, and route calculations
- **ArcGIS** - Satellite map tile provider

---

## Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (v14 or higher)
- **npm** or **yarn**
- **Git** (for cloning the repository)

Optional:
- **MongoDB** (if using database features)
- **OpenRouteService API Key** (for distance calculations)

---

## Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/JatinPhogat/Ecommerce-Delivery-Realtime-Tracker.git
cd Ecommerce-Delivery-Realtime-Tracker
```

### 2. Install Backend Dependencies

```bash
cd server
npm install
```

### 3. Install Frontend Dependencies

```bash
cd ../client
npm install
```

### 4. Environment Configuration (Optional)

Create a `.env` file in the `server` directory for optional features:

```env
PORT=4000
MONGO_URI=your_mongodb_connection_string
ORS_API_KEY=your_openrouteservice_api_key
```

> **Note:** The application works without these configurations, but distance/ETA features require an API key.

### 5. Start the Application

**Terminal 1 - Backend Server:**

```bash
cd server
npm start
```
The server will start on `http://localhost:4000`

**Terminal 2 - Frontend Client:**

```bash
cd client
npm start
```
The client will start on `http://localhost:3000`

### 6. Access the Application

Open your browser and navigate to:
```
http://localhost:3000
```

---

## Project Structure

```
Ecommerce-Delivery-Realtime-Tracker/
│
├── client/                          # Frontend React Application
│   ├── public/
│   │   ├── index.html              # HTML template
│   │   └── mypin.png               # Custom map marker
│   ├── src/
│   │   ├── components/
│   │   │   ├── Map.jsx             # Map component with markers
│   │   │   ├── Sidebar.jsx         # User list sidebar
│   │   │   └── UserCard.jsx        # Individual user card
│   │   ├── image/
│   │   │   └── delivery.json       # Lottie animation
│   │   ├── App.jsx                 # Main application component
│   │   ├── index.js                # Entry point
│   │   ├── socket.js               # Socket.io configuration
│   │   └── styles.css              # Global styles
│   ├── package.json
│   ├── tailwind.config.js
│   └── postcss.config.js
│
├── server/                          # Backend Node.js Application
│   ├── controllers/
│   │   └── locationController.js   # Location & route logic
│   ├── models/
│   │   └── User.js                 # User schema (MongoDB)
│   ├── routes/
│   │   └── locationRoutes.js       # API routes
│   ├── server.js                   # Express server setup
│   ├── socketHandlers.js           # Socket.io event handlers
│   └── package.json
│
└── README.md
```

---

## How It Works

### Socket.io Event Flow

**Client Side:**
1. Connects to the server via Socket.io
2. Requests user's geolocation permission
3. Joins a specific room using room ID
4. Emits location updates periodically
5. Listens for location updates from other users

**Server Side:**
1. Accepts Socket.io connections
2. Manages room-based user groups
3. Receives location data from clients
4. Calculates distances and ETAs between users
5. Broadcasts updated user locations to all room members

### Key Features Explained

- **Room System:** Users can create or join rooms by entering a room name/ID
- **Live Updates:** Location data is transmitted in real-time using WebSocket technology
- **Distance Calculation:** OpenRouteService API calculates driving distance and time
- **Route Display:** Visual route lines are drawn on the map between selected users

---

## Usage

1. **Create/Join a Room**
   - Enter a room name on the home page
   - Share the room URL with other users

2. **Grant Location Permission**
   - Allow browser location access when prompted
   - Your location will appear on the map

3. **Track Deliveries**
   - View all connected users in the sidebar
   - Click on a user to see the route and distance
   - Monitor real-time position updates

4. **Share Room**
   - Copy the room URL from the top bar
   - Send to team members for collaborative tracking

---

## Testing

### Local Testing
1. Open two browser tabs or use different browsers
2. Navigate to `http://localhost:3000` in both
3. Create/join the same room
4. Grant location permissions
5. Verify both users appear on the map

### Multi-Device Testing
1. Ensure all devices are on the same network
2. Replace `localhost` with your computer's IP address
3. Access from mobile devices
4. Test location tracking across devices

---

## Future Enhancements

- [ ] User authentication and profiles
- [ ] Delivery history and analytics
- [ ] Push notifications for delivery updates
- [ ] Multi-language support
- [ ] Offline mode capabilities
- [ ] Admin dashboard for fleet management


---

**⭐ If you find this project helpful, please consider giving it a star!**
