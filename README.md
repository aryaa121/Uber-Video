🚗 Uber Backend API Documentation
This backend provides authentication, user management, captain management, maps services, and ride operations.

👤 User APIs
🔹 POST /users/register
Description
Registers a new user.

Request Body
{
  "fullname": {
    "firstname": "Arya",
    "lastname": "Stark"
  },
  "email": "arya@test.com",
  "password": "123456"
}
Response
{
  "token": "JWT_TOKEN",
  "user": { ... }
}
🔹 POST /users/login
Description
Authenticates a user and returns a JWT token.

Request Body
{
  "email": "arya@test.com",
  "password": "123456"
}
Response
{
  "token": "JWT_TOKEN",
  "user": { ... }
}
🔹 GET /users/profile
Description
Returns logged-in user profile.

Authentication
Bearer Token required.

🔹 GET /users/logout
Description
Logs out user and clears token.

🚖 Captain APIs
🔹 POST /captains/register
Request Body
{
  "fullname": {
    "firstname": "John",
    "lastname": "Driver"
  },
  "email": "driver@test.com",
  "password": "123456",
  "vehicle": {
    "color": "Black",
    "plate": "UP32AB1234",
    "capacity": 4,
    "vehicleType": "car"
  }
}
🔹 POST /captains/login
Login captain and receive JWT.

🔹 GET /captains/profile
Returns captain profile (JWT required).

🔹 GET /captains/logout
Logs out captain.

🗺 Maps APIs
🔹 GET /maps/get-coordinates
/maps/get-coordinates?address=Location
Returns latitude & longitude.

🔹 GET /maps/get-distance-time
/maps/get-distance-time?origin=A&destination=B
Returns travel distance & duration.

🔹 GET /maps/get-suggestions
/maps/get-suggestions?input=Address
Returns autocomplete suggestions.

🚕 Ride APIs
🔹 POST /rides/create
Creates a ride.

Body
{
  "pickup": "Location A",
  "destination": "Location B",
  "vehicleType": "car"
}
🔹 GET /rides/get-fare
/rides/get-fare?pickup=A&destination=B
Returns fare estimate.

🔐 Authentication
Protected routes require:

Authorization: Bearer <JWT_TOKEN>
⚙️ Tech Stack
Node.js
Express.js
MongoDB
JWT Authentication
Google Maps API
✅ Features
✔ User & Captain authentication ✔ Ride creation & fare estimation ✔ Map location services ✔ JWT security ✔ MongoDB persistence

🚀 Backend Ready
This backend supports a ride-booking workflow similar to Uber with modular architecture and secure authenticati
