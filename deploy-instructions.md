# Deployment Instructions for Inventory Management System

This document provides step-by-step instructions for deploying the backend and frontend of the Inventory Management System.

## Prerequisites

1. Node.js (v14 or higher)
2. MongoDB Atlas account (free tier available)
3. Railway account (free tier available)
4. GitHub account (optional but recommended)

## Backend Deployment

### 1. MongoDB Atlas Setup

1. Create a MongoDB Atlas account at https://www.mongodb.com/cloud/atlas
2. Create a new cluster (select the free tier)
3. Create a database user:
   - Go to "Database Access" in the left sidebar
   - Click "Add New Database User"
   - Enter a username and password
   - Select "Atlas Admin" for user privileges
4. Configure network access:
   - Go to "Network Access" in the left sidebar
   - Click "Add IP Address"
   - For development, you can add "0.0.0.0/0" to allow access from anywhere
   - For production, add your specific IP addresses
5. Get your connection string:
   - Go to "Clusters" in the left sidebar
   - Click "Connect" on your cluster
   - Select "Connect your application"
   - Copy the connection string and replace `<password>` with your database user password

### 2. Railway Deployment

1. Create a Railway account at https://railway.app/
2. Create a new project:
   - Click "New Project"
   - Select "Deploy from GitHub" if you have a repository, or "Deploy from Source" to upload files directly
3. If deploying from source:
   - Upload the following files:
     - `server.js`
     - `package.json`
     - `.env` (with your MongoDB connection string)
   - Railway will automatically detect this is a Node.js application
4. Set environment variables:
   - Go to your project settings
   - Click "Variables"
   - Add the following variables:
     - `MONGODB_URI`: Your MongoDB connection string
     - `PORT`: 3000 (or any port you prefer)
5. Railway will automatically deploy your application and provide a URL

### 3. Testing the Backend

1. After deployment, Railway will provide a URL for your backend API
2. You can test the API endpoints using curl or a tool like Postman:
   - GET `https://your-railway-url.up.railway.app/api/items` (get all items)
   - POST `https://your-railway-url.up.railway.app/api/items` (create new item)
   - PUT `https://your-railway-url.up.railway.app/api/items/:id` (update item)
   - DELETE `https://your-railway-url.up.railway.app/api/items/:id` (delete item)

## Frontend Deployment

### 1. Update API URL

1. Open `index.html` in a text editor
2. Find the line `const API_BASE_URL = 'http://localhost:3000/api';`
3. Replace `http://localhost:3000/api` with your Railway backend URL (e.g., `https://your-railway-url.up.railway.app/api`)

### 2. Deploy to Netlify

1. If you haven't already, create a Netlify account at https://www.netlify.com/
2. Deploy the frontend:
   - Go to your Netlify dashboard
   - Click "New site from Git" if you have a repository
   - Or drag and drop your project folder (containing index.html and image files) to deploy manually
3. Update environment variables if needed:
   - Go to your site settings
   - Click "Environment variables"
   - Add any necessary variables

## Connecting Frontend and Backend

1. After deploying both frontend and backend, make sure the frontend is pointing to the correct backend URL
2. Test the connection by:
   - Opening your frontend URL in a browser
   - Logging in with the default credentials (username: 80907793, password: 80907793)
   - Adding a new item to the inventory
   - Refreshing the page to verify the item persists

## Troubleshooting

### Common Issues

1. **CORS errors**: Make sure your backend has CORS enabled (it's already configured in server.js)
2. **Connection errors**: Verify your MongoDB connection string is correct and your IP is whitelisted
3. **404 errors**: Check that your API endpoints are correct in the frontend code

### Checking Logs

1. **Railway logs**: In your Railway project, you can view application logs in real-time
2. **Netlify logs**: In your Netlify site dashboard, you can view deploy logs and function logs

## Updating the Application

To update your application:

1. Make changes to your code
2. Commit and push to your GitHub repository (if using Git)
3. Railway will automatically redeploy when you push to GitHub
4. For Netlify, it will also automatically redeploy when you push to GitHub

## Security Considerations

1. For production use:
   - Use environment variables for sensitive information
   - Implement proper user authentication and authorization
   - Use HTTPS for all communications
   - Regularly update dependencies
   - Implement rate limiting and other security measures

## Support

If you encounter any issues during deployment, please check:
1. All environment variables are correctly set
2. Network access is properly configured
3. Dependencies are correctly installed
4. The application works locally before deploying
