# Overview

أشغال (Ashghal) is a field services management application built for the Arabic market, specifically designed to connect users with certified contractors for home maintenance and repair services. The application is structured as a modern React-based web platform that facilitates service requests, contractor management, and real-time service coordination.

The application serves three primary user roles: regular users who request services, workers/contractors who provide services, and administrators who manage the platform. The core functionality revolves around a service marketplace where users can create service requests, contractors can accept and fulfill them, and administrators can oversee the entire operation.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture

The frontend is built using React 18 with TypeScript and Vite as the build tool. The application uses a component-based architecture with clear separation of concerns:

- **Routing**: Uses Wouter for client-side navigation, providing lightweight routing without the complexity of React Router
- **State Management**: Combines React Context API for global state (authentication, requests) with TanStack Query for server state management
- **UI Framework**: Built with Tailwind CSS for utility-first styling and Shadcn/UI components for consistent, accessible UI elements
- **Internationalization**: Fully supports Arabic language with RTL (right-to-left) layout as the default configuration

The application follows a page-based routing structure with protected routes using role-based guards. Components are organized into logical groups (Auth, Layout, Requests, UI) with reusable components following the compound component pattern.

## Backend Architecture

The current architecture is primarily client-side with minimal backend Express server serving static files and handling development middleware. The backend is intentionally lightweight as Firebase handles most server-side operations directly from the client.

The Express server configuration includes:
- Development-only Vite middleware for HMR (Hot Module Replacement)
- Static file serving for production builds
- Basic request logging and error handling

## Authentication & Authorization

The application uses Firebase Authentication with email/password authentication. User roles are stored in Firestore and managed through a custom AuthContext:

- **Role-based Access Control**: Three distinct roles (user, worker, admin) with different permissions
- **Protected Routes**: RoleGuard component ensures users can only access appropriate sections
- **Session Management**: Firebase handles session persistence and token management automatically

User profiles are stored in a separate Firestore collection with extended metadata beyond what Firebase Auth provides.

## Data Management

The application uses Firebase Firestore as the primary database with the following collections:

- **users**: Extended user profiles with role information
- **requests**: Service requests with full lifecycle tracking
- **ratings**: User feedback system (designed but not fully implemented)

Real-time data synchronization is achieved through Firestore's onSnapshot listeners, ensuring all users see live updates. The RequestsContext manages complex state transitions for service requests.

## File Storage

Firebase Storage handles image uploads for service requests. The system supports multiple image uploads per request with automatic resizing and optimization handled client-side before upload.

## UI/UX Design Decisions

The interface uses a mobile-first responsive design with RTL support built-in. The design system is based on:

- **Arabic Typography**: Uses Noto Sans Arabic font for optimal Arabic text rendering
- **Color System**: Custom CSS variables allowing for easy theming
- **Component Library**: Shadcn/UI provides accessible, customizable components
- **Icon System**: Font Awesome for consistent iconography throughout the application

The layout follows a dashboard pattern with sidebar navigation and contextual top bars, adapting to mobile with collapsible menus.

## Development Architecture

The project uses modern development tools and practices:

- **TypeScript**: Provides type safety across the entire application
- **Build System**: Vite for fast development and optimized production builds
- **Code Organization**: Clear separation between client, server, and shared code
- **Asset Management**: Vite handles asset optimization and bundling

The configuration supports both development and production environments with appropriate optimizations for each.

# External Dependencies

## Firebase Services
- **Firebase Authentication**: User authentication and session management
- **Firestore Database**: Real-time NoSQL database for application data
- **Firebase Storage**: File storage for images and documents
- **Firebase Hosting**: Planned for production deployment (not currently configured)

## Frontend Libraries
- **React & React DOM**: Core UI framework (v18+)
- **TypeScript**: Type safety and developer experience
- **Vite**: Build tool and development server
- **Wouter**: Lightweight client-side routing
- **TanStack Query**: Server state management and caching
- **Tailwind CSS**: Utility-first CSS framework

## UI Component Libraries
- **Radix UI**: Unstyled, accessible UI primitives
- **Shadcn/UI**: Pre-styled components built on Radix UI
- **Lucide Icons**: Modern icon library
- **Font Awesome**: Additional icon library for Arabic-friendly icons

## Development Tools
- **ESBuild**: Fast JavaScript/TypeScript bundler for server code
- **PostCSS**: CSS processing with Tailwind CSS
- **Autoprefixer**: CSS vendor prefixing

## Third-party Services
- **Google Fonts**: Arabic font hosting (Noto Sans Arabic)
- **Replit Integration**: Development environment integration with runtime error handling

The application is designed to be database-agnostic through its use of Firebase, but could potentially be migrated to use PostgreSQL with Drizzle ORM based on the existing configuration files, though this is not currently implemented.