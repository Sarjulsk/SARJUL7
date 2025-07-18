# Smart Village Management System

## Overview

This is a full-stack web application built to digitally manage a village's residents, resources, and activities. It combines social platform functionality with administrative tools for transparent community management. The system serves as a centralized platform for village activities, resident profiles, event management, donation tracking, and content sharing.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a modern full-stack architecture with clear separation between client and server responsibilities:

### Frontend Architecture
- **Framework**: React 18 with TypeScript and Vite for build tooling
- **UI Framework**: Shadcn/UI components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom CSS variables for theming
- **State Management**: TanStack Query (React Query) for server state management
- **Routing**: Wouter for lightweight client-side routing
- **Forms**: React Hook Form with Zod validation
- **Authentication**: Context-based auth provider with protected routes

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **Authentication**: Passport.js with local strategy and session-based auth
- **Session Storage**: PostgreSQL-backed sessions using connect-pg-simple
- **API Design**: RESTful endpoints with JSON responses
- **Security**: CSRF protection, secure session handling, admin role-based access

### Database Architecture
- **Database**: PostgreSQL with Neon serverless driver
- **ORM**: Drizzle ORM with schema-first approach
- **Schema Location**: Shared between client and server (`shared/schema.ts`)
- **Migrations**: Drizzle Kit for schema migrations

## Key Components

### Authentication System
- Flexible authentication supporting both username and Gmail/email login
- Session-based authentication using express-session
- Protected routes that redirect unauthenticated users
- Secure password hashing using Node.js crypto module
- Admin role-based access control for sensitive operations
- Email-based registration with Gmail support for village residents
- Multiple login methods: username, email, or Gmail address

### Resident Management
- Comprehensive resident profiles with personal and family details
- Location tracking for migration data
- Admin approval system for new registrations
- Search and filtering capabilities by name, occupation, and area
- Profile creation available to all users, approval required by admin

### Event & News Management
- Admin-created events with categories (wedding, meeting, health, etc.)
- Event scheduling with date, location, and descriptions
- News posting system for village announcements
- Active/inactive status management for content

### Donation & Fund Transparency
- Donation tracking with donor information and purposes
- Anonymous donation support
- Fund utilization tracking with proof documents
- Financial transparency reports with real-time calculations
- Admin-only access for financial data management

### Gallery System
- User-submitted photos and videos of village events
- Category-based organization (events, festivals, development, community)
- Admin approval required before content goes live
- Like functionality for approved content
- Upload interface for community contributions

### Settings Management
- Configurable helpline information (phone and email)
- Admin-controlled system settings
- Village-specific customization options

## Data Flow

1. **User Registration**: Users submit resident profiles → Admin approval required → Profile becomes visible
2. **Content Upload**: Users upload gallery items → Admin moderation → Approved content appears publicly
3. **Event Creation**: Admin creates events → Immediately visible to all users
4. **Donation Process**: Admin records donations → Automatically included in transparency reports
5. **Fund Utilization**: Admin logs expenses with proof → Real-time fund balance updates

## External Dependencies

### Production Dependencies
- **UI Components**: Extensive Radix UI component library for accessible UI primitives
- **Database**: Neon serverless PostgreSQL with WebSocket support
- **Authentication**: Passport.js ecosystem for secure login handling
- **Validation**: Zod for runtime type checking and form validation
- **Date Handling**: date-fns for date formatting and manipulation
- **Styling**: Tailwind CSS with class-variance-authority for component variants

### Development Dependencies
- **Build Tools**: Vite with React plugin and TypeScript support
- **Code Quality**: TypeScript for type safety
- **Development Experience**: Replit-specific plugins for enhanced development

## Deployment Strategy

### Development Environment
- Vite dev server with HMR (Hot Module Replacement)
- Express server with TypeScript compilation via tsx
- Environment variables for database connection
- Replit-specific development tooling integration

### Production Build
- Frontend: Vite build outputting to `dist/public`
- Backend: ESBuild compilation of server code to `dist/index.js`
- Single deployment artifact with static file serving
- Session persistence through PostgreSQL store
- Environment-based configuration for database connections

### Database Management
- Schema definitions in shared TypeScript files
- Drizzle migrations for schema updates
- Connection pooling through Neon's serverless driver
- Automatic database provisioning requirement check

The application is designed as a monolithic deployment with clear internal boundaries, making it suitable for small to medium village communities while maintaining professional development practices and security standards.