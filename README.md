# Vue.js + Laravel CRUD with User Authentication

This is a full‑stack web application built with **Vue.js** for the frontend and **Laravel** for the backend. It features complete **CRUD functionality** and **user authentication**, including registration, login, and protected routes.

## 🚀 Features

* Full‑stack CRUD operations (Create, Read, Update, Delete)
* RESTful API built with Laravel
* Authentication system (register, login, logout)
* Protected routes for authenticated users
* Vue.js frontend with Axios for API calls
* Token‑based authentication using Laravel Sanctum or Passport (customizable)
* Clean, modular structure for scalability

## 🛠️ Tech Stack

* **Frontend**: Vue.js, Vue Router, Axios
* **Backend**: Laravel, Laravel Sanctum/Passport, MySQL/PostgreSQL
* **Tools**: Composer, NPM/Yarn, Laravel Artisan

## 📦 Installation

### Backend (Laravel)

1. Clone the repository:

   ```bash
   git clone https://github.com/riordi80/vue-laravel-crud.git
   cd your-repo-name/backend
   ```

2. Install PHP dependencies:

   ```bash
   composer install
   ```

3. Set up environment variables:

   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. Configure `.env` with your database credentials.

5. Run migrations:

   ```bash
   php artisan migrate
   ```

6. (Optional) Install Sanctum or Passport:

   ```bash
   composer require laravel/sanctum
   php artisan vendor:publish --provider="Laravel\\Sanctum\\SanctumServiceProvider"
   php artisan migrate
   ```

7. Serve the backend:

   ```bash
   php artisan serve
   ```

---

### Frontend (Vue.js)

1. Navigate to the frontend folder:

   ```bash
   cd ../frontend
   ```

2. Install Node dependencies:

   ```bash
   npm install
   ```

3. Create a `.env` file if needed and set the API base URL:

   ```
   VITE_API_URL=http://localhost:8000/api
   ```

4. Start the development server:

   ```bash
   npm run dev
   ```

---

## 🧪 Usage

* Visit the frontend app at `http://localhost:5173/` (or the port Vue is using)
* Register a new user
* Login and perform CRUD operations on your entities
* Logout when finished

---

## 📁 Project Structure

```
├── backend/         # Laravel backend
│   ├── app/
│   ├── routes/
│   └── ...
├── frontend/        # Vue.js frontend
│   ├── src/
│   └── ...
```

---

## 🔒 Authentication

Authentication is handled via Laravel Sanctum (or Passport). Once logged in, users receive a token that is used to access protected API routes. The frontend stores the token in local storage or Vuex/Pinia (configurable).

---

## 📃 License

This project is open source and available under the [MIT License](LICENSE).

---

## 👤 Author

Created by [Richard O.](https://github.com/riordi80)
Feel free to reach out for questions, issues, or contributions!
