# Hotel Booking System

A full-stack hotel booking application with Node.js/Express backend and React frontend.

## Project Structure

```
hotel-booking-system/
├── backend/          - Node.js + Express REST API
├── frontend/         - React + Vite + Tailwind CSS
├── database/         - MySQL schema
└── postman/          - API collection
```

## Quick Start

### 1. Database Setup
```bash
mysql -u root -p < database/schema.sql
```

### 2. Backend
```bash
cd backend
npm install
# Edit .env with your credentials
npm run dev   # runs on http://localhost:5000
```

### 3. Frontend
```bash
cd frontend
npm install
npm run dev   # runs on http://localhost:5173
```

### 4. Create Admin User
```sql
USE hotel_booking_system;
INSERT INTO users (name, email, password, phone, role)
VALUES ('Admin', 'admin@hotel.com', '$2a$10$...', '0000000000', 'admin');
-- Generate hashed password with: node -e "const b=require('bcryptjs');b.hash('yourpass',10).then(console.log)"
```

## Features

- JWT Authentication (register, login, profile)
- Browse & search hotels by city/price
- Room availability checking
- Date-based booking with conflict prevention
- Booking history & cancellation
- Admin dashboard with charts
- Hotel/Room CRUD management
- Email booking confirmations
- Dark mode support
- Responsive design

## API Endpoints

### Auth
- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET  /api/auth/profile` (protected)
- `PUT  /api/auth/profile` (protected)

### Hotels
- `GET /api/hotels`
- `GET /api/hotels/:id`

### Rooms
- `GET /api/rooms/hotel/:hotelId`
- `GET /api/rooms/available`

### Bookings (protected)
- `POST /api/bookings`
- `GET  /api/bookings`
- `PUT  /api/bookings/:id/cancel`

### Admin (admin only)
- `GET    /api/admin/stats`
- `POST   /api/admin/hotels`
- `PUT    /api/admin/hotels/:id`
- `DELETE /api/admin/hotels/:id`
- `POST   /api/admin/rooms`
- `PUT    /api/admin/rooms/:id`
- `DELETE /api/admin/rooms/:id`
- `GET    /api/admin/bookings`
- `GET    /api/admin/users`

## Tech Stack

**Backend:** Node.js, Express, MySQL2, JWT, bcryptjs, Nodemailer  
**Frontend:** React 18, Vite, Tailwind CSS, React Router, Axios, Recharts
