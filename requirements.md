# Backend Feature Requirements for ALX Airbnb Project

## 1. User Authentication

**Description:** Allows users to sign up, log in, and manage sessions.

**API Endpoints:**

- `POST /api/auth/register`

  - Input: `{ "username": "string", "email": "string", "password": "string" }`
  - Output: `{ "message": "User registered successfully", "userId": "string" }`
  - Validation: Email format, password min 8 chars, username required
  - Performance: Response < 500ms

- `POST /api/auth/login`
  - Input: `{ "email": "string", "password": "string" }`
  - Output: `{ "token": "JWT token", "user": { "id": "string", "username": "string" } }`
  - Validation: Correct email/password
  - Performance: Response < 500ms

---

## 2. Property Management

**Description:** CRUD operations for property listings.

**API Endpoints:**

- `POST /api/properties`

  - Input: `{ "title": "string", "description": "string", "price": number, "location": "string", "images": [url] }`
  - Output: `{ "message": "Property added", "propertyId": "string" }`
  - Validation: Title, price > 0, location required
  - Performance: Response < 1s

- `GET /api/properties`

  - Output: `[ { "id": "string", "title": "string", "price": number, "location": "string" } ]`
  - Performance: Response < 1s

- `PUT /api/properties/:id`

  - Input: `{ "title": "string", "price": number }`
  - Output: `{ "message": "Property updated" }`
  - Validation: Price > 0
  - Performance: Response < 1s

- `DELETE /api/properties/:id`
  - Output: `{ "message": "Property deleted" }`
  - Performance: Response < 1s

---

## 3. Booking System

**Description:** Allows users to book properties and manage reservations.

**API Endpoints:**

- `POST /api/bookings`

  - Input: `{ "propertyId": "string", "userId": "string", "startDate": "YYYY-MM-DD", "endDate": "YYYY-MM-DD" }`
  - Output: `{ "message": "Booking confirmed", "bookingId": "string" }`
  - Validation: Start date < end date, property available
  - Performance: Response < 1s

- `GET /api/bookings/user/:userId`

  - Output: `[ { "bookingId": "string", "propertyId": "string", "startDate": "YYYY-MM-DD", "endDate": "YYYY-MM-DD" } ]`
  - Performance: Response < 1s

- `DELETE /api/bookings/:id`
  - Output: `{ "message": "Booking canceled" }`
  - Validation: Booking exists and belongs to user
  - Performance: Response < 1s
