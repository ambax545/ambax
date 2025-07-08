# ambax
....
I'll create a music production website for AM BAX with an AI assistant feature. The site will focus on music production, singing, and mastering, with your contact information and a support chat feature in the corner.
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AM BAX - استودیو آهنگسازی و مسترینگ</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@100;400;700;900&display=swap" rel="stylesheet">
    <style>
        * {
            font-family: 'Vazirmatn', sans-serif;
        }
        
        body {
            background-color: #0f172a;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='400' viewBox='0 0 800 800'%3E%3Cg fill='none' stroke='%23172554' stroke-width='1'%3E%3Cpath d='M769 229L1037 260.9M927 880L731 737 520 660 309 538 40 599 295 764 126.5 879.5 40 599-197 493 102 382-31 229 126.5 79.5-69-63'/%3E%3Cpath d='M-31 229L237 261 390 382 603 493 308.5 537.5 101.5 381.5M370 905L295 764'/%3E%3Cpath d='M520 660L578 842 731 737 840 599 603 493 520 660 295 764 309 538 390 382 539 269 769 229 577.5 41.5 370 105 295 -36 126.5 79.5 237 261 102 382 40 599 -69 737 127 880'/%3E%3Cpath d='M520-140L578.5 42.5 731-63M603 493L539 269 237 261 370 105M902 382L539 269M390 382L102 382'/%3E%3Cpath d='M-222 42L126.5 79.5 370 105 539 269 577.5 41.5 927 80 769 229 902 382 603 493 731 737M295-36L577.5 41.5M578 842L295 764M40-201L127 80M102 382L-261 269'/%3E%3C/g%3E%3Cg fill='%232563eb'%3E%3Ccircle cx='769' cy='229' r='5'/%3E%3Ccircle cx='539' cy='269' r='5'/%3E%3Ccircle cx='603' cy='493' r='5'/%3E%3Ccircle cx='731' cy='737' r='5'/%3E%3Ccircle cx='520' cy='660' r='5'/%3E%3Ccircle cx='309' cy='538' r='5'/%3E%3Ccircle cx='295' cy='764' r='5'/%3E%3Ccircle cx='40' cy='599' r='5'/%3E%3Ccircle cx='102' cy='382' r='5'/%3E%3Ccircle cx='127' cy='80' r='5'/%3E%3Ccircle cx='370' cy='105' r='5'/%3E%3Ccircle cx='578' cy='42' r='5'/%3E%3Ccircle cx='237' cy='261' r='5'/%3E%3Ccircle cx='390' cy='382' r='5'/%3E%3C/g%3E%3C/svg%3E");
            background-attachment: fixed;
        }
        
        .chat-container {
            height: 300px;
            overflow-y: auto;
        }
        
        .logo-text {
            font-weight: 900;
            letter-spacing: 1px;
        }
        
        .user-message {
            background-color: #1e293b;
            border-radius: 18px 18px 0 18px;
        }
        
        .bot-message {
            background-color: #3b82f6;
            color: white;
            border-radius: 18px 18px 18px 0;
        }
        
        .chat-widget {
            position: fixed;
            bottom: 20px;
            left: 20px;
            z-index: 1000;
        }
        
        .chat-popup {
            width: 320px;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
            display: none;
        }
        
        .chat-button {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: #3b82f6;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }
        
        .sound-wave {
            animation: pulse 1.5s infinite;
        }
        
        @keyframes pulse {
            0% {
                transform: scale(0.95);
                opacity: 0.7;
            }
            50% {
                transform: scale(1);
                opacity: 1;
            }
            100% {
                transform: scale(0.95);
                opacity: 0.7;
            }
        }
        
        .service-card:hover {
            transform: translateY(-5px);
        }
    </style>
</head>
<body class="min-h-screen text-white">
    <header class="bg-gradient-to-r from-blue-900 to-indigo-900 shadow-lg">
        <div class="container mx-auto px-4 py-6 flex flex-col md:flex-row items-center justify-between">
            <div class="flex items-center mb-4 md:mb-0">
                <div class="mr-3">
                    <svg xmlns="http://www.w3.org/2000/svg" width="60" height="60" viewBox="0 0 100 100" class="fill-current">
                        <circle cx="50" cy="50" r="45" fill="#1e3a8a"/>
                        <circle cx="50" cy="50" r="35" fill="#1e40af"/>
                        <path d="M30,50 C30,40 35,30 50,30 C65,30 70,40 70,50 C70,60 65,70 50,70 C35,70 30,60 30,50 Z" fill="#2563eb"/>
                        <text x="50" y="45" font-family="Arial, sans-serif" font-size="18" font-weight="bold" text-anchor="middle" fill="#ffffff">AM</text>
                        <text x="50" y="65" font-family="Arial, sans-serif" font-size="14" font-weight="bold" text-anchor="middle" fill="#ffffff">BAX</text>
                        <path d="M20,50 C20,30 30,20 50,20 C70,20 80,30 80,50" stroke="#60a5fa" stroke-width="2" fill="none" stroke-dasharray="5,5"/>
                        <path d="M20,50 C20,70 30,80 50,80 C70,80 80,70 80,50" stroke="#60a5fa" stroke-width="2" fill="none" stroke-dasharray="5,5"/>
                    </svg>
                </div>
                <div>
                    <h1 class="text-2xl md:text-3xl font-bold logo-text">AM BAX</h1>
                    <p class="text-sm md:text-base text-blue-200">استودیو آهنگسازی و مسترینگ</p>
                </div>
            </div>
            <div class="flex flex-col items-end">
                <div class="flex items-center mb-2">
                    <span class="ml-2">تماس:</span>
                    <a href="tel:09195561271" class="text-white hover:text-blue-200 transition">09195561271</a>
                </div>
                <div class="flex items-center">
                    <span class="ml-2">ایمیل:</span>
                    <a href="mailto:norouziali696@gmail.com" class="text-white hover:text-blue-200 transition">norouziali696@gmail.com</a>
                </div>
            </div>
        </div>
    </header>

    <main>
        <!-- Hero Section -->
        <section class="py-16 md:py-24 px-4">
            <div class="container mx-auto max-w-6xl">
                <div class="flex flex-col md:flex-row items-center">
                    <div class="md:w-1/2 mb-8 md:mb-0">
                        <h2 class="text-4xl md:text-5xl font-bold mb-6 text-blue-400">هنر صدا را با ما تجربه کنید</h2>
                        <p class="text-xl text-gray-300 mb-8">در استودیو AM BAX، ما به شما کمک می‌کنیم تا رویاهای موسیقی خود را به واقعیت تبدیل کنید. از آهنگسازی تا مسترینگ حرفه‌ای، همه چیز زیر یک سقف.</p>
                        <div class="flex flex-wrap gap-4">
                            <a href="#services" class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-3 rounded-lg transition transform hover:scale-105">خدمات ما</a>
                            <a href="#contact" class="bg-transparent border-2 border-blue-600 text-blue-400 hover:bg-blue-900 hover:text-white px-6 py-3 rounded-lg transition transform hover:scale-105">تماس با ما</a>
                        </div>
                    </div>
                    <div class="md:w-1/2 flex justify-center">
                        <svg xmlns="http://www.w3.org/2000/svg" width="400" height="300" viewBox="0 0 100 100" class="sound-wave">
                            <rect x="10" y="30" width="5" height="40" rx="2" fill="#3b82f6">
                                <animate attributeName="height" values="40;10;40" dur="1s" repeatCount="indefinite" />
                                <animate attributeName="y" values="30;45;30" dur="1s" repeatCount="indefinite" />
                            </rect>
                            <rect x="20" y="20" width="5" height="60" rx="2" fill="#60a5fa">
                                <animate attributeName="height" values="60;20;60" dur="1.3s" repeatCount="indefinite" />
                                <animate attributeName="y" values="20;40;20" dur="1.3s" repeatCount="indefinite" />
                            </rect>
                            <rect x="30" y="10" width="5" height="80" rx="2" fill="#93c5fd">
                                <animate attributeName="height" values="80;30;80" dur="0.8s" repeatCount="indefinite" />
                                <animate attributeName="y" values="10;35;10" dur="0.8s" repeatCount="indefinite" />
                            </rect>
                            <rect x="40" y="25" width="5" height="50" rx="2" fill="#bfdbfe">
                                <animate attributeName="height" values="50;15;50" dur="1.1s" repeatCount="indefinite" />
                                <animate attributeName="y" values="25;42;25" dur="1.1s" repeatCount="indefinite" />
                            </rect>
                            <rect x="50" y="15" width="5" height="70" rx="2" fill="#dbeafe">
                                <animate attributeName="height" values="70;25;70" dur="0.9s" repeatCount="indefinite" />
                                <animate attributeName="y" values="15;37;15" dur="0.9s" repeatCount="indefinite" />
                            </rect>
                            <rect x="60" y="25" width="5" height="50" rx="2" fill="#bfdbfe">
                                <animate attributeName="height" values="50;15;50" dur="1.2s" repeatCount="indefinite" />
                                <animate attributeName="y" values="25;42;25" dur="1.2s" repeatCount="indefinite" />
                            </rect>
                            <rect x="70" y="10" width="5" height="80" rx="2" fill="#93c5fd">
                                <animate attributeName="height" values="80;30;80" dur="0.7s" repeatCount="indefinite" />
                                <animate attributeName="y" values="10;35;10" dur="0.7s" repeatCount="indefinite" />
                            </rect>
                            <rect x="80" y="20" width="5" height="60" rx="2" fill="#60a5fa">
                                <animate attributeName="height" values="60;20;60" dur="1.4s" repeatCount="indefinite" />
                                <animate attributeName="y" values="20;40;20" dur="1.4s" repeatCount="indefinite" />
                            </rect>
                            <rect x="90" y="30" width="5" height="40" rx="2" fill="#3b82f6">
                                <animate attributeName="height" values="40;10;40" dur="1s" repeatCount="indefinite" />
                                <animate attributeName="y" values="30;45;30" dur="1s" repeatCount="indefinite" />
                            </rect>
                        </svg>
                    </div>
                </div>
            </div>
        </section>

        <!-- Services Section -->
        <section id="services" class="py-16 bg-blue-900/30 backdrop-blur-sm">
            <div class="container mx-auto px-4 max-w-6xl">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold mb-4">خدمات استودیو</h2>
                    <p class="text-xl text-gray-300 max-w-3xl mx-auto">ما مجموعه کاملی از خدمات تولید موسیقی را ارائه می‌دهیم تا به شما در خلق آثار هنری با کیفیت کمک کنیم.</p>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- Service 1 -->
                    <div class="bg-gradient-to-br from-blue-800/50 to-indigo-900/50 backdrop-blur-sm rounded-xl p-6 shadow-lg transition duration-300 service-card">
                        <div class="mb-4 text-blue-400">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19V6l12-3v13M9 19c0 1.105-1.343 2-3 2s-3-.895-3-2 1.343-2 3-2 3 .895 3 2zm12-3c0 1.105-1.343 2-3 2s-3-.895-3-2 1.343-2 3-2 3 .895 3 2zM9 10l12-3" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold mb-3">آهنگسازی</h3>
                        <p class="text-gray-300 mb-4">از ایده تا اجرا، ما به شما کمک می‌کنیم تا آهنگ‌های خود را با بهترین کیفیت تولید کنید. تیم ما از آهنگسازان حرفه‌ای تشکیل شده است.</p>
                        <ul class="text-gray-300 mb-4 pr-5">
                            <li class="mb-1">• تنظیم آهنگ</li>
                            <li class="mb-1">• ساخت ملودی</li>
                            <li class="mb-1">• تولید بیت</li>
                            <li>• هارمونی‌سازی</li>
                        </ul>
                    </div>
                    
                    <!-- Service 2 -->
                    <div class="bg-gradient-to-br from-blue-800/50 to-indigo-900/50 backdrop-blur-sm rounded-xl p-6 shadow-lg transition duration-300 service-card">
                        <div class="mb-4 text-blue-400">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11a7 7 0 01-7 7m0 0a7 7 0 01-7-7m7 7v4m0 0H8m4 0h4m-4-8a3 3 0 01-3-3V5a3 3 0 116 0v6a3 3 0 01-3 3z" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold mb-3">ضبط صدا</h3>
                        <p class="text-gray-300 mb-4">استودیوی مجهز ما با آکوستیک حرفه‌ای و تجهیزات پیشرفته، محیطی ایده‌آل برای ضبط صدای با کیفیت فراهم می‌کند.</p>
                        <ul class="text-gray-300 mb-4 pr-5">
                            <li class="mb-1">• ضبط وکال</li>
                            <li class="mb-1">• ضبط سازهای موسیقی</li>
                            <li class="mb-1">• ضبط گروهی</li>
                            <li>• ویرایش صدا</li>
                        </ul>
                    </div>
                    
                    <!-- Service 3 -->
                    <div class="bg-gradient-to-br from-blue-800/50 to-indigo-900/50 backdrop-blur-sm rounded-xl p-6 shadow-lg transition duration-300 service-card">
                        <div class="mb-4 text-blue-400">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 4v16M17 4v16M3 8h4m10 0h4M3 12h18M3 16h4m10 0h4M4 20h16a1 1 0 001-1V5a1 1 0 00-1-1H4a1 1 0 00-1 1v14a1 1 0 001 1z" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold mb-3">میکس و مسترینگ</h3>
                        <p class="text-gray-300 mb-4">با استفاده از تکنیک‌های پیشرفته و تجهیزات حرفه‌ای، صدای شما را به بهترین کیفیت ممکن می‌رسانیم.</p>
                        <ul class="text-gray-300 mb-4 pr-5">
                            <li class="mb-1">• میکس چند لایه</li>
                            <li class="mb-1">• مسترینگ حرفه‌ای</li>
                            <li class="mb-1">• تنظیم اکولایزر</li>
                            <li>• بهینه‌سازی صدا</li>
                        </ul>
                    </div>
                    
                    <!-- Service 4 -->
                    <div class="bg-gradient-to-br from-blue-800/50 to-indigo-900/50 backdrop-blur-sm rounded-xl p-6 shadow-lg transition duration-300 service-card">
                        <div class="mb-4 text-blue-400">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.536 8.464a5 5 0 010 7.072m2.828-9.9a9 9 0 010 12.728M5.586 15.536a5 5 0 001.414 1.414m2.828-9.9a9 9 0 012.728-2.728" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold mb-3">آموزش خوانندگی</h3>
                        <p class="text-gray-300 mb-4">دوره‌های آموزشی ما به شما کمک می‌کند تا مهارت‌های خوانندگی خود را توسعه دهید و صدای خود را به بهترین شکل ارائه کنید.</p>
                        <ul class="text-gray-300 mb-4 pr-5">
                            <li class="mb-1">• تکنیک‌های صداسازی</li>
                            <li class="mb-1">• کنترل نفس</li>
                            <li class="mb-1">• گسترش محدوده صدا</li>
                            <li>• تمرین‌های عملی</li>
                        </ul>
                    </div>
                    
                    <!-- Service 5 -->
                    <div class="bg-gradient-to-br from-blue-800/50 to-indigo-900/50 backdrop-blur-sm rounded-xl p-6 shadow-lg transition duration-300 service-card">
                        <div class="mb-4 text-blue-400">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z" />
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold mb-3">تولید موزیک ویدیو</h3>
                        <p class="text-gray-300 mb-4">از طراحی کانسپت تا تدوین نهایی، ما به شما کمک می‌کنیم تا موزیک ویدیوهای حرفه‌ای تولید کنید.</p>
                        <ul class="text-gray-300 mb-4 pr-5">
                            <li class="mb-1">• فیلمبرداری حرفه‌ای</li>
                            <li class="mb-1">• تدوین ویدیو</li>
                            <li class="mb-1">• جلوه‌های ویژه</li>
                            <li>• گریدینگ رنگ</li>
                        </ul>
                    </div>
                    
                    <!-- Service 6 -->
                    <div class="bg-gradient-to-br from-blue-800/50 to-indigo-900/50 backdrop-blur-sm rounded-xl p-6 shadow-lg transition duration-300 service-card">
                        <div class="mb-4 text-blue-400">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-12 w-12" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-bold mb-3">آموزش تولید موسیقی</h3>
                        <p class="text-gray-300 mb-4">دوره‌های آموزشی ما به شما کمک می‌کند تا با نرم‌افزارها و تکنیک‌های تولید موسیقی آشنا شوید.</p>
                        <ul class="text-gray-300 mb-4 pr-5">
                            <li class="mb-1">• آموزش DAW ها</li>
                            <li class="mb-1">• تکنیک‌های میکس</li>
                            <li class="mb-1">• تولید بیت</li>
                            <li>• پروژه‌های عملی</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- Equipment Section -->
        <section class="py-16">
            <div class="container mx-auto px-4 max-w-6xl">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold mb-4">تجهیزات استودیو</h2>
                    <p class="text-xl text-gray-300 max-w-3xl mx-auto">استودیو AM BAX مجهز به پیشرفته‌ترین تجهیزات ضبط و تولید موسیقی است.</p>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-blue-900/20 backdrop-blur-sm rounded-xl p-6 shadow-lg">
                        <h3 class="text-xl font-bold mb-4 text-blue-400">تجهیزات ضبط صدا</h3>
                        <ul class="text-gray-300 space-y-2">
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                میکروفون‌های Neumann U87
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                پری‌آمپ‌های SSL
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                کنسول میکس Avid S6
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                مانیتورهای Genelec
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                هدفون‌های Sennheiser HD 800
                            </li>
                        </ul>
                    </div>
                    
                    <div class="bg-blue-900/20 backdrop-blur-sm rounded-xl p-6 shadow-lg">
                        <h3 class="text-xl font-bold mb-4 text-blue-400">نرم‌افزارها و پلاگین‌ها</h3>
                        <ul class="text-gray-300 space-y-2">
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                Pro Tools Ultimate
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                Ableton Live Suite
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                Logic Pro X
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                پلاگین‌های Waves Complete
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5 ml-2 text-blue-400" viewBox="0 0 20 20" fill="currentColor">
                                    <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                                </svg>
                                Fabfilter Bundle
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- Testimonials Section -->
        <section class="py-16 bg-blue-900/30 backdrop-blur-sm">
            <div class="container mx-auto px-4 max-w-6xl">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold mb-4">نظرات هنرجویان</h2>
                    <p class="text-xl text-gray-300 max-w-3xl mx-auto">آنچه هنرجویان ما درباره تجربه‌شان در استودیو AM BAX می‌گویند.</p>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    <!-- Testimonial 1 -->
                    <div class="bg-gradient-to-br from-blue-800/30 to-indigo-900/30 backdrop-blur-sm rounded-xl p-6 shadow-lg">
                        <div class="flex items-center mb-4">
                            <div class="text-yellow-400 flex">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                            </div>
                        </div>
                        <p class="text-gray-300 mb-4">"تجربه کار با استودیو AM BAX فوق‌العاده بود. کیفیت ضبط و میکس آهنگ من بسیار عالی بود و تیم حرفه‌ای استودیو در تمام مراحل کار همراه من بودند."</p>
                        <div class="font-bold">سامان محمدی</div>
                        <div class="text-sm text-gray-400">خواننده</div>
                    </div>
                    
                    <!-- Testimonial 2 -->
                    <div class="bg-gradient-to-br from-blue-800/30 to-indigo-900/30 backdrop-blur-sm rounded-xl p-6 shadow-lg">
                        <div class="flex items-center mb-4">
                            <div class="text-yellow-400 flex">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                            </div>
                        </div>
                        <p class="text-gray-300 mb-4">"دوره آموزشی تولید موسیقی در AM BAX به من کمک کرد تا مهارت‌های خود را به سطح حرفه‌ای برسانم. اساتید با تجربه و محتوای آموزشی کاربردی، این دوره را به یک تجربه یادگیری عالی تبدیل کرد."</p>
                        <div class="font-bold">نیلوفر احمدی</div>
                        <div class="text-sm text-gray-400">تهیه‌کننده موسیقی</div>
                    </div>
                    
                    <!-- Testimonial 3 -->
                    <div class="bg-gradient-to-br from-blue-800/30 to-indigo-900/30 backdrop-blur-sm rounded-xl p-6 shadow-lg">
                        <div class="flex items-center mb-4">
                            <div class="text-yellow-400 flex">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                                </svg>
                            </div>
                        </div>
                        <p class="text-gray-300 mb-4">"کیفیت مسترینگ در استودیو AM BAX بی‌نظیر است. آهنگ من پس از مسترینگ در این استودیو، کیفیت صدای فوق‌العاده‌ای پیدا کرد و بازخوردهای بسیار مثبتی از مخاطبان دریافت کردم."</p>
                        <div class="font-bold">امیر رضایی</div>
                        <div class="text-sm text-gray-400">آهنگساز</div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-16">
            <div class="container mx-auto px-4 max-w-6xl">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold mb-4">تماس با ما</h2>
                    <p class="text-xl text-gray-300 max-w-3xl mx-auto">برای رزرو استودیو، ثبت‌نام در دوره‌های آموزشی یا کسب اطلاعات بیشتر با ما در تماس باشید.</p>
                </div>
                
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-blue-900/20 backdrop-blur-sm rounded-xl p-6 shadow-lg">
                        <h3 class="text-xl font-bold mb-4 text-blue-400">اطلاعات تماس</h3>
                        <div class="space-y-4">
                            <div class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 ml-3 text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
                                </svg>
                                <div>
                                    <div class="text-sm text-gray-400">شماره تماس</div>
                                    <a href="tel:09195561271" class="text-white hover:text-blue-300 transition">09195561271</a>
                                </div>
                            </div>
                            
                            <div class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 ml-3 text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                                </svg>
                                <div>
                                    <div class="text-sm text-gray-400">ایمیل</div>
                                    <a href="mailto:norouziali696@gmail.com" class="text-white hover:text-blue-300 transition">norouziali696@gmail.com</a>
                                </div>
                            </div>
                            
                            <div class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 ml-3 text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
                                </svg>
                                <div>
                                    <div class="text-sm text-gray-400">ساعات کاری</div>
                                    <div class="text-white">شنبه تا پنجشنبه: 10 صبح تا 8 شب</div>
                                </div>
                            </div>
                        </div>
                        
                        <div class="mt-8">
                            <h4 class="font-bold mb-3 text-blue-400">ما را در شبکه‌های اجتماعی دنبال کنید</h4>
                            <div class="flex space-x-4">
                                <a href="#" class="text-gray-300 hover:text-white transition">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-instagram" viewBox="0 0 16 16">
                                        <path d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.917 3.917 0 0 0-1.417.923A3.927 3.927 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.916 3.916 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.926 3.926 0 0 0-.923-1.417A3.911 3.911 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0h.003zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599.28.28.453.546.598.92.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.47 2.47 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.478 2.478 0 0 1-.92-.598 2.48 2.48 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233 0-2.136.008-2.388.046-3.231.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92.28-.28.546-.453.92-.598.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045v.002zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92zm-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217zm0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334z"/>
                                    </svg>
                                </a>
                                <a href="#" class="text-gray-300 hover:text-white transition">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-telegram" viewBox="0 0 16 16">
                                        <path d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0zM8.287 5.906c-.778.324-2.334.994-4.666 2.01-.378.15-.577.298-.595.442-.03.243.275.339.69.47l.175.055c.408.133.958.288 1.243.294.26.006.549-.1.868-.32 2.179-1.471 3.304-2.214 3.374-2.23.05-.012.12-.026.166.016.047.041.042.12.037.141-.03.129-1.227 1.241-1.846 1.817-.193.18-.33.307-.358.336a8.154 8.154 0 0 1-.188.186c-.38.366-.664.64.015 1.088.327.216.589.393.85.571.284.194.568.387.936.629.093.06.183.125.27.187.331.236.63.448.997.414.214-.02.435-.22.547-.82.265-1.417.786-4.486.906-5.751a1.426 1.426 0 0 0-.013-.315.337.337 0 0 0-.114-.217.526.526 0 0 0-.31-.093c-.3.005-.763.166-2.984 1.09z"/>
                                    </svg>
                                </a>
                                <a href="#" class="text-gray-300 hover:text-white transition">
                                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-youtube" viewBox="0 0 16 16">
                                        <path d="M8.051 1.999h.089c.822.003 4.987.033 6.11.335a2.01 2.01 0 0 1 1.415 1.42c.101.38.172.883.22 1.402l.01.104.022.26.008.104c.065.914.073 1.77.074 1.957v.075c-.001.194-.01 1.108-.082 2.06l-.008.105-.009.104c-.05.572-.124 1.14-.235 1.558a2.007 2.007 0 0 1-1.415 1.42c-1.16.312-5.569.334-6.18.335h-.142c-.309 0-1.587-.006-2.927-.052l-.17-.006-.087-.004-.171-.007-.171-.007c-1.11-.049-2.167-.128-2.654-.26a2.007 2.007 0 0 1-1.415-1.419c-.111-.417-.185-.986-.235-1.558L.09 9.82l-.008-.104A31.4 31.4 0 0 1 0 7.68v-.123c.002-.215.01-.958.064-1.778l.007-.103.003-.052.008-.104.022-.26.01-.104c.048-.519.119-1.023.22-1.402a2.007 2.007 0 0 1 1.415-1.42c.487-.13 1.544-.21 2.654-.26l.17-.007.172-.006.086-.003.171-.007A99.788 99.788 0 0 1 7.858 2h.193zM6.4 5.209v4.818l4.157-2.408L6.4 5.209z"/>
                                    </svg>
                                </a>
                            </div>
                        </div>
                    </div>
                    
                    <div class="bg-blue-900/20 backdrop-blur-sm rounded-xl p-6 shadow-lg">
                        <h3 class="text-xl font-bold mb-4 text-blue-400">ارسال پیام</h3>
                        <form>
                            <div class="mb-4">
                                <label for="name" class="block text-gray-300 mb-2">نام و نام خانوادگی</label>
                                <input type="text" id="name" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-2 text-white focus:outline-none focus:ring-2 focus:ring-blue-500">
                            </div>
                            
                            <div class="mb-4">
                                <label for="email" class="block text-gray-300 mb-2">ایمیل</label>
                                <input type="email" id="email" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-2 text-white focus:outline-none focus:ring-2 focus:ring-blue-500">
                            </div>
                            
                            <div class="mb-4">
                                <label for="phone" class="block text-gray-300 mb-2">شماره تماس</label>
                                <input type="tel" id="phone" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-2 text-white focus:outline-none focus:ring-2 focus:ring-blue-500">
                            </div>
                            
                            <div class="mb-4">
                                <label for="message" class="block text-gray-300 mb-2">پیام</label>
                                <textarea id="message" rows="4" class="w-full bg-gray-800 border border-gray-700 rounded-lg px-4 py-2 text-white focus:outline-none focus:ring-2 focus:ring-blue-500"></textarea>
                            </div>
                            
                            <button type="submit" class="bg-blue-600 hover:bg-blue-700 text-white px-6 py-3 rounded-lg transition w-full">ارسال پیام</button>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer class="bg-gray-900 text-white py-8">
        <div class="container mx-auto px-4">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="mb-6 md:mb-0 flex items-center">
                    <svg xmlns="http://www.w3.org/2000/svg" width="40" height="40" viewBox="0 0 100 100" class="fill-current mr-3">
                        <circle cx="50" cy="50" r="45" fill="#1e3a8a"/>
                        <circle cx="50" cy="50" r="35" fill="#1e40af"/>
                        <path d="M30,50 C30,40 35,30 50,30 C65,30 70,40 70,50 C70,60 65,70 50,70 C35,70 30,60 30,50 Z" fill="#2563eb"/>
                        <text x="50" y="45" font-family="Arial, sans-serif" font-size="18" font-weight="bold" text-anchor="middle" fill="#ffffff">AM</text>
                        <text x="50" y="65" font-family="Arial, sans-serif" font-size="14" font-weight="bold" text-anchor="middle" fill="#ffffff">BAX</text>
                    </svg>
                    <div>
                        <h3 class="text-xl font-bold logo-text">AM BAX</h3>
                        <p class="text-gray-400">استودیو آهنگسازی و مسترینگ</p>
                    </div>
                </div>
                <div class="flex flex-col items-center md:items-end">
                    <div class="mb-2">
                        <a href="tel:09195561271" class="text-gray-300 hover:text-white transition">09195561271</a>
                    </div>
                    <div>
                        <a href="mailto:norouziali696@gmail.com" class="text-gray-300 hover:text-white transition">norouziali696@gmail.com</a>
                    </div>
                </div>```
                
