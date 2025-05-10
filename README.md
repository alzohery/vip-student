<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIP Student - README</title>
    <style>
        body {
            font-family: 'Noto Serif Arabic', Arial, sans-serif; /* Keep Arabic font for potential Arabic display */
            line-height: 1.6;
            color: #333;
            background-color: #f5f5f5;
            margin: 0;
            padding: 0;
            /* direction: rtl;  No need for this in English */
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        header {
            background: linear-gradient(90deg, #007bff, #0056b3);
            color: white;
            padding: 20px;
            text-align: center;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        header h1 {
            margin: 0;
            font-size: 2.5em;
        }
        nav {
            background-color: #fff;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
        }
        nav ul {
            list-style: none;
            padding: 0;
            margin: 0;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
        }
        nav ul li {
            margin: 0 10px;
        }
        nav ul li a {
            text-decoration: none;
            color: #007bff;
            font-weight: bold;
        }
        nav ul li a:hover {
            color: #0056b3;
        }
        section {
            background-color: #fff;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        section h2 {
            color: #007bff;
            font-size: 1.8em;
            border-bottom: 2px solid #007bff;
            padding-bottom: 10px;
            margin-bottom: 20px;
        }
        section h3 {
            color: #333;
            font-size: 1.5em;
            margin-top: 20px;
        }
        section ul, section ol {
            margin: 10px 0;
            padding-left: 20px; /* Changed from right to left */
        }
        section ul li, section ol li {
            margin-bottom: 10px;
        }
        .code-block {
            background-color: #f8f9fa;
            border: 1px solid #ddd;
            padding: 15px;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
            direction: ltr;
            text-align: left;
            overflow-x: auto;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        table th, table td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: left; /* Changed from right to left */
        }
        table th {
            background-color: #007bff;
            color: white;
        }
        .erd-diagram {
            background-color: #e9ecef;
            padding: 15px;
            border-radius: 5px;
            font-family: 'Courier New', monospace;
            direction: ltr;
            text-align: left;
        }
        footer {
            text-align: center;
            padding: 20px;
            background-color: #007bff;
            color: white;
            border-radius: 8px;
            margin-top: 20px;
        }
        @media (max-width: 768px) {
            nav ul {
                flex-direction: column;
                align-items: center;
            }
            nav ul li {
                margin: 5px 0;
            }
            header h1 {
                font-size: 2em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>VIP Student Educational Platform</h1>
            <p>A comprehensive guide to developing and using a multilingual educational platform</p>
        </header>

        <nav>
            <ul>
                <li><a href="#overview">Overview</a></li>
                <li><a href="#objectives">Objectives</a></li>
                <li><a href="#features">Features</a></li>
                <li><a href="#tech-stack">Tech Stack</a></li>
                <li><a href="#database">Database Structure</a></li>
                <li><a href="#roadmap">Roadmap</a></li>
                <li><a href="#installation">Installation</a></li>
                <li><a href="#usage">Usage</a></li>
                <li><a href="#api">API Documentation</a></li>
                <li><a href="#contributing">Contributing</a></li>
                <li><a href="#license">License</a></li>
            </ul>
        </nav>

        <section id="overview">
            <h2>Overview</h2>
            <p>
                The <strong>VIP Student</strong> platform is an advanced educational platform aimed at providing a seamless educational experience for students, trainers, parents, and administrators. The platform supports multiple languages (such as Arabic and English) and offers comprehensive management of courses, exams, payments, and notifications, with a scalable and secure design. The platform is built using Laravel with robust translation support using the Laravel Translatable package.
            </p>
            <p>
                This file aims to provide a detailed guide for developers and users, including a project description, database structure, development plan, and installation and usage instructions.
            </p>
        </section>

        <section id="objectives">
            <h2>Objectives</h2>
            <ul>
                <li>Provide a multilingual educational platform that supports Arabic, English, and other languages.</li>
                <li>Enable institutes to manage courses, lessons, and exams with flexible categories and multi-currency pricing.</li>
                <li>Support role-based access control (administrator, trainer, student, parent).</li>
                <li>Integrate secure payment gateways and translated instant notifications.</li>
                <li>Ensure high performance using caching (Redis) and optimized database queries.</li>
                <li>Provide a user-friendly interface with a powerful administrative dashboard using Filament.</li>
                <li>Create comprehensive API documentation using Swagger.</li>
            </ul>
        </section>

        <section id="features">
            <h2>Features</h2>
            <ul>
                <li><strong>Multilingual Support</strong>: Translation of content for courses, exams, notifications, and pages using Laravel Translatable.</li>
                <li><strong>User Management</strong>: Roles (administrator, trainer, student, parent) with custom permissions via Spatie Laravel Permission.</li>
                <li><strong>Institute Management</strong>: Registration of institutes, uploading certificates, and management of social media and advertisements.</li>
                <li><strong>Course Management</strong>: Creation and categorization of courses, units, and lessons with support for various educational systems (Egyptian, British).</li>
                <li><strong>Exams and Assessments</strong>: Creation of exams (multiple choice, true/false, text) with result tracking.</li>
                <li><strong>Payments</strong>: Multi-currency pricing and secure payment processing via Stripe.</li>
                <li><strong>Notifications</strong>: Translated instant notifications for users.</li>
                <li><strong>User Interface</strong>: Responsive front-end using Vue.js and Tailwind CSS.</li>
                <li><strong>Administrative Dashboard</strong>: Management of users, courses, and settings via Filament.</li>
                <li><strong>Support System</strong>: Multilingual support tickets with translated messages.</li>
                <li><strong>Reports and Analytics</strong>: Trainer reports, exam results, and audit logs.</li>
            </ul>
        </section>

        <section id="tech-stack">
            <h2>Tech Stack</h2>
            <table>
                <tr>
                    <th>Category</th>
                    <th>Technology</th>
                </tr>
                <tr>
                    <td>Backend</td>
                    <td>Laravel 11, PHP 8.2</td>
                </tr>
                <tr>
                    <td>Frontend</td>
                    <td>Vue.js, Tailwind CSS</td>
                </tr>
                <tr>
                    <td>Database</td>
                    <td>MySQL</td>
                </tr>
                <tr>
                    <td>Caching</td>
                    <td>Redis</td>
                </tr>
                <tr>
                    <td>Authentication</td>
                    <td>Laravel Sanctum (JWT)</td>
                </tr>
                <tr>
                    <td>Authorization</td>
                    <td>Spatie Laravel Permission</td>
                </tr>
                <tr>
                    <td>Translation</td>
                    <td>Astrotomic Laravel Translatable</td>
                </tr>
                <tr>
                    <td>Control Panel</td>
                    <td>Filament</td>
                </tr>
                <tr>
                    <td>API Documentation</td>
                    <td>L5-Swagger</td>
                </tr>
                <tr>
                    <td>Payments</td>
                    <td>Stripe SDK</td>
                </tr>
                <tr>
                    <td>Testing</td>
                    <td>PHPUnit, Laravel Dusk</td>
                </tr>
                <tr>
                    <td>Deployment</td>
                    <td>Laravel Forge, DigitalOcean, Docker (Laravel Sail)</td>
                </tr>
                <tr>
                    <td>Version Control</td>
                    <td>Git, GitHub</td>
                </tr>
            </table>
        </section>

        <section id="database">
            <h2>Database Structure (ERD)</h2>
            <p>
                The database is designed to support the multilingual platform and modular structure. MySQL is used with separate translation tables for each entity that supports translation (such as courses, exams, notifications). The following is a summary of the main entities and relationships:
            </p>

            <h3>Main Entities</h3>
            <ol>
                <li><strong>Languages</strong> (<code>languages</code>): Stores language codes (e.g., <code>en</code>, <code>ar</code>) and their names.
                    <ul>
                        <li><strong>Fields</strong>: <code>id</code>, <code>code</code>, <code>name</code>, <code>is_default</code>, <code>created_at</code>, <code>updated_at</code></li>
                    </ul>
                </li>
                <li><strong>Users</strong> (<code>users</code>): Manages user accounts with roles and institute affiliations.
                    <ul>
                        <li><strong>Fields</strong>: <code>id</code>, <code>role_id</code>, <code>institute_id</code>, <code>name</code>, <code>email</code>, <code>password</code>, <code>city_id</code>, etc.</li>
                    </ul>
                </li>
                <li><strong>Roles</strong> (<code>roles</code>) and <strong>Permissions</strong> (<code>permissions</code>): Manages access control with translated names.
                    <ul>
                        <li><strong>Relationships</strong>: Many-to-Many relationship via <code>role_permissions</code>.</li>
                    </ul>
                </li>
                <li><strong>Institutes</strong> (<code>institutes</code>): Stores details of institutes, certificates, and communication methods.
                    <ul>
                        <li><strong>Fields</strong>: <code>id</code>, <code>city_id</code>, <code>approved</code>, <code>logo</code>, <code>training_license</code>, etc.</li>
                        <li><strong>Relationships</strong>: HasMany <code>institute_certificates</code>, <code>institute_communications</code>.</li>
                    </ul>
                </li>
                <li><strong>Courses</strong> (<code>courses</code>): Manages courses with prices, categories, and educational system.
                    <ul>
                        <li><strong>Fields</strong>: <code>id</code>, <code>institute_id</code>, <code>subject_id</code>, <code>educational_system</code>, <code>registration_start_date</code>, etc.</li>
                        <li><strong>Relationships</strong>: HasMany <code>course_units</code>, BelongsToMany <code>categories</code>, <code>sub_categories</code>, <code>tags</code>.</li>
                    </ul>
                </li>
                <li><strong>Lessons</strong> (<code>lessons</code>): Stores lesson details with types (online, offline, recorded, live).
                    <ul>
                        <li><strong>Fields</strong>: <code>id</code>, <code>course_unit_id</code>, <code>instructor_id</code>, <code>lesson_type</code>, <code>link</code>, etc.</li>
                    </ul>
                </li>
                <li><strong>Exams</strong> (<code>exams</code>) and <strong>Questions</strong> (<code>questions</code>): Manages assessments with translated content.
                    <ul>
                        <li><strong>Relationships</strong>: <code>exams</code> HasMany <code>questions</code>, <code>questions</code> HasMany <code>question_options</code>.</li>
                    </ul>
                </li>
                <li><strong>Payments</strong> (<code>payments</code>): Tracks payments with multi-currency support.
                    <ul>
                        <li><strong>Fields</strong>: <code>id</code>, <code>user_id</code>, <code>amount</code>, <code>currency_id</code>, <code>status</code>, etc.</li>
                    </ul>
                </li>
                <li><strong>Notifications</strong> (<code>notifications</code>): Manages user notifications with translated content.
                    <ul>
                        <li><strong>Fields</strong>: <code>id</code>, <code>user_id</code>, <code>is_read</code>, <code>created_at</code>, <code>updated_at</code>.</li>
                    </ul>
                </li>
            </ol>

            <h3>Main Relationships</h3>
            <ul>
                <li><strong>Users ↔ Roles</strong>: One-to-Many (a user has one role, a role has many users).</li>
                <li><strong>Institutes ↔ Courses</strong>: One-to-Many (an institute offers many courses).</li>
                <li><strong>Courses ↔ Course Units ↔ Lessons</strong>: Hierarchical structure (a course has units, a unit has lessons).</li>
                <li><strong>Exams ↔ Questions ↔ Question Options</strong>: Hierarchical structure (an exam has questions, a question has options).</li>
                <li><strong>Translations</strong>: Most entities (such as <code>courses</code>, <code>exams</code>, <code>notifications</code>) have translation tables linked to <code>languages.code</code>.</li>
            </ul>

            <h3>ERD Diagram</h3>
            <div class="erd-diagram">
                [Languages] --(one-to-many)-- [Translations]<br>
                   |<br>
                [Users] --(belongs-to)-- [Roles] --(many-to-many)-- [Permissions]<br>
                   |                         |<br>
                   | (owns/offers)          | (manages)<br>
                   |                         |<br>
                [Institutes] --(one-to-many)-- [Courses] --(one-to-many)-- [Course_Units] --(one-to-many)-- [Lessons]<br>
                   |                                                     |<br>
                   | (enrolls in)                                        | (assessed by)<br>
                   |                                                     |<br>
                [Enrollments]                                         [Exams] --(one-to-many)-- [Questions] --(one-to-many)-- [Question_Options]<br>
                   |                                                     |<br>
                   | (pays for)                                          | (results in)<br>
                   |                                                     |<br>
                [Payments] --(uses)-- [Currencies]                    [Exam_Results]<br>
                   |<br>
                [Notifications]
            </div>
            <p><strong>Note</strong>: A detailed diagram can be generated using tools like DBML or found in <code>docs/erd.png</code>.</p>
        </section>

        <section id="roadmap">
            <h2>Roadmap</h2>
            <p>
                The platform's development is divided into 6 sprints over 12 weeks, with details of subtasks and task lists for each sprint:
            </p>

            <h3>Sprint 1: Environment and Database Setup (Weeks 1-2)</h3>
            <p><strong>Objective</strong>: Set up the Laravel project, install packages, and create the database.</p>
            <p><strong>Duration</strong>: 10 working days</p>
            <ul>
                <li><strong>Task 1.1: Set up the development environment</strong>
                    <ul>
                        <li><strong>Subtask 1.1.1: Create the Laravel project</strong>
                            <ul>
                                <li>Install Laravel 11: <code>composer create-project laravel/laravel vip-student</code></li>
                                <li>Create a Git repository: <code>git init</code></li>
                                <li>Set up Laravel Sail: <code>./vendor/bin/sail up</code></li>
                            </ul>
                        </li>
                        <li><strong>Subtask 1.1.2: Install essential packages</strong>
                            <ul>
                                <li>Install <code>astrotomic/laravel-translatable</code>: <code>composer require astrotomic/laravel-translatable</code></li>
                                <li>Install <code>spatie/laravel-permission</code>: <code>composer require spatie/laravel-permission</code></li>
                                <li>Install <code>laravel/sanctum</code>: <code>composer require laravel/sanctum</code></li>
                            </ul>
                        </li>
                        <li><strong>Task Testing</strong>:
                            <ul>
                                <li>Run <code>php artisan serve</code> and check the Laravel page at <code>http://localhost:8000</code>.</li>
                                <li>Check the presence of packages in <code>vendor</code>: <code>ls vendor</code>.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li><strong>Task 1.2: Set up the database</strong>
                    <ul>
                        <li><strong>Subtask 1.2.1: Set up MySQL</strong>
                            <ul>
                                <li>Create a database: <code>CREATE DATABASE vip_student</code></li>
                                <li>Update <code>.env</code>: <code>DB_DATABASE=vip_student</code></li>
                                <li>Test the connection: <code>php artisan migrate:status</code></li>
                            </ul>
                        </li>
                        <li><strong>Subtask 1.2.2
                            <ul>
                                <li>Install Redis: <code>apt-get install redis-server</code></li>
                                <li>Update <code>.env</code>: <code>CACHE_DRIVER=redis</code></li>
                                <li>Test the connection: <code>redis-cli ping</code> (Response: <code>PONG</code>)</li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li><strong>Task 1.3: Create Migrations and Seeders</strong>
                    <ul>
                        <li><strong>Subtask 1.3.1: Write Migrations</strong>
                            <ul>
                                <li>Create Migrations for <code>languages</code>, <code>cities</code>, <code>users</code>, <code>roles</code>, <code>institutes</code>, etc.</li>
                                <li>Add indexes for <code>email</code> and translation tables.</li>
                            </ul>
                        </li>
                        <li><strong>Subtask 1.3.2: Create Seeders</strong>
                            <ul>
                                <li>Seeder for languages: <code>en</code>, <code>ar</code>.</li>
                                <li>Seeder for cities: Cairo, Riyadh.</li>
                                <li>Seeder for roles: Admin, Instructor, Student.</li>
                            </ul>
                        </li>
                        <li><strong>Task Testing</strong>:
                            <ul>
                                <li>Check the tables: <code>SHOW TABLES</code>.</li>
                                <li>Check the data: <code>Language::all()</code> in <code>php artisan tinker</code>.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
            </ul>
            <p><strong>Outputs</strong>: Configured Laravel project, ready MySQL/Redis database, completed Migrations and Seeders.</p>

            <h3>Sprint 2: User and Permission Management (Weeks 3-4)</h3>
            <p><strong>Objective</strong>: Implement authentication, roles, permissions, and the dashboard.</p>
            <p><strong>Duration</strong>: 10 working days</p>
            <ul>
                <li><strong>Task 2.1: Create user models</strong>
                    <ul>
                        <li><strong>Subtask 2.1.1: Set up models</strong>
                            <ul>
                                <li><code>User</code> model with <code>password</code> encryption.</li>
                                <li><code>Role</code> model with <code>name</code> translation.</li>
                                <li><code>Permission</code> model with <code>name</code>, <code>description</code> translation.</li>
                            </ul>
                        </li>
                        <li><strong>Subtask 2.1.2: Set up relationships</strong>
                            <ul>
                                <li><code>belongsTo</code> relationship between <code>User</code> and <code>Role</code>.</li>
                                <li><code>hasMany</code> relationship between <code>Role</code> and <code>User</code>.</li>
                                <li><code>role_permissions</code> relationship using Spatie.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li><strong>Task 2.2: Implement login and translations</strong>
                    <ul>
                        <li><strong>Subtask 2.2.1: Set up login</strong>
                            <ul>
                                <li>Install Sanctum: <code>composer require laravel/sanctum</code>.</li>
                                <li>Create <code>AuthController</code>: <code>php artisan make:controller AuthController</code>.</li>
                                <li>Add <code>login</code> and <code>register</code> functions.</li>
                            </ul>
                        </li>
                        <li><strong>Subtask 2.2.2: Support translations</strong>
                            <ul>
                                <li>Create <code>SetLocale</code> Middleware.</li>
                                <li>Set up translation files: <code>lang/ar/auth.php</code>, <code>lang/en/auth.php</code>.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li><strong>Task 2.3: Manage permissions and the dashboard</strong>
                    <ul>
                        <li><strong>Subtask 2.3.1: Set up permissions</strong>
                            <ul>
                                <li>Create permissions such as <code>edit_users</code>, <code>view_courses</code>.</li>
                                <li>Set up Middleware for <code>role</code> and <code>permission</code>.</li>
                            </ul>
                        </li>
                        <li><strong>Subtask 2.3.2: Create a dashboard</strong>
                            <ul>
                                <li>Install Filament: <code>composer require filament/filament</code>.</li>
                                <li>Create resources: <code>php artisan make:filament-resource User</code>.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
            </ul>
            <p><strong>Outputs</strong>: User system, multilingual login, Filament dashboard.</p>

            <h3>Sprint 3: Institute and Course Management (Weeks 5-6)</h3>
            <p><strong>Objective</strong>: Develop management for institutes, courses, and categories.</p>
            <p><strong>Duration</strong>: 10 working days</p>
            <ul>
                <li><strong>Task 3.1: Create institute models</strong>
                    <ul>
                        <li><code>Institute</code> model with translation: <code>name</code>, <code>description</code>.</li>
                        <li><code>hasMany</code> relationship with <code>InstituteCertificate</code>.</li>
                    </ul>
                </li>
                <li><strong>Task 3.2: Manage courses and categories</strong>
                    <ul>
                        <li><code>Course</code> model with translation: <code>title</code>, <code>description</code>.</li>
                        <li><code>course_categories</code> relationships using <code>belongsToMany</code>.</li>
                    </ul>
                </li>
                <li><strong>Task 3.3: Create institute and course interface</strong>
                    <ul>
                        <li>Set up Vue.js and Tailwind CSS.</li>
                        <li>Integrate API with Axios.</li>
                    </ul>
                </li>
            </ul>
            <p><strong>Outputs</strong>: Institute and course management system, front-end interface.</p>

            <h3>Sprint 4: Exams and Assessments (Weeks 7-8)</h3>
            <p><strong>Objective</strong>: Implement exams, questions, and results.</p>
            <p><strong>Duration</strong>: 10 working days</p>
            <ul>
                <li><strong>Task 4.1: Create exam models</strong>
                    <ul>
                        <li><code>Exam</code> model with translation: <code>title</code>.</li>
                        <li><code>hasMany</code> relationship with <code>Question</code>.</li>
                    </ul>
                </li>
                <li><strong>Task 4.2: Manage answers and results</strong>
                    <ul>
                        <li><code>Answer</code> and <code>ExamResult</code> models.</li>
                        <li>Logic to calculate scores.</li>
                    </ul>
                </li>
                <li><strong>Task 4.3: Create exam interface</strong>
                    <ul>
                        <li>Design <code>ExamView.vue</code>.</li>
                        <li>Integrate API for questions.</li>
                    </ul>
                </li>
            </ul>
            <p><strong>Outputs</strong>: Exam system, front-end exam interface.</p>

            <h3>Sprint 5: Payments and Notifications (Weeks 9-10)</h3>
            <p><strong>Objective</strong>: Integrate payments, currencies, notifications, and pages.</p>
            <p><strong>Duration</strong>: 10 working days</p>
            <ul>
                <li><strong>Task 5.1: Manage currencies and payments</strong>
                    <ul>
                        <li><code>Currency</code> model with translation: <code>code</code>, <code>name</code>.</li>
                        <li>Integrate Stripe SDK.</li>
                    </ul>
                </li>
                <li><strong>Task 5.2: Manage notifications and pages</strong>
                    <ul>
                        <li><code>Notification</code> model with translation: <code>content</code>.</li>
                        <li><code>Page</code> model with translation: <code>title</code>, <code>slug</code>.</li>
                    </ul>
                </li>
                <li><strong>Task 5.3: Create payment and page interface</strong>
                    <ul>
                        <li>Design <code>PaymentForm.vue</code>.</li>
                        <li>Integrate API for notifications.</li>
                    </ul>
                </li>
            </ul>
            <p><strong>Outputs</strong>: Payment system, notifications, static pages.</p>

            <h3>Sprint 6: Testing and Launch (Weeks 11-12)</h3>
            <p><strong>Objective</strong>: Test the application, optimize performance, and deploy.</p>
            <p><strong>Duration</strong>: 10 working days</p>
            <ul>
                <li><strong>Task 6.1: Test the application</strong>
                    <ul>
                        <li>Unit tests for <code>User</code>, <code>Course</code>.</li>
                        <li>Integration tests using Laravel Dusk.</li>
                    </ul>
                </li>
                <li><strong>Task 6.2: Optimize performance and deploy</strong>
                    <ul>
                        <li>Set up Cache with Redis.</li>
                        <li>Deploy to DigitalOcean using Forge.</li>
                    </ul>
                </li>
                <li><strong>Task 6.3: Document the API</strong>
                    <ul>
                        <li>Install L5-Swagger.</li>
                        <li>Create a documentation page: <code>/api/documentation</code>.</li>
                    </ul>
                </li>
            </ul>
            <p><strong>Outputs</strong>: Tested and deployed application, API documentation, optimized performance.</p>
        </section>

        <section id="installation">
            <h2>Installation</h2>
            <p>Follow the steps below to install the project locally:</p>
            <h3>Requirements</h3>
            <ul>
                <li>PHP 8.2+</li>
                <li>Composer</li>
                <li>Node.js (v16+)</li>
                <li>MySQL (v8+)</li>
                <li>Redis</li>
                <li>Git</li>
                <li>Docker (optional for Laravel Sail)</li>
            </ul>
            <h3>Steps</h3>
            <ol>
                <li><strong>Clone the repository</strong>:
                    <div class="code-block">
                        git clone https://github.com/your-repo/vip-student.git<br>
                        cd vip-student
                    </div>
                </li>
                <li><strong>Install dependencies</strong>:
                    <div class="code-block">
                        composer install<br>
                        npm install
                    </div>
                </li>
                <li><strong>Set up environment variables</strong>:
                    <div class="code-block">
                        cp .env.example .env
                    </div>
                    <p>Update <code>.env</code> with database, Redis, and Stripe settings:</p>
                    <div class="code-block">
                        DB_CONNECTION=mysql<br>
                        DB_DATABASE=vip_student<br>
                        DB_USERNAME=root<br>
                        DB_PASSWORD=<br>
                        CACHE_DRIVER=redis<br>
                        REDIS_HOST=127.0.0.1<br>
                        STRIPE_KEY=your_stripe_key<br>
                        STRIPE_SECRET=your_stripe_secret
                    </div>
                </li>
                <li><strong>Generate application key</strong>:
                    <div class="code-block">
                        php artisan key:generate
                    </div>
                </li>
                <li><strong>Run Migrations and Seeders</strong>:
                    <div class="code-block">
                        php artisan migrate<br>
                        php artisan db:seed
                    </div>
                </li>
                <li><strong>Run the server</strong>:
                    <div class="code-block">
                        php artisan serve<br>
                        npm run dev
                    </div>
                    <p>Or using Sail:</p>
                    <div class="code-block">
                        ./vendor/bin/sail up
                    </div>
                </li>
                <li><strong>Access the application</strong>:
                    <ul>
                        <li>Backend: <code>http://localhost:8000</code></li>
                        <li>Frontend: <code>http://localhost:5173</code></li>
                        <li>Dashboard: <code>http://localhost:8000/admin</code></li>
                    </ul>
                </li>
            </ol>
        </section>

        <section id="usage">
            <h2>Usage</h2>
            <ul>
                <li><strong>Users</strong>: Register or log in to access courses and exams.</li>
                <li><strong>Trainers</strong>: Manage lessons, create exams, and submit reports via the Filament dashboard.</li>
                <li><strong>Administrators</strong>: Use the Filament dashboard to manage users and institutes.</li>
                <li><strong>Students</strong>: Enroll in courses, take exams, and view results.</li>
                <li><strong>Parents</strong>: Monitor student progress and receive notifications.</li>
                <li><strong>API</strong>: Use endpoints like <code>/api/courses</code> with the <code>Accept-Language</code> header for translation.</li>
            </ul>
        </section>

        <section id="api">
            <h2>API Documentation</h2>
            <p>
                The API is documented using L5-Swagger. After installation, the documentation can be accessed at:
            </p>
            <ul>
                <li><strong>Link</strong>: <code>http://localhost:8000/api/documentation</code></li>
                <li><strong>Features</strong>:
                    <ul>
                        <li>Displays all endpoints (e.g., <code>/api/institutes</code>, <code>/api/courses</code>).</li>
                        <li>Supports testing endpoints directly via Swagger UI.</li>
                        <li>Includes translation instructions (e.g., <code>Accept-Language: ar</code>).</li>
                    </ul>
                </li>
            </ul>
        </section>

        <section id="contributing">
            <h2>Contributing</h2>
            <p>We welcome contributions to the VIP Student platform! To contribute:</p>
            <ol>
                <li>Fork the repository.</li>
                <li>Create a new branch: <code>git checkout -b feature/your-feature</code>.</li>
                <li>Commit your changes: <code>git commit -m "Add your feature"</code>.</li>
                <li>Push the branch: <code>git push origin feature/your-feature</code>.</li>
                <li>Open a Pull Request with a detailed description.</li>
            </ol>
            <p>Please adhere to the <a href="CODE_OF_CONDUCT.md">Code of Conduct</a> and follow the <a href="CONTRIBUTING.md">Contribution Guidelines</a>.</p>
        </section>

        <section id="license">
            <h2>License</h2>
            <p>This project is licensed under the MIT License. See the <a href="LICENSE">LICENSE</a> file for details.</p>
        </section>

        <footer>
            <p>&copy; 2025 VIP Student. All rights reserved.</p>
        </footer>
    </div>
</body>
</html>
