<p align="center">
  <a href="https://laravel.com" target="_blank">
    <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo">
  </a>
</p>

<p align="center">
  <a href="https://github.com/xAI/vip-student/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
  <a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# 🎓 VIP Student Educational Platform

## 📖 About VIP Student

The **VIP Student** platform is a cutting-edge educational framework designed to enhance the learning experience for students, instructors, parents, and administrators. Powered by **Laravel 11**, it supports multiple languages (e.g., Arabic and English) and offers comprehensive management of courses, exams, payments, and notifications. Our goal is to make development enjoyable and efficient, leveraging tools like Redis caching and **Laravel Translatable**.

This README provides a detailed guide, including objectives, features, technology stack, database structure, roadmap, setup instructions, API endpoints, and more.

---

## 🎯 Objectives

- 🌍 Provide a multilingual educational platform supporting Arabic, English, and beyond.
- 📚 Enable institutes to manage courses, lessons, and exams with flexible categories and multi-currency pricing.
- 🔐 Implement role-based access control (Admin, Instructor, Student, Parent).
- 💳 Integrate secure payment gateways and real-time translated notifications.
- ⚡ Optimize performance with Redis caching and efficient database queries.
- 🖥️ Deliver a user-friendly interface with a Filament-powered admin dashboard.
- 📖 Generate detailed API documentation using Swagger.

---

## ✨ Key Features

- **Multilingual Support** 🌐: Translate course content, exams, notifications, and pages with Laravel Translatable.
- **User Management** 👥: Manage roles (Admin, Instructor, Student, Parent) using Spatie Laravel Permission.
- **Institute Management** 🏫: Handle institute registration, certificate uploads, and communication/ads.
- **Course Management** 📚: Create and categorize courses, units, and lessons for systems like Egyptian and British.
- **Exams & Assessments** 📝: Design exams (multiple-choice, true/false, essays) with result tracking.
- **Payments** 💳: Support multi-currency pricing and secure transactions via Stripe.
- **Notifications** 🔔: Send real-time translated notifications to users.
- **Responsive UI** 💻: Build a responsive frontend with Vue.js and Tailwind CSS.
- **Admin Dashboard** ⚙️: Manage users, courses, and settings via Filament.
- **Support System** 📞: Offer multilingual support tickets with translated messages.
- **Reports & Analytics** 📊: Provide instructor reports, exam results, and audit logs.

---

## 🛠️ Technologies Used

| **Category**         | **Technology**                       |
|----------------------|--------------------------------------|
| **Backend**          | Laravel 11, PHP 8.2                 |
| **Frontend**         | Vue.js, Tailwind CSS                |
| **Database**         | MySQL                               |
| **Caching**          | Redis                               |
| **Authentication**   | Laravel Sanctum                     |
| **Permissions**      | Spatie Laravel Permission           |
| **Translation**      | Astrotomic Laravel Translatable     |
| **Admin Panel**      | Filament                            |
| **API Documentation**| L5-Swagger                          |
| **Payments**         | Stripe SDK                          |
| **Testing**          | PHPUnit, Laravel Dusk               |
| **Deployment**       | Laravel Forge, DigitalOcean, Docker |
| **Version Control**  | Git, GitHub                         |

---

## 📋 Prerequisites

- **PHP** >= 8.2
- **Composer**
- **Node.js** and **npm** (for frontend assets)
- **Web Server** (e.g., Apache or Nginx)
- **MySQL Database** (v8+)
- **Redis**
- **Git**

---

## 🚀 Setup Instructions

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-repo/vip-student.git
   cd vip-student
   ```

2. **Install Composer Dependencies:**
   ```bash
   composer install
   ```

3. **Copy the Environment File:**
   ```bash
   cp .env.example .env
   ```

4. **Configure the Environment File:**
   - Update database settings:
     ```bash
     DB_CONNECTION=mysql
     DB_DATABASE=vip_student
     DB_USERNAME=root
     DB_PASSWORD=
     ```
   - Set caching:
     ```bash
     CACHE_DRIVER=redis
     REDIS_HOST=127.0.0.1
     ```
   - Configure Stripe:
     ```bash
     STRIPE_KEY=your_stripe_key
     STRIPE_SECRET=your_stripe_secret
     ```
   - Set `APP_URL=http://localhost:8000`.

5. **Generate Application Key:**
   ```bash
   php artisan key:generate
   ```

6. **Run Migrations and Seeders:**
   ```bash
   php artisan migrate --seed
   ```
   - The `--seed` flag populates initial data (e.g., languages, roles).

7. **Install Laravel Sanctum:**
   ```bash
   php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
   php artisan migrate
   ```

8. **Start the Development Server:**
   ```bash
   php artisan serve
   ```
   - Access at `http://127.0.0.1:8000`. Use Apache/Nginx for production.

---

## 📡 API Endpoints

