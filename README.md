# ConnectRide - Unified Ride-Sharing, Matchmaking, and Profile Marketing App

## Overview
ConnectRide is a self-hosted, open-source application that combines:
- **Profile Marketing**: HumHub-inspired social networking
- **Matchmaking**: pH7Builder-style dating with interest-based matching
- **Ride-Sharing**: Real-time booking and tracking with Socket.io
- **Frontend**: React with Material-UI and **OpenStreetMap (Leaflet.js)**

## Quick Start

### Prerequisites
- Docker & Docker Compose
- Node.js 18+
- PHP 8.3+
- MySQL/MariaDB

### Setup
1. Clone and navigate: `git clone <your-repo> && cd connectride`
2. Start services: `docker-compose up -d`
3. Install dependencies:
    ```bash
    cd backend && composer install
    cd ../frontend && npm install
    cd ../realtime-server && npm install
    ```
4. Access:
    - Frontend: http://localhost:3000
    - Backend API: http://localhost:8000
    - Realtime: http://localhost:4000 (Socket.io)

### Features
- Create user profiles with interests and vehicle info
- Find matches based on shared interests
- Book rides with pickup/dropoff locations using free, open-source mapping.
- Real-time ride tracking with live location updates
- JWT authentication for secure API access

### Testing
```bash
# Create profile
curl -X POST "http://localhost:8000/index.php?action=profile" \
-H "Content-Type: application/json" \
-d '{"name":"Alice","email":"alice@test.com","interests":"hiking","vehicle":"car","password":"password123"}'

# Find matches
curl -X POST "http://localhost:8000/index.php?action=matches" \
-H "Authorization: Bearer YOUR_JWT_TOKEN" \
-H "Content-Type: application/json" \
-d '{"interests":"hiking"}'