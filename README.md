<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

VIP Student - Educational Platform
Overview
VIP Student is a multilingual educational platform designed to provide a seamless learning experience for students, instructors, guardians, and administrators. Built with Laravel, it supports course management, role-based access control, exams, payments, and notifications, with robust multilingual capabilities using astrotomic/laravel-translatable. The platform is tailored for various educational systems (e.g., Egyptian, British) and emphasizes scalability, security, and user-friendliness.
This README provides a detailed guide to the project, covering its objectives, features, database schema, development roadmap, installation, usage, and contribution guidelines.

Table of Contents

Project Objectives
Features
Technology Stack
Database Schema (ERD)
Roadmap
Installation
Usage
API Documentation
Contributing
License


Project Objectives
The core objectives of the VIP Student platform are:

Deliver a multilingual learning management system supporting Arabic, English, and other languages.
Enable institutes to manage courses, lessons, and exams with flexible categorization and pricing.
Implement role-based access control for admins, instructors, students, and guardians.
Integrate secure payment gateways and real-time, translated notifications.
Ensure high performance through caching (Redis) and optimized database queries.
Provide a user-friendly interface with a powerful admin panel using Filament.
Offer comprehensive API documentation via L5-Swagger.


Features

Multilingual Support: Translated content for courses, exams, notifications, and static pages using Laravel Translatable.
User Management: Role-based access (Admin, Instructor, Student, Guardian) with permissions via Spatie Laravel Permission.
Institute Management: Institutes can register, upload certifications, and manage communications and announcements.
Course Management: Create and categorize courses, units, and lessons, supporting multiple educational systems.
Exams and Assessments: Build exams with multiple-choice, true/false, or text-based questions, with result tracking.
Payments: Multi-currency pricing and secure payment processing via Stripe.
Notifications: Real-time, translated notifications for users.
Frontend Interface: Responsive UI using Vue.js and Tailwind CSS for institutes, courses, and exams.
Admin Panel: Manage users, courses, and settings via Filament.
Support System: Ticket-based support with multilingual messaging.
Analytics: Instructor reports, exam results, and audit logs.


Technology Stack



Category
Technology



Backend
Laravel 11, PHP 8.2


Frontend
Vue.js, Tailwind CSS


Database
MySQL


Caching
Redis


Authentication
Laravel Sanctum (JWT-based)


Permissions
Spatie Laravel Permission


Translation
Astrotomic Laravel Translatable


Admin Panel
Filament


API Docs
L5-Swagger


Payments
Stripe SDK


Testing
PHPUnit, Laravel Dusk


Deployment
Laravel Forge, DigitalOcean, Docker (Sail)


Version Control
Git, GitHub



Database Schema (ERD)
The database is designed to support the platform’s multilingual and modular structure. Below is a detailed overview of the key entities and relationships based on the DBML schema.
Key Entities

Languages (languages):

Purpose: Stores language codes (e.g., en, ar) and names.
Fields: id, code, name, is_default, created_at, updated_at
Indexes: Unique index on code.


Users (users):

Purpose: Manages user accounts with role and institute affiliations.
Fields: id, role_id, institute_id, name, email, password, city_id, phone, status, etc.
Relationships: BelongsTo Role, Institute, City.


Roles (roles) and Permissions (permissions):

Purpose: Manages role-based access with translated names.
Fields (Roles): id, name, created_at, updated_at
Fields (Permissions): id, name, description, created_at, updated_at
Relationships: Many-to-Many via role_permissions.


Institutes (institutes):

Purpose: Stores institute details, certifications, and communications.
Fields: id, city_id, approved, logo, training_license, name, description, etc.
Relationships: HasMany institute_certificates, institute_communications, courses.


Courses (courses):

Purpose: Manages courses with pricing and categorization.
Fields: id, institute_id, subject_id, educational_system, registration_start_date, registration_end_date, price, etc.
Relationships: HasMany course_units, BelongsToMany categories, sub_categories, tags.


Lessons (lessons):

Purpose: Stores lesson details with types (online, offline, recorded, live).
Fields: id, course_unit_id, instructor_id, lesson_type, link, file_path, start_time, end_time, etc.
Relationships: BelongsTo CourseUnit, Instructor.


Exams (exams) and Questions (questions):

