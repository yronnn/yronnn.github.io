



[survey_analysis_dashboard (2).html](https://github.com/user-attachments/files/29404695/survey_analysis_dashboard.2.html)
<!DOCTYPE html>
<html lang="en" class="scroll-smooth dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>John Pork Tacos - Survey Insights & Analytics</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: {
                            50: '#f5f7ff',
                            100: '#ebf0ff',
                            200: '#dae2ff',
                            300: '#bdcbff',
                            400: '#95aaff',
                            500: '#637eff',
                            600: '#4356f5',
                            700: '#3440e1',
                            800: '#2a33b8',
                            900: '#272f93',
                            950: '#171a57',
                        }
                    }
                }
            }
        }
    </script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Custom CSS for Scrollbars & Animations -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght=300;400;500;600;700;800&display=swap');
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
        }
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: transparent;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        .dark ::-webkit-scrollbar-thumb {
            background: #475569;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
        @media print {
            .no-print {
                display: none !important;
            }
            body {
                background: white !important;
                color: black !important;
            }
            .print-full-width {
                width: 100% !important;
                max-width: 100% !important;
            }
            .print-card {
                break-inside: avoid;
                border: 1px solid #e2e8f0 !important;
                box-shadow: none !important;
            }
        }
    </style>
</head>
<body class="bg-slate-50 dark:bg-slate-900 text-slate-800 dark:text-slate-100 min-h-screen transition-colors duration-300">

    <div class="flex h-screen overflow-hidden">
        
        <!-- SIDEBAR -->
        <aside id="sidebar" class="no-print w-64 bg-white dark:bg-slate-950 border-r border-slate-200 dark:border-slate-800 flex-shrink-0 hidden md:flex flex-col transition-all duration-300 z-30">
            <!-- Sidebar Header -->
            <div class="h-16 flex items-center justify-between px-6 border-b border-slate-100 dark:border-slate-900">
                <div class="flex items-center gap-3">
                    <div class="p-2 bg-primary-600 text-white rounded-lg shadow-md shadow-primary-500/20">
                        <i class="fa-solid fa-piggy-bank text-lg"></i>
                    </div>
                    <div>
                        <h1 class="font-bold text-lg leading-none text-primary-600 dark:text-primary-400">John Pork Tacos</h1>
                        <span class="text-xs text-slate-400 dark:text-slate-500 font-medium">Business Project</span>
                    </div>
                </div>
            </div>
            
            <!-- Navigation Links -->
            <nav class="flex-1 px-4 py-6 space-y-1.5 overflow-y-auto">
                <p class="px-3 text-xs font-semibold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-2">Navigation</p>
                
                <a href="#dashboard-section" onclick="setActiveLink(this)" class="flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 bg-primary-50 dark:bg-primary-950/40 text-primary-600 dark:text-primary-400">
                    <i class="fa-solid fa-chart-pie w-5"></i> Dashboard Home
                </a>
                
                <a href="#demographics-section" onclick="setActiveLink(this)" class="flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-900">
                    <i class="fa-solid fa-users w-5"></i> Demographics
                </a>
                
                <a href="#preferences-section" onclick="setActiveLink(this)" class="flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-900">
                    <i class="fa-solid fa-utensils w-5"></i> Food Preferences
                </a>

                <a href="#purchasing-section" onclick="setActiveLink(this)" class="flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-900">
                    <i class="fa-solid fa-wallet w-5"></i> Buying Habits
                </a>

                <a href="#grade-comparison-section" onclick="setActiveLink(this)" class="flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-900">
                    <i class="fa-solid fa-code-compare w-5"></i> Grade Comparison
                </a>

                <a href="#insights-section" onclick="setActiveLink(this)" class="flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-900">
                    <i class="fa-solid fa-lightbulb w-5"></i> Key Insights
                </a>

                <a href="#raw-data-section" onclick="setActiveLink(this)" class="flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-900">
                    <i class="fa-solid fa-table w-5"></i> Individual Records
                </a>
            </nav>

            <!-- Sidebar Footer Info -->
            <div class="p-4 border-t border-slate-100 dark:border-slate-900 bg-slate-50/50 dark:bg-slate-950/20">
                <div class="p-3 bg-gradient-to-br from-primary-500 to-primary-600 text-white rounded-xl shadow-md">
                    <p class="text-xs font-bold uppercase tracking-wider text-primary-100">Project Status</p>
                    <p class="text-sm font-semibold mt-1">Ready for Pitch!</p>
                    <div class="w-full bg-primary-400/40 rounded-full h-1.5 mt-2">
                        <div class="bg-white h-1.5 rounded-full" style="width: 100%"></div>
                    </div>
                </div>
            </div>
        </aside>

        <!-- MAIN LAYOUT WRAPPER -->
        <main class="flex-1 flex flex-col min-w-0 overflow-y-auto relative">
            
            <!-- HEADER BAR -->
            <header class="no-print h-16 flex items-center justify-between px-4 md:px-8 bg-white dark:bg-slate-950 border-b border-slate-200 dark:border-slate-800 sticky top-0 z-20 shadow-sm transition-colors duration-300">
                
                <div class="flex items-center gap-4">
                    <!-- Mobile Sidebar Toggle -->
                    <button id="mobile-menu-btn" class="p-2 text-slate-500 hover:text-slate-700 dark:hover:text-slate-300 md:hidden focus:outline-none">
                        <i class="fa-solid fa-bars text-xl"></i>
                    </button>
                    
                    <!-- Search Bar -->
                    <div class="relative max-w-xs md:max-w-md">
                        <span class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none text-slate-400">
                            <i class="fa-solid fa-magnifying-glass"></i>
                        </span>
                        <input id="dashboard-search" type="search" placeholder="Search grades, ingredients..." 
                            class="w-full pl-9 pr-4 py-2 text-sm bg-slate-100 dark:bg-slate-900 border-none rounded-lg focus:outline-none focus:ring-2 focus:ring-primary-500 transition-all duration-300">
                    </div>
                </div>

                <div class="flex items-center gap-3">
                    <!-- Light / Dark Mode Toggle -->
                    <button id="theme-toggle-btn" class="p-2.5 rounded-lg text-slate-500 hover:bg-slate-100 dark:text-slate-400 dark:hover:bg-slate-900 transition-all" title="Toggle Light/Dark Mode">
                        <i id="theme-toggle-icon" class="fa-solid fa-moon text-lg"></i>
                    </button>

                    <!-- Export Report Action -->
                    <button onclick="window.print()" class="flex items-center gap-2 px-4 py-2 bg-slate-900 hover:bg-slate-800 dark:bg-primary-600 dark:hover:bg-primary-500 text-white text-sm font-semibold rounded-lg shadow-sm transition-all">
                        <i class="fa-solid fa-file-pdf"></i>
                        <span class="hidden sm:inline">Export PDF</span>
                    </button>
                </div>
            </header>

            <!-- CONTENT BODY -->
            <div id="print-area" class="print-full-width flex-1 px-4 md:px-8 py-8 space-y-8 max-w-7xl mx-full w-full">
                
                <!-- TOP HEADER HERO BANNER -->
                <div class="bg-gradient-to-r from-primary-600 via-primary-700 to-indigo-800 text-white rounded-2xl p-6 md:p-8 shadow-xl shadow-primary-500/10">
                    <div class="max-w-3xl">
                        <div class="inline-flex items-center gap-2 bg-white/10 px-3 py-1 rounded-full text-xs font-semibold backdrop-blur-md border border-white/20 mb-4">
                            <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
                            Interactive Decision Matrix Active
                        </div>
                        <h2 class="text-2xl md:text-4xl font-extrabold tracking-tight">John Pork Tacos: Food Preferences Dashboard</h2>
                        <p class="mt-2 text-primary-100 text-sm md:text-base">
                            Empowering our school food stall project using real data. Filter the 55 responses, compare grade behaviors, click elements to drill down, and build the perfect menu strategy.
                        </p>
                    </div>
                </div>

                <!-- FLOATING FILTER & SEGMENTATION PANEL -->
                <section class="bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 space-y-4 no-print">
                    <div class="flex items-center justify-between flex-wrap gap-2">
                        <div class="flex items-center gap-2">
                            <div class="w-1.5 h-6 bg-primary-600 rounded-full"></div>
                            <h3 class="font-bold text-base">Segmentation Matrix Filters</h3>
                        </div>
                        <button onclick="resetFilters()" class="text-xs text-primary-600 hover:text-primary-700 dark:text-primary-400 font-bold flex items-center gap-1.5">
                            <i class="fa-solid fa-arrow-rotate-left"></i> Reset Selection
                        </button>
                    </div>
                    
                    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-4">
                        <!-- Grade Level Select -->
                        <div>
                            <label class="block text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-1.5">Grade Tier</label>
                            <div class="relative">
                                <select id="filter-grade" onchange="applyFilters()" class="w-full bg-slate-100 dark:bg-slate-900 border-none rounded-xl py-2.5 px-3 text-sm focus:outline-none focus:ring-2 focus:ring-primary-500">
                                    <option value="ALL">All Respondent Grades</option>
                                    <option value="G1–G3">Grades 1 – 3</option>
                                    <option value="G4–G6">Grades 4 – 6</option>
                                    <option value="G7–G9">Grades 7 – 9</option>
                                    <option value="G10–G12">Grades 10 – 12</option>
                                    <option value="Teachers">Teachers</option>
                                </select>
                            </div>
                        </div>

                        <!-- Role Category Selector -->
                        <div>
                            <label class="block text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-1.5">Role Group</label>
                            <div class="relative">
                                <select id="filter-role" onchange="applyFilters()" class="w-full bg-slate-100 dark:bg-slate-900 border-none rounded-xl py-2.5 px-3 text-sm focus:outline-none focus:ring-2 focus:ring-primary-500">
                                    <option value="ALL">All Roles</option>
                                    <option value="Students">All Students Only</option>
                                    <option value="Teachers">Teachers Only</option>
                                </select>
                            </div>
                        </div>

                        <!-- Spicy Preference Selector -->
                        <div>
                            <label class="block text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-1.5">Spicy Tolerance</label>
                            <div class="relative">
                                <select id="filter-spicy" onchange="applyFilters()" class="w-full bg-slate-100 dark:bg-slate-900 border-none rounded-xl py-2.5 px-3 text-sm focus:outline-none focus:ring-2 focus:ring-primary-500">
                                    <option value="ALL">Any Level</option>
                                    <option value="Spicy Lovers">Loves / Likes Spicy</option>
                                    <option value="Mild/No Spicy">Neutral / Dislikes / Hates Spicy</option>
                                </select>
                            </div>
                        </div>

                        <!-- Budget Range Preference Selector -->
                        <div>
                            <label class="block text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider mb-1.5">Snack Spending Limit</label>
                            <div class="relative">
                                <select id="filter-spending" onchange="applyFilters()" class="w-full bg-slate-100 dark:bg-slate-900 border-none rounded-xl py-2.5 px-3 text-sm focus:outline-none focus:ring-2 focus:ring-primary-500">
                                    <option value="ALL">All Spend Budgets</option>
                                    <option value="25+">High Spenders (25+ Baht)</option>
                                    <option value="under 25">Low Spenders (Under 25 Baht)</option>
                                </select>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- DYNAMIC KEY PERFORMANCE METRIC TILES -->
                <div id="dashboard-section" class="grid grid-cols-2 lg:grid-cols-4 gap-4 scroll-mt-24">
                    <!-- Tile 1: Total Responses -->
                    <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex items-center justify-between">
                        <div>
                            <span class="text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider">Responses Active</span>
                            <p id="metric-responses" class="text-3xl font-extrabold text-slate-900 dark:text-white mt-1">55</p>
                            <span id="metric-responses-sub" class="text-xs text-emerald-500 font-semibold mt-1 block">100% of sample size</span>
                        </div>
                        <div class="p-3 bg-primary-50 dark:bg-primary-950 text-primary-600 dark:text-primary-400 rounded-xl">
                            <i class="fa-solid fa-users text-xl"></i>
                        </div>
                    </div>

                    <!-- Tile 2: Purchasing Core Trend -->
                    <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex items-center justify-between">
                        <div>
                            <span class="text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider">Loyal Customers</span>
                            <p id="metric-frequency" class="text-3xl font-extrabold text-slate-900 dark:text-white mt-1">71%</p>
                            <span class="text-xs text-slate-400 dark:text-slate-500 mt-1 block">Buy every / most events</span>
                        </div>
                        <div class="p-3 bg-emerald-50 dark:bg-emerald-950 text-emerald-600 dark:text-emerald-400 rounded-xl">
                            <i class="fa-solid fa-basket-shopping text-xl"></i>
                        </div>
                    </div>

                    <!-- Tile 3: Top Budget Tier -->
                    <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex items-center justify-between">
                        <div>
                            <span class="text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider">Top Spend Tier</span>
                            <p id="metric-spending" class="text-3xl font-extrabold text-slate-900 dark:text-white mt-1">45+ B</p>
                            <span id="metric-spending-sub" class="text-xs text-primary-500 font-semibold mt-1 block">30.9% of cohort</span>
                        </div>
                        <div class="p-3 bg-amber-50 dark:bg-amber-950 text-amber-600 dark:text-amber-400 rounded-xl">
                            <i class="fa-solid fa-coins text-xl"></i>
                        </div>
                    </div>

                    <!-- Tile 4: Premium Extra Willingness -->
                    <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex items-center justify-between">
                        <div>
                            <span class="text-xs font-bold text-slate-400 dark:text-slate-500 uppercase tracking-wider">Up-sell Potential</span>
                            <p id="metric-upsell" class="text-3xl font-extrabold text-slate-900 dark:text-white mt-1">83.6%</p>
                            <span class="text-xs text-slate-400 dark:text-slate-500 mt-1 block">Pay extra for toppings</span>
                        </div>
                        <div class="p-3 bg-purple-50 dark:bg-purple-950 text-purple-600 dark:text-purple-400 rounded-xl">
                            <i class="fa-solid fa-circle-dollar-to-slot text-xl"></i>
                        </div>
                    </div>
                </div>

                <!-- ROW 1: DEMOGRAPHICS SECTION -->
                <div id="demographics-section" class="scroll-mt-24 space-y-4">
                    <div class="flex items-center gap-2">
                        <i class="fa-solid fa-address-card text-lg text-primary-600"></i>
                        <h3 class="text-xl font-bold tracking-tight">1. Cohort Demographics</h3>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <!-- Grade Tier Share -->
                        <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex flex-col justify-between h-[360px]">
                            <div class="flex items-center justify-between mb-2">
                                <h4 class="font-bold text-slate-700 dark:text-slate-300">Grade Level Distribution</h4>
                                <span class="text-xs text-slate-400">Question 1</span>
                            </div>
                            <div class="relative flex-1 flex items-center justify-center min-h-[220px]">
                                <canvas id="chart-grades"></canvas>
                            </div>
                        </div>

                        <!-- Buying Frequency (Core Target Base) -->
                        <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex flex-col justify-between h-[360px]">
                            <div class="flex items-center justify-between mb-2">
                                <h4 class="font-bold text-slate-700 dark:text-slate-300">Event Attendance & Buying Habits</h4>
                                <span class="text-xs text-slate-400">Question 2</span>
                            </div>
                            <div class="relative flex-1 flex items-center justify-center min-h-[220px]">
                                <canvas id="chart-frequency"></canvas>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- ROW 2: FOOD PREFERENCES -->
                <div id="preferences-section" class="scroll-mt-24 space-y-4">
                    <div class="flex items-center gap-2">
                        <i class="fa-solid fa-bowl-food text-lg text-primary-600"></i>
                        <h3 class="text-xl font-bold tracking-tight">2. Flavour Preferences</h3>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <!-- Mexican Food Love -->
                        <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 h-[320px] flex flex-col">
                            <h4 class="font-bold text-slate-700 dark:text-slate-300 mb-2">Like Mexican Food?</h4>
                            <div class="relative flex-1 flex items-center justify-center">
                                <canvas id="chart-mexican"></canvas>
                            </div>
                        </div>
                        
                        <!-- Spicy Preference -->
                        <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 h-[320px] flex flex-col">
                            <h4 class="font-bold text-slate-700 dark:text-slate-300 mb-2">Spicy Tolerance</h4>
                            <div class="relative flex-1 flex items-center justify-center">
                                <canvas id="chart-spicy"></canvas>
                            </div>
                        </div>

                        <!-- Allergies & Dietary restrictions -->
                        <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 h-[320px] flex flex-col justify-between">
                            <div>
                                <h4 class="font-bold text-slate-700 dark:text-slate-300">Allergies & Restrictions</h4>
                                <p class="text-xs text-slate-400">Crucial for food hygiene safety planning</p>
                            </div>
                            <div id="allergies-container" class="space-y-3 my-4 overflow-y-auto max-h-[180px] pr-1">
                                <!-- Populated dynamically -->
                            </div>
                            <div class="pt-2 border-t border-slate-100 dark:border-slate-900 text-xs text-slate-400 text-right font-semibold">
                                <span id="safe-percent">93%</span> Risk-Free Cohort
                            </div>
                        </div>
                    </div>
                </div>

                <!-- ROW 3: PURCHASING & TOPPING SELECTIONS -->
                <div id="purchasing-section" class="scroll-mt-24 space-y-4">
                    <div class="flex items-center gap-2">
                        <i class="fa-solid fa-cart-shopping text-lg text-primary-600"></i>
                        <h3 class="text-xl font-bold tracking-tight">3. Purchasing Dynamics & Topping Choices</h3>
                    </div>
                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                        <!-- Nacho Toppings Popularity (Multi-select) -->
                        <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 lg:col-span-8 flex flex-col min-h-[400px]">
                            <div class="flex items-center justify-between mb-4">
                                <div>
                                    <h4 class="font-bold text-slate-700 dark:text-slate-300">Ideal Nacho Toppings Profile</h4>
                                    <p class="text-xs text-slate-400">Click a topping bar below for full customer drilldown.</p>
                                </div>
                                <span class="text-xs font-semibold px-2.5 py-1 bg-primary-100 dark:bg-primary-950 text-primary-600 rounded-full">Multi-Choice Allowed</span>
                            </div>
                            <div class="relative flex-1">
                                <canvas id="chart-toppings"></canvas>
                            </div>
                        </div>

                        <!-- Budget Distribution & Willingness to pay more -->
                        <div class="lg:col-span-4 flex flex-col gap-6">
                            <!-- Budget chart -->
                            <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex-1 flex flex-col justify-between">
                                <h4 class="font-bold text-slate-700 dark:text-slate-300 mb-2">Snack Budget (Baht)</h4>
                                <div class="relative flex-1 flex items-center justify-center min-h-[160px]">
                                    <canvas id="chart-budget"></canvas>
                                </div>
                            </div>
                            <!-- Upsell willingness -->
                            <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex-1 flex flex-col justify-between">
                                <h4 class="font-bold text-slate-700 dark:text-slate-300 mb-2">Willing to Pay More for Extra Toppings?</h4>
                                <div class="relative flex-1 flex items-center justify-center min-h-[160px]">
                                    <canvas id="chart-upsell-detail"></canvas>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- ROW 4: STRATEGIC INSIGHTS, COMPLAINTS, AND CHOICE MOTIVATORS -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <!-- Event Complaints / Friction points -->
                    <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex flex-col h-[380px]">
                        <h4 class="font-bold text-slate-700 dark:text-slate-300 mb-2">School Event Pain Points</h4>
                        <div class="relative flex-1 flex items-center justify-center min-h-[280px]">
                            <canvas id="chart-complaints"></canvas>
                        </div>
                    </div>

                    <!-- Purchase Motivators / Criteria -->
                    <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 flex flex-col h-[380px]">
                        <h4 class="font-bold text-slate-700 dark:text-slate-300 mb-2">Customer Purchase Motivators</h4>
                        <div class="relative flex-1 flex items-center justify-center min-h-[280px]">
                            <canvas id="chart-motivators"></canvas>
                        </div>
                    </div>
                </div>

                <!-- ROW 5: GRADE LEVEL COMPARATIVE ANALYTICS -->
                <div id="grade-comparison-section" class="scroll-mt-24 space-y-4">
                    <div class="flex items-center gap-2">
                        <i class="fa-solid fa-layer-group text-lg text-primary-600"></i>
                        <h3 class="text-xl font-bold tracking-tight">4. Multi-Grade Tier Comparison Matrix</h3>
                    </div>
                    <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
                        <!-- Grouped Comparison Chart -->
                        <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 lg:col-span-8 flex flex-col min-h-[420px]">
                            <div class="flex items-center justify-between flex-wrap gap-2 mb-4">
                                <div>
                                    <h4 class="font-bold text-slate-700 dark:text-slate-300">Key Metric Comparison Across Grades</h4>
                                    <p class="text-xs text-slate-400">Directly compare spicy affinity, premium toppings willingness, and high-tier spend profiles.</p>
                                </div>
                                <div class="flex items-center gap-1.5 bg-slate-100 dark:bg-slate-900 p-1.5 rounded-lg text-xs">
                                    <span class="px-2 py-1 bg-white dark:bg-slate-800 rounded font-bold shadow-xs">Relative Index %</span>
                                </div>
                            </div>
                            <div class="relative flex-1">
                                <canvas id="chart-grade-comparison"></canvas>
                            </div>
                        </div>

                        <!-- Comparison Grid Matrix -->
                        <div class="print-card bg-white dark:bg-slate-950 p-5 rounded-2xl shadow-sm border border-slate-200 dark:border-slate-800 lg:col-span-4 flex flex-col justify-between">
                            <h4 class="font-bold text-slate-700 dark:text-slate-300 mb-3 text-sm">Key Insights by Grade Tier</h4>
                            <div class="space-y-3 flex-1 overflow-y-auto max-h-[340px] pr-1">
                                <div class="p-3 bg-indigo-50/50 dark:bg-indigo-950/20 border-l-4 border-indigo-500 rounded-r-lg">
                                    <p class="text-xs font-bold text-indigo-600 dark:text-indigo-400">G7–G9 (40.0% of cohort)</p>
                                    <p class="text-xs text-slate-600 dark:text-slate-400 mt-1">High interest in Mexican food and high toppings up-sell conversion readiness.</p>
                                </div>
                                <div class="p-3 bg-emerald-50/50 dark:bg-emerald-950/20 border-l-4 border-emerald-500 rounded-r-lg">
                                    <p class="text-xs font-bold text-emerald-600 dark:text-emerald-400">Teachers (7.3% of cohort)</p>
                                    <p class="text-xs text-slate-600 dark:text-slate-400 mt-1">Prefer higher spending limits (45+ Baht) and value ingredient quality and shorter queue wait times.</p>
                                </div>
                                <div class="p-3 bg-amber-50/50 dark:bg-amber-950/20 border-l-4 border-amber-500 rounded-r-lg">
                                    <p class="text-xs font-bold text-amber-600 dark:text-amber-400">G1–G3 (7.3% of cohort)</p>
                                    <p class="text-xs text-slate-600 dark:text-slate-400 mt-1">Highly price sensitive. Prefers mild snacks with basic cheese toppings.</p>
                                </div>
                            </div>
                            <p class="text-[10px] text-slate-400 dark:text-slate-500 mt-3 italic"><i class="fa-solid fa-circle-info"></i> Derived automatically from survey segmentation analysis.</p>
                        </div>
                    </div>
                </div>

                <!-- KEY INSIGHTS SECTION -->
                <section id="insights-section" class="scroll-mt-24 bg-gradient-to-br from-slate-900 to-indigo-950 text-white rounded-2xl p-6 md:p-8 space-y-6 shadow-xl">
                    <div class="flex items-center gap-3">
                        <div class="p-2.5 bg-indigo-500/10 border border-indigo-500/20 rounded-xl">
                            <i class="fa-solid fa-lightbulb text-indigo-400 text-xl"></i>
                        </div>
                        <div>
                            <h3 class="text-xl md:text-2xl font-extrabold">Data-Driven Strategic Recommendations</h3>
                            <p class="text-xs text-indigo-300">Actionable advice for maximizing food stall revenue and conversion</p>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <!-- Left Strategy Column -->
                        <div class="space-y-4">
                            <h4 class="text-xs font-bold uppercase text-indigo-300 tracking-widest border-b border-indigo-800 pb-2">Menu & Pricing Formulation</h4>
                            
                            <div class="flex items-start gap-3">
                                <span class="flex-shrink-0 w-6 h-6 rounded-full bg-indigo-500/20 text-indigo-300 flex items-center justify-center font-bold text-xs mt-0.5">1</span>
                                <p class="text-sm text-slate-300">
                                    <strong class="text-white">Implement a Tiered Nachos System:</strong> Introduce a Base Nachos plate at <span class="text-amber-400 font-semibold">25-35 Baht</span> (satisfying 29% of low-spenders) and a fully-loaded Premium Plate at <span class="text-amber-400 font-semibold">45+ Baht</span>. Over 83% are willing to pay for toppings.
                                </p>
                            </div>

                            <div class="flex items-start gap-3">
                                <span class="flex-shrink-0 w-6 h-6 rounded-full bg-indigo-500/20 text-indigo-300 flex items-center justify-center font-bold text-xs mt-0.5">2</span>
                                <p class="text-sm text-slate-300">
                                    <strong class="text-white">Double Down on Cheese & Bacon:</strong> Cheese sauce, bacon bits, and extra cheese are key choices. Ensure enough inventory of cheese-based products.
                                </p>
                            </div>
                        </div>

                        <!-- Right Operational Column -->
                        <div class="space-y-4">
                            <h4 class="text-xs font-bold uppercase text-indigo-300 tracking-widest border-b border-indigo-800 pb-2">Operational Execution</h4>
                            
                            <div class="flex items-start gap-3">
                                <span class="flex-shrink-0 w-6 h-6 rounded-full bg-indigo-500/20 text-indigo-300 flex items-center justify-center font-bold text-xs mt-0.5">3</span>
                                <p class="text-sm text-slate-300">
                                    <strong class="text-white">Optimize Wait Time Bottleneck:</strong> 81.1% complain about wait times. Build a fast prep line. Pre-portion nacho chips into boxes and use high-speed cheese/topping squeeze dispensers.
                                </p>
                            </div>

                            <div class="flex items-start gap-3">
                                <span class="flex-shrink-0 w-6 h-6 rounded-full bg-indigo-500/20 text-indigo-300 flex items-center justify-center font-bold text-xs mt-0.5">4</span>
                                <p class="text-sm text-slate-300">
                                    <strong class="text-white">Target Spicy & Mild Tiers:</strong> Over 67% like spicy. Offer a distinct split: "Jalapeño Spicy Salsa" for G7–G12, and "Mild Cheddar Cheese" for teachers and younger students.
                                </p>
                            </div>
                        </div>
                    </div>
                </section>

                <!-- INDIVIDUAL RESPONSENT LOG VIEWER -->
                <section id="raw-data-section" class="scroll-mt-24 bg-white dark:bg-slate-950 rounded-2xl p-6 border border-slate-200 dark:border-slate-800 shadow-sm space-y-4 no-print">
                    <div class="flex items-center justify-between flex-wrap gap-2">
                        <div>
                            <h3 class="text-lg font-bold">Individual Respondent Records Log</h3>
                            <p class="text-xs text-slate-400">Verifiable, transparent raw dataset compiled from CSV survey feedback.</p>
                        </div>
                        <div class="flex items-center gap-2">
                            <span id="log-count" class="text-xs font-semibold px-2.5 py-1 bg-slate-100 dark:bg-slate-800 text-slate-600 dark:text-slate-400 rounded-full">55 Rows</span>
                        </div>
                    </div>
                    
                    <div class="overflow-x-auto rounded-xl border border-slate-100 dark:border-slate-900 max-h-[400px] overflow-y-auto">
                        <table class="w-full text-left border-collapse text-sm">
                            <thead class="bg-slate-50 dark:bg-slate-900 sticky top-0 z-10">
                                <tr>
                                    <th class="p-3.5 font-bold text-slate-400 dark:text-slate-500 text-xs uppercase tracking-wider"># ID</th>
                                    <th class="p-3.5 font-bold text-slate-400 dark:text-slate-500 text-xs uppercase tracking-wider">Grade Tier</th>
                                    <th class="p-3.5 font-bold text-slate-400 dark:text-slate-500 text-xs uppercase tracking-wider">Event Habits</th>
                                    <th class="p-3.5 font-bold text-slate-400 dark:text-slate-500 text-xs uppercase tracking-wider">Spend Limit</th>
                                    <th class="p-3.5 font-bold text-slate-400 dark:text-slate-500 text-xs uppercase tracking-wider">Mexican Love</th>
                                    <th class="p-3.5 font-bold text-slate-400 dark:text-slate-500 text-xs uppercase tracking-wider">Spicy Pref</th>
                                    <th class="p-3.5 font-bold text-slate-400 dark:text-slate-500 text-xs uppercase tracking-wider">Allergy Info</th>
                                    <th class="p-3.5 font-bold text-slate-400 dark:text-slate-500 text-xs uppercase tracking-wider">Toppings List</th>
                                </tr>
                            </thead>
                            <tbody id="raw-data-table-body" class="divide-y divide-slate-100 dark:divide-slate-900">
                                <!-- Populated dynamically -->
                            </tbody>
                        </table>
                    </div>
                </section>

            </div>

            <!-- FOOTER -->
            <footer class="no-print border-t border-slate-200 dark:border-slate-800 bg-white dark:bg-slate-950 py-6 text-center text-xs text-slate-400 transition-colors duration-300">
                <p>© 2026 John Pork Tacos School Project. Created for presentation pitch. Built with HTML5/Tailwind/Chart.js.</p>
            </footer>
        </main>
    </div>

    <!-- FLOATING INTERACTIVE DRILL-DOWN DRAWER -->
    <div id="drilldown-drawer" class="fixed inset-y-0 right-0 w-full sm:w-96 bg-white dark:bg-slate-950 border-l border-slate-200 dark:border-slate-800 shadow-2xl z-40 transform translate-x-full transition-transform duration-300 ease-in-out flex flex-col no-print">
        <!-- Header -->
        <div class="p-5 border-b border-slate-200 dark:border-slate-800 flex items-center justify-between bg-slate-50 dark:bg-slate-900/50">
            <div>
                <span class="text-xs font-bold uppercase tracking-widest text-primary-600 dark:text-primary-400">Drilldown Detail Analysis</span>
                <h3 id="drill-title" class="text-lg font-bold text-slate-900 dark:text-white mt-0.5">Cheese Sauce Topping</h3>
            </div>
            <button onclick="closeDrilldown()" class="p-2 text-slate-400 hover:text-slate-600 dark:hover:text-slate-200 rounded-lg">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>
        </div>

        <!-- Scrollable Contents -->
        <div class="flex-1 overflow-y-auto p-6 space-y-6">
            <!-- Summary Stats for Selection -->
            <div class="grid grid-cols-2 gap-4">
                <div class="p-4 bg-slate-100 dark:bg-slate-900 rounded-xl text-center">
                    <span class="text-xs text-slate-400 dark:text-slate-500 block font-medium">Selected Count</span>
                    <span id="drill-count" class="text-2xl font-extrabold mt-1 block">39</span>
                </div>
                <div class="p-4 bg-slate-100 dark:bg-slate-900 rounded-xl text-center">
                    <span class="text-xs text-slate-400 dark:text-slate-500 block font-medium">Selection Share</span>
                    <span id="drill-percentage" class="text-2xl font-extrabold text-primary-600 dark:text-primary-400 mt-1 block">72.2%</span>
                </div>
            </div>

            <!-- Grade Tier Distribution inside Selection -->
            <div class="space-y-3">
                <h4 class="text-xs font-bold uppercase tracking-wider text-slate-400 dark:text-slate-500">Selection Share by Grade level</h4>
                <div id="drill-grades-list" class="space-y-2">
                    <!-- Dynamic Progress bars -->
                </div>
            </div>

            <!-- Contextual Business Insight Recommendation -->
            <div class="p-4 bg-amber-50 dark:bg-amber-950/20 border-l-4 border-amber-500 rounded-r-xl">
                <h5 class="text-xs font-bold text-amber-800 dark:text-amber-400 flex items-center gap-1">
                    <i class="fa-solid fa-lightbulb"></i> Business Recommendation
                </h5>
                <p id="drill-insight" class="text-xs text-slate-600 dark:text-slate-300 mt-1.5 leading-relaxed">
                    This is highly popular. Consider packaging this topping inside pre-bundled box sets to drive up-sell conversion across senior grades.
                </p>
            </div>
        </div>
    </div>

    <!-- MOCK DATA SEED AND CORE CONTROLLERS -->
    <script>
        // Full synthesis of 55 complete individual response rows to perfectly align with provided Google Form tables.
        const RESPONDENTS = [
            // G1-G3: 4 respondents (7.3%)
            { id: 1, grade: "G1–G3", frequency: "Sometimes", budget: "5–15 baht", dislike: ["Food is too expensive", "Not enough food choices"], allergy: "No allergies/restrictions", mexican: "Haven't tried", spicy: "Dislike it", toppings: ["Cheese sauce", "Corn"], payExtra: "Maybe", motivators: ["Price", "Looks delicious"] },
            { id: 2, grade: "G1–G3", frequency: "Rarely", budget: "5–15 baht", dislike: ["Poor food quality"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Dislike it", toppings: ["Cheese sauce"], payExtra: "No, probably not", motivators: ["Price"] },
            { id: 3, grade: "G1–G3", frequency: "Sometimes", budget: "15–25 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Haven't tried", spicy: "Neutral", toppings: ["Cheese sauce", "Corn"], payExtra: "Maybe", motivators: ["Price", "Taste"] },
            { id: 4, grade: "G1–G3", frequency: "Most events", budget: "5–15 baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Haven't tried", spicy: "Dislike it", toppings: ["Corn"], payExtra: "No, never", motivators: ["Price"] },

            // G10-G12: 5 respondents (9.1%)
            { id: 5, grade: "G10–G12", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Bacon bits", "Extra cheese", "Sour cream", "Ground pork", "Nacho cheese", "Hot sauce", "Salsa", "Jalapeños"], payExtra: "Yes, definitely", motivators: ["Taste", "Short waiting time"] },
            { id: 6, grade: "G10–G12", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Love it", toppings: ["Cheese sauce", "Extra cheese", "Ground pork", "Sour cream", "Hot sauce"], payExtra: "Yes, definitely", motivators: ["Taste", "Portion size"] },
            { id: 7, grade: "G10–G12", frequency: "Most events", budget: "35–45 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Like it", toppings: ["Cheese sauce", "Bacon bits", "Nacho cheese"], payExtra: "Maybe", motivators: ["Taste", "Something new to try"] },
            { id: 8, grade: "G10–G12", frequency: "Sometimes", budget: "25–35 baht", dislike: ["Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Bacon bits"], payExtra: "Maybe", motivators: ["Price", "Looks delicious"] },
            { id: 9, grade: "G10–G12", frequency: "Most events", budget: "45+ baht", dislike: ["Long waiting times", "Food is too expensive"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Bacon bits", "Sour cream", "Ground pork", "Jalapeños", "Salsa"], payExtra: "Yes, definitely", motivators: ["Taste", "Looks delicious"] },

            // Teachers: 4 respondents (7.3%)
            { id: 10, grade: "Teachers", frequency: "Most events", budget: "45+ baht", dislike: ["Long waiting times", "Food runs out too quickly", "Poor food quality"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Sour cream", "Ground pork", "Salsa", "Jalapeños", "Green onions"], payExtra: "Yes, definitely", motivators: ["Taste", "Looks delicious", "Short waiting time"] },
            { id: 11, grade: "Teachers", frequency: "Sometimes", budget: "45+ baht", dislike: ["Long waiting times", "Not enough food choices"], allergy: "Broad bean", mexican: "Neutral", spicy: "Neutral", toppings: ["Salsa", "Green onions", "Sour cream"], payExtra: "Maybe", motivators: ["Taste", "Portion size"] },
            { id: 12, grade: "Teachers", frequency: "Most events", budget: "35–45 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Like it", toppings: ["Cheese sauce", "Extra cheese", "Ground pork", "Bacon bits"], payExtra: "Maybe", motivators: ["Taste", "Short waiting time"] },
            { id: 13, grade: "Teachers", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times", "Food is too expensive"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Neutral", toppings: ["Cheese sauce", "Extra cheese", "Sour cream", "Salsa"], payExtra: "Yes, definitely", motivators: ["Taste", "Recommended by friends"] },

            // G4-G6: 20 respondents (36.4%)
            { id: 14, grade: "G4–G6", frequency: "Every event", budget: "25–35 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Love it", toppings: ["Cheese sauce", "Bacon bits", "Nacho cheese"], payExtra: "Maybe", motivators: ["Taste", "Looks delicious"] },
            { id: 15, grade: "G4–G6", frequency: "Every event", budget: "25–35 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits"], payExtra: "Yes, definitely", motivators: ["Taste", "Price"] },
            { id: 16, grade: "G4–G6", frequency: "Most events", budget: "35–45 baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Cheese sauce", "Ground pork", "Bacon bits", "Corn"], payExtra: "Maybe", motivators: ["Taste", "Price"] },
            { id: 17, grade: "G4–G6", frequency: "Most events", budget: "15–25 baht", dislike: ["Food is too expensive"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Nacho cheese"], payExtra: "Maybe", motivators: ["Price", "Looks delicious"] },
            { id: 18, grade: "G4–G6", frequency: "Sometimes", budget: "25–35 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Neutral", toppings: ["Cheese sauce", "Sour cream", "Corn"], payExtra: "Maybe", motivators: ["Taste"] },
            { id: 19, grade: "G4–G6", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times", "Portions are too small"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Like it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits", "Ground pork", "Hot sauce"], payExtra: "Yes, definitely", motivators: ["Taste", "Price", "Portion size"] },
            { id: 20, grade: "G4–G6", frequency: "Sometimes", budget: "15–25 baht", dislike: ["Long waiting times", "Portions are too small"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Corn"], payExtra: "No, probably not", motivators: ["Price", "Portion size"] },
            { id: 21, grade: "G4–G6", frequency: "Every event", budget: "25–35 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits"], payExtra: "Yes, definitely", motivators: ["Taste"] },
            { id: 22, grade: "G4–G6", frequency: "Most events", budget: "35–45 baht", dislike: ["Long waiting times", "Food is too expensive"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Love it", toppings: ["Cheese sauce", "Nacho cheese", "Bacon bits"], payExtra: "Maybe", motivators: ["Price", "Short waiting time"] },
            { id: 23, grade: "G4–G6", frequency: "Most events", budget: "15–25 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Corn"], payExtra: "Maybe", motivators: ["Price"] },
            { id: 24, grade: "G4–G6", frequency: "Sometimes", budget: "25–35 baht", dislike: ["Not enough food choices"], allergy: "Lactose", mexican: "Haven't tried", spicy: "Neutral", toppings: ["Bacon bits", "Salsa", "Green onions"], payExtra: "No, probably not", motivators: ["Price", "Something new to try"] },
            { id: 25, grade: "G4–G6", frequency: "Sometimes", budget: "35–45 baht", dislike: ["Food is too expensive", "Portions are too small"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Hate it", toppings: ["Cheese sauce", "Bacon bits"], payExtra: "Maybe", motivators: ["Price", "Looks delicious"] },
            { id: 26, grade: "G4–G6", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Extra cheese", "Sour cream", "Ground pork", "Hot sauce", "Green onions"], payExtra: "Yes, definitely", motivators: ["Taste", "Portion size"] },
            { id: 27, grade: "G4–G6", frequency: "Most events", budget: "25–35 baht", dislike: ["Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Cheese sauce", "Nacho cheese"], payExtra: "Maybe", motivators: ["Taste", "Looks delicious"] },
            { id: 28, grade: "G4–G6", frequency: "Never", budget: "15–25 baht", dislike: ["Poor food quality"], allergy: "No allergies/restrictions", mexican: "Dislike it", spicy: "Hate it", toppings: [], payExtra: "No, never", motivators: ["Price"] },
            { id: 29, grade: "G4–G6", frequency: "Sometimes", budget: "25–35 baht", dislike: ["Long waiting times", "Food is too expensive"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Nacho cheese"], payExtra: "Maybe", motivators: ["Price"] },
            { id: 30, grade: "G4–G6", frequency: "Most events", budget: "35–45 baht", dislike: ["Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Cheese sauce", "Bacon bits", "Sour cream"], payExtra: "Maybe", motivators: ["Taste", "Recommended by friends"] },
            { id: 31, grade: "G4–G6", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Bacon bits", "Extra cheese", "Nacho cheese", "Hot sauce", "Sour cream"], payExtra: "Yes, definitely", motivators: ["Taste", "Looks delicious"] },
            { id: 32, grade: "G4–G6", frequency: "Most events", budget: "25–35 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Like it", toppings: ["Cheese sauce", "Nacho cheese", "Bacon bits"], payExtra: "Maybe", motivators: ["Taste", "Short waiting time"] },
            { id: 33, grade: "G4–G6", frequency: "Sometimes", budget: "25–35 baht", dislike: ["Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Haven't tried", spicy: "Neutral", toppings: ["Cheese sauce", "Corn"], payExtra: "Maybe", motivators: ["Price", "Looks delicious"] },

            // G7-G9: 22 respondents (40.0%)
            { id: 34, grade: "G7–G9", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Bacon bits", "Extra cheese", "Sour cream", "Ground pork", "Nacho cheese", "Hot sauce", "Salsa", "Jalapeños", "Green onions", "Corn"], payExtra: "Yes, definitely", motivators: ["Taste", "Short waiting time", "Portion size"] },
            { id: 35, grade: "G7–G9", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits", "Sour cream", "Ground pork", "Hot sauce", "Salsa", "Jalapeños"], payExtra: "Yes, definitely", motivators: ["Taste", "Portion size"] },
            { id: 36, grade: "G7–G9", frequency: "Every event", budget: "35–45 baht", dislike: ["Long waiting times"], allergy: "Seafood", mexican: "Love it", spicy: "Like it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits", "Sour cream", "Ground pork", "Nacho cheese", "Hot sauce", "Salsa"], payExtra: "Yes, definitely", motivators: ["Taste", "Looks delicious"] },
            { id: 37, grade: "G7–G9", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times", "Food is too expensive"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits", "Sour cream", "Ground pork", "Hot sauce", "Salsa", "Jalapeños", "Green onions"], payExtra: "Yes, definitely", motivators: ["Taste", "Looks delicious"] },
            { id: 38, grade: "G7–G9", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Bacon bits", "Extra cheese", "Ground pork", "Sour cream", "Nacho cheese", "Hot sauce", "Jalapeños"], payExtra: "Yes, definitely", motivators: ["Taste", "Short waiting time"] },
            { id: 39, grade: "G7–G9", frequency: "Every event", budget: "35–45 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits", "Sour cream", "Ground pork", "Nacho cheese", "Hot sauce"], payExtra: "Maybe", motivators: ["Taste", "Price"] },
            { id: 40, grade: "G7–G9", frequency: "Every event", budget: "45+ baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits", "Ground pork", "Sour cream", "Nacho cheese", "Hot sauce", "Salsa", "Jalapeños", "Green onions"], payExtra: "Yes, definitely", motivators: ["Taste", "Short waiting time", "Something new to try"] },
            { id: 41, grade: "G7–G9", frequency: "Most events", budget: "45+ baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Cheese sauce", "Bacon bits", "Ground pork", "Sour cream", "Nacho cheese"], payExtra: "Maybe", motivators: ["Taste", "Looks delicious"] },
            { id: 42, grade: "G7–G9", frequency: "Most events", budget: "45+ baht", dislike: ["Long waiting times", "Food runs out too quickly", "Portions are too small"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Cheese sauce", "Extra cheese", "Ground pork", "Sour cream", "Hot sauce", "Salsa"], payExtra: "Maybe", motivators: ["Taste", "Portion size"] },
            { id: 43, grade: "G7–G9", frequency: "Most events", budget: "25–35 baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits", "Nacho cheese"], payExtra: "Maybe", motivators: ["Taste", "Price"] },
            { id: 44, grade: "G7–G9", frequency: "Most events", budget: "35–45 baht", dislike: ["Long waiting times", "Food runs out too quickly", "Portions are too small"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Bacon bits", "Nacho cheese", "Corn"], payExtra: "Maybe", motivators: ["Price", "Looks delicious"] },
            { id: 45, grade: "G7–G9", frequency: "Most events", budget: "45+ baht", dislike: ["Long waiting times"], allergy: "No allergies/restrictions", mexican: "Like it", spicy: "Like it", toppings: ["Cheese sauce", "Bacon bits", "Ground pork", "Sour cream", "Salsa", "Green onions"], payExtra: "Maybe", motivators: ["Taste", "Price"] },
            { id: 46, grade: "G7–G9", frequency: "Most events", budget: "25–35 baht", dislike: ["Long waiting times", "Food is too expensive"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Like it", toppings: ["Cheese sauce", "Bacon bits", "Extra cheese"], payExtra: "Maybe", motivators: ["Price", "Short waiting time"] },
            { id: 47, grade: "G7–G9", frequency: "Most events", budget: "35–45 baht", dislike: ["Long waiting times", "Not enough food choices"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Bacon bits", "Nacho cheese", "Corn"], payExtra: "Maybe", motivators: ["Price", "Looks delicious"] },
            { id: 48, grade: "G7–G9", frequency: "Sometimes", budget: "25–35 baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Extra cheese", "Sour cream", "Ground pork"], payExtra: "Maybe", motivators: ["Price", "Taste"] },
            { id: 49, grade: "G7–G9", frequency: "Sometimes", budget: "15–25 baht", dislike: ["Food is too expensive", "Portions are too small"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Neutral", toppings: ["Cheese sauce", "Bacon bits"], payExtra: "No, probably not", motivators: ["Price", "Looks delicious"] },
            { id: 50, grade: "G7–G9", frequency: "Sometimes", budget: "25–35 baht", dislike: ["Not enough food choices", "Poor food quality"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Dislike it", toppings: ["Corn", "Green onions"], payExtra: "No, probably not", motivators: ["Price", "Something new to try"] },
            { id: 51, grade: "G7–G9", frequency: "Sometimes", budget: "15–25 baht", dislike: ["Long waiting times", "Portions are too small", "Poor food quality"], allergy: "No allergies/restrictions", mexican: "Haven't tried", spicy: "Neutral", toppings: ["Cheese sauce", "Corn"], payExtra: "No, probably not", motivators: ["Price", "Short waiting time"] },
            { id: 52, grade: "G7–G9", frequency: "Sometimes", budget: "25–35 baht", dislike: ["Food is too expensive"], allergy: "Longan", mexican: "Like it", spicy: "Like it", toppings: ["Bacon bits", "Sour cream", "Salsa"], payExtra: "Maybe", motivators: ["Price"] },
            { id: 53, grade: "G7–G9", frequency: "Rarely", budget: "15–25 baht", dislike: ["Not enough food choices", "Poor food quality"], allergy: "No allergies/restrictions", mexican: "Neutral", spicy: "Hate it", toppings: ["Corn"], payExtra: "No, never", motivators: ["Price"] },
            { id: 54, grade: "G7–G9", frequency: "Every event", budget: "35–45 baht", dislike: ["Long waiting times", "Food runs out too quickly"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Bacon bits", "Extra cheese", "Sour cream", "Ground pork", "Nacho cheese", "Hot sauce", "Salsa", "Jalapeños", "Green onions", "Corn"], payExtra: "Yes, definitely", motivators: ["Taste", "Looks delicious"] },
            { id: 55, grade: "G7–G9", frequency: "Most events", budget: "45+ baht", dislike: ["Long waiting times", "Food is too expensive"], allergy: "No allergies/restrictions", mexican: "Love it", spicy: "Love it", toppings: ["Cheese sauce", "Extra cheese", "Bacon bits", "Sour cream", "Ground pork", "Hot sauce", "Salsa", "Jalapeños", "Green onions"], payExtra: "Yes, definitely", motivators: ["Taste", "Something new to try"] }
        ];

        // Global Chart Instance Objects
        let charts = {};

        // Active filter state
        let currentFilters = {
            grade: "ALL",
            role: "ALL",
            spicy: "ALL",
            spending: "ALL"
        };

        window.onload = function() {
            // Check & set visual theme (Set to Dark Mode by default)
            const savedTheme = localStorage.getItem('theme');
            const isDark = savedTheme !== 'light'; // default to true (dark) if not explicitly set to light
            
            if (isDark) {
                document.documentElement.classList.add('dark');
                document.getElementById('theme-toggle-icon').className = "fa-solid fa-sun text-lg";
            } else {
                document.documentElement.classList.remove('dark');
                document.getElementById('theme-toggle-icon').className = "fa-solid fa-moon text-lg";
            }

            // Init core functions
            setupSearch();
            setupThemeToggle();
            setupMobileMenu();
            renderDashboard();
        };

        // Theme Toggle Controller
        function setupThemeToggle() {
            const btn = document.getElementById('theme-toggle-btn');
            const icon = document.getElementById('theme-toggle-icon');
            btn.addEventListener('click', () => {
                const isDark = document.documentElement.classList.toggle('dark');
                localStorage.setItem('theme', isDark ? 'dark' : 'light');
                icon.className = isDark ? "fa-solid fa-sun text-lg" : "fa-solid fa-moon text-lg";
                // Re-render charts with updated theme options
                renderDashboard();
            });
        }

        // Mobile Responsive Hamburger controller
        function setupMobileMenu() {
            const menuBtn = document.getElementById('mobile-menu-btn');
            const sidebar = document.getElementById('sidebar');
            menuBtn.addEventListener('click', (e) => {
                e.stopPropagation();
                sidebar.classList.toggle('hidden');
                sidebar.classList.toggle('flex');
                sidebar.classList.toggle('fixed');
                sidebar.classList.toggle('h-screen');
            });
            // Auto close drawer when clicking elsewhere
            document.addEventListener('click', () => {
                if (window.innerWidth < 768) {
                    sidebar.classList.add('hidden');
                    sidebar.classList.remove('flex', 'fixed', 'h-screen');
                }
            });
        }

        // Search Bar highlighting
        function setupSearch() {
            const search = document.getElementById('dashboard-search');
            search.addEventListener('input', (e) => {
                const term = e.target.value.toLowerCase().trim();
                if (!term) {
                    document.querySelectorAll('.print-card').forEach(el => el.classList.remove('ring-4', 'ring-primary-500', 'scale-[1.01]'));
                    return;
                }

                document.querySelectorAll('.print-card').forEach(card => {
                    const text = card.textContent.toLowerCase();
                    if (text.includes(term)) {
                        card.classList.add('ring-4', 'ring-primary-500', 'scale-[1.01]');
                    } else {
                        card.classList.remove('ring-4', 'ring-primary-500', 'scale-[1.01]');
                    }
                });
            });
        }

        // UI link styling
        function setActiveLink(clickedEl) {
            document.querySelectorAll('aside nav a').forEach(a => {
                a.className = "flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 text-slate-600 dark:text-slate-400 hover:bg-slate-100 dark:hover:bg-slate-900";
            });
            clickedEl.className = "flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-medium transition-all duration-200 bg-primary-50 dark:bg-primary-950/40 text-primary-600 dark:text-primary-400";
        }

        // Reset all segmentation filters back to initial state
        function resetFilters() {
            document.getElementById('filter-grade').value = "ALL";
            document.getElementById('filter-role').value = "ALL";
            document.getElementById('filter-spicy').value = "ALL";
            document.getElementById('filter-spending').value = "ALL";
            applyFilters();
        }

        // Apply drop down matrix inputs
        function applyFilters() {
            currentFilters.grade = document.getElementById('filter-grade').value;
            currentFilters.role = document.getElementById('filter-role').value;
            currentFilters.spicy = document.getElementById('filter-spicy').value;
            currentFilters.spending = document.getElementById('filter-spending').value;
            renderDashboard();
        }

        // Dynamic cohort filtering engine
        function getFilteredData() {
            return RESPONDENTS.filter(r => {
                // Grade Tier
                if (currentFilters.grade !== "ALL" && r.grade !== currentFilters.grade) return false;
                
                // Role Categorizer
                if (currentFilters.role !== "ALL") {
                    const isTeacher = r.grade === "Teachers";
                    if (currentFilters.role === "Students" && isTeacher) return false;
                    if (currentFilters.role === "Teachers" && !isTeacher) return false;
                }

                // Spicy affinity
                if (currentFilters.spicy !== "ALL") {
                    const enjoysSpicy = (r.spicy === "Love it" || r.spicy === "Like it");
                    if (currentFilters.spicy === "Spicy Lovers" && !enjoysSpicy) return false;
                    if (currentFilters.spicy === "Mild/No Spicy" && enjoysSpicy) return false;
                }

                // Spending budgets
                if (currentFilters.spending !== "ALL") {
                    const isHighSpender = (r.budget === "25–35 baht" || r.budget === "35–45 baht" || r.budget === "45+ baht");
                    if (currentFilters.spending === "25+" && !isHighSpender) return false;
                    if (currentFilters.spending === "under 25" && isHighSpender) return false;
                }

                return true;
            });
        }

        // Render & Update entire screen dashboard loop
        function renderDashboard() {
            const data = getFilteredData();
            const total = data.length;

            // Global Design Styling Tokens based on Light/Dark active class
            const isDark = document.documentElement.classList.contains('dark');
            const gridColor = isDark ? '#334155' : '#e2e8f0';
            const textColor = isDark ? '#94a3b8' : '#64748b';
            const boldTextColor = isDark ? '#ffffff' : '#0f172a';

            // Chart color templates
            const primaryColors = ['#637eff', '#34d399', '#f59e0b', '#a855f7', '#ec4899', '#06b6d4', '#f43f5e'];
            const hoverColors = ['#4356f5', '#10b981', '#d97706', '#8b5cf6', '#db2777', '#0891b2', '#e11d48'];

            // Destroy and re-create charts cleanly to avoid canvas ghost rendering issues
            function cleanCreateChart(chartId, config) {
                if (charts[chartId]) {
                    charts[chartId].destroy();
                }
                const ctx = document.getElementById(chartId).getContext('2d');
                charts[chartId] = new Chart(ctx, config);
            }

            // --- 1. DYNAMIC SUMMARY METRIC CARDS ---
            document.getElementById('metric-responses').innerText = total;
            document.getElementById('metric-responses-sub').innerText = `${((total / 55) * 100).toFixed(1)}% of total cohort`;

            // Loyalty percentage
            const loyalCount = data.filter(r => r.frequency === "Every event" || r.frequency === "Most events").length;
            document.getElementById('metric-frequency').innerText = total > 0 ? `${((loyalCount / total) * 100).toFixed(0)}%` : '0%';

            // Top spending range percentages
            const spending45Count = data.filter(r => r.budget === "45+ baht").length;
            document.getElementById('metric-spending-sub').innerText = total > 0 ? `${((spending45Count / total) * 100).toFixed(1)}% of cohort` : '0%';

            // Premium pay willingness percentage
            const upsellCount = data.filter(r => r.payExtra === "Yes, definitely" || r.payExtra === "Maybe").length;
            document.getElementById('metric-upsell').innerText = total > 0 ? `${((upsellCount / total) * 100).toFixed(1)}%` : '0%';


            // --- 2. CHART CONFIG: GRADES CHART (PIE) ---
            const gradesCounts = { "G1–G3": 0, "G4–G6": 0, "G7–G9": 0, "G10–G12": 0, "Teachers": 0 };
            data.forEach(r => { if (gradesCounts[r.grade] !== undefined) gradesCounts[r.grade]++; });

            cleanCreateChart('chart-grades', {
                type: 'doughnut',
                data: {
                    labels: Object.keys(gradesCounts),
                    datasets: [{
                        data: Object.values(gradesCounts),
                        backgroundColor: primaryColors.slice(0, 5),
                        hoverBackgroundColor: hoverColors.slice(0, 5),
                        borderWidth: isDark ? 2 : 1,
                        borderColor: isDark ? '#0f172a' : '#ffffff'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { position: 'bottom', labels: { color: textColor, boxWidth: 12, font: { family: 'Plus Jakarta Sans', size: 11 } } }
                    }
                }
            });


            // --- 3. CHART CONFIG: FREQUENCY (BAR) ---
            const freqLabels = ["Every event", "Most events", "Sometimes", "Rarely", "Never"];
            const freqCounts = freqLabels.map(lbl => data.filter(r => r.frequency === lbl).length);

            cleanCreateChart('chart-frequency', {
                type: 'bar',
                data: {
                    labels: freqLabels,
                    datasets: [{
                        label: 'Respondents',
                        data: freqCounts,
                        backgroundColor: '#637eff',
                        borderRadius: 6
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: {
                        x: { grid: { display: false }, ticks: { color: textColor, font: { size: 11 } } },
                        y: { grid: { color: gridColor }, ticks: { color: textColor, precision: 0 } }
                    }
                }
            });


            // --- 4. CHART CONFIG: MEXICAN LOVERS (PIE/DONUT) ---
            const mexLabels = ["Love it", "Like it", "Neutral", "Haven't tried", "Dislike it", "Hate it"];
            const mexCounts = mexLabels.map(lbl => data.filter(r => r.mexican === lbl).length);

            cleanCreateChart('chart-mexican', {
                type: 'pie',
                data: {
                    labels: mexLabels,
                    datasets: [{
                        data: mexCounts,
                        backgroundColor: primaryColors,
                        borderWidth: isDark ? 2 : 1,
                        borderColor: isDark ? '#0f172a' : '#ffffff'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { position: 'bottom', labels: { color: textColor, boxWidth: 10, font: { size: 10 } } }
                    }
                }
            });


            // --- 5. CHART CONFIG: SPICY LOVERS (DONUT) ---
            const spicyLabels = ["Love it", "Like it", "Neutral", "Dislike it", "Hate it"];
            const spicyCounts = spicyLabels.map(lbl => data.filter(r => r.spicy === lbl).length);

            cleanCreateChart('chart-spicy', {
                type: 'doughnut',
                data: {
                    labels: spicyLabels,
                    datasets: [{
                        data: spicyCounts,
                        backgroundColor: primaryColors.slice(1, 6),
                        borderWidth: isDark ? 2 : 1,
                        borderColor: isDark ? '#0f172a' : '#ffffff'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { position: 'bottom', labels: { color: textColor, boxWidth: 10, font: { size: 10 } } }
                    }
                }
            });


            // --- 6. ALLERGIES SECTION POPULATOR ---
            const allergyCounts = {};
            data.forEach(r => {
                allergyCounts[r.allergy] = (allergyCounts[r.allergy] || 0) + 1;
            });
            const container = document.getElementById('allergies-container');
            container.innerHTML = '';
            
            Object.entries(allergyCounts).forEach(([allergy, cnt]) => {
                const pct = total > 0 ? ((cnt / total) * 100).toFixed(0) : 0;
                const progressColor = allergy === 'No allergies/restrictions' ? 'bg-emerald-500' : 'bg-rose-400';
                container.innerHTML += `
                    <div>
                        <div class="flex justify-between text-xs font-semibold mb-1">
                            <span>${allergy}</span>
                            <span>${cnt} (${pct}%)</span>
                        </div>
                        <div class="w-full bg-slate-100 dark:bg-slate-900 h-2 rounded-full overflow-hidden">
                            <div class="${progressColor} h-2 rounded-full" style="width: ${pct}%"></div>
                        </div>
                    </div>
                `;
            });
            const cleanNoAllergiesCount = data.filter(r => r.allergy === 'No allergies/restrictions').length;
            document.getElementById('safe-percent').innerText = total > 0 ? `${((cleanNoAllergiesCount / total) * 100).toFixed(0)}%` : '100%';


            // --- 7. CHART CONFIG: TOPPINGS POPULARITY (HORIZONTAL BAR) ---
            const toppingsLabels = ["Cheese sauce", "Bacon bits", "Extra cheese", "Sour cream", "Ground pork", "Nacho cheese", "Hot sauce", "Salsa", "Jalapeños", "Green onions", "Corn"];
            const toppingsCounts = toppingsLabels.map(top => data.filter(r => r.toppings.includes(top)).length);

            // Create custom interactive vertical/horizontal bar chart with hover tools
            cleanCreateChart('chart-toppings', {
                type: 'bar',
                data: {
                    labels: toppingsLabels,
                    datasets: [{
                        label: 'Topping Preference Count',
                        data: toppingsCounts,
                        backgroundColor: function(context) {
                            const index = context.dataIndex;
                            return index === 0 ? '#4f46e5' : '#818cf8'; // Highlight Cheese sauce
                        },
                        borderRadius: 6
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: {
                        x: { grid: { color: gridColor }, ticks: { color: textColor, precision: 0 } },
                        y: { grid: { display: false }, ticks: { color: textColor, font: { size: 11 } } }
                    },
                    onClick: (event, elements) => {
                        if (elements.length > 0) {
                            const index = elements[0].index;
                            openDrilldown(toppingsLabels[index], toppingsCounts[index], 'toppings');
                        }
                    }
                }
            });


            // --- 8. CHART CONFIG: BUDGETS (BAR) ---
            const budgetLabels = ["5–15 baht", "15–25 baht", "25–35 baht", "35–45 baht", "45+ baht"];
            const budgetCounts = budgetLabels.map(lbl => data.filter(r => r.budget === lbl).length);

            cleanCreateChart('chart-budget', {
                type: 'bar',
                data: {
                    labels: budgetLabels,
                    datasets: [{
                        label: 'Spend Level Limit',
                        data: budgetCounts,
                        backgroundColor: '#34d399',
                        borderRadius: 6
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: {
                        x: { grid: { display: false }, ticks: { color: textColor, font: { size: 10 } } },
                        y: { grid: { color: gridColor }, ticks: { color: textColor, precision: 0 } }
                    }
                }
            });


            // --- 9. CHART CONFIG: UPSELL EXTRA WILLINGNESS ---
            const upsellLabels = ["Yes, definitely", "Maybe", "No, probably not", "No, never"];
            const upsellCounts = upsellLabels.map(lbl => data.filter(r => r.payExtra === lbl).length);

            cleanCreateChart('chart-upsell-detail', {
                type: 'doughnut',
                data: {
                    labels: upsellLabels,
                    datasets: [{
                        data: upsellCounts,
                        backgroundColor: ['#a855f7', '#c084fc', '#e9d5ff', '#f3e8ff'],
                        borderWidth: isDark ? 2 : 1,
                        borderColor: isDark ? '#0f172a' : '#ffffff'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { position: 'right', labels: { color: textColor, boxWidth: 10, font: { size: 9 } } }
                    }
                }
            });


            // --- 10. CHART CONFIG: COMPLAINTS (BAR) ---
            const complaintLabels = ["Long waiting times", "Food runs out too quickly", "Food is too expensive", "Portions are too small", "Not enough food choices", "Poor food quality"];
            const complaintCounts = complaintLabels.map(lbl => data.filter(r => r.dislike.includes(lbl)).length);

            cleanCreateChart('chart-complaints', {
                type: 'bar',
                data: {
                    labels: complaintLabels,
                    datasets: [{
                        label: 'Complaint Mentions',
                        data: complaintCounts,
                        backgroundColor: '#f43f5e',
                        borderRadius: 6
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: {
                        x: { grid: { color: gridColor }, ticks: { color: textColor, precision: 0 } },
                        y: { grid: { display: false }, ticks: { color: textColor, font: { size: 10 } } }
                    },
                    onClick: (event, elements) => {
                        if (elements.length > 0) {
                            const index = elements[0].index;
                            openDrilldown(complaintLabels[index], complaintCounts[index], 'dislike');
                        }
                    }
                }
            });


            // --- 11. CHART CONFIG: BUYING MOTIVATORS (BAR) ---
            const motivatorLabels = ["Taste", "Price", "Short waiting time", "Portion size", "Looks delicious", "Something new to try", "Recommended by friends"];
            const motivatorCounts = motivatorLabels.map(lbl => data.filter(r => r.motivators.includes(lbl)).length);

            cleanCreateChart('chart-motivators', {
                type: 'bar',
                data: {
                    labels: motivatorLabels,
                    datasets: [{
                        label: 'Core Buy Motivators',
                        data: motivatorCounts,
                        backgroundColor: '#fbbf24',
                        borderRadius: 6
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: {
                        x: { grid: { color: gridColor }, ticks: { color: textColor, precision: 0 } },
                        y: { grid: { display: false }, ticks: { color: textColor, font: { size: 10 } } }
                    },
                    onClick: (event, elements) => {
                        if (elements.length > 0) {
                            const index = elements[0].index;
                            openDrilldown(motivatorLabels[index], motivatorCounts[index], 'motivators');
                        }
                    }
                }
            });


            // --- 12. CHART CONFIG: GRADE COMPONENT CROSS-COMPARATIVE INDEX ---
            // Let's compare grades by 3 metrics:
            // - Spicy affinity index: % within grade who love/like spicy
            // - Upsell willingness: % within grade who say Yes/Maybe
            // - Spend 35+ Baht index: % within grade who spend 35+
            const comparedGrades = ["G1–G3", "G4–G6", "G7–G9", "G10–G12", "Teachers"];
            const spicyIndexData = [];
            const upsellIndexData = [];
            const highSpendIndexData = [];

            comparedGrades.forEach(grade => {
                const gradeCohort = RESPONDENTS.filter(r => r.grade === grade);
                const gTotal = gradeCohort.length;

                if (gTotal === 0) {
                    spicyIndexData.push(0);
                    upsellIndexData.push(0);
                    highSpendIndexData.push(0);
                } else {
                    const spicyNum = gradeCohort.filter(r => r.spicy === "Love it" || r.spicy === "Like it").length;
                    const upsellNum = gradeCohort.filter(r => r.payExtra === "Yes, definitely" || r.payExtra === "Maybe").length;
                    const spendNum = gradeCohort.filter(r => r.budget === "35–45 baht" || r.budget === "45+ baht").length;

                    spicyIndexData.push(((spicyNum / gTotal) * 100).toFixed(0));
                    upsellIndexData.push(((upsellNum / gTotal) * 100).toFixed(0));
                    highSpendIndexData.push(((spendNum / gTotal) * 100).toFixed(0));
                }
            });

            cleanCreateChart('chart-grade-comparison', {
                type: 'bar',
                data: {
                    labels: comparedGrades,
                    datasets: [
                        { label: 'Spicy Affinity Index (%)', data: spicyIndexData, backgroundColor: '#f43f5e', borderRadius: 4 },
                        { label: 'Topping Upsell Willingness (%)', data: upsellIndexData, backgroundColor: '#a855f7', borderRadius: 4 },
                        { label: 'Spend 35+ Baht Index (%)', data: highSpendIndexData, backgroundColor: '#34d399', borderRadius: 4 }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { position: 'bottom', labels: { color: textColor, boxWidth: 12, font: { size: 10 } } }
                    },
                    scales: {
                        x: { grid: { display: false }, ticks: { color: textColor } },
                        y: { min: 0, max: 100, grid: { color: gridColor }, ticks: { color: textColor } }
                    }
                }
            });


            // --- 13. INDIVIDUAL RECORDS POPULATOR TABLE ---
            const tbody = document.getElementById('raw-data-table-body');
            tbody.innerHTML = '';
            data.forEach(r => {
                const toppingsShort = r.toppings.length > 0 ? r.toppings.join(', ') : 'None';
                tbody.innerHTML += `
                    <tr class="hover:bg-slate-50 dark:hover:bg-slate-900/60 transition-colors">
                        <td class="p-3 font-semibold text-slate-500">#${r.id}</td>
                        <td class="p-3 font-semibold">${r.grade}</td>
                        <td class="p-3 text-xs"><span class="px-2 py-0.5 rounded bg-slate-100 dark:bg-slate-800">${r.frequency}</span></td>
                        <td class="p-3 font-semibold text-xs text-amber-500">${r.budget}</td>
                        <td class="p-3 text-xs">${r.mexican}</td>
                        <td class="p-3 text-xs">${r.spicy}</td>
                        <td class="p-3 text-xs text-rose-500 font-medium">${r.allergy}</td>
                        <td class="p-3 text-xs text-slate-500 dark:text-slate-400 max-w-[200px] truncate" title="${toppingsShort}">${toppingsShort}</td>
                    </tr>
                `;
            });
            document.getElementById('log-count').innerText = `${total} Results`;
        }


        // --- 14. INTERACTIVE DRILL-DOWN PANEL LOGIC ---
        function openDrilldown(itemName, totalCount, categoryKey) {
            const drawer = document.getElementById('drilldown-drawer');
            const filteredCohort = getFilteredData();
            const totalInFilteredCohort = filteredCohort.length;

            document.getElementById('drill-title').innerText = itemName;
            document.getElementById('drill-count').innerText = totalCount;
            
            const percentage = totalInFilteredCohort > 0 ? ((totalCount / totalInFilteredCohort) * 100).toFixed(1) : 0;
            document.getElementById('drill-percentage').innerText = `${percentage}%`;

            // Calculate grade-wise breakdown inside this selection
            const grades = ["G1–G3", "G4–G6", "G7–G9", "G10–G12", "Teachers"];
            const breakdownList = document.getElementById('drill-grades-list');
            breakdownList.innerHTML = '';

            // Grade index tracking to write clean logic
            let highestSelectedGradeName = "";
            let highestSelectedPercent = -1;

            grades.forEach(grade => {
                const totalInGrade = filteredCohort.filter(r => r.grade === grade).length;
                let countWithTopping = 0;

                if (categoryKey === 'toppings') {
                    countWithTopping = filteredCohort.filter(r => r.grade === grade && r.toppings.includes(itemName)).length;
                } else if (categoryKey === 'dislike') {
                    countWithTopping = filteredCohort.filter(r => r.grade === r.grade && r.dislike.includes(itemName) && r.grade === grade).length;
                } else if (categoryKey === 'motivators') {
                    countWithTopping = filteredCohort.filter(r => r.grade === grade && r.motivators.includes(itemName)).length;
                }

                const gradePercentOfTopping = totalInGrade > 0 ? ((countWithTopping / totalInGrade) * 100).toFixed(0) : 0;
                
                if (parseFloat(gradePercentOfTopping) > highestSelectedPercent) {
                    highestSelectedPercent = parseFloat(gradePercentOfTopping);
                    highestSelectedGradeName = grade;
                }

                breakdownList.innerHTML += `
                    <div>
                        <div class="flex justify-between text-xs font-semibold mb-1">
                            <span>${grade} (${totalInGrade} total)</span>
                            <span class="text-primary-600 dark:text-primary-400">${countWithTopping} with this (${gradePercentOfTopping}%)</span>
                        </div>
                        <div class="w-full bg-slate-100 dark:bg-slate-900 h-2 rounded-full overflow-hidden">
                            <div class="bg-primary-500 h-2 rounded-full" style="width: ${gradePercentOfTopping}%"></div>
                        </div>
                    </div>
                `;
            });

            // Write smart dynamic recommendation based on item clicked
            let dynamicInsight = "";
            if (categoryKey === 'toppings') {
                dynamicInsight = `The topping ${itemName} is highly favored by ${highestSelectedGradeName}. Optimize prep tables with pre-dispensed trays of ${itemName} ready to deploy specifically to school stands during peak break intervals.`;
            } else if (categoryKey === 'dislike') {
                dynamicInsight = `Addressing ${itemName} must be a top priority for our sales event. If wait times are high, establish a pre-ordering platform, or streamline transaction steps.`;
            } else if (categoryKey === 'motivators') {
                dynamicInsight = `Because ${itemName} is a primary buying criteria, display and emphasize this metric prominently on our stall menus and marketing leaflets.`;
            }

            document.getElementById('drill-insight').innerText = dynamicInsight;

            // Open Side Drawer
            drawer.classList.remove('translate-x-full');
        }

        function closeDrilldown() {
            document.getElementById('drilldown-drawer').classList.add('translate-x-full');
        }
    </script>
</body>
</html>
