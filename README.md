# new-muslim-community# New Muslim Community - Microservices Platform

A comprehensive, cross-platform community platform for new Muslims, built with a modern microservices architecture. This platform provides educational content, community support, event management, and real-time communication features.

## 🌟 Project Overview

The New Muslim Community platform is designed to support new converts to Islam through:

- **Educational Resources**: Structured learning modules covering Islamic fundamentals
- **Community Support**: Real-time chat, mentorship, and peer support
- **Event Management**: Local mosque events and online sessions
- **Progress Tracking**: Personal learning journey and achievements
- **Cross-Platform Access**: iOS, Android, and Web applications

## 🏗️ Architecture

### Microservices Structure

```
New_Muslim_Community/
├── gateway/                     # API Gateway (Port 3000)
├── services/
│   ├── auth-service/           # Authentication & Authorization (Port 3001)
│   ├── user-service/           # User Management (Port 3002)
│   ├── learning-service/       # Educational Content (Port 3003)
│   ├── community-service/      # Social Features & Chat (Port 3004)
│   ├── event-service/          # Events & Calendar (Port 3005)
│   └── notification-service/   # Push Notifications (Port 3006)
├── frontend/                   # React Native + Expo App
├── shared/                     # Shared libraries and utilities
└── infrastructure/             # Docker and deployment configs
```

### Technology Stack

#### Backend Services
- **Runtime**: Node.js 18+ with Express.js
- **Database**: Firebase Firestore (NoSQL Document Store)
- **Authentication**: Firebase Auth + JWT
- **Real-time**: Socket.io for chat and live features
- **Caching**: Redis for session management and performance
- **Container**: Docker with docker-compose orchestration

#### Frontend Application
- **Framework**: React Native with Expo SDK 49
- **Language**: TypeScript for type safety
- **State Management**: Redux Toolkit with Redux Persist
- **Navigation**: React Navigation v6
- **UI Components**: React Native Paper (Material Design)
- **Real-time**: Socket.io client for live features

#### Infrastructure & DevOps
- **Containerization**: Docker and Docker Compose
- **API Gateway**: Express.js with http-proxy-middleware
- **Load Balancing**: Ready for horizontal scaling
- **Monitoring**: Health checks and logging
- **Security**: Helmet.js, CORS, rate limiting

## 🚀 Quick Start

### Prerequisites

Before running the application, ensure you have:

