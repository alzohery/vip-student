<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>
<script type="text/javascript">
        var gk_isXlsx = false;
        var gk_xlsxFileLookup = {};
        var gk_fileData = {};
        function filledCell(cell) {
          return cell !== '' && cell != null;
        }
        function loadFileData(filename) {
        if (gk_isXlsx && gk_xlsxFileLookup[filename]) {
            try {
                var workbook = XLSX.read(gk_fileData[filename], { type: 'base64' });
                var firstSheetName = workbook.SheetNames[0];
                var worksheet = workbook.Sheets[firstSheetName];

                // Convert sheet to JSON to filter blank rows
                var jsonData = XLSX.utils.sheet_to_json(worksheet, { header: 1, blankrows: false, defval: '' });
                // Filter out blank rows (rows where all cells are empty, null, or undefined)
                var filteredData = jsonData.filter(row => row.some(filledCell));

                // Heuristic to find the header row by ignoring rows with fewer filled cells than the next row
                var headerRowIndex = filteredData.findIndex((row, index) =>
                  row.filter(filledCell).length >= filteredData[index + 1]?.filter(filledCell).length
                );
                // Fallback
                if (headerRowIndex === -1 || headerRowIndex > 25) {
                  headerRowIndex = 0;
                }

                // Convert filtered JSON back to CSV
                var csv = XLSX.utils.aoa_to_sheet(filteredData.slice(headerRowIndex)); // Create a new sheet from filtered array of arrays
                csv = XLSX.utils.sheet_to_csv(csv, { header: 1 });
                return csv;
            } catch (e) {
                console.error(e);
                return "";
            }
        }
        return gk_fileData[filename] || "";
        }
        </script><!DOCTYPE html>
