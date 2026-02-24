🚗 Uber Clone – Complete Backend API Documentation

This backend powers a real-time ride-booking system similar to Uber, supporting authentication, ride lifecycle management, geo-spatial captain discovery, real-time communication, and secure session handling.

🌐 Base URL
http://localhost:4000
🔐 Authentication

All protected routes require:

Authorization: Bearer <JWT_TOKEN>

JWT Expiry: 24 hours
Logout Mechanism: Token Blacklisting

👤 USER APIs
🔹 1. Register User
POST /users/register
Description:

Creates a new user account.

Request Body:
{
  "fullname": {
    "firstname": "Arya",
    "lastname": "Stark"
  },
  "email": "arya@test.com",
  "password": "123456"
}
Success Response:
{
  "token": "JWT_TOKEN",
  "user": {
    "_id": "user_id",
    "fullname": {
      "firstname": "Arya",
      "lastname": "Stark"
    },
    "email": "arya@test.com"
  }
}
Validations:

Email must be unique

Password minimum length enforced

🔹 2. Login User
POST /users/login
Description:

Authenticates user and returns JWT token.

🔹 3. Get User Profile
GET /users/profile

🔒 Protected Route

Returns logged-in user details.

🔹 4. Logout User
GET /users/logout

🔒 Protected Route

Adds token to blacklist

Prevents reuse of token

🚖 CAPTAIN APIs
🔹 1. Register Captain
POST /captains/register
Request Body:
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
Additional Fields Stored:

location (GeoJSON format)

status (active/inactive)

🔹 2. Login Captain
POST /captains/login

Returns JWT token.

🔹 3. Get Captain Profile
GET /captains/profile

🔒 Protected

🔹 4. Logout Captain
GET /captains/logout

🔒 Protected
Token added to blacklist.

🗺 MAP SERVICES APIs

Integrated with Google Maps API.

🔹 1. Get Coordinates
GET /maps/get-coordinates?address=Location
Response:
{
  "latitude": 28.6139,
  "longitude": 77.2090
}
🔹 2. Get Distance & Duration
GET /maps/get-distance-time?origin=A&destination=B
Response:
{
  "distance": "12 km",
  "duration": "25 mins"
}
🔹 3. Get Address Suggestions
GET /maps/get-suggestions?input=Address

Returns autocomplete suggestions.

🚕 RIDE APIs
🔹 1. Create Ride
POST /rides/create

🔒 Protected (User)

Request Body:
{
  "pickup": "Location A",
  "destination": "Location B",
  "vehicleType": "car"
}
Internal Flow:

Convert pickup/destination → coordinates

Calculate fare

Create ride (status: pending)

Find captains in 2km radius

Emit real-time notification

🔹 2. Get Fare Estimate
GET /rides/get-fare?pickup=A&destination=B

Returns:

{
  "vehicleType": "car",
  "fare": 250
}
🔹 3. Accept Ride (Captain)
POST /rides/accept

🔒 Protected (Captain)

Updates ride status → accepted

🔹 4. Start Ride
POST /rides/start

🔒 Protected

Validates OTP before changing status → ongoing

🔹 5. End Ride
POST /rides/end

🔒 Protected

Updates ride status → completed

🔔 Real-Time Socket Events

Using Socket.IO:

User Events:

join

ride-confirmed

ride-started

ride-ended

Captain Events:

join

new-ride

location-update

📍 Geo-Spatial Implementation

Captain location stored as:

{
  "type": "Point",
  "coordinates": [longitude, latitude]
}

Indexed using:

2dsphere index

Used for:

$geoWithin

$centerSphere

2km radius search

🧱 Database Collections
users

fullname

email

password

socketId

captains

fullname

email

password

vehicle

location

socketId

rides

user (ref)

captain (ref)

pickup

destination

fare

otp

status

timestamps

blackListTokens

token

createdAt

🔐 Security Features

✔ JWT Authentication
✔ Password hashing (bcrypt)
✔ Token Blacklisting
✔ OTP Ride Verification
✔ Protected Middleware Routes
✔ Request Validation
✔ Geo-index optimization

🚀 Ride Lifecycle
Pending
   ↓
Accepted
   ↓
Ongoing
   ↓
Completed
⚙️ Architecture Pattern
Routes → Controllers → Services → Models

Clean MVC separation with business logic abstraction.

📈 Scalability Enhancements (Future Improvements)

Redis for Socket scaling

Rate limiting

Surge pricing logic

Payment gateway integration

Microservices architecture

Docker deployment

🏆 Backend Status

✅ Production-style structure
✅ Secure authentication
✅ Real-time event system
✅ Geo-spatial captain matching
✅ Modular architecture

Arya 🔥
