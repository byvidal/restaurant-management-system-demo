# Comprehensive Restaurant Management System (Django 5)

A production-ready, full-stack ERP solution designed for high-volume food service environments. This system integrates Point of Sale (POS), Kitchen Display Systems (KDS), and Logistics management into a single, cohesive platform.

## Product Overview

This project goes beyond simple management templates. It is a fully operational operating system for pizzerias and restaurants, built to handle the chaotic reality of a busy kitchen. 

The architecture is designed API-First using Django REST Framework, ensuring that the backend logic is decoupled and ready to support native mobile applications or third-party integrations in the future. It focuses heavily on operational efficiency, reducing human error through automated financial calculations and providing real-time visibility into the business.

## Core Modules

### 1. Point of Sale (POS) Terminal
Designed for speed and reliability. The interface is optimized for touchscreen monitors and tablets, allowing cashiers to process orders rapidly.
* **Smart Product Visualization:** Automatically categorizes items for quick access.
* **Error-Free Financials:** All totals and subtotals are calculated securely on the server side to prevent manipulation or calculation errors.

### 2. Kitchen Display System (KDS)
Replaces traditional paper tickets with intelligent digital monitors. This module improves communication between the front of house and the kitchen.
* **Time-Based Priority System:** Orders automatically change color based on their wait time (Green for new, Yellow for attention, Red for delayed), helping chefs prioritize effectively.
* **Workflow Automation:** One-click status updates sync immediately across all devices.

### 3. Delivery Driver Web App
A mobile-first interface designed specifically for logistics and delivery staff.
* **Battery-Saving Design:** Features a dark mode interface to reduce battery consumption on OLED smartphone screens during shifts.
* **GPS Integration:** Direct integration with mapping services to provide one-tap navigation to the customer's address.
* **Fleet Management:** Drivers can claim ready orders and update delivery status in real-time.

### 4. Management & Analytics Dashboard
A central control tower for business owners and managers.
* **Real-Time KPIs:** Monitor daily sales, active orders, and product performance live.
* **Security Protocols:** Critical actions, such as voiding orders or authorizing refunds, are protected by a supervisor password system.

## Technical Architecture

* **Backend Framework:** Python / Django 5.0+
* **API:** Django REST Framework (ViewSet Architecture)
* **Database:** PostgreSQL (Production ready) or SQLite (Development)
* **Security:** Authentication uses HttpOnly Cookies to prevent XSS attacks, superior to standard local storage tokens.
* **Data Integrity:** Financial logic is handled via Django Signals to ensure data consistency across the database.

## Installation Guide

Follow these steps to set up the project locally for development or testing.

### 1. Clone and Configure Environment

```bash
git clone [https://github.com/.......git]
cd restaurant-management-system-django

# Create a virtual environment
python -m venv venv

# Activate the environment (Windows)
.\venv\Scripts\activate

# Activate the environment (Mac/Linux)
source venv/bin/activate
````

### 2\. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3\. Environment Variables

Create a file named .env in the root directory (you can use .env.example as a reference) and configure your database settings.

```ini
DEBUG=True
SECRET_KEY=your_secure_secret_key_here
DB_NAME=your_db_name
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=localhost
```

### 4\. Database Setup and Initialization

We have included a custom automation script to save you time configuring user permissions.

```bash
# Apply database migrations
python manage.py makemigrations
python manage.py migrate

# AUTOMATED SETUP: Configures groups and permissions (Manager, Cashier, Cook, Driver)
python manage.py setup_roles

# Create an administrative user
python manage.py createsuperuser
```

### 5\. Run the Server

```bash
python manage.py runserver
```

## User Roles and Testing

After running the setup\_roles command, the system is ready for testing. You can create users in the Django Admin panel and assign them one of the following roles to access their specific interfaces:

  * **Gerente (Manager):** Access to /dashboard for analytics and control.
  * **Cajero (Cashier):** Access to /pos for order entry.
  * **Cocinero (Cook):** Access to /cocina for the KDS monitor.
  * **Repartidor (Driver):** Access to /repartidor for delivery management.

## License

This source code is available for commercial use. Unauthorized redistribution or resale of the original source code is strictly prohibited.
