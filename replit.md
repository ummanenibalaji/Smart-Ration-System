# Smart Ration System

A modern digital platform for managing ration distribution in urban areas, built with React, Express, PostgreSQL, and TypeScript.

## Project Overview

Smart Ration System (SRS) modernizes the traditional ration shop experience by providing:
- Online booking for ration groceries
- Real-time quota tracking
- Home delivery and store pickup options
- Multi-role access (Citizens, Shopkeepers, Admins)
- Digital receipts and order tracking

## Tech Stack

### Frontend
- **React** with TypeScript
- **Wouter** for routing
- **TanStack Query** for server state management
- **React Hook Form** with Zod validation
- **Shadcn UI** components with Tailwind CSS
- **Recharts** for data visualization

### Backend
- **Express** server
- **PostgreSQL** database (Neon)
- **Drizzle ORM** for database operations
- **Bcrypt** for password hashing
- **Zod** for API validation

## Database Schema

- **users**: User accounts (citizen, shopkeeper, admin roles)
- **ration_cards**: Digital ration cards linked to users
- **items**: Ration grocery items (rice, wheat, oil, etc.)
- **quotas**: Monthly quota allocations per user per item
- **orders**: Booking records
- **order_items**: Line items in orders

## Demo Credentials

**Citizen Account:**
- Mobile: 9876543210
- Password: password123
- Features: Browse items, place orders, track quota

**Shopkeeper Account:**
- Mobile: 9876543211
- Password: password123
- Features: Manage inventory, approve orders

**Admin Account:**
- Mobile: 9876543212
- Password: password123
- Features: User management, analytics, quota configuration

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `POST /api/auth/verify-otp` - Verify OTP (mock for MVP)

### Ration Cards
- `POST /api/ration-cards` - Link ration card
- `GET /api/ration-cards/user/:userId` - Get user's ration card
- `GET /api/quotas/user/:userId` - Get user quotas

### Items
- `GET /api/items` - List all items
- `GET /api/items/:id` - Get item details
- `POST /api/items` - Create item (admin/shopkeeper)
- `PATCH /api/items/:id/stock` - Update stock (shopkeeper)

### Orders
- `POST /api/orders` - Create order
- `GET /api/orders/user/:userId` - Get user orders
- `GET /api/orders/:id` - Get order details
- `PATCH /api/orders/:id/status` - Update order status

### Shopkeeper
- `GET /api/shopkeeper/orders` - Get all orders (filter by status)

### Admin
- `GET /api/admin/orders` - Get all orders
- `GET /api/admin/analytics` - Get system analytics

## Running the Project

The application runs on a single port (5000) with Vite serving the frontend and Express handling the API.

```bash
npm run dev
```

To reseed the database:
```bash
tsx server/seed.ts
```

## User Flows

### Citizen Flow
1. Register with mobile number → OTP verification
2. Link ration card with card number
3. View dashboard with quota status
4. Browse items and add to cart
5. Checkout with delivery slot selection
6. Track order status

### Shopkeeper Flow
1. Login with credentials
2. View pending orders
3. Approve/reject orders
4. Update inventory stock levels

### Admin Flow
1. Login with credentials
2. View system analytics
3. Manage users and ration cards
4. Monitor all orders and stock

## Design System

The UI follows Material Design 3 principles with government service adaptations:

- **Colors**: Professional green primary (#22c55e), neutral grays
- **Typography**: Inter for UI, JetBrains Mono for data
- **Spacing**: Consistent 4/6/8/12/16/24px scale
- **Components**: All shadcn/ui components pre-configured
- **Interactions**: Subtle hover elevations, smooth transitions

See `design_guidelines.md` for complete design specifications.

## Current Status

✅ Complete database schema with relations
✅ All API endpoints implemented
✅ Full frontend UI with all pages
✅ Authentication system (bcrypt password hashing)
✅ Seed data for testing
🔄 Frontend-backend integration (in progress)