Purpose: Manages assessments with translated content.
Fields (Exams): id, course_id, title, duration, total_marks, created_at, updated_at
Fields (Questions): id, exam_id, question_type, marks, created_at, updated_at
Relationships: exams HasMany questions, questions HasMany question_options.


Payments (payments):

Purpose: Tracks payments with multi-currency support.
Fields: id, user_id, course_id, amount, currency_id, status, method, transaction_id, etc.
Relationships: BelongsTo User, Course, Currency.


Notifications (notifications):

Purpose: Manages user notifications with translated content.
Fields: id, user_id, content, is_read, created_at, updated_at
Relationships: BelongsTo User.



Key Relationships

Users ↔ Roles: One-to-Many (a user has one role, a role has many users).
Institutes ↔ Courses: One-to-Many (an institute offers multiple courses).
Courses ↔ Course Units ↔ Lessons: Hierarchical (a course has units, a unit has lessons).
Exams ↔ Questions ↔ Question Options: Hierarchical (an exam has questions, a question has options).
Translations: Entities like courses, exams, and notifications have translation tables linked to languages.code.

ERD Visualization
[Languages] --(one-to-many)-- [Translations]
   |
[Users] --(belongs-to)-- [Roles] --(many-to-many)-- [Permissions]
   |                         |
   | (owns/offers)          | (manages)
   |                         |
[Institutes] --(one-to-many)-- [Courses] --(one-to-many)-- [Course_Units] --(one-to-many)-- [Lessons]
   |                                                     |
   | (enrolls in)                                        | (assessed by)
   |                                                     |
[Enrollments]                                         [Exams] --(one-to-many)-- [Questions] --(one-to-many)-- [Question_Options]
   |                                                     |
   | (pays for)                                          | (results in)
   |                                                     |
[Payments] --(uses)-- [Currencies]                    [Exam_Results]
   |
[Notifications]


Note: A detailed ERD diagram can be generated using DBML tools or found in docs/erd.png.


Roadmap
The development is divided into 6 sprints over 12 weeks, with detailed tasks and sub-tasks for each sprint.
Sprint 1: Environment and Database Setup (Weeks 1-2)

Goal: Set up the Laravel project, install dependencies, and create the database schema.
Duration: 10 working days
Tasks:
Setup Development Environment
Sub-task 1.1: Initialize Laravel project
Run composer create-project laravel/laravel vip-student.
Initialize Git: git init.
Setup Laravel Sail: ./vendor/bin/sail up.


Sub-task 1.2: Install core packages
Install astrotomic/laravel-translatable: composer require astrotomic/laravel-translatable.
Install spatie/laravel-permission: composer require spatie/laravel-permission.
Install laravel/sanctum: composer require laravel/sanctum.


Test: Verify Laravel runs at http://localhost:8000 and packages exist in vendor.


Configure Database
Sub-task 2.1: Setup MySQL
Create database: CREATE DATABASE vip_student.
Update .env: DB_DATABASE=vip_student.
Test connection: php artisan migrate:status.


Sub-task 2.2: Setup Redis
Install Redis: apt-get install redis-server.
Update .env: CACHE_DRIVER=redis.
Test connection: redis-cli ping (should return PONG).




Create Migrations and Seeders
Sub-task 3.1: Write migrations
Create migrations for languages, cities, users, roles, institutes, etc.
Add indexes for email, translation tables.


Sub-task 3.2: Create seeders
Seed languages: en, ar.
Seed cities: Cairo, Riyadh.
Seed roles: Admin, Instructor, Student.


Test: Verify tables with SHOW TABLES and data with Language::all() in php artisan tinker.




Deliverables: Laravel project with MySQL/Redis, migrations, and seeders.

Sprint 2: User and Permission Management (Weeks 3-4)

Goal: Implement authentication, roles, permissions, and admin panel.
Duration: 10 working days
Tasks:
Create User Models
Sub-task 1.1: Setup models
Model User with encrypted password.
Model Role with translated name.
Model Permission with translated name, description.


Sub-task 1.2: Setup relationships
belongsTo between User and Role.
hasMany between Role and User.
role_permissions using Spatie.




Implement Authentication and Translations
Sub-task 2.1: Setup authentication
Install Sanctum: composer require laravel/sanctum.
Create AuthController: php artisan make:controller AuthController.
Add login and register methods.


Sub-task 2.2: Setup translations
Create SetLocale middleware.
Setup translation files: lang/ar/auth.php, lang/en/auth.php.




