# News Aggregator Web Application using Laravel and React.js

This project is a News Aggregator Web Application built using **Laravel** for the backend and **React.js** for the frontend. It fetches and displays news from various sources.

---

## Project Overview

The **News Aggregator** is a web application that fetches and displays the latest news articles using a **Laravel API** and a **React.js frontend**. The backend handles news aggregation, while the frontend provides an interactive user interface for easy access to the news.

---

## Docker Configuration

This application uses **Docker** to containerize both the backend (Laravel) and frontend (React) services, along with a **MySQL database**.

### Steps to Run the Project

1. **Copy the `.env.example` file to `.env`** in the root of the project directory.
   
   ```bash
   cp .env.example .env
   ```

2. **Build the Docker containers** by running:

   ```bash
   docker-compose build
   ```

3. **Start the containers**:

   ```bash
   docker-compose up
   ```

   Wait for a few minutes while Docker initializes the backend, frontend, and MySQL containers.

4. Once the containers are running, execute the following command to set up the database:

   ```bash
   docker-compose exec backend-app php artisan migrate --seed
   ```

   This will create the necessary database tables and seed data.

5. The application will be available at **http://localhost:3000/**. You can click on the **"Get News"** button to fetch the latest news.

---

## Verifying MySQL Database Tables

To verify the tables in the MySQL container, follow these steps:

1. List the running containers to find the MySQL container ID:

   ```bash
   docker ps
   ```

2. Enter the MySQL container:

   ```bash
   docker exec -it <mysql-container-id> sh
   ```

   Replace `<mysql-container-id>` with the actual ID of the MySQL container.

3. Log in to MySQL:

   ```bash
   mysql -u root -p
   ```

   When prompted, enter `root` as the password.

4. Show the available databases:

   ```bash
   show databases;
   ```

5. Use the `news` database:

   ```bash
   use news;
   ```

6. Verify the tables:

   ```bash
   show tables;
   ```

The tables should match the ones defined in the Laravel migrations.

---

## Monitoring Laravel Logs

To monitor the Laravel container logs, execute the following commands:

1. Access the Laravel container:

   ```bash
   docker exec -it <container_name_or_id> sh
   ```

   Replace `<container_name_or_id>` with the actual container name or ID.

2. Navigate to the Laravel log directory:

   ```bash
   cd /var/www/html/storage
   ```

3. View the Laravel log:

   ```bash
   cat logs/laravel.log
   ```

---

## Manual Configuration

In case you need to manually set up the environment, follow the steps below.

### Frontend Setup

1. Install the frontend dependencies:

   ```bash
   npm install
   ```

2. Build the frontend project:

   ```bash
   npm run build
   ```

### Backend Setup

1. Install the backend dependencies:

   ```bash
   composer install
   ```

2. Generate the Laravel application key:

   ```bash
   php artisan key:generate
   ```

3. Run the migrations to create the necessary database tables:

   ```bash
   php artisan migrate
   ```

4. Seed the database with sample data:

   ```bash
   php artisan db:seed
   ```

---

With these instructions, you should be able to set up, run, and troubleshoot the News Aggregator Web Application successfully.