- **Node.js 18+** - [Download here](https://nodejs.org/)
- **Docker & Docker Compose** - [Download here](https://www.docker.com/)
- **Firebase Project** - [Create here](https://console.firebase.google.com/)
- **Expo CLI** - Install with `npm install -g @expo/cli`

### 1. Clone and Setup

```bash
# Clone the repository
git clone <repository-url>
cd New_Muslim_Community

# Install dependencies for all services
make install-deps
# OR manually:
# npm run install:all
```

### 2. Environment Configuration

```bash
# Copy environment template
cp .env.example .env

# Edit .env with your Firebase and other configurations
# Required configurations:
# - FIREBASE_PROJECT_ID
# - FIREBASE_ADMIN_PRIVATE_KEY
# - FIREBASE_ADMIN_CLIENT_EMAIL
# - JWT_SECRET
```

### 3. Start Backend Services

```bash
# Build and start all microservices
make build
make up

# Check service health
make health
```

### 4. Start Frontend Application

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Start Expo development server
npm start

# Run on specific platforms
npm run android    # Android emulator/device
npm run ios        # iOS simulator/device
npm run web        # Web browser
```

## 📋 Available Commands

### Project Management
```bash
make help          # Show all available commands
make install-deps  # Install dependencies for all services
make build         # Build all Docker services
make up            # Start all services in background
make down          # Stop all services
make logs          # View logs from all services
make clean         # Clean up containers and volumes
make health        # Check health of all services
```

### Development
```bash
make dev           # Start services in development mode
make test          # Run tests for all services
npm run lint       # Lint all code
npm run type-check # TypeScript type checking
```

### Frontend Specific
```bash
cd frontend
npm start          # Start Expo development server
npm run android    # Run on Android
npm run ios        # Run on iOS
npm run web        # Run on web browser
npm test           # Run frontend tests
```

## 🔧 Service Architecture

### API Gateway (Port 3000)
Central entry point that routes requests to appropriate microservices:
- **Route Management**: Intelligent request routing
- **Load Balancing**: Distributes traffic across service instances
- **Security**: CORS, rate limiting, and request validation
- **Monitoring**: Health checks and service discovery

### Authentication Service (Port 3001)
Handles user authentication and authorization:
- **User Registration**: New user signup with validation
- **Login/Logout**: Secure authentication with JWT tokens
- **Token Management**: Access and refresh token handling
- **Password Security**: Secure password hashing and reset

### Learning Service (Port 3003)
Manages educational content and progress tracking:
- **Module Management**: Structured learning modules
- **Progress Tracking**: Individual user progress monitoring
- **Achievement System**: Badges and milestone tracking
- **Content Delivery**: Optimized content serving

### Community Service (Port 3004)
Provides social features and real-time communication:
- **Group Management**: Community groups and membership
- **Real-time Chat**: Socket.io powered messaging
- **Content Moderation**: Automated and manual content filtering
- **User Interactions**: Social features and networking

## 🔐 Security Features

### Authentication & Authorization
- **JWT Tokens**: Secure stateless authentication
- **Refresh Tokens**: Long-lived token refresh mechanism
- **Role-Based Access**: User, mentor, moderator, and admin roles
- **Session Management**: Secure session handling with Redis

### API Security
- **Rate Limiting**: Prevent abuse with configurable limits
- **CORS Protection**: Cross-origin request security
- **Input Validation**: Comprehensive request validation
- **Security Headers**: Helmet.js security headers

### Data Protection
- **Firebase Security Rules**: Database-level security
- **Content Filtering**: Automated inappropriate content detection
- **Privacy Controls**: User privacy settings and data protection

## 📱 Frontend Features

### User Interface
- **Material Design**: Modern, accessible UI components
- **Islamic Theme**: Custom color scheme with Islamic green
- **Responsive Design**: Optimized for all screen sizes
- **Dark/Light Mode**: User preference support

### Cross-Platform Support
- **iOS**: Native iOS app through Expo
- **Android**: Native Android app through Expo
- **Web**: Progressive Web App (PWA) support
- **Unified Codebase**: Single codebase for all platforms

### Real-time Features
- **Live Chat**: Instant messaging with typing indicators
- **Push Notifications**: Native push notification support
- **Offline Support**: Offline functionality with data sync
- **Real-time Updates**: Live data updates across the app

## 🔄 Development Workflow

### Local Development

1. **Start Backend Services**:
   ```bash
   make dev  # Starts all services in development mode
   ```

2. **Start Frontend**:
   ```bash
   cd frontend
   npm start
   ```

3. **Access Services**:
   - API Gateway: http://localhost:3000
   - Frontend Web: http://localhost:19006
   - Individual service health checks available

### Testing

```bash
# Run all tests
make test

# Frontend tests
cd frontend && npm test

# Individual service tests
cd services/auth-service && npm test
```

### Code Quality

```bash
# Lint all code
npm run lint

# Fix linting issues
npm run lint:fix

# Type checking
npm run type-check
```

## 🚀 Deployment

### Docker Deployment

```bash
# Production build
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d

# Scale services
docker-compose up --scale community-service=3
```

### Mobile App Deployment

```bash
# Build for production
cd frontend

# Android
eas build --platform android

# iOS
eas build --platform ios

# Submit to stores
eas submit
```

## 📊 Monitoring & Logging

### Health Monitoring
- **Service Health**: Individual service health endpoints
- **API Gateway**: Central health monitoring
- **Database**: Firebase monitoring dashboard
- **Performance**: Request timing and throughput metrics

### Logging
- **Structured Logging**: JSON-formatted logs
- **Error Tracking**: Comprehensive error logging
- **Audit Trail**: User action logging
- **Debug Information**: Development-friendly logging

## 🤝 Contributing

### Code Standards
- **TypeScript**: Strict type checking enabled
- **ESLint**: Code quality and consistency
- **Prettier**: Code formatting
- **Conventional Commits**: Standardized commit messages

### Development Process
1. Fork the repository
2. Create a feature branch
3. Make your changes with tests
4. Run quality checks
5. Submit a pull request

## 📄 API Documentation

### Authentication Endpoints
```
POST /api/auth/register    # User registration
POST /api/auth/login       # User login
POST /api/auth/verify      # Token verification
POST /api/auth/refresh     # Refresh access token
POST /api/auth/logout      # User logout
```

### Learning Endpoints
```
GET  /api/learning/modules           # Get all modules
GET  /api/learning/modules/:id       # Get specific module
GET  /api/learning/lessons/:id       # Get lesson content
POST /api/learning/progress/lesson   # Update lesson progress
GET  /api/learning/progress          # Get user progress
```

### Community Endpoints
```
GET  /api/community/groups           # Get community groups
POST /api/community/groups/:id/join  # Join a group
GET  /api/community/groups/:id/messages # Get group messages
```

## 🔧 Configuration

### Environment Variables
```bash
# Firebase Configuration
FIREBASE_PROJECT_ID=your-project-id
FIREBASE_ADMIN_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----..."
FIREBASE_ADMIN_CLIENT_EMAIL=firebase-adminsdk-...@your-project.iam.gserviceaccount.com

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRE_TIME=7d

# Service Ports
GATEWAY_PORT=3000
AUTH_SERVICE_PORT=3001
LEARNING_SERVICE_PORT=3003
COMMUNITY_SERVICE_PORT=3004

# Redis Configuration
REDIS_URL=redis://localhost:6379
```

## 🎯 Roadmap

### Phase 1 (Current)
- ✅ Core microservices architecture
- ✅ Authentication and user management
- ✅ Learning content management
- ✅ Real-time community features
- ✅ Cross-platform mobile app

### Phase 2 (Next)
- 🔄 Event management service
- 🔄 Notification service
- 🔄 Advanced progress analytics
- 🔄 Mentorship matching system
- 🔄 Content creation tools

### Phase 3 (Future)
- 📋 AI-powered learning recommendations
- 📋 Multi-language support
- 📋 Advanced community moderation
- 📋 Offline-first mobile experience
- 📋 Integration with mosque systems

## 📞 Support

### Getting Help
- **Documentation**: Comprehensive guides and API docs
- **Issues**: GitHub issue tracker for bugs and features
- **Community**: Community discussions and support
- **Email**: Direct support for critical issues

### Common Issues
1. **Firebase Setup**: Ensure all Firebase credentials are correctly configured
2. **Port Conflicts**: Check that required ports (3000-3006) are available
3. **Docker Issues**: Ensure Docker is running and has sufficient resources
4. **Mobile Development**: Install Expo CLI and ensure mobile development setup

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Firebase**: For providing excellent backend-as-a-service
- **Expo**: For simplifying React Native development
- **React Native Community**: For amazing open-source packages
- **Islamic Community**: For inspiration and guidance

---

**Built with ❤️ for the Muslim community**

*May Allah bless this project and make it beneficial for all Muslims, especially those new to Islam.*
