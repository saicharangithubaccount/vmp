# E-commerce Platform

A comprehensive full-stack e-commerce platform built with modern technologies including React 18, Node.js, Express.js, and PostgreSQL.

## 🚀 Features

- **Modern Frontend**: React 18 with Vite for fast development
- **State Management**: Redux Toolkit with Redux-Saga for async operations
- **UI Components**: Ant Design with Tailwind CSS for beautiful, responsive design
- **Authentication**: JWT-based authentication with secure password hashing
- **Database**: PostgreSQL with Sequelize ORM for robust data management
- **API**: RESTful API with comprehensive error handling and validation
- **Security**: Helmet, CORS, rate limiting, and input validation
- **File Uploads**: Multer for handling product images and documents
- **Email**: Nodemailer for notifications and password resets

## 🛠 Tech Stack

### Frontend
- **React 18** with Vite for fast development and building
- **Redux Toolkit** for predictable state management
- **Redux-Saga** for handling side effects and async operations
- **React Router v6** for client-side routing
- **Ant Design (antd)** for professional UI components
- **Tailwind CSS** for custom styling and responsive design
- **Axios** for HTTP client with interceptors
- **TypeScript** for type safety

### Backend
- **Node.js** with Express.js framework
- **PostgreSQL** database with connection pooling
- **Sequelize ORM** for database operations and migrations
- **JWT** authentication with bcrypt password hashing
- **Express middleware** for validation, error handling, and security
- **Multer** for file uploads and image handling
- **Nodemailer** for email notifications
- **Joi** for request validation
- **TypeScript** for type safety

## 📁 Project Structure

```
/ecommerce-platform
├── /client                    # React frontend application
│   ├── /src
│   │   ├── /components        # Reusable UI components
│   │   ├── /pages            # Page components
│   │   ├── /redux            # Redux store and logic
│   │   │   ├── /slices        # Redux Toolkit slices
│   │   │   └── /sagas         # Redux-Saga effects
│   │   ├── /services         # API service layer
│   │   ├── /utils            # Utility functions
│   │   └── /assets           # Static assets
│   ├── package.json
│   ├── vite.config.ts
│   └── tailwind.config.js
├── /server                    # Express.js backend API
│   ├── /src
│   │   ├── /config           # Configuration files
│   │   ├── /controllers      # Route controllers
│   │   ├── /models           # Sequelize models
│   │   ├── /routes           # API routes
│   │   ├── /middleware       # Express middleware
│   │   ├── /services         # Business logic services
│   │   └── /utils            # Utility functions
│   ├── package.json
│   └── tsconfig.json
├── package.json              # Root package.json
├── setup.sh                  # Setup script for Unix/Linux
├── setup.bat                 # Setup script for Windows
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- **Node.js** (v18 or higher)
- **PostgreSQL** (v13 or higher)
- **npm** or **yarn**

### Quick Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd ecommerce-platform
   ```

2. **Run the setup script**
   
   For Unix/Linux/macOS:
   ```bash
   chmod +x setup.sh
   ./setup.sh
   ```
   
   For Windows:
   ```cmd
   setup.bat
   ```

3. **Configure environment variables**
   
   Update the following files with your configuration:
   - `client/.env` - Frontend configuration
   - `server/.env` - Backend configuration (database, JWT secret, etc.)

4. **Set up PostgreSQL database**
   ```sql
   CREATE DATABASE ecommerce_db;
   ```

5. **Start the development servers**
   ```bash
   npm run dev
   ```

### Manual Setup

If you prefer to set up manually:

1. **Install dependencies**
   ```bash
   npm run install:all
   ```

2. **Set up environment files**
   ```bash
   cp client/env.example client/.env
   cp server/env.example server/.env
   ```

3. **Configure your environment variables**
   - Update database credentials in `server/.env`
   - Set JWT secret in `server/.env`
   - Configure email settings if needed

