## Online Marketplace API Documentation

This API documentation provides details on the endpoints and functionality of the Online Marketplace system.

### User API

#### 1. User Registration

- **Endpoint:** `/api/user/register`
- **Method:** POST
- **Description:** Registers a new user in the marketplace.
- **Request Body:**
  ```json
  {
    "username": "example_user",
    "email": "user@example.com",
    "password": "password123"
  }
  ```
- **Response:**
  - Status: 201 Created
  - Body: 
    ```json
    {
      "message": "User registered successfully",
      "user_id": "user_id_here"
    }
    ```

#### 2. User Login

- **Endpoint:** `/api/user/login`
- **Method:** POST
- **Description:** Logs in an existing user.
- **Request Body:**
  ```json
  {
    "email": "user@example.com",
    "password": "password123"
  }
  ```
- **Response:**
  - Status: 200 OK
  - Body: 
    ```json
    {
      "message": "Login successful",
      "user_id": "user_id_here",
      "token": "auth_token_here"
    }
    ```

#### 3. User Profile

- **Endpoint:** `/api/user/profile`
- **Method:** GET
- **Description:** Retrieves user profile information.
- **Authorization Header:** Bearer Token
- **Response:**
  - Status: 200 OK
  - Body:
    ```json
    {
      "username": "example_user",
      "email": "user@example.com",
      "location": "user_location_here"
    }
    ```

### Product API

#### 1. Create Product Listing

- **Endpoint:** `/api/product/create`
- **Method:** POST
- **Description:** Allows users to create a new product listing.
- **Authorization Header:** Bearer Token
- **Request Body:**
  ```json
  {
    "title": "Product Title",
    "description": "Product Description",
    "price": 50.99,
    "category": "Product Category",
    "location": "Product Location"
  }
  ```
- **Response:**
  - Status: 201 Created
  - Body: 
    ```json
    {
      "message": "Product listed successfully",
      "product_id": "product_id_here"
    }
    ```

#### 2. Get Product Details

- **Endpoint:** `/api/product/:product_id`
- **Method:** GET
- **Description:** Retrieves detailed information about a specific product.
- **Response:**
  - Status: 200 OK
  - Body:
    ```json
    {
      "title": "Product Title",
      "description": "Product Description",
      "price": 50.99,
      "category": "Product Category",
      "location": "Product Location",
      "seller": "Seller Username"
    }
    ```

#### 3. Update Product Listing

- **Endpoint:** `/api/product/:product_id/update`
- **Method:** PUT
- **Description:** Allows users to update an existing product listing.
- **Authorization Header:** Bearer Token
- **Request Body:**
  ```json
  {
    "title": "New Product Title",
    "price": 60.99
  }
  ```
- **Response:**
  - Status: 200 OK
  - Body: 
    ```json
    {
      "message": "Product updated successfully"
    }
    ```

### Search and Filter API

#### 1. Search Products

- **Endpoint:** `/api/search`
- **Method:** GET
- **Description:** Allows users to search for products based on various criteria.
- **Query Parameters:**
  - `category`: Product category
  - `location`: Product location
  - `min_price`: Minimum price
  - `max_price`: Maximum price
- **Response:**
  - Status: 200 OK
  - Body:
    ```json
    [
      {
        "title": "Product Title",
        "description": "Product Description",
        "price": 50.99,
        "category": "Product Category",
        "location": "Product Location",
        "seller": "Seller Username"
      },
      ...
    ]
    ```

### Transaction API

#### 1. Purchase Product

- **Endpoint:** `/api/transaction/purchase/:product_id`
- **Method:** POST
- **Description:** Allows users to purchase a product.
- **Authorization Header:** Bearer Token
- **Response:**
  - Status: 200 OK
  - Body: 
    ```json
    {
      "message": "Purchase successful"
    }
    ```

### Admin API

#### 1. Manage Listings

- **Endpoint:** `/api/admin/listings`
- **Method:** GET
- **Description:** Retrieves all product listings.
- **Authorization Header:** Bearer Token (Admin)
- **Response:**
  - Status: 200 OK
  - Body:
    ```json
    [
      {
        "title": "Product Title",
        "description": "Product Description",
        "price": 50.99,
        "category": "Product Category",
        "location": "Product Location",
        "seller": "Seller Username"
      },
      ...
    ]
    ```

#### 2. Manage Users

- **Endpoint:** `/api/admin/users`
- **Method:** GET
- **Description:** Retrieves all user profiles.
- **Authorization Header:** Bearer Token (Admin)
- **Response:**
  - Status: 200 OK
  - Body:
    ```json
    [
      {
        "username": "example_user",
        "email": "user@example.com",
        "location": "user_location_here"
      },
      ...
    ]
    ```

#### 3. Manage Transactions

- **Endpoint:** `/api/admin/transactions`
- **Method:** GET
- **Description:** Retrieves all transaction records.
- **Authorization Header:** Bearer Token (Admin)
- **Response:**
  - Status: 200 OK
  - Body:
    ```json
    [
      {
        "transaction_id": "transaction_id_here",
        "buyer": "Buyer Username",
        "seller": "Seller Username",
        "product": "Product Title",
        "amount": 50.99,
        "timestamp": "timestamp_here"
      },
      ...
    ]
    ```

### Authentication

- Authentication is implemented using JWT (JSON Web Tokens). Users receive a token upon successful login, which they include in the Authorization header for subsequent requests.
- Admin authentication is also JWT-based, with a separate token issued for administrative tasks.

### Error Handling

- Errors are returned with appropriate HTTP status codes and error messages in JSON format.
- Example: 
  ```json
  {
    "error": "Invalid credentials"
  }
  ```

### Security

- All endpoints requiring authentication are secured using JWT tokens.
- Sensitive data is encrypted before storage.
- HTTPS protocol is enforced for all communication.

This concludes the API documentation for the Online Marketplace system. For any further inquiries or issues, please contact the system administrator.
