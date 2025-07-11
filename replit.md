# Electronics Franchise ERP System

## Overview

This is a full-stack electronics franchise management system built with React, FastAPI, and PostgreSQL. The application provides comprehensive product management capabilities including inventory tracking, sell-in/sell-through analytics, and bulk product operations for electronics retailers.

## System Architecture

This project is split into two micro services:

1. **Client Service** – a React application served by a lightweight Express server. The client code lives in `client/` and the Express server code lives in `server/`.
2. **API Service** – a FastAPI application located in `python_server/`.

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Library**: Radix UI primitives with shadcn/ui components
- **Styling**: Tailwind CSS with custom design system
- **State Management**: TanStack Query for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Forms**: React Hook Form with Zod validation

### Backend Architecture
- **Runtime**: Python 3.11 with FastAPI
- **Language**: Python with type hints
- **Database**: PostgreSQL with SQLAlchemy ORM
- **Session Management**: FastAPI session or authentication middleware (future)
- **API Design**: RESTful endpoints with JSON responses

### Database Design
- **ORM**: SQLAlchemy with Python models
- **Database**: PostgreSQL 16 with connection pooling via Neon serverless
- **Migrations**: Alembic (planned)
- **Schema Location**: `python_server/db_models.py`

## Key Components

### Product Management System
- **Product CRUD**: Complete create, read, update, delete operations
- **Search Functionality**: Real-time product search by name, code, or brand
- **Bulk Operations**: CSV upload/import for batch product management
- **Field Validation**: Comprehensive validation using Zod schemas

### Sales Analytics
- **Sell-In Tracking**: Inventory purchases from distributors
- **Sell-Through Analysis**: Sales to end customers
- **Monthly Partitioning**: Data organized by month for efficient queries
- **Performance Metrics**: Real-time analytics dashboard

### Data Models
- **Products**: Core product catalog with pricing, availability, and metadata
- **Sell-Ins**: Purchase transactions from distributors
- **Sell-Throughs**: Sales transactions to customers
- **Analytics**: Computed metrics for business intelligence

## Data Flow

### Client-Server Communication
1. React components make API calls using TanStack Query
2. FastAPI routes handle business logic and data validation
3. SQLAlchemy ORM manages database operations
4. Results are cached on the client for performance

### Form Handling
1. React Hook Form manages form state and validation
2. Zod schemas validate data on both client and server
3. Server performs additional business rule validation
4. Success/error states are managed through toast notifications

### Search Implementation
1. Client sends search queries with minimum 2 characters
2. Server performs SQL LIKE queries across multiple product fields
3. Results are debounced and cached for performance
4. Real-time dropdown displays matching products

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL connection for serverless environments
- **sqlalchemy**: Python ORM for database access
- **@tanstack/react-query**: Server state management
- **react-hook-form**: Form state management
- **zod**: Runtime type validation

### UI Dependencies
- **@radix-ui/***: Accessible UI primitives
- **tailwindcss**: Utility-first CSS framework
- **lucide-react**: Icon library
- **date-fns**: Date manipulation utilities

### Development Dependencies
- **vite**: Build tool for bundling the frontend
- **typescript**: Type system
- **uvicorn**: Development server for FastAPI

## Deployment Strategy

### Development Environment
- **Client Command**: `npm run dev` – builds the React app in watch mode and runs the Express server.
- **API Command**: `uvicorn python_server.main:app --reload --host 0.0.0.0 --port 5001`
- **Database**: PostgreSQL connection via environment variable

### Production Build
 - **Client Build**: `vite build` – produces static assets served by Express
 - **API Build**: install Python modules from `requirements.txt`
 - **Client Start**: `npm start`
 - **API Start**: `gunicorn -k uvicorn.workers.UvicornWorker python_server.main:app`

### Platform Configuration
 - **Deployment Target**: Replit autoscale infrastructure
 - **Port Configuration**: Client service runs on port 3000 and the API service on port 5001
- **Environment**: Node.js 20, Python 3.11, and PostgreSQL 16 modules
- **Build Process**: Automated via Replit deployment configuration

### Database Management
- **Schema**: Managed through future Alembic migrations
- **Push Command**: `npm run db:push` - Applies schema changes
- **Connection**: Serverless PostgreSQL via DATABASE_URL environment variable

## Changelog

```
Changelog:
- June 15, 2025. Initial setup
```

## User Preferences

Preferred communication style: Simple, everyday language.