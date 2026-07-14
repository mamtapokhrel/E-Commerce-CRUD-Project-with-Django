E-Commerce Platform: Django + MySQL

A mini e-commerce application built with Django and MySQL, featuring custom authentication, role-based access control, full CRUD operations, a persistent shopping cart, and sales reporting.

Built by: Mamata Pokharel | BSc.CSIT, St. Xavier's College, Kathmandu 
| Course: E-Commerce |  6th Semester

Tech stack
. Python 3.12 
· Django 4.2 
· MySQL 8.0 
· Django ORM 
· Pillow (image uploads) 
· Bootstrap 5 
· Git

Features

Authentication & authorisation
•	Custom signup, login, and logout views built on Django's auth system
•	Three-tier role-based access control enforced by a custom @role_required decorator: 
o	Viewer   browse products, use the cart, place orders (default role on signup)
o	Accountant   access order history and aggregated sales reports
o	Admin   full CRUD over products and categories

Data layer
•	Six models: Role, Category, Product, Cart, Order, OrderItem
•	Relational schema with foreign keys and a one-to-one user–role mapping, managed through the Django ORM

Store functionality
•	Full CRUD for products and categories, including product image uploads
•	Category-filtered shop page, product detail pages, and a featured-products home page
•	Database-backed persistent cart tied to the logged-in user (survives sessions)
•	Checkout that converts a cart into an Order with line-item OrderItem records
•	Sales report aggregating total revenue and order count for accountants

Setup
1. Clone and enter the project
git clone <repo-url>
cd ecommerce_lab

2. Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # macOS / Linux

3. Install dependencies
pip install -r requirements.txt

4. Create the MySQL database
   CREATE DATABASE ecommerce_name;

5. Add database credentials to a .env file (see .env.example)

6. Run migrations and create an admin user
python manage.py migrate
python manage.py createsuperuser

7. Start the server
python manage.py runserver
The site runs at http://127.0.0.1:8000/ and the Django admin at http://127.0.0.1:8000/admin/.
Project structure
ecommerce/          # Project settings, root URL config
shop/
  models.py         # Role, Category, Product, Cart, Order, OrderItem
  views.py          # Auth, CRUD, cart, checkout, reporting
  decorators.py     # @role_required   RBAC enforcement
  urls.py           # Route definitions
  admin.py          # Model registration
templates/          # Django templates
media/              # Uploaded product images (gitignored)

Possible extensions
· Payment gateway integration
· email order notifications
· search and filtering
· product reviews
· a REST API for a mobile client

