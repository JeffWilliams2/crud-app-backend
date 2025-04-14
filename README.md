# REST API

A RESTful CRUD API built with Node.js, Express, and MongoDB that allows users to manage store product data through standard HTTP methods. This project demonstrates the fundamentals of building a backend API with the MERN stack.

## Features

- **Complete CRUD Operations**:
  - Create new products
  - Retrieve all products or a specific product by ID
  - Update existing products
  - Delete products

- **MongoDB Integration**: Store product data persistently with proper schema validation
- **RESTful Architecture**: Follow REST principles with appropriate HTTP methods and status codes
- **Error Handling**: Robust error handling with appropriate status codes
- **Middleware**: Express middleware for parsing JSON and URL-encoded data

## Tech Stack

- **Node.js**: JavaScript runtime environment
- **Express.js**: Web application framework for Node.js
- **MongoDB**: NoSQL database
- **Mongoose**: MongoDB object modeling for Node.js
- **dotenv**: Environment variable management

## API Endpoints

| Method | Endpoint | Description | Status Codes |
|--------|----------|-------------|-------------|
| GET | /api/products | Retrieve all products | 200 OK |
| GET | /api/products/:id | Retrieve a specific product by ID | 200 OK, 500 Error |
| POST | /api/products | Create a new product | 200 OK, 500 Error |
| PUT | /api/products/:id | Update an existing product | 200 OK, 404 Not Found, 500 Error |
| DELETE | /api/products/:id | Delete a product | 200 OK, 404 Not Found, 500 Error |

The root endpoint (`/`) returns a "Hello from Node API Server!" message to confirm the server is running.

## Product Schema

```javascript
{
  name: {
    type: String,
    required: [true, "Please enter a product name"]
  },
  quantity: {
    type: Number,
    required: true,
    default: 0
  },
  price: {
    type: Number,
    required: true,
    default: 0
  },
  image: {
    type: String,
    required: false
  },
  timestamps: true  // Automatically adds createdAt and updatedAt fields
}
```

The schema includes automatic timestamps tracking when products are created or modified.

## Getting Started

### Prerequisites

- Node.js (v14.x or higher)
- MongoDB (local or MongoDB Atlas account)
- npm or yarn package manager

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/JeffWilliams2/crud-app-backend.git
   cd crud-app-backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory with the following:
   ```
   MONGODB_URI=your_mongodb_connection_string
   PORT=3000
   ```

4. Start the server:
   ```bash
   npm start
   ```

5. The API will be available at `http://localhost:3000`

## Testing the API

You can test the API using tools like:
- Postman
- Thunder Client (VS Code extension)
- Insomnia

### Example Requests

#### Create a Product
```
POST /api/products
Content-Type: application/json

{
  "name": "Sample Product",
  "quantity": 10,
  "price": 29.99,
  "image": "image_url.jpg"
}
```

#### Get All Products
```
GET /api/products
```

#### Get Product by ID
```
GET /api/products/60f1a7b9e6b3a50015c9a1a3
```

#### Update a Product
```
PUT /api/products/60f1a7b9e6b3a50015c9a1a3
Content-Type: application/json

{
  "name": "Product Name",
  "price": 39.99
}
```

#### Delete a Product
```
DELETE /api/products/60f1a7b9e6b3a50015c9a1a3
```

## Project Structure

```
crud-app-backend/
├── controllers/
│   └── product.controller.js
├── models/
│   └── product.model.js
├── routes/
│   └── product.route.js
├── .env
├── .gitignore
├── index.js
├── package.json
└── README.md
```

## Database Connection

This project uses MongoDB Atlas as the database service. The connection is established in `index.js` using Mongoose:

```javascript
mongoose
  .connect(process.env.MONGODB_URI)
  .then(() => {
    console.log("Connected to database!");
    app.listen(3000, () => {
      console.log('Server is running on port 3000');
    });
  })
  .catch(() => {
    console.log("Connection failed!");
  });
```

## Future Improvements

- Add user authentication and authorization
- Add pagination for GET requests
- Implement sorting and filtering options
- Add unit/integration tests
- Set up CI/CD pipeline
- Add image upload functionality for product images

## License

[MIT](LICENSE)

## Acknowledgements

This project was built as an exercise for backend dev with Node.js, Express, and MongoDB.

## What I Learned

Through building this REST API project, I gained practical experience in:

- **Backend Architecture**: Designing and implementing a Node.js application with proper separation (routes, controllers, models)
- **RESTful API Design**: Creating endpoints that follow REST principles and standard HTTP methods 
- **Database Integration**: Working with MongoDB through Mongoose including:
  - Schema design and validation
  - CRUD operations
  - Data modeling
- **Asynchronous JavaScript**: Using async/await syntax for database operations and API responses
- **Error Handling**: Implementing comprehensive error handling with appropriate HTTP status codes
- **Environment Configuration**: Setting up environment variables with dotenv for secure configuration
- **API Testing**: Testing endpoints with Insomnia and validating.
- **Database Management**: Using MongoDB Atlas cloud database service
- **Middleware Implementation**: Configuring Express middleware for parsing requests, handling CORS, etc.
