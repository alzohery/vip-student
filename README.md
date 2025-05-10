<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

VIP Student - Educational Platform
Overview
VIP Student is a multilingual educational platform built to support students, instructors, and institutes with a seamless learning experience. The platform leverages Laravel Translatable for multilingual support and is developed over 6 sprints (12 weeks), ensuring a robust, scalable, and user-friendly system. This README provides a detailed breakdown of the project roadmap, including objectives, tasks, timelines, and deliverables for each sprint.

Project Roadmap
Sprint 1: Environment Setup and Database Configuration (Weeks 1-2)
Objective
Set up the development environment, install necessary packages, and configure the database to kickstart the project.
Duration
2 weeks (10 working days)
Tasks and Deliverables

Task 1.1: Development Environment Setup (2 days)  

Initialized a new Laravel 11 project (composer create-project laravel/laravel vip-student).  
Set up a Git repository (git init) for version control.  
Configured Laravel Sail for containerized development (./vendor/bin/sail up).  
Installed core packages:  
astrotomic/laravel-translatable for multilingual support.  
spatie/laravel-permission for role and permission management.  
laravel/sanctum for API authentication.


Validation:  
Confirmed Laravel setup by running php artisan serve and accessing http://localhost:8000.  
Verified package installation in the vendor directory (ls vendor).  
Checked Git repository initialization (git status).




Task 1.2: Database Setup (2 days)  

Configured MySQL:  
Created a database named vip_student (CREATE DATABASE vip_student).  
Updated .env with MySQL settings (DB_DATABASE=vip_student).  
Tested connection (php artisan migrate:status).


Configured Redis:  
Installed Redis (apt-get install redis-server).  
Updated .env for caching (CACHE_DRIVER=redis).  
Tested Redis connection (php artisan cache:clear).


Validation:  
Ensured no connection errors (php artisan migrate:status).  
Tested caching (Cache::put('test', 'value', 60) and Cache::get('test')).  
Verified Redis response (redis-cli ping returns PONG).




Task 1.3: Migrations and Seeders (6 days)  

Created migrations for core tables: languages, cities, city_translations, users, roles, permissions, institutes, courses.  
Added indexes for fields like email and translations.  
Developed seeders for initial data:  
Languages: en, ar.  
Cities: Cairo, Riyadh.  
Roles: Admin, Instructor, Student.


Validation:  
Confirmed table creation (SHOW TABLES).  
Verified seeded data (Language::all() in php artisan tinker).  
Tested translation functionality (City::first()->translate('ar')->name).





Key Deliverables

A fully configured Laravel project with Git integration.
MySQL and Redis databases ready for use.
Initial migrations and seeders for core functionality.


Sprint 2: User and Permission Management (Weeks 3-4)
Objective
Implement user management, roles, permissions, and a basic admin panel with multilingual support.
Duration
2 weeks (10 working days)
Tasks and Deliverables

Task 2.1: User Models Setup (3 days)  

Created models: User, Role, Permission.  
Added password encryption for User.  
Enabled translation for Role (name) and Permission (name, description).  
Defined relationships:  
User belongs to Role.  
Role has many User.  
Configured role_permissions using Spatie.


Validation:  
Tested relationships (User::first()->role).  
Verified role translation (Role::first()->translate('ar')->name).  
Confirmed password encryption (User::first()->password).




Task 2.2: Authentication and Translation (3 days)  

Set up authentication with Laravel Sanctum.  
Created AuthController with login and register methods.  
Implemented translation support:  
Added SetLocale middleware.  
Created translation files (lang/ar/auth.php, lang/en/auth.php).


Validation:  
Tested login API (POST /api/login) with Postman, ensuring a token is returned.  
Verified Arabic error messages with Accept-Language: ar.  
Confirmed new user registration (php artisan tinker).




Task 2.3: Permissions and Admin Panel (4 days)  

