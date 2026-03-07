🚗 RideSync Backend API Documentation

This backend powers RideSync, a real-time ride-sharing platform.
It provides user authentication, driver (captain) management, map services, and ride operations.

The system allows users to book rides, drivers to accept rides, and both to track ride information securely using JWT authentication.

👤 User APIs
🔹 POST /users/register
Description

Registers a new user in the RideSync platform.

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

Authenticates a user and returns a JWT authentication token.

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

Returns the profile details of the logged-in user.

Authentication

Bearer Token required.

Example:

Authorization: Bearer JWT_TOKEN
🔹 GET /users/logout
Description

Logs out the user and clears the authentication token.

🚖 Captain (Driver) APIs

In RideSync, drivers are called Captains.

🔹 POST /captains/register
Description

Registers a new captain (driver) along with vehicle information.

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
Description

Authenticates a captain and returns a JWT token.

🔹 GET /captains/profile
Description

Returns the profile information of the logged-in captain.

Authentication

JWT Token required.

🔹 GET /captains/logout
Description

Logs out the captain and clears the authentication token.

🗺 Maps APIs

RideSync integrates location services to support ride booking and navigation.

🔹 GET /maps/get-coordinates
Description

Returns latitude and longitude of a given address.

Endpoint
/maps/get-coordinates?address=Location
Example
/maps/get-coordinates?address=Delhi
🔹 GET /maps/get-distance-time
Description

Returns distance and estimated travel time between two locations.

Endpoint
/maps/get-distance-time?origin=A&destination=B
🔹 GET /maps/get-suggestions
Description

Returns location autocomplete suggestions.

Endpoint
/maps/get-suggestions?input=Address
🚕 Ride APIs

These APIs handle the ride booking workflow.

🔹 POST /rides/create
Description

Creates a new ride request.

Request Body
{
  "pickup": "Location A",
  "destination": "Location B",
  "vehicleType": "car"
}
🔹 GET /rides/get-fare
Description

Returns estimated ride fare.

Endpoint
/rides/get-fare?pickup=A&destination=B
🔐 Authentication

RideSync uses JWT (JSON Web Token) for secure authentication.

Protected routes require:

Authorization: Bearer <JWT_TOKEN>
⚙️ Tech Stack

Backend technologies used in RideSync:

Node.js

Express.js

MongoDB

JWT Authentication

Google Maps API

✅ Features

✔ User Authentication
✔ Driver (Captain) Authentication
✔ Ride Booking System
✔ Fare Estimation
✔ Location Services (Maps API)
✔ Secure JWT Authentication
✔ MongoDB Database Storage

🚀 Backend Ready

RideSync backend provides a scalable ride-booking system similar to modern ride-sharing platforms, built using a modular architecture with secure authentication and location services.
