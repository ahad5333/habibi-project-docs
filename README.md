# HABIBI HALAL EXPRESS - COMPREHENSIVE PROJECT RESEARCH & IMPLEMENTATION GUIDE

## Complete Step-by-Step Breakdown | Full Checklist | Progress Tracking

---

## TABLE OF CONTENTS

1. [Project Initialization & Setup](#1-project-initialization--setup)
2. [Database Architecture & Schema](#2-database-architecture--schema)
3. [Backend API Development](#3-backend-api-development)
4. [Frontend Website Development](#4-frontend-website-development)
5. [Mobile App Development](#5-mobile-app-development)
6. [Payment Integration](#6-payment-integration)
7. [Delivery Partner Integration](#7-delivery-partner-integration)
8. [Real-time Features](#8-real-time-features)
9. [Admin Control Panel](#9-admin-control-panel)
10. [Testing & QA](#10-testing--quality-assurance)
11. [Deployment & Launch](#11-deployment--launch)
12. [Complete Checklist & Tracking](#12-complete-checklist--tracking)

---

## 1. PROJECT INITIALIZATION & SETUP

### 1.1 Pre-Development Setup (Week 1)

#### Infrastructure Decisions
- [ ] Choose cloud provider (AWS/Azure/DigitalOcean)
- [ ] Set up VPC/Network isolation
- [ ] Configure security groups/firewall rules
- [ ] Set up logging infrastructure (ELK or CloudWatch)
- [ ] Set up monitoring (Prometheus/Grafana or NewRelic)
- [ ] Set up alerting (Slack, PagerDuty)

#### Version Control & Collaboration
- [ ] Create GitHub repository
- [ ] Set up branch protection rules
  - [ ] Require pull request reviews (2 approvals)
  - [ ] Require status checks to pass
  - [ ] Require code review dismissal
- [ ] Create develop, staging, production branches
- [ ] Configure .gitignore for secrets
- [ ] Set up GitHub Actions runners
- [ ] Create CODEOWNERS file

#### Team Setup
- [ ] Create Slack workspace
- [ ] Create project channels (#general, #backend, #frontend, #mobile, #devops, #emergencies)
- [ ] Set up JIRA/Trello project
- [ ] Create team calendar
- [ ] Schedule daily standups (30 min)
- [ ] Schedule weekly planning (2 hours)
- [ ] Schedule sprint retrospectives

#### Development Environment Standards
- [ ] Create .editorconfig file
- [ ] Set up ESLint configuration
- [ ] Set up Prettier formatting
- [ ] Create Git hooks (pre-commit, pre-push)
- [ ] Create development Docker Compose setup
- [ ] Document environment setup in README
- [ ] Create onboarding guide for new developers

---

### 1.2 Technology Stack Installation & Configuration

#### Backend Setup (Node.js/Express)

**Step 1: Initialize Project**
```bash
mkdir habibi-backend
cd habibi-backend
npm init -y
```

**Step 2: Install Core Dependencies**
```bash
npm install express dotenv cors helmet bcryptjs jsonwebtoken
npm install pg redis sequelize mongoose axios nodemailer
npm install socket.io socket.io-redis
npm install compression morgan winston
npm install joi express-validator
```

**Step 3: Install Development Dependencies**
```bash
npm install --save-dev nodemon eslint prettier jest supertest
npm install --save-dev dotenv-cli rimraf
```

**Step 4: Create Project Structure**
```
habibi-backend/
├── src/
│   ├── config/
│   │   ├── database.js
│   │   ├── redis.js
│   │   ├── smtp.js
│   │   └── env.js
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── userController.js
│   │   ├── locationController.js
│   │   ├── menuController.js
│   │   ├── orderController.js
│   │   ├── paymentController.js
│   │   └── deliveryController.js
│   ├── models/
│   │   ├── User.js
│   │   ├── Location.js
│   │   ├── Menu.js
│   │   ├── Order.js
│   │   ├── Payment.js
│   │   └── Delivery.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── users.js
│   │   ├── locations.js
│   │   ├── menus.js
│   │   ├── orders.js
│   │   ├── payments.js
│   │   └── deliveries.js
│   ├── middleware/
│   │   ├── auth.js
│   │   ├── errorHandler.js
│   │   ├── validation.js
│   │   └── logging.js
│   ├── services/
│   │   ├── authService.js
│   │   ├── orderService.js
│   │   ├── paymentService.js
│   │   ├── deliveryService.js
│   │   └── emailService.js
│   ├── utils/
│   │   ├── validators.js
│   │   ├── helpers.js
│   │   └── constants.js
│   ├── socket/
│   │   ├── handlers.js
│   │   └── namespaces.js
│   └── app.js
├── tests/
│   ├── unit/
│   ├── integration/
│   └── fixtures/
├── .env.example
├── .eslintrc.js
├── .prettierrc
├── jest.config.js
├── docker-compose.yml
└── server.js
```

**Step 5: Package.json Scripts**
```json
{
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js",
    "test": "jest",
    "test:watch": "jest --watch",
    "test:coverage": "jest --coverage",
    "lint": "eslint src/",
    "lint:fix": "eslint src/ --fix",
    "format": "prettier --write \"src/**/*.js\"",
    "db:migrate": "node src/db/migrate.js"
  }
}
```

**Checklist:**
- [ ] Backend project initialized
- [ ] All dependencies installed
- [ ] Project structure created
- [ ] npm scripts configured
- [ ] ESLint & Prettier configured
- [ ] Docker Compose setup complete
- [ ] Sample .env.example created
- [ ] README created with setup instructions

#### Frontend Setup (React/Vite)

**Step 1: Create React App**
```bash
npm create vite@latest habibi-web -- --template react
cd habibi-web
npm install
```

**Step 2: Install Dependencies**
```bash
npm install react-router-dom axios zustand
npm install tailwindcss postcss autoprefixer
npm install @googlemaps/js-api-loader
npm install lodash-es clsx
npm install date-fns
```

**Step 3: Configure Tailwind**
```bash
npx tailwindcss init -p
```

**Step 4: Project Structure**
```
habibi-web/
├── src/
│   ├── components/
│   │   ├── common/
│   │   │   ├── Header.jsx
│   │   │   ├── Footer.jsx
│   │   │   ├── Navigation.jsx
│   │   │   └── Sidebar.jsx
│   │   ├── menu/
│   │   │   ├── MenuCategory.jsx
│   │   │   ├── MenuItem.jsx
│   │   │   └── MenuSearch.jsx
│   │   ├── order/
│   │   │   ├── Cart.jsx
│   │   │   ├── Checkout.jsx
│   │   │   └── OrderTracking.jsx
│   │   ├── location/
│   │   │   ├── LocationSelector.jsx
│   │   │   └── LocationMap.jsx
│   │   └── auth/
│   │       ├── LoginForm.jsx
│   │       └── RegisterForm.jsx
│   ├── pages/
│   │   ├── HomePage.jsx
│   │   ├── MenuPage.jsx
│   │   ├── CheckoutPage.jsx
│   │   ├── OrderTrackingPage.jsx
│   │   ├── LocationsPage.jsx
│   │   ├── ProfilePage.jsx
│   │   └── NotFoundPage.jsx
│   ├── services/
│   │   ├── api.js
│   │   ├── authService.js
│   │   └── orderService.js
│   ├── store/
│   │   ├── authStore.js
│   │   ├── cartStore.js
│   │   └── orderStore.js
│   ├── hooks/
│   │   ├── useAuth.js
│   │   ├── useCart.js
│   │   └── useLocation.js
│   ├── styles/
│   │   ├── globals.css
│   │   └── tailwind.css
│   ├── utils/
│   │   ├── validators.js
│   │   └── helpers.js
│   ├── App.jsx
│   └── main.jsx
├── .env.example
├── tailwind.config.js
├── postcss.config.js
└── vite.config.js
```

**Checklist:**
- [ ] React project created with Vite
- [ ] All dependencies installed
- [ ] Project structure created
- [ ] Tailwind CSS configured
- [ ] Routing structure planned
- [ ] State management (Zustand) configured
- [ ] API service structure created
- [ ] Environment variables setup

---

## 2. DATABASE ARCHITECTURE & SCHEMA

### 2.1 PostgreSQL Database Design

#### Core Tables

##### USERS Table
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  phone VARCHAR(20) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  first_name VARCHAR(100) NOT NULL,
  last_name VARCHAR(100) NOT NULL,
  profile_image_url VARCHAR(500),
  phone_verified BOOLEAN DEFAULT FALSE,
  email_verified BOOLEAN DEFAULT FALSE,
  role VARCHAR(20) DEFAULT 'customer', -- 'customer', 'merchant', 'admin'
  status VARCHAR(20) DEFAULT 'active', -- 'active', 'inactive', 'suspended'
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  last_login TIMESTAMP,
  
  CONSTRAINT email_format CHECK (email ~ '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}$'),
  CONSTRAINT phone_format CHECK (phone ~ '^\+?[0-9]{10,}$')
);

CREATE INDEX idx_users_email ON users(email);
CREATE INDEX idx_users_phone ON users(phone);
CREATE INDEX idx_users_role ON users(role);
CREATE INDEX idx_users_status ON users(status);
CREATE INDEX idx_users_created_at ON users(created_at);
```

**Checklist:**
- [ ] USERS table created
- [ ] Email validation constraint added
- [ ] Phone validation constraint added
- [ ] All indexes created
- [ ] Test data inserted
- [ ] Constraints verified

##### LOCATIONS Table
```sql
CREATE TABLE locations (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(255) NOT NULL,
  address_street VARCHAR(255) NOT NULL,
  address_city VARCHAR(100) NOT NULL,
  address_state VARCHAR(50) NOT NULL,
  address_zip VARCHAR(20) NOT NULL,
  latitude DECIMAL(10, 8) NOT NULL,
  longitude DECIMAL(11, 8) NOT NULL,
  phone VARCHAR(20) NOT NULL,
  email VARCHAR(255),
  opening_hour TIME,
  closing_hour TIME,
  is_24_hours BOOLEAN DEFAULT FALSE,
  holiday_dates JSONB DEFAULT '[]'::jsonb,
  delivery_radius_miles INT DEFAULT 300,
  in_house_delivery BOOLEAN DEFAULT TRUE,
  express_delivery BOOLEAN DEFAULT TRUE,
  long_distance_delivery BOOLEAN DEFAULT FALSE,
  status VARCHAR(20) DEFAULT 'active',
  preference_level INT DEFAULT 1 CHECK (preference_level >= 1 AND preference_level <= 5),
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_locations_status ON locations(status);
CREATE INDEX idx_locations_coordinates ON locations(latitude, longitude);
CREATE INDEX idx_locations_preference ON locations(preference_level);
```

**Checklist:**
- [ ] LOCATIONS table created
- [ ] Coordinates properly stored
- [ ] Holiday dates JSON format defined
- [ ] Delivery preferences configured
- [ ] Indexes created
- [ ] Test locations inserted

##### MENUS Table
```sql
CREATE TABLE menus (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  location_id UUID NOT NULL REFERENCES locations(id) ON DELETE CASCADE,
  name VARCHAR(255) NOT NULL,
  description TEXT,
  category VARCHAR(100) NOT NULL,
  base_price DECIMAL(10, 2) NOT NULL CHECK (base_price > 0),
  partner_price DECIMAL(10, 2),
  image_url VARCHAR(500),
  is_available BOOLEAN DEFAULT TRUE,
  is_sold_out BOOLEAN DEFAULT FALSE,
  is_active BOOLEAN DEFAULT TRUE,
  special_visual_effect VARCHAR(50), -- 'smoke', 'ice', NULL
  preparation_time_minutes INT DEFAULT 15,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  
  CONSTRAINT valid_preparation_time CHECK (preparation_time_minutes > 0)
);

CREATE INDEX idx_menus_location_id ON menus(location_id);
CREATE INDEX idx_menus_category ON menus(category);
CREATE INDEX idx_menus_is_available ON menus(is_available);
CREATE INDEX idx_menus_is_active ON menus(is_active);
CREATE INDEX idx_menus_location_category ON menus(location_id, category);
```

**Checklist:**
- [ ] MENUS table created
- [ ] Price validation constraints
- [ ] Category field configured
- [ ] Visual effects enumerated
- [ ] Preparation time logic added
- [ ] Indexes created
- [ ] Test menu items inserted

##### ORDERS Table
```sql
CREATE TABLE orders (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID NOT NULL REFERENCES users(id),
  location_id UUID NOT NULL REFERENCES locations(id),
  delivery_address_street VARCHAR(255) NOT NULL,
  delivery_address_city VARCHAR(100) NOT NULL,
  delivery_address_zip VARCHAR(20) NOT NULL,
  delivery_latitude DECIMAL(10, 8),
  delivery_longitude DECIMAL(11, 8),
  delivery_type VARCHAR(50), -- 'express', 'in_house', 'long_distance'
  delivery_phone VARCHAR(20),
  order_subtotal DECIMAL(10, 2) NOT NULL CHECK (order_subtotal >= 0),
  tax_amount DECIMAL(10, 2) DEFAULT 0 CHECK (tax_amount >= 0),
  delivery_fee DECIMAL(10, 2) DEFAULT 0 CHECK (delivery_fee >= 0),
  service_fee DECIMAL(10, 2) DEFAULT 0 CHECK (service_fee >= 0),
  total_amount DECIMAL(10, 2) NOT NULL CHECK (total_amount >= 0),
  coupon_code VARCHAR(50),
  discount_amount DECIMAL(10, 2) DEFAULT 0,
  special_instructions TEXT,
  status VARCHAR(50) DEFAULT 'received',
  -- Status flow: received → accepted → cooking → ready → driver_pickup → delivered
  is_scheduled BOOLEAN DEFAULT FALSE,
  scheduled_time TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_orders_user_id ON orders(user_id);
CREATE INDEX idx_orders_location_id ON orders(location_id);
CREATE INDEX idx_orders_status ON orders(status);
CREATE INDEX idx_orders_created_at ON orders(created_at);
CREATE INDEX idx_orders_user_created ON orders(user_id, created_at);
```

**Checklist:**
- [ ] ORDERS table created
- [ ] Order status enum defined
- [ ] Calculation fields validated
- [ ] Scheduling logic added
- [ ] Coupon field added
- [ ] Indexes created for performance
- [ ] Test orders inserted

##### ORDER_ITEMS Table
```sql
CREATE TABLE order_items (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  order_id UUID NOT NULL REFERENCES orders(id) ON DELETE CASCADE,
  menu_id UUID NOT NULL REFERENCES menus(id),
  quantity INT NOT NULL CHECK (quantity > 0),
  unit_price DECIMAL(10, 2) NOT NULL CHECK (unit_price > 0),
  choices_json JSONB, -- {size: "large", spice_level: "medium"}
  add_ons_json JSONB, -- [{name: "Extra sauce", price: 0.50}]
  special_instructions TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_order_items_order_id ON order_items(order_id);
CREATE INDEX idx_order_items_menu_id ON order_items(menu_id);
```

**Checklist:**
- [ ] ORDER_ITEMS table created
- [ ] Choices JSON structure defined
- [ ] Add-ons JSON structure defined
- [ ] Quantity constraints added
- [ ] Indexes created
- [ ] Test data inserted

##### PAYMENTS Table
```sql
CREATE TABLE payments (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  order_id UUID NOT NULL REFERENCES orders(id),
  user_id UUID NOT NULL REFERENCES users(id),
  amount DECIMAL(10, 2) NOT NULL CHECK (amount > 0),
  payment_method VARCHAR(50) NOT NULL,
  -- 'credit_card', 'apple_pay', 'google_pay', 'paypal', 'cash_app', 'zelle', 'cash'
  transaction_id VARCHAR(255),
  merchant_reference VARCHAR(255),
  status VARCHAR(50) DEFAULT 'pending',
  -- 'pending', 'completed', 'failed', 'refunded'
  response_data JSONB, -- Store full API response
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_payments_order_id ON payments(order_id);
CREATE INDEX idx_payments_user_id ON payments(user_id);
CREATE INDEX idx_payments_status ON payments(status);
CREATE INDEX idx_payments_transaction_id ON payments(transaction_id);
```

**Checklist:**
- [ ] PAYMENTS table created
- [ ] Payment methods enumerated
- [ ] Transaction ID field added
- [ ] Response data field for debugging
- [ ] Indexes created
- [ ] Test payments inserted

##### DELIVERIES Table
```sql
CREATE TABLE deliveries (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  order_id UUID NOT NULL REFERENCES orders(id),
  delivery_partner VARCHAR(100), -- 'doordash', 'uber_eats', 'grubhub', 'roadie', 'in_house'
  partner_order_id VARCHAR(255),
  driver_id VARCHAR(255),
  driver_name VARCHAR(255),
  driver_phone VARCHAR(20),
  vehicle_details VARCHAR(255), -- "Blue Honda Civic, License plate XYZ123"
  status VARCHAR(50) DEFAULT 'assigned',
  -- 'assigned', 'pickup', 'in_transit', 'arrived', 'completed', 'cancelled'
  current_latitude DECIMAL(10, 8),
  current_longitude DECIMAL(11, 8),
  estimated_arrival_time TIMESTAMP,
  actual_arrival_time TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_deliveries_order_id ON deliveries(order_id);
CREATE INDEX idx_deliveries_status ON deliveries(status);
CREATE INDEX idx_deliveries_partner ON deliveries(delivery_partner);
```

**Checklist:**
- [ ] DELIVERIES table created
- [ ] Delivery partners enumerated
- [ ] Status flow defined
- [ ] Location tracking fields added
- [ ] Driver info fields added
- [ ] Indexes created

---

### 2.2 Redis Cache Architecture

#### Cache Key Naming Convention

```
user:{user_id}:profile
user:{user_id}:cart
user:{user_id}:addresses
user:{user_id}:orders

location:{location_id}:menu
location:{location_id}:hours
location:{location_id}:delivery_info

menu:{menu_id}:details
menu:{menu_id}:availability

order:{order_id}:details
order:{order_id}:tracking
order:{order_id}:status

session:{session_id}
rate_limit:{ip_address}:{endpoint}
```

#### TTL (Time-to-Live) Configuration

```javascript
// Cache configuration
const CACHE_TTL = {
  user_profile: 3600, // 1 hour
  user_cart: 604800, // 7 days
  menu_items: 86400, // 24 hours
  location_hours: 86400, // 24 hours
  order_details: 2592000, // 30 days
  session: 86400, // 24 hours
  otp: 300, // 5 minutes
  rate_limit_window: 60 // 1 minute
};
```

**Checklist:**
- [ ] Cache key naming convention documented
- [ ] TTL values configured
- [ ] Cache invalidation strategy planned
- [ ] Redis connection pooling configured
- [ ] Cache warming strategy defined

---

## 3. BACKEND API DEVELOPMENT

### 3.1 API Architecture Overview

#### Authentication & Authorization
- JWT token-based authentication
- Refresh token mechanism
- Role-based access control (RBAC)
- Rate limiting (100 requests/minute per IP)

#### API Endpoints Structure

**Authentication Endpoints**

```
POST   /api/v1/auth/register
  Request: { email, phone, password, first_name, last_name }
  Response: { user_id, token, refresh_token }
  Status: 201
  Checklist:
  - [ ] Email validation
  - [ ] Phone validation
  - [ ] Password strength check
  - [ ] Duplicate email check
  - [ ] Duplicate phone check
  - [ ] Hash password with bcryptjs
  - [ ] Generate JWT token
  - [ ] Generate refresh token
  - [ ] Send verification email
  - [ ] Store in database

POST   /api/v1/auth/login
  Request: { email_or_phone, password }
  Response: { user_id, token, refresh_token, user_data }
  Status: 200
  Checklist:
  - [ ] Find user by email or phone
  - [ ] Verify password
  - [ ] Update last_login
  - [ ] Generate new JWT
  - [ ] Generate refresh token
  - [ ] Return user profile

POST   /api/v1/auth/refresh
  Request: { refresh_token }
  Response: { token, refresh_token }
  Status: 200
  Checklist:
  - [ ] Validate refresh token
  - [ ] Check token expiration
  - [ ] Generate new JWT
  - [ ] Rotate refresh token

POST   /api/v1/auth/logout
  Request: { refresh_token }
  Response: { message: "Logged out successfully" }
  Status: 200
  Checklist:
  - [ ] Blacklist refresh token
  - [ ] Clear session

POST   /api/v1/auth/forgot-password
  Request: { email }
  Response: { message: "Reset link sent to email" }
  Status: 200
  Checklist:
  - [ ] Find user by email
  - [ ] Generate reset token
  - [ ] Store in Redis (5 minutes TTL)
  - [ ] Send email with reset link

POST   /api/v1/auth/reset-password
  Request: { reset_token, new_password }
  Response: { message: "Password reset successfully" }
  Status: 200
  Checklist:
  - [ ] Validate reset token
  - [ ] Update password
  - [ ] Invalidate all sessions
```

**User Endpoints**

```
GET    /api/v1/users/profile
  Auth: Required (Bearer token)
  Response: { user_data }
  Checklist:
  - [ ] Fetch from cache first (Redis)
  - [ ] If not in cache, fetch from DB
  - [ ] Cache result for 1 hour
  - [ ] Return user profile

PUT    /api/v1/users/profile
  Auth: Required
  Request: { first_name, last_name, phone, profile_image_url }
  Response: { user_data }
  Checklist:
  - [ ] Validate input
  - [ ] Update database
  - [ ] Invalidate cache
  - [ ] Return updated profile

POST   /api/v1/users/addresses
  Auth: Required
  Request: { street, city, state, zip, latitude, longitude, is_default }
  Response: { address_id, address_data }
  Checklist:
  - [ ] Validate address format
  - [ ] Validate coordinates
  - [ ] Check max 12 addresses per user
  - [ ] Store in database
  - [ ] Update cache

GET    /api/v1/users/addresses
  Auth: Required
  Response: { addresses: [] }
  Checklist:
  - [ ] Fetch from cache
  - [ ] If not cached, fetch from DB
  - [ ] Cache result
  - [ ] Return all user addresses

DELETE /api/v1/users/addresses/{address_id}
  Auth: Required
  Response: { message: "Address deleted" }
  Checklist:
  - [ ] Validate address belongs to user
  - [ ] Delete from database
  - [ ] Invalidate cache

POST   /api/v1/users/payment-methods
  Auth: Required
  Request: { card_token, is_default }
  Response: { payment_method_id }
  Checklist:
  - [ ] Validate payment token
  - [ ] Store securely (tokenization)
  - [ ] Do NOT store raw card data
  - [ ] Update cache

GET    /api/v1/users/orders
  Auth: Required
  Query: { page, limit, status, date_from, date_to }
  Response: { orders: [], total, page, limit }
  Checklist:
  - [ ] Paginate results
  - [ ] Filter by status
  - [ ] Filter by date range
  - [ ] Sort by created_at DESC
  - [ ] Include order items
  - [ ] Calculate totals
```

**Location Endpoints**

```
GET    /api/v1/locations
  Query: { latitude?, longitude?, include_closed=false }
  Response: { locations: [] }
  Checklist:
  - [ ] Fetch all active locations
  - [ ] If lat/lng provided, sort by distance
  - [ ] Cache result for 24 hours
  - [ ] Return location array

GET    /api/v1/locations/{location_id}
  Response: { location_data }
  Checklist:
  - [ ] Fetch location details
  - [ ] Include hours
  - [ ] Include delivery zones
  - [ ] Cache for 24 hours

GET    /api/v1/locations/{location_id}/menu
  Query: { category?, search? }
  Response: { menu: [] }
  Checklist:
  - [ ] Fetch menu items for location
  - [ ] Filter by category if provided
  - [ ] Search items if query provided
  - [ ] Cache for 24 hours
  - [ ] Include prices and availability

GET    /api/v1/locations/{location_id}/hours
  Response: { opening_hour, closing_hour, is_24_hours, holiday_dates }
  Checklist:
  - [ ] Check if location is open now
  - [ ] Return hours
  - [ ] Cache for 24 hours

POST   /api/v1/locations/search
  Request: { latitude, longitude, search_query }
  Response: { locations: [] }
  Checklist:
  - [ ] Calculate distance using Haversine
  - [ ] Filter by delivery radius
  - [ ] Filter by delivery type
  - [ ] Sort by distance & preference
  - [ ] Cache results

GET    /api/v1/locations/{location_id}/delivery-zones
  Response: { zones: [] }
  Checklist:
  - [ ] Fetch delivery coverage zones
  - [ ] Include service area info
  - [ ] Return GeoJSON for mapping
```

**Menu Endpoints**

```
GET    /api/v1/menus/{menu_id}
  Response: { menu_item_data, choices, add_ons }
  Checklist:
  - [ ] Fetch menu item
  - [ ] Fetch related choice groups
  - [ ] Fetch related add-ons
  - [ ] Cache for 24 hours

GET    /api/v1/locations/{location_id}/menus/search
  Query: { q (search query), category }
  Response: { results: [] }
  Checklist:
  - [ ] Search by item name
  - [ ] Search by description
  - [ ] Filter by category
  - [ ] Return matching items
  - [ ] Include relevance score
  - [ ] Cache results

GET    /api/v1/choice-groups/{group_id}
  Response: { group_data, options: [] }
  Checklist:
  - [ ] Fetch choice group
  - [ ] Fetch all options
  - [ ] Include pricing modifiers
  - [ ] Cache for 24 hours
```

**Order Endpoints**

```
POST   /api/v1/orders
  Auth: Required
  Request: {
    location_id,
    items: [{ menu_id, quantity, choices, add_ons, special_instructions }],
    delivery_address_id OR delivery_address: { street, city, zip, lat, lng },
    delivery_type,
    coupon_code?,
    special_instructions?,
    scheduled_time?
  }
  Response: { order_id, total, estimated_time }
  Status: 201
  Checklist:
  - [ ] Validate user authentication
  - [ ] Validate location open
  - [ ] Validate all items available
  - [ ] Check delivery area coverage
  - [ ] Calculate totals
  - [ ] Apply coupon if provided
  - [ ] Validate payment method (if saved)
  - [ ] Create order
  - [ ] Create order items
  - [ ] Notify kitchen
  - [ ] Send confirmation email/SMS

GET    /api/v1/orders/{order_id}
  Auth: Required
  Response: { order_data, items, payment, delivery, status_history }
  Checklist:
  - [ ] Verify user owns order
  - [ ] Fetch order details
  - [ ] Fetch order items
  - [ ] Fetch payment info
  - [ ] Fetch delivery info
  - [ ] Include status history
  - [ ] Cache for 30 days

GET    /api/v1/orders/{order_id}/tracking
  Response: { status, estimated_arrival, driver_info, location }
  Checklist:
  - [ ] Fetch current status
  - [ ] Calculate ETA
  - [ ] Fetch driver info (masked phone)
  - [ ] Fetch driver location
  - [ ] Return via WebSocket for real-time

PUT    /api/v1/orders/{order_id}/status
  Auth: Required (Admin/Merchant)
  Request: { status }
  Response: { order_data }
  Checklist:
  - [ ] Validate new status
  - [ ] Verify state transition allowed
  - [ ] Update database
  - [ ] Send notification to customer
  - [ ] Broadcast via WebSocket
  - [ ] Send SMS alert

POST   /api/v1/orders/{order_id}/cancel
  Auth: Required
  Request: { reason }
  Response: { message, refund_status }
  Checklist:
  - [ ] Check if order can be cancelled
  - [ ] Calculate refund amount
  - [ ] Process refund
  - [ ] Update order status
  - [ ] Notify payment provider
  - [ ] Send notification to customer

GET    /api/v1/orders/{order_id}/receipt
  Response: { PDF or HTML receipt }
  Checklist:
  - [ ] Generate receipt
  - [ ] Include itemization
  - [ ] Include payment method
  - [ ] Include delivery address
  - [ ] Include company info
  - [ ] Add QR code for reorder
```

**Payment Endpoints**

```
POST   /api/v1/payments/process
  Auth: Required
  Request: { order_id, payment_method_id, amount }
  Response: { transaction_id, status }
  Checklist:
  - [ ] Validate order exists
  - [ ] Validate amount matches
  - [ ] Call payment gateway
  - [ ] Handle response
  - [ ] Create payment record
  - [ ] Update order status
  - [ ] Send confirmation

POST   /api/v1/payments/webhook/square
  Request: { Webhook payload from Square }
  Response: { status: 200 }
  Checklist:
  - [ ] Verify webhook signature
  - [ ] Parse event
  - [ ] Update payment status
  - [ ] Update order status if needed

POST   /api/v1/payments/refund
  Auth: Required (Admin)
  Request: { payment_id, reason }
  Response: { refund_id, status }
  Checklist:
  - [ ] Validate payment exists
  - [ ] Validate amount
  - [ ] Call payment gateway
  - [ ] Create refund record
  - [ ] Notify customer
```

**Delivery Endpoints**

```
POST   /api/v1/deliveries/assign
  Auth: Required (Admin)
  Request: { order_id, delivery_partner, partner_order_id }
  Response: { delivery_id, driver_info }
  Checklist:
  - [ ] Create delivery record
  - [ ] Assign delivery partner
  - [ ] Notify customer
  - [ ] Broadcast via WebSocket

GET    /api/v1/deliveries/{delivery_id}/tracking
  Response: { status, driver_location, eta, vehicle_info }
  Checklist:
  - [ ] Fetch delivery status
  - [ ] Get current location
  - [ ] Calculate ETA
  - [ ] Return vehicle info

PUT    /api/v1/deliveries/{delivery_id}/location
  Request: { latitude, longitude }
  Response: { status: 200 }
  Checklist:
  - [ ] Update driver location
  - [ ] Store in Redis
  - [ ] Broadcast via WebSocket
  - [ ] Calculate new ETA

POST   /api/v1/deliveries/{delivery_id}/complete
  Request: { notes?, photo_url? }
  Response: { message: "Delivery completed" }
  Checklist:
  - [ ] Update delivery status
  - [ ] Update order status to 'delivered'
  - [ ] Notify customer
  - [ ] Trigger rating request
```

**Admin Endpoints**

```
POST   /api/v1/admin/locations
  Auth: Required (Admin)
  Request: { location_data }
  Response: { location_id }

PUT    /api/v1/admin/locations/{location_id}
  Auth: Required (Admin)
  Request: { location_data }
  Response: { location_data }

DELETE /api/v1/admin/locations/{location_id}
  Auth: Required (Admin)
  Response: { message: "Location deleted" }

POST   /api/v1/admin/menus
  Auth: Required (Admin)
  Request: { menu_data, location_id }
  Response: { menu_id }

PUT    /api/v1/admin/menus/{menu_id}
  Auth: Required (Admin)
  Request: { menu_data }
  Response: { menu_data }

DELETE /api/v1/admin/menus/{menu_id}
  Auth: Required (Admin)
  Response: { message: "Menu item deleted" }

GET    /api/v1/admin/reports/sales
  Auth: Required (Admin)
  Query: { date_from, date_to, location_id }
  Response: { sales_data, charts }

GET    /api/v1/admin/reports/orders
  Auth: Required (Admin)
  Query: { status, date_from, date_to }
  Response: { order_data, analytics }

GET    /api/v1/admin/business-partners
  Auth: Required (Admin)
  Response: { partners: [], pending: [] }

PUT    /api/v1/admin/business-partners/{partner_id}
  Auth: Required (Admin)
  Request: { status, approval_notes }
  Response: { partner_data }
```

---

## 4. FRONTEND WEBSITE DEVELOPMENT

### 4.1 Page Components & Features

**Detailed Checklist for Each Page:**

#### HomePage
- [ ] Hero section with background carousel
- [ ] Location selector with autocomplete
- [ ] Delivery/Pickup toggle
- [ ] "Order Now" CTA button
- [ ] Featured items carousel
- [ ] "Why Choose Us" features section
- [ ] Locations map integration
- [ ] Footer with links & social media
- [ ] Mobile responsive layout
- [ ] Loading states
- [ ] Error handling

#### MenuBrowsePage
- [ ] Category tabs/sidebar
- [ ] Search bar with autocomplete
- [ ] Filter options (price, rating, availability)
- [ ] Sort options (popular, price, new)
- [ ] Menu items grid/list view
- [ ] Item image, name, description, price
- [ ] Add to cart button
- [ ] Availability indicator
- [ ] Item detail modal
- [ ] Customization modal (choices/add-ons)
- [ ] Infinite scroll or pagination
- [ ] Loading skeletons
- [ ] No results message

#### CheckoutPage
Step 1 - Delivery Address
- [ ] Show saved addresses
- [ ] Address search with autocomplete
- [ ] Manual address entry form
- [ ] Address validation
- [ ] Delivery coverage check
- [ ] Estimated delivery time
- [ ] Map preview
- [ ] Set default address

Step 2 - Order Review
- [ ] Order items list
- [ ] Item customizations shown
- [ ] Edit/remove items
- [ ] Subtotal calculation
- [ ] Tax calculation (8.875%)
- [ ] Service fee calculation (4.273%)
- [ ] Delivery fee display
- [ ] Coupon code input
- [ ] Total amount
- [ ] Special instructions

Step 3 - Payment Method
- [ ] Payment method selector
- [ ] Credit card form
- [ ] Apple Pay integration
- [ ] Google Pay integration
- [ ] PayPal integration
- [ ] Cash on delivery option
- [ ] Saved payment methods
- [ ] Security badges
- [ ] Terms & conditions checkbox

Step 4 - Confirmation
- [ ] Final order summary
- [ ] Delivery details
- [ ] Payment method masked
- [ ] Estimated arrival time
- [ ] "Place Order" button
- [ ] Loading state
- [ ] Error handling

#### OrderTrackingPage
- [ ] Order status timeline
- [ ] Current status highlighted
- [ ] Estimated time remaining
- [ ] Cooking progress animation
- [ ] Driver information (when ready)
- [ ] Driver location map (when in transit)
- [ ] Real-time location updates
- [ ] ETA calculation
- [ ] Driver contact button
- [ ] Order details accessible
- [ ] Support button

#### LocationsPage
- [ ] Map view of all locations
- [ ] List view of locations
- [ ] Location detail card
- [ ] Hours of operation
- [ ] Delivery info
- [ ] Contact information
- [ ] "Order from this location" button
- [ ] Filter by delivery type
- [ ] Mobile responsive

#### ProfilePage
- [ ] User information display
- [ ] Edit profile form
- [ ] Saved addresses management
- [ ] Order history
- [ ] Saved payment methods
- [ ] Notification preferences
- [ ] Logout button
- [ ] Account deletion option

### 4.2 Component Architecture

```
App
├── Header
│  ├── Logo
│  ├── Navigation
│  │  └── NavLinks
│  ├── SearchBar
│  ├── UserIcon
│  └── CartIcon
├── Layout
│  ├── Sidebar (conditional)
│  ├── Main Content
│  └── Footer
└── Modals
   ├── AuthModal
   ├── ItemDetailModal
   └── CartModal
```

**Checklist for Components:**
- [ ] All components created
- [ ] Props properly typed
- [ ] State management integrated
- [ ] Loading states added
- [ ] Error handling added
- [ ] Accessibility checked (ARIA labels, keyboard navigation)
- [ ] Mobile responsive
- [ ] Performance optimized (memoization, lazy loading)

---

## 5. MOBILE APP DEVELOPMENT

### 5.1 iOS App (Swift)

**Project Structure:**
```
HabibiApp/
├── Models/
├── ViewModels/
├── Views/
├── Services/
├── Utilities/
└── Resources/
```

**Key Screens:**
1. Splash Screen
2. Authentication (Register/Login)
3. Location Selection
4. Menu Browsing
5. Item Detail
6. Cart
7. Checkout
8. Order Tracking
9. Order History
10. Profile

**Checklist:**
- [ ] All screens created
- [ ] Navigation flow implemented
- [ ] API integration
- [ ] Location permissions
- [ ] Push notifications
- [ ] Payment SDK integration
- [ ] Testing on real devices
- [ ] App store preparation
- [ ] Privacy policy
- [ ] Terms and conditions

### 5.2 Android App (Kotlin)

Similar structure and checklist as iOS

### 5.3 Merchant Tablet App

Features:
- [ ] New order alerts
- [ ] Order management
- [ ] Status updates
- [ ] Fulfillment tracking
- [ ] Offline mode
- [ ] Settings

---

## 6. PAYMENT INTEGRATION

### 6.1 Payment Gateway Integration Roadmap

**Phase 1: Square (Primary) - Weeks 1-2**
- [ ] Create Square account
- [ ] Get API credentials
- [ ] Install Square SDK
- [ ] Create payment form
- [ ] Implement card tokenization
- [ ] Handle webhooks
- [ ] Test in sandbox
- [ ] Deploy to staging
- [ ] Go live

**Phase 2: Apple Pay & Google Pay - Week 3**
- [ ] Set up Apple Pay
- [ ] Set up Google Pay
- [ ] Integrate with Square
- [ ] Test on devices
- [ ] Deploy

**Phase 3: PayPal - Week 4**
- [ ] Create PayPal account
- [ ] Implement PayPal button
- [ ] Handle approval/capture
- [ ] Setup webhooks
- [ ] Test
- [ ] Deploy

**Phase 4: Cash App & Zelle - Week 5**
- [ ] Research availability
- [ ] Implement if available
- [ ] Setup webhooks
- [ ] Test
- [ ] Deploy

**Phase 5: Cash on Delivery - Week 6**
- [ ] Implement COD flow
- [ ] Create collection workflow
- [ ] Setup confirmation system

---

## 7. DELIVERY PARTNER INTEGRATION

### 7.1 DoorDash Integration (CRITICAL) - 7 Weeks

**Week 1: Setup**
- [ ] Create merchant account
- [ ] Complete merchant onboarding
- [ ] Set up Stripe Connect
- [ ] Get API credentials
- [ ] Review documentation
- [ ] Setup webhook endpoints

**Weeks 2-3: Menu Sync**
- [ ] Map menu to DoorDash format
- [ ] Create upload function
- [ ] Implement menu updates
- [ ] Handle availability changes
- [ ] Test complete sync

**Weeks 4-5: Order Integration**
- [ ] Create webhook handler
- [ ] Implement order creation
- [ ] Status update mapping
- [ ] Delivery tracking
- [ ] Error handling

**Weeks 6-7: Testing & Refinement**
- [ ] Integration testing
- [ ] Error scenarios
- [ ] Performance testing
- [ ] Security audit

### 7.2 Uber Eats - 6-7 Weeks
- [ ] Similar to DoorDash
- [ ] Specific Uber Eats requirements

### 7.3 Grubhub - 5-6 Weeks
- [ ] Similar to others
- [ ] Grubhub-specific features

### 7.4 Roadie (Long-distance) - 3-4 Weeks
- [ ] Research API
- [ ] Implement shipment creation
- [ ] Driver assignment
- [ ] Tracking
- [ ] Pricing

---

## 8. REAL-TIME FEATURES

### 8.1 WebSocket/Socket.io Setup

**Backend:**
- [ ] Install socket.io
- [ ] Configure CORS
- [ ] Set up namespaces
- [ ] Implement Redis adapter
- [ ] Create authentication middleware
- [ ] Setup logging

**Frontend:**
- [ ] Install socket.io-client
- [ ] Create connection manager
- [ ] Handle reconnection
- [ ] Listen for events
- [ ] Handle offline/online

### 8.2 Features to Implement

**Order Status Updates:**
- [ ] Emit status changes
- [ ] Update UI in real-time
- [ ] Send notifications
- [ ] Update tracking page

**Driver Location:**
- [ ] Get user location
- [ ] Emit location updates
- [ ] Show on map
- [ ] Calculate ETA

**Tablet Notifications:**
- [ ] New order alerts
- [ ] Sound notifications
- [ ] Order management
- [ ] Status updates

---

## 9. ADMIN CONTROL PANEL

### 9.1 Dashboard Components

**Dashboard Overview:**
- [ ] KPI cards (Today's sales, Orders, Customers)
- [ ] Sales chart (last 7/30 days)
- [ ] Order status distribution
- [ ] Top items
- [ ] Recent orders list

**Location Management:**
- [ ] Create location form
- [ ] Edit location form
- [ ] Location list
- [ ] Status management
- [ ] Hours configuration
- [ ] Delivery zones

**Menu Management:**
- [ ] Item CRUD operations
- [ ] Category management
- [ ] Choice groups management
- [ ] Add-ons management
- [ ] Bulk actions
- [ ] Image upload

**Order Management:**
- [ ] Order list with filters
- [ ] Order detail view
- [ ] Status update buttons
- [ ] Refund processing
- [ ] Notes addition
- [ ] Receipt generation

**Business Partner Management:**
- [ ] Application list
- [ ] Approval workflow
- [ ] Partner pricing
- [ ] Menu assignment
- [ ] Reporting

**Reports & Analytics:**
- [ ] Sales reports
- [ ] Order analytics
- [ ] Customer analytics
- [ ] Partner performance
- [ ] Revenue breakdown
- [ ] Export functionality

---

## 10. TESTING & QUALITY ASSURANCE

### 10.1 Testing Strategy

**Unit Testing:**
- [ ] Frontend components (Jest + RTL)
- [ ] Backend functions (Jest)
- [ ] Utilities and helpers
- [ ] Target: 80%+ coverage

**Integration Testing:**
- [ ] API endpoints
- [ ] Database operations
- [ ] Payment processing
- [ ] Delivery integration

**E2E Testing:**
- [ ] User registration flow
- [ ] Order flow
- [ ] Payment flow
- [ ] Admin workflows

**Performance Testing:**
- [ ] Load testing (1000+ concurrent users)
- [ ] API response times
- [ ] Database query optimization
- [ ] Frontend performance (Lighthouse)

**Security Testing:**
- [ ] SQL injection tests
- [ ] XSS vulnerability tests
- [ ] CSRF protection
- [ ] Authentication tests
- [ ] Authorization tests
- [ ] Payment data security

---

## 11. DEPLOYMENT & LAUNCH

### 11.1 Pre-Launch Checklist

**Infrastructure:**
- [ ] Production servers setup
- [ ] Database replication
- [ ] Backup systems
- [ ] CDN configuration
- [ ] SSL certificates
- [ ] Load balancer configuration

**Code Quality:**
- [ ] All tests passing
- [ ] Code review completed
- [ ] Linting passed
- [ ] No security vulnerabilities

**Documentation:**
- [ ] API documentation
- [ ] Admin documentation
- [ ] Staff training materials
- [ ] Runbooks created

**Launch Day:**
- [ ] Website goes live
- [ ] Apps available on stores
- [ ] Email notifications sent
- [ ] Support team ready
- [ ] Monitoring active
- [ ] Incident response ready

---

## 12. COMPLETE CHECKLIST & TRACKING

### 12.1 Week-by-Week Timeline

**Month 1: Planning & Setup (Weeks 1-4)**
- Week 1: Project initialization, GitHub setup, team structure
- Week 2: Database design, API planning, tech stack setup
- Week 3: Frontend structure, routing setup, component planning
- Week 4: Backend APIs skeleton, authentication setup

**Month 2: Core Development (Weeks 5-8)**
- Week 5: User authentication complete, basic menu APIs
- Week 6: Menu browsing frontend, order creation APIs
- Week 7: Cart functionality, checkout flow
- Week 8: Payment integration (Square)

**Month 3: Advanced Features (Weeks 9-12)**
- Week 9: Delivery partner integration (DoorDash)
- Week 10: Real-time tracking, WebSocket setup
- Week 11: Admin panel basic features
- Week 12: Testing & bug fixes

**Month 4: Mobile & Polish (Weeks 13-16)**
- Week 13-14: iOS app development
- Week 15-16: Android app development

**Month 5: Testing & Launch Prep (Weeks 17-20)**
- Week 17-18: Integration testing, E2E testing
- Week 19: Performance optimization
- Week 20: Security audit, launch preparation

**Month 6-7: Launch & Beyond (Weeks 21-28)**
- Week 21-22: App store submission, final testing
- Week 23-24: Launch, post-launch monitoring
- Weeks 25-28: Bug fixes, optimization, feature enhancements

---

### 12.2 Risk Tracking Matrix

| Risk | Impact | Probability | Mitigation | Status |
|------|--------|-------------|-----------|--------|
| Third-party API downtime | High | Medium | Implement fallback, caching | 📋 |
| Database performance issues | High | Medium | Query optimization, indexing | 📋 |
| Payment processing failures | Critical | Low | Extensive testing, backup gateway | 📋 |
| Scope creep | High | High | Strict change control, sprint planning | 📋 |
| Resource shortage | Medium | Low | Contingency team identified | 📋 |
| Security vulnerabilities | Critical | Low | Regular security audits, penetration testing | 📋 |

---

## TRACKING TEMPLATE

Create a spreadsheet with these columns:

| Task | Component | Owner | Status | % Complete | Blockers | Notes | Due Date |
|------|-----------|-------|--------|-----------|----------|-------|----------|
| | | | TODO/IN PROGRESS/DONE | 0-100% | | | |

---

## SUCCESS METRICS

- [ ] Website loads in < 2 seconds
- [ ] API responds in < 200ms (95th percentile)
- [ ] 99.9% uptime
- [ ] Zero PCI compliance violations
- [ ] All endpoints tested (>90% coverage)
- [ ] Customer onboarding < 5 minutes
- [ ] Order placement < 2 minutes
- [ ] Payment success rate > 99%
- [ ] Delivery partner integration 100% synchronized

---

## CONCLUSION

This comprehensive guide provides a detailed roadmap for implementing the Habibi Halal Express project. Use this as your reference for every decision, implementation, and tracking checkpoint. Update regularly as you progress.

**Start Date:** [Enter your start date]
**Target Launch:** [Enter target launch date]
**Team Lead:** [Enter name]

---