Defined permissions like edit_users, view_courses using Spatie.  
Created middleware for role/permission checks.  
Set up an admin panel with Filament:  
Installed Filament (composer require filament/filament).  
Created resources for User, Role, Permission.  
Added translations (lang/ar/filament.php).


Validation:  
Accessed /admin and confirmed Filament dashboard display.  
Created a new user via Filament and verified in users table.  
Tested permission enforcement (API request without permission returns 403).





Key Deliverables

A multilingual user management system with roles and permissions.
API-based authentication supporting multiple languages.
A functional admin panel using Filament.


Sprint 3: Institutes and Courses Management (Weeks 5-6)
Objective
Develop the core functionality for managing institutes, courses, and categories with a user-facing frontend.
Duration
2 weeks (10 working days)
Tasks and Deliverables

Task 3.1: Institute Models (3 days)  

Created models: Institute, InstituteCertificate, InstituteCommunication.  
Enabled translations for fields like name, description, certificate_name, value.  
Defined relationships:  
Institute has many InstituteCertificate.  
Institute belongs to City.


Validation:  
Tested relationships (Institute::first()->certificates).  
Verified institute translation (Institute::first()->translate('ar')->name).  
Created a new institute and confirmed in institutes table.




Task 3.2: Courses and Categories (4 days)  

Created models: Course, CourseUnit, Lesson, Category, SubCategory.  
Enabled translations for fields like title, description, name.  
Defined relationships:  
Course belongs to many Category (course_categories).


Validation:  
Tested relationships (Course::first()->categories).  
Verified course translation (Course::first()->translate('ar')->title).  
Created a course with a category and confirmed in course_categories.




Task 3.3: Frontend for Institutes and Courses (3 days)  

Set up frontend with Vue.js, Vue Router, Axios, and Tailwind CSS.  
Designed InstitutesList.vue for displaying institutes.  
Created API routes (/api/institutes, /api/courses) and integrated with Vue.js using Axios.  
Validation:  
Visited /institutes in the browser and confirmed institute list display.  
Tested API with Accept-Language: ar in Postman for translations.  
Verified course filtering by category in the frontend.





Key Deliverables

A multilingual system for managing institutes and courses.
A responsive frontend to display institutes and courses.


Sprint 4: Exams and Assessments (Weeks 7-8)
Objective
Implement exams, questions, and assessments with a frontend for students to take exams.
Duration
2 weeks (10 working days)
Tasks and Deliverables

Task 4.1: Exam Models (3 days)  

Created models: Exam, Question, QuestionOption.  
Enabled translations for title, question_text, option_text.  
Defined relationships:  
Exam has many Question.  
Question has many QuestionOption.


Validation:  
Tested relationships (Exam::first()->questions).  
Verified question translation (Question::first()->translate('ar')->question_text).  
Created a new exam and confirmed in exams table.




Task 4.2: Answers and Results (3 days)  

Created models: Answer, ExamResult.  
Developed ExamController with a submitAnswers method to save answers and calculate scores.  
Validation:  
Tested API (POST /api/exams/{id}/submit) with Postman, ensuring answers are saved.  
Verified score calculation in exam_results (php artisan tinker).  
Tested correct/incorrect answers for accuracy.




Task 4.3: Exams Frontend (4 days)  

Designed ExamView.vue and QuestionForm.vue for taking exams.  
Created API routes (/api/exams, /api/exams/{id}/questions) and integrated with Vue.js.  
Validation:  
Visited /exams/{id} and confirmed questions/options display.  
Submitted answers via frontend and verified in exam_results.  
Tested Arabic question display with Accept-Language: ar.





Key Deliverables

A multilingual exam and assessment system.
A frontend interface for students to take exams.


Sprint 5: Payments and Notifications (Weeks 9-10)
Objective
Implement payments, currency support, notifications, and static pages with a frontend.
Duration
2 weeks (10 working days)
Tasks and Deliverables

Task 5.1: Currency and Payments (4 days)  

