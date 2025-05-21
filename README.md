# Vue.js + Laravel CRUD with User Authentication

This is a full‑stack web application built with **Laravel** as the backend and **Vue.js** integrated into it via **Laravel Breeze and Inertia.js**. It features complete **CRUD functionality** and **user authentication**, including registration, login, and protected routes.

## 🚀 Features

* Full CRUD operations (Create, Read, Update, Delete)
* Inertia.js for seamless server-driven SPA experience
* Authentication with Laravel Breeze and Sanctum
* Protected routes for authenticated users
* Vue.js frontend powered by Vite
* Clean, modular structure for scalability

## 🛠️ Tech Stack

* **Framework**: Laravel 12 with Breeze (Vue + Inertia preset)
* **Frontend**: Vue.js, Inertia.js, Axios
* **Authentication**: Laravel Sanctum
* **Database**: MySQL/PostgreSQL
* **Tools**: Composer, NPM/Yarn, Laravel Artisan

## 📦 Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/riordi80/vue-laravel-crud.git
   cd your-repo-name
   ```

2. Install PHP dependencies:

   ```bash
   composer install
   ```

3. Install Node dependencies:

   ```bash
   npm install
   ```

4. Set up environment variables:

   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

5. Configure `.env` with your database credentials.

6. Run database migrations:

   ```bash
   php artisan migrate
   ```

7. Run the development servers:

   ```bash
   php artisan serve
   npm run dev
   ```

---

## 🧪 Usage

* Visit the application at `http://localhost:8000`
* Register a new user
* Login to access protected routes
* Use the interface to perform CRUD operations

---

## 📁 Project Structure

```
├── app/
├── bootstrap/
├── database/
├── public/
├── resources/
│   └── js/        # Vue.js components and Inertia pages
├── routes/
├── package.json
├── vite.config.js
├── artisan
└── ...
```

---

## 🔒 Authentication

Authentication is handled via Laravel Breeze and Sanctum. Inertia.js acts as a bridge between Laravel and Vue, enabling server-side routing and frontend rendering. Sanctum provides CSRF-based token authentication. Routes are protected using Laravel middleware.

---

## 📃 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👤 Author

Created by [Richard O.](https://github.com/riordi80)
Feel free to reach out for questions, issues, or contributions!
