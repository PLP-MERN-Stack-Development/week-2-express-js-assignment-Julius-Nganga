# Product API

A RESTful API for managing products with Express.js

## Setup

1. Clone the repository
2. Run `npm install`
3. Create a `.env` file based on `.env.example`
4. Run `node server.js`

## API Endpoints

### Products

- `GET /api/products` - List all products
  - Query params:
    - `category` - Filter by category
    - `inStock` - Filter by stock status (true/false)
    - `page` - Page number for pagination
    - `limit` - Items per page
  - Example: `GET /api/products?category=electronics&page=1&limit=2`

- `GET /api/products/search?term=query` - Search products by name/description
  - Example: `GET /api/products/search?term=laptop`

- `GET /api/products/stats` - Get product statistics
  - Returns counts by category and stock status

- `GET /api/products/:id` - Get a specific product
  - Example: `GET /api/products/1`

- `POST /api/products` - Create a new product
  - Requires authentication (X-API-Key header)
  - Example body:
    ```json
    {
      "name": "New Product",
      "description": "Product description",
      "price": 99.99,
      "category": "category",
      "inStock": true
    }
    ```

- `PUT /api/products/:id` - Update a product
  - Requires authentication
  - Same body format as POST

- `DELETE /api/products/:id` - Delete a product
  - Requires authentication

## Authentication

Include `X-API-Key` header with valid API key for protected routes.

## Error Responses

All errors follow this format:
```json
{
  "error": {
    "name": "ErrorName",
    "message": "Error description",
    "statusCode": 400
  }
}