Created models: Currency, CoursePrice.  
Enabled translations for code, name.  
Integrated Stripe for payments:  
Installed Stripe SDK (composer require stripe/stripe-php).  
Created PaymentController with processPayment.


Validation:  
Tested payment API (POST /api/payments) with Postman, confirming in Stripe Dashboard.  
Verified course price in course_prices (php artisan tinker).  
Confirmed currency symbol display based on language.




Task 5.2: Notifications and Pages (3 days)  

Created models: Notification, Page, Faq.  
Enabled translations for content, title, slug, question, answer.  
Developed NewCourseNotification and PageController.  
Validation:  
Tested API (GET /api/pages/about) with Postman for page content.  
Created a notification and verified in notifications table.  
Confirmed FAQ translation (Faq::first()->translate('ar')->question).




Task 5.3: Payments and Pages Frontend (3 days)  

Designed PaymentForm.vue and StaticPage.vue.  
Created API routes (/api/notifications, /api/pages/{slug}) and integrated with Vue.js.  
Validation:  
Visited /payment and confirmed payment form display.  
Visited /pages/about and verified content in selected language.  
Tested API (GET /api/notifications) for translated notifications.





Key Deliverables

A multilingual payment and currency system with Stripe integration.
Notifications and static pages with translations.
A frontend for payments and static pages.


Sprint 6: Testing and Deployment (Weeks 11-12)
Objective
Test the application, optimize performance, and deploy to production with API documentation.
Duration
2 weeks (10 working days)
Tasks and Deliverables

Task 6.1: Application Testing (4 days)  

Wrote unit tests for User, Course, Exam (including translations).  
Set up integration tests with Laravel Dusk:  
Installed Dusk (composer require --dev laravel/dusk).  
Tested authentication and payments (tests/Browser/AuthTest.php).


Validation:  
Ran unit tests (php artisan test) and confirmed all passed.  
Ran integration tests (php artisan dusk) and verified success.  
Ensured translation coverage (e.g., Arabic error messages).




Task 6.2: Performance Optimization and Deployment (3 days)  

Optimized performance:  
Cached translations with Redis (Cache::remember).  
Used Eager Loading (with('translations')).  
Installed Laravel Telescope for monitoring (composer require laravel/telescope).


Deployed to production:  
Set up a DigitalOcean server with Laravel Forge.  
Pushed code (git push) and ran migrations (php artisan migrate --force).


Validation:  
Visited the production site and confirmed all pages work.  
Monitored API performance with Telescope (/api/courses).  
Verified caching (Cache::get).




Task 6.3: API Documentation (3 days)  

Set up Swagger for API documentation:  
Installed l5-swagger (composer require darkaonline/l5-swagger).  
Configured Swagger and added PHPDoc comments for API routes.  
Generated documentation (php artisan l5-swagger:generate).


Validation:  
Visited /api/documentation and confirmed all API routes are listed.  
Tested an API request via Swagger UI (GET /api/institutes).  
Verified translation instructions (e.g., Accept-Language header).





Key Deliverables

A thoroughly tested and deployed application.
API documentation using Swagger.
Optimized performance with Redis caching.


Project Timeline



Sprint
Duration
Focus Area



1
Weeks 1-2
Environment and Database Setup


2
Weeks 3-4
User and Permission Management


3
Weeks 5-6
Institutes and Courses


4
Weeks 7-8
Exams and Assessments


5
Weeks 9-10
Payments and Notifications


6
Weeks 11-12
Testing and Deployment



Technology Stack

Backend: Laravel 11, MySQL, Redis  
Frontend: Vue.js, Tailwind CSS, Axios  
Packages: Laravel Translatable, Spatie Laravel Permission, Laravel Sanctum, Filament, Stripe, Swagger  
Testing: PHPUnit, Laravel Dusk  
Deployment: DigitalOcean, Laravel Forge


Future Enhancements

Add support for more languages beyond English and Arabic.  
Integrate a recommendation system for courses.  
Enhance the admin panel with analytics dashboards.