| **Method** | **Path**                  | **Description**                              | **Authentication** | **Role(s)**       | **HTTP Status** |
|------------|---------------------------|---------------------------------------------|--------------------|-------------------|-----------------|
| POST       | `/api/register`           | Register a new user (specify role)           | No                 | None              | 201 Created     |
| POST       | `/api/login`              | Log in and receive an Access Token           | No                 | None              | 200 OK          |
| POST       | `/api/logout`             | Log out authenticated user                   | Yes                | Authenticated     | 200 OK          |
| GET        | `/api/user`               | View authenticated user info                 | Yes                | Authenticated     | 200 OK          |
| GET        | `/api/courses`            | View all available courses                   | Yes                | Authenticated     | 200 OK          |
| POST       | `/api/courses`            | Create a new course (for instructors)        | Yes                | Instructor        | 201 Created     |
| GET        | `/api/courses/{id}`       | View details of a specific course            | Yes                | Authenticated     | 200 OK          |
| PUT/PATCH  | `/api/courses/{id}`       | Update a course (owner only)                 | Yes                | Instructor (owner)| 200 OK          |
| DELETE     | `/api/courses/{id}`       | Delete a course (owner only)                 | Yes                | Instructor (owner)| 204 No Content  |
| GET        | `/api/instructor/courses` | View courses created by the instructor       | Yes                | Instructor        | 200 OK          |
| POST       | `/api/enrollments`        | Enroll in a course (for students)            | Yes                | Student           | 201 Created     |
| GET        | `/api/student/enrollments`| View booked courses (for students)           | Yes                | Student           | 200 OK          |
| GET        | `/api/exams`              | View available exams                         | Yes                | Authenticated     | 200 OK          |
| POST       | `/api/exams/{id}/submit`  | Submit exam answers                          | Yes                | Student           | 200 OK          |

> **Note**: Full API details are in the Swagger documentation at `/api/documentation`.

---

## 📦 Postman Collection

[Download VIP Student API.postman_collection.json](https://example.com/vip-student-postman.json)

## 🧪 Testing Instructions with Postman

1. **Import the Postman Collection** (linked above).
2. **Register a New User (POST `/api/register`):**
   - Request Body (raw JSON):
     ```json
     {
       "name": "User Name",
       "email": "user@example.com",
       "password": "password",
       "password_confirmation": "password",
       "role": "student"
     }
     ```
3. **Log In (POST `/api/login`):**
   - Request Body (raw JSON):
     ```json
     {
       "email": "user@example.com",
       "password": "password"
     }
     ```
   - Save the `access_token` from the response.
4. **Set Authorization:**
   - In Postman, go to "Authorization" > "Bearer Token" and paste the `access_token`.
5. **Test Endpoints:**
   - **As Instructor:**
     - Create a course (POST `/api/courses`) with:
       ```json
       {"title": "Course Name", "description": "Description", "max_students": 50}
       ```
     - View own courses (GET `/api/instructor/courses`).
     - Update course (PUT `/api/courses/{id}`) with new details.
     - Delete course (DELETE `/api/courses/{id}`).
     - Attempt to book a course (should return 403).
   - **As Student:**
     - View courses (GET `/api/courses`).
     - Book a course (POST `/api/enrollments`) with:
       ```json
       {"course_id": 1}
       ```
     - View booked courses (GET `/api/student/enrollments`).
     - Attempt to book the same course twice (should return 409).
     - Attempt to create a course (should return 403).

---

## ⚠️ Error Handling

- Returns standard HTTP status codes (e.g., 200 OK, 403 Forbidden).
- Errors in JSON format with a `message` field.
- Validation errors return 422 Unprocessable Entity with an `errors` object.

---

## 🗄️ Database Structure (ERD)

### Main Entities

- **Languages** (`languages`): Stores language codes (e.g., `en`, `ar`).
  - Fields: `id`, `code`, `name`, `is_default`.
- **Users** (`users`): Manages user accounts with roles.
  - Fields: `id`, `role_id`, `name`, `email`, `password`.
- **Roles** (`roles`): Defines user roles.
  - Relationships: Many-to-Many with `permissions` via `role_permissions`.
- **Institutes** (`institutes`): Stores institute details.
  - Fields: `id`, `name`, `city_id`, `approved`.
  - Relationships: HasMany `courses`.
- **Courses** (`courses`): Manages course data.
  - Fields: `id`, `institute_id`, `title`, `description`, `max_students`.
  - Relationships: HasMany `course_units`.
- **Exams** (`exams`): Stores exam details.
  - Relationships: HasMany `questions`.
- **Payments** (`payments`): Tracks payment transactions.
  - Fields: `id`, `user_id`, `amount`, `currency_id`.

### Relationships

- **Users ↔ Roles**: One-to-Many.
- **Institutes ↔ Courses**: One-to-Many.
- **Courses ↔ Exams**: One-to-Many.
- Translations managed via tables like `course_translations`.

> **Note**: Detailed ERD in `docs/erd.png`.

---

## 🗺️ Development Roadmap

| **Sprint** | **Duration** | **Focus Area**            | **Status** |
|------------|--------------|---------------------------|------------|
| Sprint 1   | Weeks 1-2    | Environment Setup         | ✅ Done    |
| Sprint 2   | Weeks 3-4    | User & Permission Mgmt    | ✅ Done    |
| Sprint 3   | Weeks 5-6    | Institutes & Courses      | ✅ Done    |
| Sprint 4   | Weeks 7-8    | Exams & Assessments       | ✅ Done    |
| Sprint 5   | Weeks 9-10   | Payments & Notifications  | ✅ Done    |
| Sprint 6   | Weeks 11-12  | Testing & Deployment      | ✅ Done    |

- **Sprint 1**: Set up Laravel, installed packages, configured MySQL/Redis.
- **Sprint 2**: Added user authentication and Filament admin panel.
- **Sprint 3**: Built institute and course management with Vue.js frontend.
- **Sprint 4**: Implemented exams and assessments.
- **Sprint 5**: Integrated Stripe payments and notifications.
- **Sprint 6**: Conducted testing and deployed to DigitalOcean.

---

## 👨‍💻 Author

- **Mohamed Alzohery**
- **Email**: mohamedmohasenalzohery@gmail.com
- **GitHub**: [https://github.com/alzohery](https://github.com/alzohery)

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

## 🌟 Future Enhancements

- Add support for more languages.
- Implement a course recommendation engine.
- Enhance analytics with real-time dashboards.
