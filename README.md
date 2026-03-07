🚗 RideSync – Real-Time Ride Sharing Platform

RideSync is a full-stack ride sharing platform that allows users to book rides, drivers to accept rides, and track routes using real-time map services.

The system provides secure authentication, ride management, and map-based navigation similar to modern ride-sharing platforms.

🏗 System Architecture
Frontend (React.js)
        │
        ▼
Backend API (Node.js + Express.js)
        │
        ▼
Authentication (JWT)
        │
        ▼
Database (MongoDB)
        │
        ▼
External Services (Google Maps API)
⚙️ Tech Stack
Frontend

React.js

Backend

Node.js

Express.js

Database

MongoDB

Authentication

JWT (JSON Web Token)

External Services

Google Maps API

📁 Project Structure
RideSync
│
├── Backend
│   ├── controllers
│   ├── models
│   ├── routes
│   ├── middleware
│   └── server.js
│
├── frontend
│   ├── components
│   ├── pages
│   ├── services
│   └── App.js
│
└── README.md
👤 User APIs
Register User

POST

/users/register
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
  "user": {}
}
Login User

POST

/users/login
Request
{
  "email": "arya@test.com",
  "password": "123456"
}
Response
{
  "token": "JWT_TOKEN",
  "user": {}
}
Get User Profile
GET /users/profile

Authentication Required

Authorization: Bearer JWT_TOKEN
Logout User
GET /users/logout
🚖 Captain (Driver) APIs

Drivers are called Captains.

Register Captain
POST /captains/register
Request
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
Captain Login
POST /captains/login

Returns a JWT token.

Captain Profile
GET /captains/profile

Requires authentication.

Captain Logout
GET /captains/logout
🗺 Maps APIs
Get Coordinates
GET /maps/get-coordinates?address=Location

Returns latitude and longitude of a location.

Example

/maps/get-coordinates?address=Delhi
Get Distance and Time
GET /maps/get-distance-time?origin=A&destination=B

Returns travel distance and estimated time.

Location Suggestions
GET /maps/get-suggestions?input=Address

Returns autocomplete location suggestions.

🚕 Ride APIs
Create Ride
POST /rides/create
Request
{
  "pickup": "Location A",
  "destination": "Location B",
  "vehicleType": "car"
}
Get Fare
GET /rides/get-fare?pickup=A&destination=B

Returns estimated ride fare.

🔐 Authentication

RideSync uses JWT authentication.

Protected routes require:

Authorization: Bearer <JWT_TOKEN>
✅ Features

✔ User Authentication
✔ Driver (Captain) Authentication
✔ Ride Booking System
✔ Fare Estimation
✔ Location Services
✔ Secure JWT Authentication
✔ MongoDB Database Storage

🚀 Installation & Setup

Clone the repository

git clone https://github.com/aryaa121/RideSync.git

Go to project folder

cd RideSync

Install backend dependencies

npm install

Run backend server

npm start

Run frontend

cd frontend
npm install
npm run dev
📌 Future Improvements

Real-time ride tracking

Payment integration

Driver rating system

Ride history

👨‍💻 Author

Arya