Manage Permissions and Admin Panel
Sub-task 3.1: Setup permissions
Create permissions like edit_users, view_courses.
Setup middleware for role and permission.


Sub-task 3.2: Create admin panel
Install Filament: composer require filament/filament.
Create resources: php artisan make:filament-resource User.






Deliverables: User system, multilingual authentication, Filament admin panel.

Sprint 3: Institute and Course Management (Weeks 5-6)

Goal: Develop institute and course management with categorization.
Duration: 10 working days
Tasks:
Create Institute, Course, CourseUnit, Lesson, Category models with translations.
Setup relationships (e.g., Institute HasMany Courses, Courses BelongsToMany Categories).
Build frontend with Vue.js and Tailwind CSS.
Create API routes for institutes and courses with multilingual support.


Deliverables: Institute/course management system, frontend interface.

Sprint 4: Exams and Assessments (Weeks 7-8)

Goal: Implement exam creation, question management, and result tracking.
Duration: 10 working days
Tasks:
Create Exam, Question, QuestionOption, Answer, ExamResult models.
Implement logic for submitting answers and calculating scores.
Build frontend for exams with Vue.js.
Create API routes for exams and questions with translations.


Deliverables: Exam system with frontend and result tracking.

Sprint 5: Payments and Notifications (Weeks 9-10)

Goal: Integrate payments, currencies, notifications, and static pages.
Duration: 10 working days
Tasks:
Create Currency, CoursePrice, Payment, Notification, Page, Faq models.
Integrate Stripe for payment processing.
Implement notification system with translations.
Build frontend for payments and static pages.


Deliverables: Payment system, notification system, static pages.

Sprint 6: Testing and Deployment (Weeks 11-12)

Goal: Test the application, optimize performance, and deploy.
Duration: 10 working days
Tasks:
Write unit and integration tests using PHPUnit and Laravel Dusk.
Optimize with Redis caching and Eager Loading.
Deploy to DigitalOcean using Laravel Forge.
Generate API documentation with L5-Swagger.


Deliverables: Tested and deployed application, API documentation.


Installation
Follow these steps to set up the project locally:
Prerequisites

PHP 8.2+
Composer
Node.js (v16+)
MySQL (v8+)
Redis
Git
Docker (optional for Laravel Sail)

Steps

Clone the Repository:
git clone https://github.com/your-repo/vip-student.git
cd vip-student


Install Dependencies:
composer install
npm install


Setup Environment Variables:

Copy .env.example to .env:cp .env.example .env


Update .env with database, Redis, and Stripe settings:DB_CONNECTION=mysql
DB_DATABASE=vip_student
DB_USERNAME=root
DB_PASSWORD=
CACHE_DRIVER=redis
REDIS_HOST=127.0.0.1
STRIPE_KEY=your_stripe_key
STRIPE_SECRET=your_stripe_secret




Generate Application Key:
php artisan key:generate


Run Migrations and Seeders:
php artisan migrate
php artisan db:seed


Start the Development Server:

For Laravel:php artisan serve


For frontend:npm run dev


For Sail:./vendor/bin/sail up




Access the Application:

Backend: http://localhost:8000
Frontend: http://localhost:5173
Admin Panel: http://localhost:8000/admin




Usage

Users: Register or log in to access courses, exams, and notifications.
Instructors: Manage lessons, create exams, and submit reports via Filament.
Admins: Use Filament to manage users, institutes, and settings.
Students: Enroll in courses, take exams, and view results.
Guardians: Monitor student progress and receive notifications.
API: Access endpoints like /api/courses with Accept-Language header for translations.


API Documentation
The API is documented using L5-Swagger. After installation, access it at:

URL: http://localhost:8000/api/documentation
Features:
Lists all endpoints (e.g., /api/institutes, /api/courses).
Supports testing via Swagger UI.
Includes translation instructions (e.g., Accept-Language: ar for Arabic).




Contributing
We welcome contributions! To contribute:

Fork the repository.
Create a feature branch: git checkout -b feature/your-feature.
Commit changes: git commit -m "Add your feature".
Push the branch: git push origin feature/your-feature.
Open a Pull Request with a detailed description.

Adhere to the Code of Conduct and Contribution Guidelines.

License
This project is licensed under the MIT License. See the LICENSE file for details.