<html lang="en" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIP Student - README</title>
    <style>
        body {
            font-family: 'Noto Serif Arabic', Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f5f5f5;
            margin: 0;
            padding: 0;
            direction: rtl;
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
            padding-right: 20px;
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
            text-align: right;
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
            <h1>منصة VIP Student التعليمية</h1>
            <p>دليل شامل لتطوير واستخدام منصة تعليمية متعددة اللغات</p>
        </header>

        <nav>
            <ul>
                <li><a href="#overview">نظرة عامة</a></li>
                <li><a href="#objectives">الأهداف</a></li>
                <li><a href="#features">الميزات</a></li>
                <li><a href="#tech-stack">التقنيات</a></li>
                <li><a href="#database">هيكلية قاعدة البيانات</a></li>
                <li><a href="#roadmap">خارطة الطريق</a></li>
                <li><a href="#installation">التثبيت</a></li>
                <li><a href="#usage">الاستخدام</a></li>
                <li><a href="#api">توثيق API</a></li>
                <li><a href="#contributing">المساهمة</a></li>
                <li><a href="#license">الترخيص</a></li>
            </ul>
        </nav>

        <section id="overview">
            <h2>نظرة عامة</h2>
            <p>
                منصة <strong>VIP Student</strong> هي منصة تعليمية متقدمة تهدف إلى توفير تجربة تعليمية سلسة للطلاب، المدربين، أولياء الأمور، والمسؤولين. تدعم المنصة تعدد اللغات (مثل العربية والإنجليزية)، وتوفر إدارة شاملة للدورات، الاختبارات، المدفوعات، والإشعارات، مع تصميم قابل للتوسع وآمن. تم بناء المنصة باستخدام Laravel مع دعم قوي للترجمة باستخدام حزمة Laravel Translatable.
            </p>
            <p>
                يهدف هذا الملف إلى توفير دليل مفصل للمطورين والمستخدمين، يشمل وصف المشروع، هيكلية قاعدة البيانات، خطة التطوير، وتعليمات التثبيت والاستخدام.
            </p>
        </section>

        <section id="objectives">
            <h2>الأهداف</h2>
            <ul>
                <li>توفير منصة تعليمية متعددة اللغات تدعم العربية، الإنجليزية، ولغات أخرى.</li>
                <li>تمكين المعاهد من إدارة الدورات، الدروس، والاختبارات مع تصنيفات مرنة وأسعار متعددة العملات.</li>
                <li>دعم التحكم في الوصول بناءً على الأدوار (مسؤول، مدرب، طالب، ولي أمر).</li>
                <li>دمج بوابات دفع آمنة وإشعارات فورية مترجمة.</li>
                <li>ضمان الأداء العالي باستخدام التخزين المؤقت (Redis) وتحسين استعلامات قاعدة البيانات.</li>
                <li>توفير واجهة مستخدم سهلة الاستخدام مع لوحة تحكم إدارية قوية باستخدام Filament.</li>
                <li>إنشاء توثيق شامل لـ API باستخدام Swagger.</li>
            </ul>
        </section>

        <section id="features">
            <h2>الميزات</h2>
            <ul>
                <li><strong>دعم متعدد اللغات</strong>: ترجمة المحتوى للدورات، الاختبارات، الإشعارات، والصفحات باستخدام Laravel Translatable.</li>
                <li><strong>إدارة المستخدمين</strong>: أدوار (مسؤول، مدرب، طالب، ولي أمر) مع صلاحيات مخصصة عبر Spatie Laravel Permission.</li>
                <li><strong>إدارة المعاهد</strong>: تسجيل المعاهد، رفع الشهادات، وإدارة وسائل التواصل والإعلانات.</li>
                <li><strong>إدارة الدورات</strong>: إنشاء وتصنيف الدورات، الوحدات، والدروس مع دعم أنظمة تعليمية متنوعة (مصري، بريطاني).</li>
                <li><strong>الاختبارات والتقييمات</strong>: إنشاء اختبارات (اختيار متعدد، صح/خطأ، نصوص) مع تتبع النتائج.</li>
                <li><strong>المدفوعات</strong>: أسعار متعددة العملات ومعالجة دفع آمنة عبر Stripe.</li>
                <li><strong>الإشعارات</strong>: إشعارات فورية مترجمة للمستخدمين.</li>
                <li><strong>واجهة المستخدم</strong>: واجهة أمامية سريعة الاستجابة باستخدام Vue.js وTailwind CSS.</li>
                <li><strong>لوحة التحكم الإدارية</strong>: إدارة المستخدمين، الدورات، والإعدادات عبر Filament.</li>
                <li><strong>نظام الدعم</strong>: تذاكر دعم متعددة اللغات مع رسائل مترجمة.</li>
                <li><strong>التقارير والتحليلات</strong>: تقارير المدربين، نتائج الاختبارات، وسجلات التدقيق.</li>
            </ul>
        </section>

        <section id="tech-stack">
            <h2>التقنيات المستخدمة</h2>
            <table>
                <tr>
                    <th>الفئة</th>
                    <th>التقنية</th>
                </tr>
                <tr>
                    <td>الواجهة الخلفية</td>
                    <td>Laravel 11, PHP 8.2</td>
                </tr>
                <tr>
                    <td>الواجهة الأمامية</td>
                    <td>Vue.js, Tailwind CSS</td>
                </tr>
                <tr>
                    <td>قاعدة البيانات</td>
                    <td>MySQL</td>
                </tr>
                <tr>
                    <td>التخزين المؤقت</td>
                    <td>Redis</td>
                </tr>
                <tr>
                    <td>المصادقة</td>
                    <td>Laravel Sanctum (JWT)</td>
                </tr>
                <tr>
                    <td>الصلاحيات</td>
                    <td>Spatie Laravel Permission</td>
                </tr>
                <tr>
                    <td>الترجمة</td>
                    <td>Astrotomic Laravel Translatable</td>
                </tr>
                <tr>
                    <td>لوحة التحكم</td>
                    <td>Filament</td>
                </tr>
                <tr>
                    <td>توثيق API</td>
                    <td>L5-Swagger</td>
                </tr>
                <tr>
                    <td>المدفوعات</td>
                    <td>Stripe SDK</td>
                </tr>
                <tr>
                    <td>الاختبار</td>
                    <td>PHPUnit, Laravel Dusk</td>
                </tr>
                <tr>
                    <td>النشر</td>
                    <td>Laravel Forge, DigitalOcean, Docker (Laravel Sail)</td>
                </tr>
                <tr>
                    <td>إدارة الإصدارات</td>
                    <td>Git, GitHub</td>
                </tr>
            </table>
        </section>

        <section id="database">
            <h2>هيكلية قاعدة البيانات (ERD)</h2>
            <p>
                تم تصميم قاعدة البيانات لدعم المنصة متعددة اللغات والهيكلية المعيارية. يتم استخدام MySQL مع جداول ترجمة منفصلة لكل كيان يدعم الترجمة (مثل الدورات، الاختبارات، الإشعارات). يلي ملخص للكيانات والعلاقات الرئيسية:
            </p>

            <h3>الكيانات الرئيسية</h3>
            <ol>
                <li><strong>اللغات</strong> (<code>languages</code>): تخزن رموز اللغات (مثل <code>en</code>، <code>ar</code>) وأسماءها.
                    <ul>
                        <li><strong>الحقول</strong>: <code>id</code>, <code>code</code>, <code>name</code>, <code>is_default</code>, <code>created_at</code>, <code>updated_at</code></li>
                    </ul>
                </li>
                <li><strong>المستخدمون</strong> (<code>users</code>): تدير حسابات المستخدمين مع الأدوار وانتماءات المعاهد.
                    <ul>
                        <li><strong>الحقول</strong>: <code>id</code>, <code>role_id</code>, <code>institute_id</code>, <code>name</code>, <code>email</code>, <code>password</code>, <code>city_id</code>, إلخ.</li>
                    </ul>
                </li>
                <li><strong>الأدوار</strong> (<code>roles</code>) و<strong>الصلاحيات</strong> (<code>permissions</code>): تدير التحكم في الوصول مع أسماء مترجمة.
                    <ul>
                        <li><strong>العلاقات</strong>: علاقة Many-to-Many عبر <code>role_permissions</code>.</li>
                    </ul>
                </li>
                <li><strong>المعاهد</strong> (<code>institutes</code>): تخزن تفاصيل المعاهد، الشهادات، ووسائل التواصل.
                    <ul>
                        <li><strong>الحقول</strong>: <code>id</code>, <code>city_id</code>, <code>approved</code>, <code>logo</code>, <code>training_license</code>, إلخ.</li>
                        <li><strong>العلاقات</strong>: HasMany <code>institute_certificates</code>, <code>institute_communications</code>.</li>
                    </ul>
                </li>
                <li><strong>الدورات</strong> (<code>courses</code>): تدير الدورات مع الأسعار، التصنيفات، والنظام التعليمي.
                    <ul>
                        <li><strong>الحقول</strong>: <code>id</code>, <code>institute_id</code>, <code>subject_id</code>, <code>educational_system</code>, <code>registration_start_date</code>, إلخ.</li>
                        <li><strong>العلاقات</strong>: HasMany <code>course_units</code>, BelongsToMany <code>categories</code>, <code>sub_categories</code>, <code>tags</code>.</li>
                    </ul>
                </li>
                <li><strong>الدروس</strong> (<code>lessons</code>): تخزن تفاصيل الدروس مع أنواع (أونلاين، أوفلاين، مسجل، مباشر).
                    <ul>
                        <li><strong>الحقول</strong>: <code>id</code>, <code>course_unit_id</code>, <code>instructor_id</code>, <code>lesson_type</code>, <code>link</code>, إلخ.</li>
                    </ul>
                </li>
                <li><strong>الاختبارات</strong> (<code>exams</code>) و<strong>الأسئلة</strong> (<code>questions</code>): تدير التقييمات مع محتوى مترجم.
                    <ul>
                        <li><strong>العلاقات</strong>: <code>exams</code> HasMany <code>questions</code>, <code>questions</code> HasMany <code>question_options</code>.</li>
                    </ul>
                </li>
                <li><strong>المدفوعات</strong> (<code>payments</code>): تتبع المدفوعات مع دعم متعدد العملات.
                    <ul>
                        <li><strong>الحقول</strong>: <code>id</code>, <code>user_id</code>, <code>amount</code>, <code>currency_id</code>, <code>status</code>, إلخ.</li>
                    </ul>
                </li>
                <li><strong>الإشعارات</strong> (<code>notifications</code>): تدير إشعارات المستخدمين مع محتوى مترجم.
                    <ul>
                        <li><strong>الحقول</strong>: <code>id</code>, <code>user_id</code>, <code>is_read</code>, <code>created_at</code>, <code>updated_at</code>.</li>
                    </ul>
                </li>
            </ol>

            <h3>العلاقات الرئيسية</h3>
            <ul>
                <li><strong>المستخدمون ↔ الأدوار</strong>: One-to-Many (مستخدم له دور واحد، دور له عدة مستخدمين).</li>
                <li><strong>المعاهد ↔ الدورات</strong>: One-to-Many (معهد يقدم عدة دورات).</li>
                <li><strong>الدورات ↔ وحدات الدورات ↔ الدروس</strong>: هيكلية هرمية (دورة بها وحدات، وحدة بها دروس).</li>
                <li><strong>الاختبارات ↔ الأسئلة ↔ خيارات الأسئلة</strong>: هيكلية هرمية (اختبار به أسئلة، سؤال به خيارات).</li>
                <li><strong>الترجمات</strong>: معظم الكيانات (مثل <code>courses</code>، <code>exams</code>، <code>notifications</code>) لها جداول ترجمة مرتبطة بـ < UEFI code>languages.code</code>.</li>
            </ul>

            <h3>رسم تخطيطي لـ ERD</h3>
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
            <p><strong>ملاحظة</strong>: يمكن إنشاء رسم تخطيطي مفصل باستخدام أدوات مثل DBML أو العثور عليه في <code>docs/erd.png</code>.</p>
        </section>

        <section id="roadmap">
            <h2>خارطة الطريق</h2>
            <p>
                تم تقسيم تطوير المنصة إلى 6 مراحل (Sprints) على مدى 12 أسبوعًا، مع تفاصيل المهام الفرعية وقوائم المهام لكل مرحلة:
            </p>

            <h3>Sprint 1: إعداد البيئة وقاعدة البيانات (الأسبوع 1-2)</h3>
            <p><strong>الهدف</strong>: إعداد مشروع Laravel، تثبيت الحزم، وإنشاء قاعدة البيانات.</p>
            <p><strong>المدة</strong>: 10 أيام عمل</p>
            <ul>
                <li><strong>المهمة 1.1: إعداد بيئة التطوير</strong>
                    <ul>
                        <li><strong>المهمة الفرعية 1.1.1: إنشاء مشروع Laravel</strong>
                            <ul>
                                <li>تثبيت Laravel 11: <code>composer create-project laravel/laravel vip-student</code></li>
                                <li>إنشاء مستودع Git: <code>git init</code></li>
                                <li>إعداد Laravel Sail: <code>./vendor/bin/sail up</code></li>
                            </ul>
                        </li>
                        <li><strong>المهمة الفرعية 1.1.2: تثبيت الحزم الأساسية</strong>
                            <ul>
                                <li>تثبيت <code>astrotomic/laravel-translatable</code>: <code>composer require astrotomic/laravel-translatable</code></li>
                                <li>تثبيت <code>spatie/laravel-permission</code>: <code>composer require spatie/laravel-permission</code></li>
                                <li>تثبيت <code>laravel/sanctum</code>: <code>composer require laravel/sanctum</code></li>
                            </ul>
                        </li>
                        <li><strong>اختبار المهمة</strong>:
                            <ul>
                                <li>تشغيل <code>php artisan serve</code> والتحقق من صفحة Laravel على <code>http://localhost:8000</code>.</li>
                                <li>التحقق من وجود الحزم في <code>vendor</code>: <code>ls vendor</code>.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li><strong>المهمة 1.2: إعداد قاعدة البيانات</strong>
                    <ul>
                        <li><strong>المهمة الفرعية 1.2.1: إعداد MySQL</strong>
                            <ul>
                                <li>إنشاء قاعدة بيانات: <code>CREATE DATABASE vip_student</code></li>
                                <li>تحديث <code>.env</code>: <code>DB_DATABASE=vip_student</code></li>
                                <li>اختبار الاتصال: <code>php artisan migrate:status</code></li>
                            </ul>
                        </li>
                        <li><strong>المهمة الفرعية 1.2.2: إعداد Redis</strong>
                            <ul>
                                <li>تثبيت Redis: <code>apt-get install redis-server</code></li>
                                <li>تحديث <code>.env</code>: <code>CACHE_DRIVER=redis</code></li>
                                <li>اختبار الاتصال: <code>redis-cli ping</code> (الرد: <code>PONG</code>)</li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li><strong>المهمة 1.3: إنشاء Migrations وSeeders</strong>
                    <ul>
                        <li><strong>المهمة الفرعية 1.3.1: كتابة Migrations</strong>
                            <ul>
                                <li>إنشاء Migration لـ <code>languages</code>, <code>cities</code>, <code>users</code>, <code>roles</code>, <code>institutes</code>, إلخ.</li>
                                <li>إضافة فهارس لـ <code>email</code> وجداول الترجمة.</li>
                            </ul>
                        </li>
                        <li><strong>المهمة الفرعية 1.3.2: إنشاء Seeders</strong>
                            <ul>
                                <li>Seeder للغات: <code>en</code>, <code>ar</code>.</li>
                                <li>Seeder للمدن: القاهرة، الرياض.</li>
                                <li>Seeder للأدوار: Admin، Instructor، Student.</li>
                            </ul>
                        </li>
                        <li><strong>اختبار المهمة</strong>:
                            <ul>
                                <li>التحقق من الجداول: <code>SHOW TABLES</code>.</li>
                                <li>التحقق من البيانات: <code>Language::all()</code> في <code>php artisan tinker</code>.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
            </ul>
            <p><strong>المخرجات</strong>: مشروع Laravel مهيأ، قاعدة بيانات MySQL/Redis جاهزة، Migrations وSeeders مكتملة.</p>

            <h3>Sprint 2: إدارة المستخدمين والصلاحيات (الأسبوع 3-4)</h3>
            <p><strong>الهدف</strong>: تنفيذ المصادقة، الأدوار، الصلاحيات، ولوحة التحكم.</p>
            <p><strong>المدة</strong>: 10 أيام عمل</p>
            <ul>
                <li><strong>المهمة 2.1: إنشاء نماذج المستخدمين</strong>
                    <ul>
                        <li><strong>المهمة الفرعية 2.1.1: إعداد النماذج</strong>
                            <ul>
                                <li>نموذج <code>User</code> مع تشفير <code>password</code>.</li>
                                <li>نموذج <code>Role</code> مع ترجمة <code>name</code>.</li>
                                <li>نموذج <code>Permission</code> مع ترجمة <code>name</code>, <code>description</code>.</li>
                            </ul>
                        </li>
                        <li><strong>المهمة الفرعية 2.1.2: إعداد العلاقات</strong>
                            <ul>
                                <li>علاقة <code>belongsTo</code> بين <code>User</code> و<code>Role</code>.</li>
                                <li>علاقة <code>hasMany</code> بين <code>Role</code> و<code>User</code>.</li>
                                <li>علاقة <code>role_permissions</code> باستخدام Spatie.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li><strong>المهمة 2.2: تنفيذ تسجيل الدخول والترجمات</strong>
                    <ul>
                        <li><strong>المهمة الفرعية 2.2.1: إعداد تسجيل الدخول</strong>
                            <ul>
                                <li>تثبيت Sanctum: <code>composer require laravel/sanctum</code>.</li>
                                <li>إنشاء <code>AuthController</code>: <code>php artisan make:controller AuthController</code>.</li>
                                <li>إضافة دوال <code>login</code> و<code>register</code>.</li>
                            </ul>
                        </li>
                        <li><strong>المهمة الفرعية 2.2.2: دعم الترجمات</strong>
                            <ul>
                                <li>إنشاء Middleware <code>SetLocale</code>.</li>
                                <li>إعداد ملفات ترجمة: <code>lang/ar/auth.php</code>, <code>lang/en/auth.php</code>.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
                <li><strong>المهمة 2.3: إدارة الصلاحيات ولوحة التحكم</strong>
                    <ul>
                        <li><strong>المهمة الفرعية 2.3.1: إعداد الصلاحيات</strong>
                            <ul>
                                <li>إنشاء صلاحيات مثل <code>edit_users</code>, <code>view_courses</code>.</li>
                                <li>إعداد Middleware لـ <code>role</code> و<code>permission</code>.</li>
                            </ul>
                        </li>
                        <li><strong>المهمة الفرعية 2.3.2: إنشاء لوحة تحكم</strong>
                            <ul>
                                <li>تثبيت Filament: <code>composer require filament/filament</code>.</li>
                                <li>إنشاء موارد: <code>php artisan make:filament-resource User</code>.</li>
                            </ul>
                        </li>
                    </ul>
                </li>
            </ul>
            <p><strong>المخرجات</strong>: نظام مستخدمين، تسجيل دخول متعدد اللغات، لوحة تحكم Filament.</p>

            <h3>Sprint 3: إدارة المعاهد والدورات (الأسبوع 5-6)</h3>
            <p><strong>الهدف</strong>: تطوير إدارة المعاهد، الدورات، والتصنيفات.</p>
            <p><strong>المدة</strong>: 10 أيام عمل</p>
            <ul>
                <li><strong>المهمة 3.1: إنشاء نماذج المعاهد</strong>
                    <ul>
                        <li>نموذج <code>Institute</code> مع ترجمة: <code>name</code>, <code>description</code>.</li>
                        <li>علاقة <code>hasMany</code> مع <code>InstituteCertificate</code>.</li>
                    </ul>
                </li>
                <li><strong>المهمة 3.2: إدارة الدورات والتصنيفات</strong>
                    <ul>
                        <li>نموذج <code>Course</code> مع ترجمة: <code>title</code>, <code>description</code>.</li>
                        <li>علاقات <code>course_categories</code> باستخدام <code>belongsToMany</code>.</li>
                    </ul>
                </li>
                <li><strong>المهمة 3.3: إنشاء واجهة المعاهد والدورات</strong>
                    <ul>
                        <li>إعداد Vue.js وTailwind CSS.</li>
                        <li>دمج API مع Axios.</li>
                    </ul>
                </li>
            </ul>
            <p><strong>المخرجات</strong>: نظام إدارة المعاهد والدورات، واجهة أمامية.</p>

            <h3>Sprint 4: الاختبارات والتقييمات (الأسبوع 7-8)</h3>
            <p><strong>الهدف</strong>: تنفيذ الاختبارات، الأسئلة، والنتائج.</p>
            <p><strong>المدة</strong>: 10 أيام عمل</p>
            <ul>
                <li><strong>المهمة 4.1: إنشاء نماذج الاختبارات</strong>
                    <ul>
                        <li>نموذج <code>Exam</code> مع ترجمة: <code>title</code>.</li>
                        <li>علاقة <code>hasMany</code> مع <code>Question</code>.</li>
                    </ul>
                </li>
                <li><strong>المهمة 4.2: إدارة الإجابات والنتائج</strong>
                    <ul>
                        <li>نموذج <code>Answer</code> و<code>ExamResult</code>.</li>
                        <li>منطق لحساب الدرجات.</li>
                    </ul>
                </li>
                <li><strong>المهمة 4.3: إنشاء واجهة الاختبارات</strong>
                    <ul>
                        <li>تصميم <code>ExamView.vue</code>.</li>
                        <li>دمج API للأسئلة.</li>
                    </ul>
                </li>
            </ul>
            <p><strong>المخرجات</strong>: نظام اختبارات، واجهة أمامية للاختبارات.</p>

            <h3>Sprint 5: المدفوعات والإشعارات (الأسبوع 9-10)</h3>
            <p><strong>الهدف</strong>: دمج المدفوعات، العملات، الإشعارات، والصفحات.</p>
            <p><strong>المدة</strong>: 10 أيام عمل</p>
            <ul>
                <li><strong>المهمة 5.1: إدارة العملات والمدفوعات</strong>
                    <ul>
                        <li>نموذج <code>Currency</code> مع ترجمة: <code>code</code>, <code>name</code>.</li>
                        <li>دمج Stripe SDK.</li>
                    </ul>
                </li>
                <li><strong>المهمة 5.2: إدارة الإشعارات والصفحات</strong>
                    <ul>
                        <li>نموذج <code>Notification</code> مع ترجمة: <code>content</code>.</li>
                        <li>نموذج <code>Page</code> مع ترجمة: <code>title</code>, <code>slug</code>.</li>
                    </ul>
                </li>
                <li><strong>المهمة 5.3: إنشاء واجهة الدفع والصفحات</strong>
                    <ul>
                        <li>تصميم <code>PaymentForm.vue</code>.</li>
                        <li>دمج API للإشعارات.</li>
                    </ul>
                </li>
            </ul>
            <p><strong>المخرجات</strong>: نظام مدفوعات، إشعارات، صفحات ثابتة.</p>

            <h3>Sprint 6: الاختبار والإطلاق (الأسبوع 11-12)</h3>
            <p><strong>الهدف</strong>: اختبار التطبيق، تحسين الأداء، والنشر.</p>
            <p><strong>المدة</strong>: 10 أيام عمل</p>
            <ul>
                <li><strong>المهمة 6.1: اختبار التطبيق</strong>
                    <ul>
                        <li>اختبارات وحدات لـ <code>User</code>, <code>Course</code>.</li>
                        <li>اختبارات تكامل باستخدام Laravel Dusk.</li>
                    </ul>
                </li>
                <li><strong>المهمة 6.2: تحسين الأداء والنشر</strong>
                    <ul>
                        <li>إعداد Cache مع Redis.</li>
                        <li>نشر على DigitalOcean باستخدام Forge.</li>
                    </ul>
                </li>
                <li><strong>المهمة 6.3: توثيق API</strong>
                    <ul>
                        <li>تثبيت L5-Swagger.</li>
                        <li>إنشاء صفحة توثيق: <code>/api/documentation</code>.</li>
                    </ul>
                </li>
            </ul>
            <p><strong>المخرجات</strong>: تطبيق مختبر ومنشور، توثيق API، أداء محسّن.</p>
        </section>

        <section id="installation">
            <h2>التثبيت</h2>
            <p>اتبع الخطوات التالية لتثبيت المشروع محليًا:</p>
            <h3>المتطلبات</h3>
            <ul>
                <li>PHP 8.2+</li>
                <li>Composer</li>
                <li>Node.js (v16+)</li>
                <li>MySQL (v8+)</li>
                <li>Redis</li>
                <li>Git</li>
                <li>Docker (اختياري لـ Laravel Sail)</li>
            </ul>
            <h3>الخطوات</h3>
            <ol>
                <li><strong>استنساخ المستودع</strong>:
                    <div class="code-block">
                        git clone https://github.com/your-repo/vip-student.git<br>
                        cd vip-student
                    </div>
                </li>
                <li><strong>تثبيت التبعيات</strong>:
                    <div class="code-block">
                        composer install<br>
                        npm install
                    </div>
                </li>
                <li><strong>إعداد متغيرات البيئة</strong>:
                    <div class="code-block">
                        cp .env.example .env
                    </div>
                    <p>قم بتحديث <code>.env</code> بإعدادات قاعدة البيانات، Redis، وStripe:</p>
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
                <li><strong>توليد مفتاح التطبيق</strong>:
                    <div class="code-block">
                        php artisan key:generate
                    </div>
                </li>
                <li><strong>تشغيل Migrations وSeeders</strong>:
                    <div class="code-block">
                        php artisan migrate<br>
                        php artisan db:seed
                    </div>
                </li>
                <li><strong>تشغيل الخادم</strong>:
                    <div class="code-block">
                        php artisan serve<br>
                        npm run dev
                    </div>
                    <p>أو باستخدام Sail:</p>
                    <div class="code-block">
                        ./vendor/bin/sail up
                    </div>
                </li>
                <li><strong>الوصول إلى التطبيق</strong>:
                    <ul>
                        <li>الواجهة الخلفية: <code>http://localhost:8000</code></li>
                        <li>الواجهة الأمامية: <code>http://localhost:5173</code></li>
                        <li>لوحة التحكم: <code>http://localhost:8000/admin</code></li>
                    </ul>
                </li>
            </ol>
        </section>

        <section id="usage">
            <h2>الاستخدام</h2>
            <ul>
                <li><strong>المستخدمون</strong>: التسجيل أو تسجيل الدخول للوصول إلى الدورات والاختبارات.</li>
                <li><strong>المدربون</strong>: إدارة الدروس، إنشاء اختبارات، وتقديم تقارير عبر لوحة Filament.</li>
                <li><strong>المسؤولون</strong>: استخدام لوحة Filament لإدارة المستخدمين والمعاهد.</li>
                <li><strong>الطلاب</strong>: التسجيل في الدورات، إجراء الاختبارات، وعرض النتائج.</li>
                <li><strong>أولياء الأمور</strong>: مراقبة تقدم الطلاب وتلقي الإشعارات.</li>
                <li><strong>API</strong>: استخدام نقاط النهاية مثل <code>/api/courses</code> مع رأس <code>Accept-Language</code> للترجمة.</li>
            </ul>
        </section>

        <section id="api">
            <h2>توثيق API</h2>
            <p>
                تم توثيق API باستخدام L5-Swagger. بعد التثبيت، يمكن الوصول إلى التوثيق على:
            </p>
            <ul>
                <li><strong>الرابط</strong>: <code>http://localhost:8000/api/documentation</code></li>
                <li><strong>الميزات</strong>:
                    <ul>
                        <li>يعرض جميع نقاط النهاية (مثل <code>/api/institutes</code>, <code>/api/courses</code>).</li>
                        <li>يدعم اختبار النقاط مباشرة عبر Swagger UI.</li>
                        <li>يتضمن تعليمات الترجمة (مثل <code>Accept-Language: ar</code>).</li>
                    </ul>
                </li>
            </ul>
        </section>

        <section id="contributing">
            <h2>المساهمة</h2>
            <p>نرحب بالمساهمات في منصة VIP Student! للمساهمة:</p>
            <ol>
                <li>قم بعمل Fork للمستودع.</li>
                <li>إنشاء فرع جديد: <code>git checkout -b feature/your-feature</code>.</li>
                <li>تسجيل التغييرات: <code>git commit -m "Add your feature"</code>.</li>
                <li>دفع الفرع: <code>git push origin feature/your-feature</code>.</li>
                <li>فتح Pull Request مع وصف تفصيلي.</li>
            </ol>
            <p>يرجى الالتزام بـ <a href="CODE_OF_CONDUCT.md">مدونة السلوك</a> واتباع <a href="CONTRIBUTING.md">إرشادات المساهمة</a>.</p>
        </section>

        <section id="license">
            <h2>الترخيص</h2>
            <p>هذا المشروع مرخص بموجب ترخيص MIT. انظر ملف <a href="LICENSE">LICENSE</a> للتفاصيل.</p>
        </section>

        <footer>
            <p>&copy; 2025 VIP Student. جميع الحقوق محفوظة.</p>
        </footer>
    </div>
</body>
</html>
