## Features

### Core Functionality

- **User Authentication**
- Secure signup, login, and logout
- JWT-based session management
- Password encryption with bcrypt
- **Product Management**
- Browse categorized product listings
- Search and filter functionality
- Detailed product views with images, descriptions, and pricing
- **Shopping Experience**
- Add/remove items to cart
- Adjust product quantities
- Cart persistence across sessions
- Order summary with pricing details
- **Responsive Design**
- Mobile-first approach with Tailwind CSS
- Modern UI components from Daisy UI
- Consistent experience across devices and screen sizes

## Technology Stack

### Frontend (Client)

- **Core Framework**: React with hooks and context API
- **Build Tool**: Vite (for faster development and optimized builds)
- **Styling**:
- Tailwind CSS for utility-first styling
- Daisy UI for pre-built component styling
- **State Management**: React Context API
- **API Communication**: Axios for RESTful requests
- **Routing**: React Router v6
- **Form Handling**: React Hook Form with Yup validation

### Backend (Server)

- **Runtime**: Node.js
- **API Framework**: Express.js
- **Database**:
- MongoDB for data storage
- Mongoose for object modeling
- **Authentication**:
- JWT (JSON Web Tokens)
- bcrypt for password hashing
- **Middleware**:
- CORS for cross-origin resource sharing
- Express Validator for request validation
- Multer for file uploads

### DevOps & Deployment

- **Version Control**: Git/GitHub
- **Frontend Hosting**: Vercel
- **Backend Hosting**: Heroku/Vercel
- **Database Hosting**: MongoDB Atlas
- **Environment Variables**: dotenv for configuration

## Getting Started

### Prerequisites

- Node.js (v14 or later)
- npm or yarn package manager
- MongoDB (local installation or MongoDB Atlas account)
- Git

### Installation & Setup

#### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/ecommerce-website.git
cd ecommerce-website
```

#### 2. Configure Environment Variables

Create `.env` files in both the client and backend directories:

**Backend (.env)**

```
# Server Configuration
PORT=5000
NODE_ENV=development

# MongoDB Connection
MONGO_URI=your_mongodb_connection_string

# Authentication
JWT_SECRET=your_secure_jwt_secret
JWT_EXPIRES_IN=7d

# Optional
CORS_ORIGIN=http://localhost:5173
```

**Client (.env)**

```
VITE_API_URL=http://localhost:5000/api
```

#### 3. Backend Setup

```bash
# Navigate to backend directory
cd backend

# Install dependencies
npm install

# Start development server
npm run dev

# Or for production
npm start
```

#### 4. Frontend Setup

```bash
# In a new terminal, navigate to client directory
cd client

# Install dependencies
npm install

# Start development server
npm run dev
```

### Access the Application

- **Frontend**: [http://localhost:5173](http://localhost:5173)
- **Backend API**: [http://localhost:5000/api](http://localhost:5000/api)

### Available Scripts

**Backend:**

- `npm start`: Start production server
- `npm run dev`: Start development server with nodemon
- `npm test`: Run tests

**Frontend:**

- `npm run dev`: Start development server
- `npm run build`: Build for production
- `npm run preview`: Preview production build
- `npm run lint`: Run ESLint

---

## API Documentation

### Authentication Endpoints

| Method   | Endpoint               | Description       | Request Body                | Response            |
| -------- | ---------------------- | ----------------- | --------------------------- | ------------------- |
| `POST` | `/api/auth/register` | Register new user | `{name, email, password}` | `{user, token}`   |
| `POST` | `/api/auth/login`    | Login user        | `{email, password}`       | `{user, token}`   |
| `POST` | `/api/auth/logout`   | Logout user       | -                           | `{success: true}` |
| `GET`  | `/api/auth/profile`  | Get user profile  | -                           | `{user}`          |

### Product Endpoints

| Method     | Endpoint                             | Description              | Request Body           | Response            |
| ---------- | ------------------------------------ | ------------------------ | ---------------------- | ------------------- |
| `GET`    | `/api/products`                    | Get all products         | -                      | `[{product}]`     |
| `GET`    | `/api/products/:id`                | Get single product       | -                      | `{product}`       |
| `GET`    | `/api/products/category/:category` | Get products by category | -                      | `[{product}]`     |
| `POST`   | `/api/products`                    | Create product (admin)   | `{name, price, ...}` | `{product}`       |
| `PUT`    | `/api/products/:id`                | Update product (admin)   | `{name, price, ...}` | `{product}`       |
| `DELETE` | `/api/products/:id`                | Delete product (admin)   | -                      | `{success: true}` |

### Cart Endpoints

| Method     | Endpoint              | Description      | Request Body              | Response   |
| ---------- | --------------------- | ---------------- | ------------------------- | ---------- |
| `GET`    | `/api/cart`         | Get user cart    | -                         | `{cart}` |
| `POST`   | `/api/cart`         | Add to cart      | `{productId, quantity}` | `{cart}` |
| `PUT`    | `/api/cart/:itemId` | Update cart item | `{quantity}`            | `{cart}` |
| `DELETE` | `/api/cart/:itemId` | Remove from cart | -                         | `{cart}` |

### Order Endpoints

| Method   | Endpoint            | Description       | Request Body                         | Response      |
| -------- | ------------------- | ----------------- | ------------------------------------ | ------------- |
| `POST` | `/api/orders`     | Create order      | `{shippingDetails, paymentMethod}` | `{order}`   |
| `GET`  | `/api/orders`     | Get user orders   | -                                    | `[{order}]` |
| `GET`  | `/api/orders/:id` | Get order details | -                                    | `{order}`   |

---

## Contribution

Contributions are welcome! If you'd like to improve this project, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature-name`).
5. Create a pull request.

---

## .env Example

Create a `.env` file in the `server` folder using the following format:

```plaintext
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret

```

## Folder Structure

```
ecommerce-website/
├── client/                   # Frontend code
│   ├── public/               # Static files
│   ├── src/
│   │   ├── assets/           # Images, fonts, etc.
│   │   ├── components/       # Reusable UI components
│   │   ├── contexts/         # React Context API states
│   │   ├── hooks/            # Custom React hooks
│   │   ├── pages/            # Page components
│   │   ├── services/         # API service modules
│   │   ├── utils/            # Helper functions
│   │   ├── App.jsx           # Root component
│   │   └── main.jsx          # Entry point
│   ├── .env                  # Environment variables
│   ├── vite.config.js        # Vite configuration
│   └── package.json          # Frontend dependencies
│
├── backend/                  # Backend code
│   ├── controllers/          # Request handlers
│   ├── database/             # Database configuration
│   ├── middlewares/          # Express middlewares
│   ├── model/                # Mongoose schemas
│   ├── routes/               # API endpoints
│   ├── utils/                # Utility functions
│   ├── index.js              # Entry point for the server
│   ├── .env                  # Environment variables
│   └── package.json          # Backend dependencies
│
├── .gitignore                # Git ignore file
├── README.md                 # Project documentation
```

---
