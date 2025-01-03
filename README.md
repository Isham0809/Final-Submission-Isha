# Admin Panel Project Documentation
Table of Contents
1. Introduction
2. Features
3. Installation
4. Environment Variables
5. API Endpoints
6. Authentication and Authorization
7. Role-Based Access Control
8. Admin Panel Functionalities
9. User Functionalities
10. Database Structure
11. Future Enhancements
1. Introduction
The Matrix Admin Panel Project is a web-based application designed to provide an 
administrative and user interface for managing and purchasing products. The platform supports 
user authentication, role-based access control, and data management capabilities.
2. Features
 User Authentication: Sign up, Login, and OTP verification using JWT tokens.
 Role-Based Access Control: Different views and actions for Admin and User roles.
 Admin Functionalities: Add, delete, edit, and view products; manage user data and 
orders.
 User Functionalities: View products, add products to a cart, and manage their cart.
 Dashboard for Admin: Track user activities, purchases, and product data.
3. Installation
1. Clone the repository: 
2. git clone <repository-url>
3. cd matrix-admin-panel
4. Install dependencies: 
5. npm install
6. Set up environment variables in a .env file.
7. Start the server: 
8. npm start
4. Environment Variables
Create a .env file in the root directory and define:
PORT=5000
DB_URI=mongodb://localhost:27017/matrix_admin_panel
JWT_SECRET=your_jwt_secret
OTP_SECRET=your_otp_secret
5. API Endpoints
Authentication
 POST /api/auth/signup - Register a new user.
 POST /api/auth/login - Login and receive a JWT token.
 POST /api/auth/verify-otp - Verify OTP.
Products
 POST /api/admin/products - Add a new product (Admin only).
 GET /api/products - View all products.
 GET /api/products/****:id - View a specific product.
 PUT /api/admin/products/****:id - Edit a product (Admin only).
 DELETE /api/admin/products/****:id - Delete a product (Admin only).
Cart
 POST /api/cart/add - Add product to cart (User only).
 GET /api/cart - View all products in the cart (User only).
Admin Dashboard
 GET /api/admin/users - View all users and their cart data (Admin only).
 PUT /api/admin/users/****:id - Update user data (Admin only).
6. Authentication and Authorization
 JWT tokens are used to secure endpoints.
 OTP verification ensures secure registration and login.
 Middleware is used to check roles before granting access.
7. Role-Based Access Control
 Admin Role: 
o Manage products (add, edit, delete, view).
o View and manage all users' cart and purchase data.
o Update user data.
 User Role: 
o View products.
o Add products to cart.
o View their own cart and purchase data.
8. Admin Panel Functionalities
 Product Management: 
o Add new products with details (name, price, description, etc.).
o View, edit, and delete existing products.
 User Management: 
o View all users and their cart data.
o Update user information.
 Dashboard: 
o Overview of user activities, purchases, and available products.
9. User Functionalities
 View Products: 
o Access a list of all available products.
 Manage Cart: 
o Add products to the cart.
o View cart items.
10. Database Structure
Collections:
 Users: 
 {
 "_id": ObjectId,
 "username": String,
 "email": String,
 "password": String,
 "role": String,
 "cart": [
 {
 "productId": ObjectId,
 "quantity": Number
 }
 ]
 }
 Products: 
 {
 "_id": ObjectId,
 "name": String,
 "description": String,
 "price": Number,
 "stock": Number
 }
 Orders: 
 {
 "_id": ObjectId,
 "userId": ObjectId,
 "products": [
 {
 "productId": ObjectId,
 "quantity": Number
 }
 ],
 "status": String,
 "createdAt": Date
 }
11. Future Enhancements
 Payment Gateway Integration: Allow users to purchase products directly.
 Search and Filter: Enable advanced search and filtering options for products.
 Notifications: Notify users of changes to orders or cart data.
 Reports: Generate sales and user activity reports for admins.
Author: Red & White Multimedia Education
Version: 1.0.0
