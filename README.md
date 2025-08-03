# Inventory Management System - Backend

This is the backend API for the Inventory Management System.

## Features
- RESTful API for inventory management
- MongoDB database integration
- CORS enabled for frontend communication
- Environment variable configuration

## Prerequisites
- Node.js (v14 or higher)
- MongoDB database (local or cloud)
- npm package manager

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
```

2. Navigate to the project directory:
```bash
cd inventory-management-backend
```

3. Install dependencies:
```bash
npm install
```

4. Configure environment variables:
- Rename `.env.example` to `.env`
- Update `MONGODB_URI` with your MongoDB connection string
- Set `PORT` to your preferred port (default is 3000)

## Usage

### Development Mode
```bash
npm run dev
```

### Production Mode
```bash
npm start
```

## API Endpoints

### Get all items
GET `/api/items`

### Get item by ID
GET `/api/items/:id`

### Create new item
POST `/api/items`
Body:
```json
{
  "name": "Item Name",
  "category": "Item Category",
  "quantity": 10,
  "location": "Storage Location",
  "description": "Item Description"
}
```

### Update item
PUT `/api/items/:id`
Body:
```json
{
  "name": "Updated Item Name",
  "category": "Updated Category",
  "quantity": 15,
  "location": "New Location",
  "description": "Updated Description"
}
```

### Delete item
DELETE `/api/items/:id`

## Deployment

### MongoDB Atlas Setup
1. Create a MongoDB Atlas account at https://www.mongodb.com/cloud/atlas
2. Create a new cluster
3. Create a database user
4. Add your IP address to the IP whitelist (or allow access from anywhere for development)
5. Get the connection string and replace in `.env` file

### Railway Deployment
1. Create a Railway account at https://railway.app/
2. Create a new project
3. Connect your GitHub repository or upload your code
4. Add environment variables in Railway dashboard
5. Railway will automatically deploy your application

## Environment Variables
- `MONGODB_URI`: MongoDB connection string
- `PORT`: Server port (default: 3000)

## License
MIT