4. **Start development servers**
   ```bash
   npm run dev
   ```

## 🔧 Available Scripts

### Root Level
- `npm run dev` - Start both client and server in development mode
- `npm run build` - Build the client for production
- `npm start` - Start the production server
- `npm run install:all` - Install dependencies for both client and server

### Client Scripts
- `npm run dev` - Start Vite development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

### Server Scripts
- `npm run dev` - Start with nodemon (development)
- `npm run build` - Compile TypeScript
- `npm start` - Start production server
- `npm run lint` - Run ESLint
- `npm test` - Run tests

## 🌐 API Endpoints

### Authentication
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `GET /api/auth/profile` - Get user profile
- `PUT /api/auth/profile` - Update user profile

### Products
- `GET /api/products` - Get products with filtering
- `GET /api/products/featured` - Get featured products
- `GET /api/products/categories` - Get product categories
- `GET /api/products/search` - Search products
- `GET /api/products/:id` - Get product by ID

### Cart
- `GET /api/cart` - Get user's cart
- `POST /api/cart` - Add item to cart
- `PUT /api/cart/:productId` - Update cart item quantity
- `DELETE /api/cart/:productId` - Remove item from cart
- `POST /api/cart/checkout` - Process checkout

### User
- `GET /api/user/orders` - Get user's orders
- `GET /api/user/orders/:id` - Get order by ID
- `PUT /api/user/preferences` - Update user preferences

## 🔒 Security Features

- **JWT Authentication** with secure token handling
- **Password Hashing** using bcrypt
- **CORS** configuration for cross-origin requests
- **Helmet** for security headers
- **Rate Limiting** to prevent abuse
- **Input Validation** using Joi schemas
- **SQL Injection Protection** via Sequelize ORM
- **XSS Protection** with proper data sanitization

## 📊 Database Schema

### Users Table
- `id` (UUID, Primary Key)
- `email` (String, Unique)
- `password` (String, Hashed)
- `firstName` (String)
- `lastName` (String)
- `role` (Enum: user, admin)
- `isActive` (Boolean)
- `emailVerified` (Boolean)
- Profile fields (phone, address, etc.)
- `preferences` (JSONB)

### Products Table
- `id` (UUID, Primary Key)
- `name` (String)
- `description` (Text)
- `price` (Decimal)
- `image` (String)
- `category` (String)
- `stock` (Integer)
- `rating` (Decimal)
- `reviews` (Integer)
- `isActive` (Boolean)
- `isFeatured` (Boolean)

### Cart Items Table
- `id` (UUID, Primary Key)
- `userId` (UUID, Foreign Key)
- `productId` (UUID, Foreign Key)
- `quantity` (Integer)

### Orders Table
- `id` (UUID, Primary Key)
- `userId` (UUID, Foreign Key)
- `total` (Decimal)
- `status` (Enum)
- `shippingAddress` (JSONB)
- `paymentMethod` (String)
- `paymentStatus` (Enum)

## 🚀 Deployment

### Production Build

1. **Build the client**
   ```bash
   cd client
   npm run build
   ```

2. **Build the server**
   ```bash
   cd server
   npm run build
   ```

3. **Set production environment variables**
   - Update `NODE_ENV=production`
   - Configure production database
   - Set secure JWT secrets
   - Configure email service

4. **Start production server**
   ```bash
   npm start
   ```

### Docker Deployment (Optional)

Create Dockerfiles for both client and server for containerized deployment.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/your-repo/issues) page
2. Create a new issue with detailed information
3. Contact the development team

## 🔮 Future Enhancements

- [ ] Payment integration (Stripe, PayPal)
- [ ] Real-time notifications
- [ ] Advanced search and filtering
- [ ] Product reviews and ratings
- [ ] Inventory management
- [ ] Admin dashboard
- [ ] Mobile app (React Native)
- [ ] Microservices architecture
- [ ] Redis caching
- [ ] Elasticsearch integration
