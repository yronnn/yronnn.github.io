[taco_nacho_project_dashboard (1).html](https://github.com/user-attachments/files/29383369/taco_nacho_project_dashboard.1.html)
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>John Pork Tacos - School Project Business Dashboard</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#fffbeb',
                            100: '#fef3c7',
                            200: '#fde68a',
                            300: '#fcd34d',
                            400: '#fbbf24',
                            500: '#f59e0b',
                            600: '#d97706',
                            700: '#b45309',
                            800: '#92400e',
                            900: '#78350f',
                        }
                    }
                }
            }
        }
    </script>
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap');
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #030712; /* Tailwind slate-950 */
        }
        /* Custom scrollbar for Dark Theme */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #0f172a; /* slate-900 */
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb {
            background: #334155; /* slate-700 */
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #475569; /* slate-600 */
        }
        @media print {
            .no-print {
                display: none !important;
            }
            body {
                background: white;
                color: black;
            }
            .print-card {
                border: 1px solid #e2e8f0 !important;
                box-shadow: none !important;
                break-inside: avoid;
                background: white !important;
                color: black !important;
            }
        }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen flex flex-col antialiased">

    <!-- Top Banner (Project Context Contextualizer) -->
    <header class="bg-gradient-to-r from-amber-950 via-orange-900 to-amber-900 text-white shadow-md no-print border-b border-orange-850">
        <div class="max-w-7xl mx-auto px-4 py-3 sm:px-6 lg:px-8 flex flex-col sm:flex-row justify-between items-center gap-2">
            <div class="flex items-center space-x-3">
                <span class="bg-white/10 text-brand-300 text-xs font-bold px-2.5 py-1 rounded-full uppercase tracking-wider backdrop-blur-sm border border-white/10">Grade 9 Entrepreneurship</span>
                <p class="text-xs sm:text-sm font-medium text-slate-200">Walking Taco & Nacho Project Dashboard</p>
            </div>
            <div class="flex items-center space-x-4 text-xs sm:text-sm text-amber-100">
                <span>⏱️ Event Duration: <strong>100 Mins</strong></span>
                <span>👥 Target: <strong>700+ Students & Teachers</strong></span>
            </div>
        </div>
    </header>

    <!-- Navigation / Brand Header -->
    <nav class="bg-slate-900/95 border-b border-slate-800 sticky top-0 z-40 no-print backdrop-blur-md">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center">
                    <div class="flex-shrink-0 flex items-center space-x-2">
                        <div class="p-2 bg-brand-600 text-white rounded-xl shadow-md shadow-brand-600/30">
                            <i data-lucide="concourse" class="w-6 h-6 rotate-45"></i>
                        </div>
                        <span class="text-xl font-bold bg-gradient-to-r from-amber-400 to-orange-400 bg-clip-text text-transparent">John Pork Tacos</span>
                    </div>
                    <div class="hidden md:ml-6 md:flex md:space-x-4">
                        <a href="#dashboard" class="border-transparent text-slate-300 hover:border-brand-400 hover:text-brand-300 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-semibold transition-all">
                            Dashboard
                        </a>
                        <a href="#survey" class="border-transparent text-slate-300 hover:border-brand-400 hover:text-brand-300 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-semibold transition-all">
                            Survey Insights
                        </a>
                        <a href="#calculators" class="border-transparent text-slate-300 hover:border-brand-400 hover:text-brand-300 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-semibold transition-all">
                            Cost & Selling Calculator
                        </a>
                        <a href="#builder" class="border-transparent text-slate-300 hover:border-brand-400 hover:text-brand-300 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-semibold transition-all">
                            Product Builder
                        </a>
                        <a href="#inventory" class="border-transparent text-slate-300 hover:border-brand-400 hover:text-brand-300 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-semibold transition-all">
                            Inventory Planner
                        </a>
                    </div>
                </div>
                <div class="flex items-center space-x-3">
                    <button onclick="window.print()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 px-3.5 py-2 rounded-xl text-sm font-bold flex items-center gap-2 transition-all border border-slate-700">
                        <i data-lucide="printer" class="w-4 h-4"></i>
                        <span>Print Report</span>
                    </button>
                    <button onclick="exportFullSummary()" class="bg-brand-600 hover:bg-brand-700 text-white px-3.5 py-2 rounded-xl text-sm font-bold flex items-center gap-2 transition-all shadow-lg shadow-brand-600/15">
                        <i data-lucide="download" class="w-4 h-4"></i>
                        <span class="hidden sm:inline">Export Calculations</span>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Container -->
    <main class="flex-grow max-w-7xl mx-auto w-full px-4 sm:px-6 lg:px-8 py-8 space-y-10">

        <!-- Custom Notification banner in app -->
        <div id="toast-container" class="fixed bottom-5 right-5 z-50 flex flex-col gap-2 pointer-events-none"></div>

        <!-- Section 1: Dashboard Analytics Grid -->
        <section id="dashboard" class="space-y-6 scroll-mt-20">
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                <div>
                    <h1 class="text-3xl font-extrabold text-slate-100 tracking-tight">Real-Time Business Model</h1>
                    <p class="text-slate-400 mt-1">Configure your variables below to watch the live simulation of your business day.</p>
                </div>
                <!-- Enhanced Customer Value Setter with quick tap action buttons -->
                <div class="bg-slate-900 p-2 rounded-xl shadow-sm border border-slate-800 flex items-center gap-3 no-print">
                    <span class="text-xs font-bold text-slate-400 pl-2 uppercase tracking-wide">Simulated Customers:</span>
                    <div class="flex items-center space-x-1">
                        <button onclick="adjustGlobalServings(-10)" class="bg-slate-800 hover:bg-slate-700 text-slate-200 w-8 h-8 rounded-lg font-black flex items-center justify-center transition-all border border-slate-700">-</button>
                        <input type="number" id="global-servings-input" value="150" min="1" step="10" oninput="syncServings(this.value)" 
                            class="w-24 h-8 text-center font-bold text-brand-400 bg-slate-950 border border-slate-800 rounded-lg focus:outline-none focus:ring-2 focus:ring-brand-500 text-sm">
                        <button onclick="adjustGlobalServings(10)" class="bg-slate-800 hover:bg-slate-700 text-slate-200 w-8 h-8 rounded-lg font-black flex items-center justify-center transition-all border border-slate-700">+</button>
                    </div>
                </div>
            </div>

            <!-- Primary Metric Cards -->
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4 sm:gap-6">
                <!-- Card 1: Estimated Cost per Serving -->
                <div class="bg-slate-900 p-5 sm:p-6 rounded-2xl border border-slate-800 shadow-sm flex flex-col justify-between hover:shadow-md transition-all relative overflow-hidden group">
                    <div class="absolute right-0 top-0 w-24 h-24 bg-amber-950/20 rounded-bl-full -z-10 transition-transform group-hover:scale-110 duration-300"></div>
                    <div class="flex justify-between items-start">
                        <div class="p-2 bg-amber-950 text-amber-300 rounded-lg border border-amber-800/50">
                            <i data-lucide="coins" class="w-5 h-5"></i>
                        </div>
                        <span class="text-xs font-semibold text-amber-400 bg-amber-950/50 px-2 py-0.5 rounded-full border border-amber-900">Unit Cost</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-xs font-semibold text-slate-400 uppercase tracking-wider">Cost / Serving</p>
                        <h3 class="text-2xl sm:text-3xl font-extrabold text-slate-100 mt-1"><span id="metric-cost-per-serving">0.00</span> <span class="text-sm font-medium text-slate-500">฿</span></h3>
                    </div>
                </div>

                <!-- Card 2: Suggested Selling Price (With enhanced tap buttons) -->
                <div class="bg-slate-900 p-5 sm:p-6 rounded-2xl border border-slate-800 shadow-sm flex flex-col justify-between hover:shadow-md transition-all relative overflow-hidden group">
                    <div class="absolute right-0 top-0 w-24 h-24 bg-orange-950/20 rounded-bl-full -z-10 transition-transform group-hover:scale-110 duration-300"></div>
                    <div class="flex justify-between items-start">
                        <div class="p-2 bg-orange-950 text-orange-300 rounded-lg border border-orange-800/50">
                            <i data-lucide="tag" class="w-5 h-5"></i>
                        </div>
                        <span class="text-xs font-semibold text-orange-400 bg-orange-950/50 px-2 py-0.5 rounded-full border border-orange-900">Price</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-xs font-semibold text-slate-400 uppercase tracking-wider">Selling Price</p>
                        <div class="flex items-center space-x-1 mt-1">
                            <button onclick="adjustPriceValue(-5)" class="bg-slate-950 hover:bg-slate-800 text-slate-300 w-7 h-7 rounded-md font-bold flex items-center justify-center transition-all border border-slate-800 text-sm">-</button>
                            <div class="flex items-baseline justify-center">
                                <input type="number" id="metric-selling-price-input" value="45" min="1" oninput="updatePricingFromMetric(this.value)"
                                    class="w-16 text-center text-xl sm:text-2xl font-extrabold text-slate-100 bg-slate-950 border border-slate-800 focus:border-brand-500 focus:outline-none rounded-lg py-0.5 px-1">
                                <span class="text-xs font-medium text-slate-500 ml-1">฿</span>
                            </div>
                            <button onclick="adjustPriceValue(5)" class="bg-slate-950 hover:bg-slate-800 text-slate-300 w-7 h-7 rounded-md font-bold flex items-center justify-center transition-all border border-slate-800 text-sm">+</button>
                        </div>
                    </div>
                </div>

                <!-- Card 3: Profit per Serving & Margin -->
                <div class="bg-slate-900 p-5 sm:p-6 rounded-2xl border border-slate-800 shadow-sm flex flex-col justify-between hover:shadow-md transition-all relative overflow-hidden group">
                    <div class="absolute right-0 top-0 w-24 h-24 bg-emerald-950/20 rounded-bl-full -z-10 transition-transform group-hover:scale-110 duration-300"></div>
                    <div class="flex justify-between items-start">
                        <div class="p-2 bg-emerald-950 text-emerald-300 rounded-lg border border-emerald-800/50">
                            <i data-lucide="trending-up" class="w-5 h-5"></i>
                        </div>
                        <span id="metric-margin" class="text-xs font-bold text-emerald-300 bg-emerald-950/50 px-2.5 py-0.5 rounded-full border border-emerald-900">0% Margin</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-xs font-semibold text-slate-400 uppercase tracking-wider">Profit / Serving</p>
                        <h3 class="text-2xl sm:text-3xl font-extrabold text-emerald-400 mt-1"><span id="metric-profit-per-serving">0.00</span> <span class="text-sm font-medium text-emerald-500">฿</span></h3>
                    </div>
                </div>

                <!-- Card 4: Break-Even Quantity -->
                <div class="bg-slate-900 p-5 sm:p-6 rounded-2xl border border-slate-800 shadow-sm flex flex-col justify-between hover:shadow-md transition-all relative overflow-hidden group">
                    <div class="absolute right-0 top-0 w-24 h-24 bg-blue-950/20 rounded-bl-full -z-10 transition-transform group-hover:scale-110 duration-300"></div>
                    <div class="flex justify-between items-start">
                        <div class="p-2 bg-blue-100 text-blue-300 rounded-lg border border-blue-800/50">
                            <i data-lucide="scale" class="w-5 h-5"></i>
                        </div>
                        <span class="text-xs font-semibold text-blue-400 bg-blue-950/50 px-2 py-0.5 rounded-full border border-blue-900">Safety</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-xs font-semibold text-slate-400 uppercase tracking-wider">Break-Even Point</p>
                        <h3 class="text-2xl sm:text-3xl font-extrabold text-slate-100 mt-1"><span id="metric-break-even">0</span> <span class="text-xs font-semibold text-slate-400">units</span></h3>
                    </div>
                </div>
            </div>

            <!-- Total Event Projections Grid -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                <!-- Forecast Summary -->
                <div class="bg-gradient-to-br from-slate-900 to-slate-800 text-white rounded-2xl p-6 border border-slate-800 shadow-xl flex flex-col justify-between relative overflow-hidden lg:col-span-1">
                    <div class="absolute right-0 bottom-0 opacity-5 pointer-events-none transform translate-y-4 translate-x-4">
                        <i data-lucide="bar-chart-3" class="w-40 h-40"></i>
                    </div>
                    <div class="space-y-4">
                        <div class="flex items-center space-x-2">
                            <span class="flex h-2.5 w-2.5 rounded-full bg-emerald-400 animate-pulse"></span>
                            <span class="text-xs font-bold uppercase tracking-widest text-slate-400">Simulation Projections</span>
                        </div>
                        <div>
                            <p class="text-sm text-slate-400">Estimated Total Revenue</p>
                            <h4 class="text-4xl font-extrabold text-white mt-1"><span id="metric-total-revenue">0.00</span> <span class="text-xl font-normal text-slate-500">฿</span></h4>
                        </div>
                        <hr class="border-slate-800">
                        <div>
                            <p class="text-sm text-slate-400">Estimated Net Profit</p>
                            <h4 class="text-4xl font-extrabold text-emerald-400 mt-1"><span id="metric-total-profit">0.00</span> <span class="text-xl font-normal text-emerald-500">฿</span></h4>
                        </div>
                    </div>
                    <div class="mt-6 pt-4 border-t border-slate-800/50 flex justify-between text-xs text-slate-400">
                        <span>Planned Servings: <strong class="text-white" id="projection-servings-count">150</strong></span>
                        <span>Total Initial Outlay: <strong class="text-white" id="projection-total-outlay">0.00 ฿</strong></span>
                    </div>
                </div>

                <!-- Quick Strategy Advice Card -->
                <div class="bg-gradient-to-br from-brand-900 to-amber-900 text-white rounded-2xl p-6 border border-brand-800 shadow-xl flex flex-col justify-between relative overflow-hidden lg:col-span-2">
                    <div class="absolute right-0 bottom-0 opacity-10 pointer-events-none transform translate-y-10 translate-x-10">
                        <i data-lucide="award" class="w-48 h-48"></i>
                    </div>
                    <div>
                        <div class="flex items-center gap-2 mb-3">
                            <span class="bg-white/10 text-brand-200 text-xs font-bold px-2.5 py-1 rounded-full uppercase tracking-wider border border-white/5">Strategy Recommendation</span>
                            <span id="target-health-badge" class="bg-emerald-500/20 text-emerald-300 text-xs font-bold px-2.5 py-1 rounded-full border border-emerald-500/30">Optimized</span>
                        </div>
                        <h3 class="text-xl sm:text-2xl font-bold">100-Minute Speed Strategy</h3>
                        <p class="text-brand-100 text-sm mt-2 max-w-xl leading-relaxed">
                            With 700 potential attendees, your primary bottleneck is serving speed. Since <strong>81.1% of surveyed customers hate waiting</strong>, you should pre-portion chip bags, set up a self-serve cheese dispenser, and pre-prep premium bacon bits. Keep your price near <strong>45 baht</strong> to maximize profit margin.
                        </p>
                    </div>
                    <div class="mt-6 grid grid-cols-2 gap-4 bg-black/35 p-4 rounded-xl backdrop-blur-sm border border-white/5">
                        <div>
                            <p class="text-xs text-brand-200 uppercase">Target Speed per Order</p>
                            <p class="text-lg font-bold text-white">Under 45 Seconds</p>
                        </div>
                        <div>
                            <p class="text-xs text-brand-200 uppercase">Hourly Run-rate</p>
                            <p class="text-lg font-bold text-white">~90 servings / hr</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 2: Survey Results Insights -->
        <section id="survey" class="space-y-6 scroll-mt-20 print-card">
            <div class="border-b border-slate-800 pb-5">
                <h2 class="text-2xl font-bold text-slate-100">Pre-Event Customer Survey Insights</h2>
                <p class="text-slate-400 mt-1">Summary and analysis of responses gathered from 55 target participants to guide purchasing and operations.</p>
            </div>

            <!-- Executive Summary Panel -->
            <div class="bg-amber-950/20 border border-amber-900/40 rounded-2xl p-5 sm:p-6 space-y-4">
                <div class="flex items-center gap-2 text-amber-300">
                    <i data-lucide="sparkles" class="w-5 h-5 text-amber-400"></i>
                    <h3 class="font-bold text-lg">Executive Summary of Market Intelligence</h3>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                    <div class="bg-slate-900/80 p-4 rounded-xl border border-slate-800 flex items-start gap-3">
                        <div class="p-1.5 bg-amber-950 text-amber-300 rounded-lg mt-0.5 border border-amber-900/50"><i data-lucide="shopping-bag" class="w-4 h-4"></i></div>
                        <div>
                            <h4 class="font-bold text-slate-200 text-sm">Regular Purchasing Habit</h4>
                            <p class="text-xs text-slate-400 mt-1">71% of respondents buy snacks at every or most school selling events. Strong core market.</p>
                        </div>
                    </div>
                    <div class="bg-slate-900/80 p-4 rounded-xl border border-slate-800 flex items-start gap-3">
                        <div class="p-1.5 bg-amber-950 text-amber-300 rounded-lg mt-0.5 border border-amber-900/50"><i data-lucide="wallet" class="w-4 h-4"></i></div>
                        <div>
                            <h4 class="font-bold text-slate-200 text-sm">Excellent Spending Tolerance</h4>
                            <p class="text-xs text-slate-400 mt-1">Over 50% are willing to pay 35 baht or higher. Pricing at 45 baht is strongly viable for nachos.</p>
                        </div>
                    </div>
                    <div class="bg-slate-900/80 p-4 rounded-xl border border-slate-800 flex items-start gap-3">
                        <div class="p-1.5 bg-red-950 text-red-300 rounded-lg mt-0.5 border border-red-900/50"><i data-lucide="alert-triangle" class="w-4 h-4"></i></div>
                        <div>
                            <h4 class="font-bold text-slate-200 text-sm">Waiting Time is Key Painpoint</h4>
                            <p class="text-xs text-slate-400 mt-1">81% named "long waiting times" their main dislike. Optimized team workflow is mandatory.</p>
                        </div>
                    </div>
                    <div class="bg-slate-900/80 p-4 rounded-xl border border-slate-800 flex items-start gap-3">
                        <div class="p-1.5 bg-amber-950 text-amber-300 rounded-lg mt-0.5 border border-amber-900/50"><i data-lucide="heart" class="w-4 h-4"></i></div>
                        <div>
                            <h4 class="font-bold text-slate-200 text-sm">High Popularity for Cheese</h4>
                            <p class="text-xs text-slate-400 mt-1">Cheese sauce (72.2%), bacon bits (57.4%), and extra cheese (48.1%) are the absolute favorite toppings.</p>
                        </div>
                    </div>
                    <div class="bg-slate-900/80 p-4 rounded-xl border border-slate-800 flex items-start gap-3">
                        <div class="p-1.5 bg-amber-950 text-amber-300 rounded-lg mt-0.5 border border-amber-900/50"><i data-lucide="sparkles" class="w-4 h-4"></i></div>
                        <div>
                            <h4 class="font-bold text-slate-200 text-sm">Willingness to Pay for Premium</h4>
                            <p class="text-xs text-slate-400 mt-1">84% will pay or consider paying extra for extra toppings. Keep base simple, charge for extras!</p>
                        </div>
                    </div>
                    <div class="bg-slate-900/80 p-4 rounded-xl border border-slate-800 flex items-start gap-3">
                        <div class="p-1.5 bg-amber-950 text-amber-300 rounded-lg mt-0.5 border border-amber-900/50"><i data-lucide="activity" class="w-4 h-4"></i></div>
                        <div>
                            <h4 class="font-bold text-slate-200 text-sm">Taste, Price & Speed First</h4>
                            <p class="text-xs text-slate-400 mt-1">These are the critical decision factors. Presentation and size are auxiliary factors.</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Charts Grid (Tabs) -->
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-sm space-y-6">
                <div class="flex flex-wrap border-b border-slate-800 gap-2 no-print">
                    <button onclick="setActiveTab('charts-demographics')" class="chart-tab px-4 py-2 text-sm font-semibold border-b-2 border-brand-400 text-brand-400 transition-all" id="tab-charts-demographics">Demographics & Frequency</button>
                    <button onclick="setActiveTab('charts-finance')" class="chart-tab px-4 py-2 text-sm font-semibold border-b-2 border-transparent text-slate-400 hover:text-slate-200 transition-all" id="tab-charts-finance">Preferences & Finance</button>
                    <button onclick="setActiveTab('charts-toppings')" class="chart-tab px-4 py-2 text-sm font-semibold border-b-2 border-transparent text-slate-400 hover:text-slate-200 transition-all" id="tab-charts-toppings">Toppings & Bottlenecks</button>
                </div>

                <!-- Tab content blocks -->
                <div id="charts-demographics" class="chart-panel grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="flex flex-col items-center justify-between p-4 border border-slate-800 rounded-xl bg-slate-950/40">
                        <h4 class="font-bold text-slate-300 text-center mb-4 text-sm sm:text-base">Respondents by Grade Level</h4>
                        <div class="w-full max-w-[280px] h-[280px] relative">
                            <canvas id="chartDemographics"></canvas>
                        </div>
                        <p class="text-xs text-slate-400 text-center mt-4">Majority are G7-G9 students (40%) and G4-G6 (36.4%). Target messaging accordingly!</p>
                    </div>
                    <div class="flex flex-col items-center justify-between p-4 border border-slate-800 rounded-xl bg-slate-950/40">
                        <h4 class="font-bold text-slate-300 text-center mb-4 text-sm sm:text-base">Buying Frequency at Events</h4>
                        <div class="w-full max-w-[280px] h-[280px] relative">
                            <canvas id="chartFrequency"></canvas>
                        </div>
                        <p class="text-xs text-slate-400 text-center mt-4">71% regular purchasers implies highly predictable, enthusiastic school demand.</p>
                    </div>
                </div>

                <div id="charts-finance" class="chart-panel hidden grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="flex flex-col items-center justify-between p-4 border border-slate-800 rounded-xl bg-slate-950/40">
                        <h4 class="font-bold text-slate-300 text-center mb-4 text-sm sm:text-base">Willingness to Spend on Snacks</h4>
                        <div class="w-full max-w-[280px] h-[280px] relative">
                            <canvas id="chartSpendLimit"></canvas>
                        </div>
                        <p class="text-xs text-slate-400 text-center mt-4">51% will spend 35฿ or higher. 45฿ is verified sweet spot for premium offerings.</p>
                    </div>
                    <div class="flex flex-col items-center justify-between p-4 border border-slate-800 rounded-xl bg-slate-950/40">
                        <h4 class="font-bold text-slate-300 text-center mb-4 text-sm sm:text-base">Willingness to Pay for Premium Extras</h4>
                        <div class="w-full max-w-[280px] h-[280px] relative">
                            <canvas id="chartPremiumWillingness"></canvas>
                        </div>
                        <p class="text-xs text-slate-400 text-center mt-4">84% will or may pay extra. Create premium toppings menu options (5-10฿ add-ons).</p>
                    </div>
                </div>

                <div id="charts-toppings" class="chart-panel hidden grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="flex flex-col items-center justify-between p-4 border border-slate-800 rounded-xl bg-slate-950/40">
                        <h4 class="font-bold text-slate-300 text-center mb-4 text-sm sm:text-base">Top 10 Preferred Nacho Toppings</h4>
                        <div class="w-full h-[280px] relative">
                            <canvas id="chartToppings"></canvas>
                        </div>
                        <p class="text-xs text-slate-400 text-center mt-4">Cheese sauce and bacon bits are dominant winners. Carry abundant inventory of these.</p>
                    </div>
                    <div class="flex flex-col items-center justify-between p-4 border border-slate-800 rounded-xl bg-slate-950/40">
                        <h4 class="font-bold text-slate-300 text-center mb-4 text-sm sm:text-base">Biggest Event Dislikes (Bottlenecks)</h4>
                        <div class="w-full h-[280px] relative">
                            <canvas id="chartDislikes"></canvas>
                        </div>
                        <p class="text-xs text-slate-400 text-center mt-4">81.1% complain of long waiting times. Design quick assembly lines immediately.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 3: Cost Calculators Grid -->
        <section id="calculators" class="grid grid-cols-1 xl:grid-cols-3 gap-6 scroll-mt-20 print-card">
            
            <!-- Left 2 Cols: Ingredient Table and Packaging Table -->
            <div class="xl:col-span-2 space-y-6">
                <!-- Ingredients Cost Table Card (With enhanced tap inputs) -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-sm space-y-4">
                    <div class="flex justify-between items-center">
                        <div class="flex items-center space-x-2">
                            <div class="p-1.5 bg-amber-950 text-amber-300 rounded-lg border border-amber-900/50"><i data-lucide="salad" class="w-5 h-5"></i></div>
                            <h3 class="font-bold text-lg text-slate-100">Interactive Ingredient Cost</h3>
                        </div>
                        <button onclick="addIngredientRow()" class="bg-slate-800 hover:bg-slate-750 text-slate-100 text-xs px-3 py-1.5 rounded-lg font-bold flex items-center gap-1.5 transition-all no-print border border-slate-700">
                            <i data-lucide="plus" class="w-3.5 h-3.5 text-brand-400"></i> Add Ingredient
                        </button>
                    </div>
                    <p class="text-xs text-slate-400">All fields are interactive and live-update. Edit purchase values and portion sizes anytime.</p>

                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse text-sm min-w-[650px]" id="ingredients-table">
                            <thead>
                                <tr class="bg-slate-950 border-y border-slate-850 text-slate-300 font-semibold">
                                    <th class="py-3 px-3">Ingredient Name</th>
                                    <th class="py-3 px-3 w-32">Buy Qty</th>
                                    <th class="py-3 px-3 w-24">Unit</th>
                                    <th class="py-3 px-3 w-32">Buy Price (฿)</th>
                                    <th class="py-3 px-3 w-32">Portion / Serve</th>
                                    <th class="py-3 px-3 text-right">Cost / Serve</th>
                                    <th class="py-3 px-3 text-right no-print w-16">Action</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-slate-850" id="ingredients-tbody">
                                <!-- Populated dynamically by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                    <div class="flex justify-between items-center pt-3 border-t border-slate-800 text-slate-300 font-semibold">
                        <span>Total Ingredients Cost:</span>
                        <span class="text-emerald-400 text-lg"><span id="total-ingredients-serving-cost">0.00</span> ฿ / serving</span>
                    </div>
                </div>

                <!-- Packaging Cost Table Card -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-sm space-y-4">
                    <div class="flex justify-between items-center">
                        <div class="flex items-center space-x-2">
                            <div class="p-1.5 bg-amber-950 text-amber-300 rounded-lg border border-amber-900/50"><i data-lucide="package" class="w-5 h-5"></i></div>
                            <h3 class="font-bold text-lg text-slate-100">Packaging Materials Cost</h3>
                        </div>
                        <button onclick="addPackagingRow()" class="bg-slate-800 hover:bg-slate-750 text-slate-100 text-xs px-3 py-1.5 rounded-lg font-bold flex items-center gap-1.5 transition-all no-print border border-slate-700">
                            <i data-lucide="plus" class="w-3.5 h-3.5 text-brand-400"></i> Add Packaging
                        </button>
                    </div>
                    <p class="text-xs text-slate-400">Essential non-food materials per taco serving (chip bag, fork, napkin, etc.).</p>

                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse text-sm min-w-[650px]" id="packaging-table">
                            <thead>
                                <tr class="bg-slate-950 border-y border-slate-850 text-slate-300 font-semibold">
                                    <th class="py-3 px-3">Item Name</th>
                                    <th class="py-3 px-3 w-32">Buy Qty</th>
                                    <th class="py-3 px-3 w-24">Unit</th>
                                    <th class="py-3 px-3 w-32">Buy Price (฿)</th>
                                    <th class="py-3 px-3 w-32">Portion / Serve</th>
                                    <th class="py-3 px-3 text-right">Cost / Serve</th>
                                    <th class="py-3 px-3 text-right no-print w-16">Action</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-slate-850" id="packaging-tbody">
                                <!-- Populated dynamically by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                    <div class="flex justify-between items-center pt-3 border-t border-slate-800 text-slate-300 font-semibold">
                        <span>Total Packaging Cost:</span>
                        <span class="text-emerald-400 text-lg"><span id="total-packaging-serving-cost">0.00</span> ฿ / serving</span>
                    </div>
                </div>
            </div>

            <!-- Right Col: Financial Modeler Summary -->
            <div class="space-y-6">
                <!-- Interactive Unit Cost Stack -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-sm space-y-6 relative overflow-hidden">
                    <div class="absolute right-0 top-0 w-2 h-full bg-brand-500"></div>
                    <div>
                        <h3 class="font-bold text-lg text-slate-100">Consolidated Product Cost</h3>
                        <p class="text-xs text-slate-400 mt-1">Combination of recipe ingredients and packaging materials.</p>
                    </div>

                    <div class="space-y-4">
                        <div class="flex justify-between items-center text-sm p-3 bg-slate-950/55 rounded-xl border border-slate-850">
                            <span class="text-slate-400">Recipe Ingredients (Unit)</span>
                            <span class="font-bold text-slate-200"><span id="summary-ing-cost">0.00</span> ฿</span>
                        </div>
                        <div class="flex justify-between items-center text-sm p-3 bg-slate-950/55 rounded-xl border border-slate-850">
                            <span class="text-slate-400">Packaging Materials (Unit)</span>
                            <span class="font-bold text-slate-200"><span id="summary-pkg-cost">0.00</span> ฿</span>
                        </div>
                        <div class="flex justify-between items-center text-base p-4 bg-emerald-950/40 text-emerald-300 rounded-xl border border-emerald-900/50">
                            <span class="font-bold">Total Cost / Serving</span>
                            <span class="text-xl font-black text-emerald-400"><span id="summary-total-serving-cost">0.00</span> ฿</span>
                        </div>
                    </div>
                </div>

                <!-- Custom Financial Modeler Box -->
                <div class="bg-slate-900 border border-slate-800 text-white rounded-2xl p-6 shadow-xl space-y-5">
                    <div>
                        <span class="bg-brand-500/10 text-brand-400 text-[10px] font-bold px-2 py-0.5 rounded-full uppercase tracking-widest border border-brand-900/40">Pricing & Volume Configurator</span>
                        <h3 class="font-bold text-lg text-slate-100 mt-2">Projection Modeler</h3>
                    </div>

                    <div class="space-y-4">
                        <!-- Metric Sliders -->
                        <div class="space-y-1">
                            <div class="flex justify-between text-xs text-slate-400">
                                <span>Selling Price / Unit</span>
                                <span class="font-bold text-brand-400" id="slider-price-label">45 ฿</span>
                            </div>
                            <input type="range" id="price-range" min="15" max="80" value="45" oninput="syncInputs('price', this.value)" class="w-full h-2 accent-brand-500 bg-slate-800 rounded-lg appearance-none cursor-pointer">
                        </div>

                        <div class="space-y-1">
                            <div class="flex justify-between text-xs text-slate-400">
                                <span>Target Event Sales (Qty)</span>
                                <span class="font-bold text-brand-400" id="slider-volume-label">150 servings</span>
                            </div>
                            <input type="range" id="volume-range" min="20" max="400" value="150" step="10" oninput="syncInputs('volume', this.value)" class="w-full h-2 accent-brand-500 bg-slate-800 rounded-lg appearance-none cursor-pointer">
                        </div>
                    </div>

                    <div class="border-t border-slate-800 pt-4 space-y-3.5">
                        <div class="flex justify-between text-sm">
                            <span class="text-slate-400">Simulated Revenue:</span>
                            <span class="font-bold text-slate-200"><span id="calc-projected-revenue">0.00</span> ฿</span>
                        </div>
                        <div class="flex justify-between text-sm">
                            <span class="text-slate-400">Simulated COGS:</span>
                            <span class="font-bold text-slate-400"><span id="calc-projected-cogs">0.00</span> ฿</span>
                        </div>
                        <div class="flex justify-between text-sm">
                            <span class="text-slate-400">Profit Margin:</span>
                            <span class="font-bold text-emerald-400"><span id="calc-projected-margin">0.00</span>%</span>
                        </div>
                        <hr class="border-slate-800/60">
                        <div class="flex justify-between text-base">
                            <span class="text-emerald-300 font-bold">Simulated Profit:</span>
                            <span class="text-emerald-400 text-xl font-extrabold"><span id="calc-projected-profit">0.00</span> ฿</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 4: Interactive Product Builder -->
        <section id="builder" class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-sm space-y-6 scroll-mt-20 print-card">
            <div>
                <h3 class="font-bold text-xl text-slate-100">John Pork Tacos Menu Customization Simulation</h3>
                <p class="text-slate-400 mt-1">Simulate custom walking taco / nacho recipes to see immediate popularity estimations (based on target market surveys) and raw assembly cost forecasts.</p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
                <!-- Checklist column -->
                <div class="lg:col-span-2 space-y-4">
                    <h4 class="font-bold text-slate-300 border-b border-slate-850 pb-2 text-sm">Available Taco Toppings Checkbox</h4>
                    
                    <!-- Predefined Toppings with Popularity and default costs -->
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-3" id="builder-toppings-container">
                        <!-- Checked by logic below -->
                    </div>
                </div>

                <!-- Simulation results box -->
                <div class="bg-slate-950/50 border border-slate-800 rounded-xl p-5 flex flex-col justify-between">
                    <div class="space-y-4">
                        <div class="flex justify-between items-center">
                            <span class="text-xs font-bold text-slate-400 uppercase tracking-wider">Custom Combo KPI</span>
                            <span class="bg-amber-950 text-amber-300 text-[10px] font-bold px-2 py-0.5 rounded-full border border-amber-900/55">Interactive</span>
                        </div>

                        <div>
                            <p class="text-xs text-slate-400">Estimated Serving Cost</p>
                            <h4 class="text-2xl font-black text-slate-100 mt-0.5"><span id="builder-calc-cost">0.00</span> <span class="text-sm font-semibold text-slate-500">฿</span></h4>
                        </div>

                        <div>
                            <p class="text-xs text-slate-400">Calculated Consumer Demand Weight (Survey Popularity)</p>
                            <div class="flex items-center gap-2 mt-1">
                                <div class="flex-grow bg-slate-800 rounded-full h-3.5 overflow-hidden border border-slate-700/50">
                                    <div id="builder-popularity-bar" class="bg-gradient-to-r from-amber-500 to-orange-500 h-full transition-all duration-500" style="width: 0%"></div>
                                </div>
                                <span class="text-sm font-extrabold text-brand-400 min-w-[32px] text-right" id="builder-popularity-label">0%</span>
                            </div>
                        </div>

                        <div>
                            <p class="text-xs text-slate-400">Recommended Add-on Price</p>
                            <h4 class="text-2xl font-black text-emerald-400 mt-0.5"><span id="builder-calc-selling-price">45.00</span> <span class="text-sm font-semibold text-emerald-500">฿</span></h4>
                        </div>
                    </div>

                    <div class="mt-6 pt-4 border-t border-slate-800 space-y-3">
                        <p class="text-[11px] text-slate-400 leading-relaxed italic">
                            💡 *Note: The builder maps recipes dynamically against 55 customer survey trends to give a mathematical target compatibility index.
                        </p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 5: Dynamic Inventory Planner -->
        <section id="inventory" class="bg-slate-900 border border-slate-800 rounded-2xl p-6 shadow-sm space-y-6 scroll-mt-20 print-card">
            <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4">
                <div>
                    <h3 class="font-bold text-xl text-slate-100">Dynamic Multi-Unit Inventory Purchase Planner</h3>
                    <p class="text-slate-400 mt-1">Shows complete physical volumes of items to purchase based on simulated targeted servings.</p>
                </div>
                <div class="flex items-center space-x-2 bg-slate-950 p-2 rounded-xl border border-slate-850">
                    <span class="text-xs font-bold text-slate-400 px-2 uppercase tracking-wide">Forecast Servings:</span>
                    <div class="flex items-center space-x-1">
                        <button onclick="adjustGlobalServings(-10)" class="bg-slate-800 hover:bg-slate-700 text-slate-200 w-8 h-8 rounded-lg font-black flex items-center justify-center transition-all border border-slate-700">-</button>
                        <input type="number" id="inventory-servings-qty" value="150" min="1" step="10" oninput="syncServings(this.value)"
                            class="w-20 bg-slate-900 border border-slate-800 rounded-lg py-1 px-1.5 text-center font-bold text-slate-100 focus:ring-1 focus:ring-brand-500 focus:outline-none text-sm">
                        <button onclick="adjustGlobalServings(10)" class="bg-slate-800 hover:bg-slate-700 text-slate-200 w-8 h-8 rounded-lg font-black flex items-center justify-center transition-all border border-slate-700">+</button>
                    </div>
                </div>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                <!-- Recipe Grocery Requirements -->
                <div class="space-y-4">
                    <div class="flex items-center space-x-2 border-b border-slate-850 pb-2">
                        <div class="p-1 bg-amber-950 text-amber-300 rounded-lg border border-amber-900/50"><i data-lucide="shopping-cart" class="w-4 h-4"></i></div>
                        <h4 class="font-bold text-slate-300 text-sm">Ingredient Bulk Grocery Requirements</h4>
                    </div>
                    
                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse text-xs sm:text-sm">
                            <thead>
                                <tr class="bg-slate-950 border-b border-slate-850 text-slate-400 font-semibold">
                                    <th class="py-2 px-3">Item Name</th>
                                    <th class="py-2 px-3 text-right">Required Quantity</th>
                                    <th class="py-2 px-3 text-right">Raw Store Package Equivalents</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-slate-850/60" id="inventory-ingredients-tbody">
                                <!-- Populated dynamically by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Packaging Grocery Requirements -->
                <div class="space-y-4">
                    <div class="flex items-center space-x-2 border-b border-slate-850 pb-2">
                        <div class="p-1 bg-amber-950 text-amber-300 rounded-lg border border-amber-900/50"><i data-lucide="package-check" class="w-4 h-4"></i></div>
                        <h4 class="font-bold text-slate-300 text-sm">Packaging Materials Supply Requirements</h4>
                    </div>
                    
                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse text-xs sm:text-sm">
                            <thead>
                                <tr class="bg-slate-950 border-b border-slate-850 text-slate-400 font-semibold">
                                    <th class="py-2 px-3">Material Name</th>
                                    <th class="py-2 px-3 text-right">Required Quantity</th>
                                    <th class="py-2 px-3 text-right">Raw Store Package Equivalents</th>
                                </tr>
                            </thead>
                            <tbody class="divide-y divide-slate-850/60" id="inventory-packaging-tbody">
                                <!-- Populated dynamically by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            
            <div class="border-t border-slate-850 pt-4 flex flex-wrap gap-3 justify-end no-print">
                <button onclick="exportShoppingList()" class="bg-slate-800 hover:bg-slate-750 text-slate-200 border border-slate-700 font-bold px-4 py-2 rounded-xl text-xs flex items-center gap-2 transition-all">
                    <i data-lucide="file-text" class="w-4 h-4 text-slate-400"></i>
                    <span>Export Shopping List (TXT)</span>
                </button>
            </div>
        </section>

        <!-- Section 6: Actionable Recommendations -->
        <section class="space-y-6 print-card">
            <div class="border-b border-slate-800 pb-5">
                <h3 class="font-bold text-2xl text-slate-100">Actionable Data-Driven Recommendations</h3>
                <p class="text-slate-400 mt-1">Calculated strategy suggestions matching your survey findings with Grade 9 project constraints.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                <!-- Rec 1: Price -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 hover:shadow-md transition-all space-y-3 relative overflow-hidden">
                    <div class="absolute right-0 top-0 w-12 h-12 bg-amber-950/35 rounded-bl-full -z-10"></div>
                    <div class="p-2 bg-amber-950 text-amber-300 rounded-lg w-fit border border-amber-900/50"><i data-lucide="tags" class="w-5 h-5"></i></div>
                    <h4 class="font-bold text-slate-200 text-base">Perfect Selling Price</h4>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        Set the base price to <strong>40-45 Baht</strong>. Survey data shows 51% are willing to spend over 35 Baht, with 30.9% comfortable spending 45+ Baht. Excellent room for high margin.
                    </p>
                </div>

                <!-- Rec 2: Toppings -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 hover:shadow-md transition-all space-y-3 relative overflow-hidden">
                    <div class="absolute right-0 top-0 w-12 h-12 bg-amber-950/35 rounded-bl-full -z-10"></div>
                    <div class="p-2 bg-amber-950 text-amber-300 rounded-lg w-fit border border-amber-900/50"><i data-lucide="chef-hat" class="w-5 h-5"></i></div>
                    <h4 class="font-bold text-slate-200 text-base">High-Margin Upgrades</h4>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        Prepare cheese sauce and bacon bits as standard toppings. Since 84% will pay for extra premium toppings, sell "Double Bacon/Extra Cheese" as a premium add-on for <strong>+10 Baht</strong>.
                    </p>
                </div>

                <!-- Rec 3: Spice Level -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 hover:shadow-md transition-all space-y-3 relative overflow-hidden">
                    <div class="absolute right-0 top-0 w-12 h-12 bg-amber-950/35 rounded-bl-full -z-10"></div>
                    <div class="p-2 bg-amber-950 text-amber-300 rounded-lg w-fit border border-amber-900/50"><i data-lucide="flame" class="w-5 h-5"></i></div>
                    <h4 class="font-bold text-slate-200 text-base">Dual Spice Tiering</h4>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        67% enjoy spicy food, while 33% prefer non-spicy. Provide a sweet non-spicy base cheese, and offer a separate jalapeño/hot sauce squeezer at checkout to let users control hotness.
                    </p>
                </div>

                <!-- Rec 4: Operations speed -->
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 hover:shadow-md transition-all space-y-3 relative overflow-hidden">
                    <div class="absolute right-0 top-0 w-12 h-12 bg-amber-950/35 rounded-bl-full -z-10"></div>
                    <div class="p-2 bg-amber-950 text-amber-300 rounded-lg w-fit border border-amber-900/50"><i data-lucide="clock" class="w-5 h-5"></i></div>
                    <h4 class="font-bold text-slate-200 text-base">Assembly Setup</h4>
                    <p class="text-xs text-slate-400 leading-relaxed">
                        81% complain of long waiting times. Assign student 1 to open bag/crunch chips, student 2 to pour warm cheese/meat, and student 3 to place premium extras. Assemble in under 45 seconds.
                    </p>
                </div>
            </div>
        </section>
    </main>

    <!-- Footer Area -->
    <footer class="bg-slate-950 text-slate-500 py-10 mt-16 border-t border-slate-900 no-print">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center space-y-4">
            <div class="flex justify-center items-center space-x-2">
                <div class="p-1 bg-brand-600 text-white rounded-lg">
                    <i data-lucide="concourse" class="w-4 h-4 rotate-45"></i>
                </div>
                <span class="font-bold text-slate-300 text-base">John Pork Tacos Business Suite</span>
            </div>
            <p class="text-xs max-w-md mx-auto text-slate-500">
                Created specifically for the Grade 9 Entrepreneurship Challenge. All model forecasting equations reflect verified student survey data.
            </p>
            <div class="text-[10px] text-slate-600">
                &copy; 2026 John Pork Tacos Team. Built with Premium UX Dark Defaults.
            </div>
        </div>
    </footer>

    <!-- Core Business Javascript Logic & State -->
    <script>
        // Initial mock database of default ingredients & packaging materials
        let ingredients = [
            { id: 1, name: 'Tostitos / Tortilla Chips Bag', buyQty: 10, unit: 'bags', price: 450, servingAmount: 0.1 }, // 1 bag makes 10 servings
            { id: 2, name: 'Squeeze Cheese Sauce', buyQty: 1000, unit: 'g', price: 180, servingAmount: 35 },
            { id: 3, name: 'Bacon Pieces / Bits', buyQty: 500, unit: 'g', price: 290, servingAmount: 15 },
            { id: 4, name: 'Mexican Ground Pork Seasoned', buyQty: 1000, unit: 'g', price: 240, servingAmount: 40 },
            { id: 5, name: 'Sliced Jalapeños Bowl', buyQty: 300, unit: 'g', price: 95, servingAmount: 10 },
            { id: 6, name: 'Sour Cream Dressing', buyQty: 450, unit: 'ml', price: 160, servingAmount: 15 }
        ];

        let packaging = [
            { id: 1, name: 'Custom Serving Craft Box', buyQty: 100, unit: 'pcs', price: 120, servingAmount: 1 },
            { id: 2, name: 'Disposable Wooden Sporks', buyQty: 100, unit: 'pcs', price: 45, servingAmount: 1 },
            { id: 3, name: 'Paper Napkins Pack', buyQty: 200, unit: 'pcs', price: 30, servingAmount: 1.5 },
            { id: 4, name: 'Food Prep Disposable Gloves', buyQty: 100, unit: 'pcs', price: 35, servingAmount: 0.2 } // 1 pair per 10 servings simulated roughly
        ];

        // Complete survey topping database matching exact question percentages & average serving costs 
        const surveyToppings = [
            { name: 'Cheese Sauce', percentage: 72.2, color: 'bg-amber-950/40 border-amber-800 text-amber-200', costEstimate: 6.30 },
            { name: 'Bacon Bits', percentage: 57.4, color: 'bg-red-950/40 border-red-900 text-red-200', costEstimate: 8.70 },
            { name: 'Extra Cheese', percentage: 48.1, color: 'bg-yellow-950/40 border-yellow-800 text-yellow-200', costEstimate: 4.50 },
            { name: 'Sour Cream', percentage: 44.4, color: 'bg-slate-900 border-slate-750 text-slate-200', costEstimate: 5.33 },
            { name: 'Ground Pork', percentage: 40.7, color: 'bg-orange-950/40 border-orange-850 text-orange-200', costEstimate: 9.60 },
            { name: 'Nacho Cheese Cubes', percentage: 35.2, color: 'bg-amber-900/30 border-amber-700 text-amber-100', costEstimate: 5.00 },
            { name: 'Hot Chili Sauce', percentage: 33.3, color: 'bg-red-950/50 border-red-800/80 text-red-100', costEstimate: 1.20 },
            { name: 'Tangy Salsa', percentage: 31.5, color: 'bg-rose-950/40 border-rose-900 text-rose-100', costEstimate: 3.40 },
            { name: 'Jalapeño Slices', percentage: 27.8, color: 'bg-green-950/40 border-green-900 text-green-200', costEstimate: 3.17 },
            { name: 'Fresh Green Onions', percentage: 27.8, color: 'bg-emerald-950/40 border-emerald-900 text-emerald-200', costEstimate: 0.80 },
            { name: 'Sweet Kernel Corn', percentage: 25.9, color: 'bg-yellow-950/30 border-yellow-850 text-yellow-200', costEstimate: 1.50 }
        ];

        // Selected status for product builder simulation (defaults)
        let selectedToppingNames = ['Cheese Sauce', 'Bacon Bits', 'Sour Cream', 'Fresh Green Onions'];

        // Global simulation states
        let simulationPrice = 45;
        let simulationVolume = 150;

        // Life-cycle setup
        window.addEventListener('DOMContentLoaded', () => {
            lucide.createIcons();
            initCharts();
            renderIngredientsTable();
            renderPackagingTable();
            renderBuilderChecklist();
            recalculateEverything();
        });

        // Helper button adjustments for touch target layout
        function adjustGlobalServings(amount) {
            let nextVal = simulationVolume + amount;
            if (nextVal < 1) nextVal = 1;
            syncServings(nextVal);
        }

        function adjustPriceValue(amount) {
            let nextPrice = simulationPrice + amount;
            if (nextPrice < 15) nextPrice = 15;
            if (nextPrice > 80) nextPrice = 80;
            updatePricingFromMetric(nextPrice);
        }

        // Trigger notifications inside the viewport
        function showNotification(message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = `flex items-center gap-2 p-3.5 rounded-xl border shadow-lg transform translate-y-2 opacity-0 transition-all duration-300 bg-slate-900 pointer-events-auto min-w-[280px] ${
                type === 'success' ? 'border-emerald-800 text-emerald-200' : 'border-amber-800 text-amber-200'
            }`;
            
            const icon = type === 'success' ? '<i data-lucide="check-circle" class="w-5 h-5 text-emerald-400"></i>' : '<i data-lucide="alert-circle" class="w-5 h-5 text-amber-400"></i>';
            toast.innerHTML = `
                ${icon}
                <div class="text-xs font-semibold">${message}</div>
            `;
            
            container.appendChild(toast);
            lucide.createIcons({attrs: {class: "w-4 h-4"}});
            
            // Trigger animation
            setTimeout(() => {
                toast.classList.remove('translate-y-2', 'opacity-0');
            }, 10);

            // Close after 3 seconds
            setTimeout(() => {
                toast.classList.add('opacity-0', 'translate-y-2');
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // TAB HANDLERS
        function setActiveTab(panelId) {
            document.querySelectorAll('.chart-panel').forEach(p => p.classList.add('hidden'));
            document.querySelectorAll('.chart-tab').forEach(t => {
                t.classList.remove('border-brand-400', 'text-brand-400');
                t.classList.add('border-transparent', 'text-slate-400');
            });

            document.getElementById(panelId).classList.remove('hidden');
            const selectedTab = document.getElementById(`tab-${panelId}`);
            selectedTab.classList.add('border-brand-400', 'text-brand-400');
            selectedTab.classList.remove('border-transparent', 'text-slate-400');
        }

        // Dynamic synchronizers
        function syncServings(val) {
            let numericVal = parseInt(val) || 1;
            if (numericVal < 1) numericVal = 1;
            simulationVolume = numericVal;
            
            document.getElementById('global-servings-input').value = numericVal;
            document.getElementById('inventory-servings-qty').value = numericVal;
            document.getElementById('projection-servings-count').textContent = numericVal;
            document.getElementById('volume-range').value = numericVal;
            document.getElementById('slider-volume-label').textContent = `${numericVal} servings`;

            recalculateEverything();
        }

        function syncInputs(source, val) {
            if (source === 'price') {
                simulationPrice = parseFloat(val) || 0;
                document.getElementById('price-range').value = val;
                document.getElementById('slider-price-label').textContent = `${val} ฿`;
                document.getElementById('metric-selling-price-input').value = val;
            } else if (source === 'volume') {
                simulationVolume = parseInt(val) || 0;
                document.getElementById('volume-range').value = val;
                document.getElementById('slider-volume-label').textContent = `${val} servings`;
                document.getElementById('global-servings-input').value = val;
                document.getElementById('inventory-servings-qty').value = val;
                document.getElementById('projection-servings-count').textContent = val;
            }
            recalculateEverything();
        }

        function updatePricingFromMetric(val) {
            let numeric = parseFloat(val) || 0;
            simulationPrice = numeric;
            document.getElementById('price-range').value = numeric;
            document.getElementById('slider-price-label').textContent = `${numeric} ฿`;
            document.getElementById('metric-selling-price-input').value = numeric;
            recalculateEverything();
        }

        // CRUD INGREDIENTS
        function addIngredientRow() {
            const newId = ingredients.length > 0 ? Math.max(...ingredients.map(i => i.id)) + 1 : 1;
            ingredients.push({
                id: newId,
                name: 'New Custom Ingredient',
                buyQty: 1000,
                unit: 'g',
                price: 100,
                servingAmount: 10
            });
            renderIngredientsTable();
            recalculateEverything();
            showNotification('New ingredient line added.');
        }

        function deleteIngredientRow(id) {
            ingredients = ingredients.filter(i => i.id !== id);
            renderIngredientsTable();
            recalculateEverything();
            showNotification('Ingredient line removed.', 'warn');
        }

        // Field change handler
        function updateIngredient(id, field, val) {
            const item = ingredients.find(i => i.id === id);
            if (!item) return;

            if (field === 'name' || field === 'unit') {
                item[field] = val;
            } else {
                item[field] = parseFloat(val) || 0;
            }
            recalculateIngredientRow(id);
            recalculateEverything();
        }

        function recalculateIngredientRow(id) {
            const item = ingredients.find(i => i.id === id);
            if (!item) return;
            
            // Cost per base unit = Price / Buy Qty
            const costPerUnit = item.buyQty > 0 ? (item.price / item.buyQty) : 0;
            // Cost per serving = Cost per unit * servingAmount
            const servingCost = costPerUnit * item.servingAmount;

            const rowElement = document.getElementById(`ing-row-${id}`);
            if (rowElement) {
                rowElement.querySelector('.serving-cost-cell').textContent = `${servingCost.toFixed(2)} ฿`;
            }
        }

        function renderIngredientsTable() {
            const tbody = document.getElementById('ingredients-tbody');
            tbody.innerHTML = '';
            
            ingredients.forEach(item => {
                const costPerUnit = item.buyQty > 0 ? (item.price / item.buyQty) : 0;
                const servingCost = costPerUnit * item.servingAmount;

                const tr = document.createElement('tr');
                tr.id = `ing-row-${item.id}`;
                tr.className = "hover:bg-slate-800/40 transition-colors";
                tr.innerHTML = `
                    <td class="py-2.5 px-3 font-medium">
                        <input type="text" value="${item.name}" onchange="updateIngredient(${item.id}, 'name', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-2">
                        <input type="number" step="any" value="${item.buyQty}" onchange="updateIngredient(${item.id}, 'buyQty', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 text-center rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-2">
                        <input type="text" value="${item.unit}" onchange="updateIngredient(${item.id}, 'unit', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 text-center rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-2">
                        <input type="number" step="any" value="${item.price}" onchange="updateIngredient(${item.id}, 'price', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 text-center font-semibold text-slate-100 rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-2">
                        <input type="number" step="any" value="${item.servingAmount}" onchange="updateIngredient(${item.id}, 'servingAmount', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 text-center font-semibold text-brand-400 rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-3 text-right font-bold text-slate-100 serving-cost-cell text-xs sm:text-sm">
                        ${servingCost.toFixed(2)} ฿
                    </td>
                    <td class="py-2.5 px-3 text-right no-print">
                        <button onclick="deleteIngredientRow(${item.id})" class="text-red-400 hover:text-red-300 p-2 hover:bg-red-950/40 rounded-lg transition-all">
                            <i data-lucide="trash-2" class="w-4 h-4"></i>
                        </button>
                    </td>
                `;
                tbody.appendChild(tr);
            });
            lucide.createIcons();
        }

        // CRUD PACKAGING
        function addPackagingRow() {
            const newId = packaging.length > 0 ? Math.max(...packaging.map(p => p.id)) + 1 : 1;
            packaging.push({
                id: newId,
                name: 'New Packaging Item',
                buyQty: 100,
                unit: 'pcs',
                price: 50,
                servingAmount: 1
            });
            renderPackagingTable();
            recalculateEverything();
            showNotification('New packaging line added.');
        }

        function deletePackagingRow(id) {
            packaging = packaging.filter(p => p.id !== id);
            renderPackagingTable();
            recalculateEverything();
            showNotification('Packaging line removed.', 'warn');
        }

        function updatePackaging(id, field, val) {
            const item = packaging.find(p => p.id === id);
            if (!item) return;

            if (field === 'name' || field === 'unit') {
                item[field] = val;
            } else {
                item[field] = parseFloat(val) || 0;
            }
            recalculatePackagingRow(id);
            recalculateEverything();
        }

        function recalculatePackagingRow(id) {
            const item = packaging.find(p => p.id === id);
            if (!item) return;

            const costPerUnit = item.buyQty > 0 ? (item.price / item.buyQty) : 0;
            const servingCost = costPerUnit * item.servingAmount;

            const rowElement = document.getElementById(`pkg-row-${id}`);
            if (rowElement) {
                rowElement.querySelector('.pkg-serving-cost-cell').textContent = `${servingCost.toFixed(2)} ฿`;
            }
        }

        function renderPackagingTable() {
            const tbody = document.getElementById('packaging-tbody');
            tbody.innerHTML = '';

            packaging.forEach(item => {
                const costPerUnit = item.buyQty > 0 ? (item.price / item.buyQty) : 0;
                const servingCost = costPerUnit * item.servingAmount;

                const tr = document.createElement('tr');
                tr.id = `pkg-row-${item.id}`;
                tr.className = "hover:bg-slate-800/40 transition-colors";
                tr.innerHTML = `
                    <td class="py-2.5 px-3 font-medium">
                        <input type="text" value="${item.name}" onchange="updatePackaging(${item.id}, 'name', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-2">
                        <input type="number" step="any" value="${item.buyQty}" onchange="updatePackaging(${item.id}, 'buyQty', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 text-center rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-2">
                        <input type="text" value="${item.unit}" onchange="updatePackaging(${item.id}, 'unit', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 text-center rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-2">
                        <input type="number" step="any" value="${item.price}" onchange="updatePackaging(${item.id}, 'price', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 text-center font-semibold text-slate-100 rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-2">
                        <input type="number" step="any" value="${item.servingAmount}" onchange="updatePackaging(${item.id}, 'servingAmount', this.value)"
                            class="w-full bg-slate-950/80 text-slate-200 border border-slate-800 hover:border-slate-700 focus:border-brand-500 focus:bg-slate-950 focus:outline-none py-1.5 px-2 text-center font-semibold text-brand-400 rounded-lg transition-all text-xs sm:text-sm">
                    </td>
                    <td class="py-2.5 px-3 text-right font-bold text-slate-100 pkg-serving-cost-cell text-xs sm:text-sm">
                        ${servingCost.toFixed(2)} ฿
                    </td>
                    <td class="py-2.5 px-3 text-right no-print">
                        <button onclick="deletePackagingRow(${item.id})" class="text-red-400 hover:text-red-300 p-2 hover:bg-red-950/40 rounded-lg transition-all">
                            <i data-lucide="trash-2" class="w-4 h-4"></i>
                        </button>
                    </td>
                `;
                tbody.appendChild(tr);
            });
            lucide.createIcons();
        }

        // RE-CALCULATOR CORE ENGINE
        function recalculateEverything() {
            // 1. Calculate Food Ingredients Sum
            let totalIngredientsCost = 0;
            ingredients.forEach(item => {
                const costPerUnit = item.buyQty > 0 ? (item.price / item.buyQty) : 0;
                totalIngredientsCost += costPerUnit * item.servingAmount;
            });
            document.getElementById('total-ingredients-serving-cost').textContent = totalIngredientsCost.toFixed(2);
            document.getElementById('summary-ing-cost').textContent = totalIngredientsCost.toFixed(2);

            // 2. Calculate Packaging Sum
            let totalPackagingCost = 0;
            packaging.forEach(item => {
                const costPerUnit = item.buyQty > 0 ? (item.price / item.buyQty) : 0;
                totalPackagingCost += costPerUnit * item.servingAmount;
            });
            document.getElementById('total-packaging-serving-cost').textContent = totalPackagingCost.toFixed(2);
            document.getElementById('summary-pkg-cost').textContent = totalPackagingCost.toFixed(2);

            // 3. Consolidated Single Serving Cost
            const servingCostSum = totalIngredientsCost + totalPackagingCost;
            document.getElementById('summary-total-serving-cost').textContent = servingCostSum.toFixed(2);
            document.getElementById('metric-cost-per-serving').textContent = servingCostSum.toFixed(2);

            // 4. Update Financial metrics
            const revenue = simulationPrice * simulationVolume;
            const totalCOGS = servingCostSum * simulationVolume;
            const profit = revenue - totalCOGS;
            const marginPercent = simulationPrice > 0 ? ((simulationPrice - servingCostSum) / simulationPrice) * 100 : 0;
            
            // Break-even Quantity = Total Outlay (cogs for simulated volume) / Margin Contribution per unit
            const contributionPerUnit = simulationPrice - servingCostSum;
            const breakEvenQty = contributionPerUnit > 0 ? Math.ceil(totalCOGS / contributionPerUnit) : 0;

            // UI Metric bindings
            document.getElementById('metric-profit-per-serving').textContent = Math.max(0, contributionPerUnit).toFixed(2);
            document.getElementById('metric-margin').textContent = `${marginPercent.toFixed(1)}% Margin`;
            
            // Color updates based on financial health status
            const marginBadge = document.getElementById('metric-margin');
            const strategyBadge = document.getElementById('target-health-badge');
            if (marginPercent >= 50) {
                marginBadge.className = "text-xs font-bold text-emerald-300 bg-emerald-950/50 px-2.5 py-0.5 rounded-full border border-emerald-800";
                strategyBadge.textContent = "High Profit Margin";
                strategyBadge.className = "bg-emerald-500/20 text-emerald-300 text-xs font-bold px-2.5 py-1 rounded-full border border-emerald-550 animate-pulse";
            } else if (marginPercent >= 25) {
                marginBadge.className = "text-xs font-bold text-amber-300 bg-amber-950/50 px-2.5 py-0.5 rounded-full border border-amber-800";
                strategyBadge.textContent = "Balanced Margin";
                strategyBadge.className = "bg-amber-500/20 text-amber-300 text-xs font-bold px-2.5 py-1 rounded-full border border-amber-500/30";
            } else {
                marginBadge.className = "text-xs font-bold text-red-300 bg-red-950/50 px-2.5 py-0.5 rounded-full border border-red-800";
                strategyBadge.textContent = "Risk Zone - Lower Price";
                strategyBadge.className = "bg-red-500/20 text-red-300 text-xs font-bold px-2.5 py-1 rounded-full border border-red-500/30";
            }

            document.getElementById('metric-break-even').textContent = isFinite(breakEvenQty) ? breakEvenQty : 'N/A';
            document.getElementById('metric-total-revenue').textContent = revenue.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('metric-total-profit').textContent = profit.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            
            document.getElementById('projection-total-outlay').textContent = `${totalCOGS.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2})} ฿`;

            // Configurator Card Bottom updates
            document.getElementById('calc-projected-revenue').textContent = revenue.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('calc-projected-cogs').textContent = totalCOGS.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2});
            document.getElementById('calc-projected-margin').textContent = marginPercent.toFixed(1);
            document.getElementById('calc-projected-profit').textContent = profit.toLocaleString('en-US', {minimumFractionDigits: 2, maximumFractionDigits: 2});

            // Trigger child table re-calculations
            recalculateInventorySheet();
        }

        // INVENTORY SHEET CALCULATOR
        function recalculateInventorySheet() {
            const ingTbody = document.getElementById('inventory-ingredients-tbody');
            ingTbody.innerHTML = '';
            
            ingredients.forEach(item => {
                const totalReq = item.servingAmount * simulationVolume;
                // Package equivalent: total required / buyQty
                const packsReq = item.buyQty > 0 ? (totalReq / item.buyQty) : 0;

                const tr = document.createElement('tr');
                tr.className = "hover:bg-slate-800/30 border-b border-slate-850/50 transition-colors";
                tr.innerHTML = `
                    <td class="py-2.5 px-3 font-medium text-slate-300">${item.name}</td>
                    <td class="py-2.5 px-3 text-right font-bold text-slate-100">${totalReq.toLocaleString('en-US', {maximumFractionDigits: 1})} <span class="text-slate-500 font-normal text-xs">${item.unit}</span></td>
                    <td class="py-2.5 px-3 text-right font-semibold text-brand-400">${packsReq.toFixed(1)} <span class="text-slate-500 font-normal text-xs">store units</span></td>
                `;
                ingTbody.appendChild(tr);
            });

            const pkgTbody = document.getElementById('inventory-packaging-tbody');
            pkgTbody.innerHTML = '';

            packaging.forEach(item => {
                const totalReq = item.servingAmount * simulationVolume;
                const packsReq = item.buyQty > 0 ? (totalReq / item.buyQty) : 0;

                const tr = document.createElement('tr');
                tr.className = "hover:bg-slate-800/30 border-b border-slate-850/50 transition-colors";
                tr.innerHTML = `
                    <td class="py-2.5 px-3 font-medium text-slate-300">${item.name}</td>
                    <td class="py-2.5 px-3 text-right font-bold text-slate-100">${totalReq.toLocaleString('en-US', {maximumFractionDigits: 1})} <span class="text-slate-500 font-normal text-xs">${item.unit}</span></td>
                    <td class="py-2.5 px-3 text-right font-semibold text-brand-400">${packsReq.toFixed(1)} <span class="text-slate-500 font-normal text-xs">store units</span></td>
                `;
                pkgTbody.appendChild(tr);
            });
        }

        // PRODUCT BUILDER CHECKLIST RENDERING
        function renderBuilderChecklist() {
            const container = document.getElementById('builder-toppings-container');
            container.innerHTML = '';

            surveyToppings.forEach(topping => {
                const isChecked = selectedToppingNames.includes(topping.name);
                const card = document.createElement('label');
                card.className = `flex justify-between items-center p-3.5 border rounded-xl cursor-pointer hover:shadow-sm transition-all select-none ${
                    isChecked ? `${topping.color} font-bold ring-2 ring-brand-500/20` : 'bg-slate-950/40 border-slate-800 text-slate-400 hover:border-slate-700'
                }`;
                card.innerHTML = `
                    <div class="flex items-center space-x-3">
                        <input type="checkbox" value="${topping.name}" ${isChecked ? 'checked' : ''} onchange="toggleTopping('${topping.name}')"
                            class="rounded text-brand-500 focus:ring-brand-500 w-5 h-5 accent-brand-500 bg-slate-900 border-slate-700">
                        <span class="text-xs sm:text-sm font-medium">${topping.name}</span>
                    </div>
                    <div class="text-right">
                        <span class="text-[10px] block opacity-70">Survey Score</span>
                        <span class="text-xs font-bold text-slate-200">${topping.percentage}%</span>
                    </div>
                `;
                container.appendChild(card);
            });
            recalculateBuilderMetrics();
        }

        function toggleTopping(name) {
            if (selectedToppingNames.includes(name)) {
                selectedToppingNames = selectedToppingNames.filter(n => n !== name);
            } else {
                selectedToppingNames.push(name);
            }
            renderBuilderChecklist();
        }

        function recalculateBuilderMetrics() {
            let totalComboCost = 12.50; // Base Taco shell / crunch packet and processing base cost
            let scoreSum = 0;
            let activeCount = 0;

            surveyToppings.forEach(topping => {
                if (selectedToppingNames.includes(topping.name)) {
                    totalComboCost += topping.costEstimate;
                    scoreSum += topping.percentage;
                    activeCount++;
                }
            });

            // Normalized demand index: Average percentage affinity of selected options
            const compatibilityIndex = activeCount > 0 ? (scoreSum / activeCount) : 0;

            // Suggested retail dynamic equation
            const recommendedPrice = totalComboCost * 2.2; 

            document.getElementById('builder-calc-cost').textContent = totalComboCost.toFixed(2);
            document.getElementById('builder-calc-selling-price').textContent = Math.round(recommendedPrice).toFixed(2);
            
            document.getElementById('builder-popularity-label').textContent = `${Math.round(compatibilityIndex)}%`;
            document.getElementById('builder-popularity-bar').style.width = `${Math.round(compatibilityIndex)}%`;
        }

        // CHARTS ENGINE (INITIALIZATION WITH FIXED SURVEY PARAMETERS & DARK THEME LOOK AND FEEL)
        function initCharts() {
            // Global Chart defaults
            Chart.defaults.color = '#94a3b8'; // slate-400
            Chart.defaults.font.family = 'Plus Jakarta Sans';

            const gridConfig = {
                color: '#1e293b', // slate-800
                borderColor: '#334155' // slate-700
            };

            // Chart 1: Demographics
            new Chart(document.getElementById('chartDemographics'), {
                type: 'pie',
                data: {
                    labels: ['G1-G3', 'G4-G6', 'G7-G9', 'G10-G12', 'Teachers'],
                    datasets: [{
                        data: [4, 20, 22, 5, 4],
                        backgroundColor: ['#78350f', '#b45309', '#f59e0b', '#fbbf24', '#fef3c7'],
                        borderColor: '#0f172a',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { 
                        legend: { 
                            position: 'bottom', 
                            labels: { 
                                boxWidth: 12, 
                                font: { size: 10 },
                                color: '#94a3b8'
                            } 
                        } 
                    }
                }
            });

            // Chart 2: Buying Frequency
            new Chart(document.getElementById('chartFrequency'), {
                type: 'doughnut',
                data: {
                    labels: ['Every Event', 'Most Events', 'Sometimes', 'Rarely', 'Never'],
                    datasets: [{
                        data: [20, 19, 13, 2, 1],
                        backgroundColor: ['#059669', '#10b981', '#34d399', '#334155', '#1e293b'],
                        borderColor: '#0f172a',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { 
                        legend: { 
                            position: 'bottom', 
                            labels: { 
                                boxWidth: 12, 
                                font: { size: 10 },
                                color: '#94a3b8'
                            } 
                        } 
                    }
                }
            });

            // Chart 3: Willingness to spend
            new Chart(document.getElementById('chartSpendLimit'), {
                type: 'bar',
                data: {
                    labels: ['5-15 ฿', '15-25 ฿', '25-35 ฿', '35-45 ฿', '45+ ฿'],
                    datasets: [{
                        label: 'Respondents',
                        data: [3, 8, 16, 11, 17],
                        backgroundColor: '#fbbf24',
                        borderRadius: 6
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: { 
                        y: { 
                            beginAtZero: true,
                            grid: gridConfig,
                            ticks: { color: '#94a3b8' }
                        },
                        x: {
                            grid: { display: false },
                            ticks: { color: '#94a3b8' }
                        }
                    }
                }
            });

            // Chart 4: Premium addon willingness
            new Chart(document.getElementById('chartPremiumWillingness'), {
                type: 'pie',
                data: {
                    labels: ['Yes, definitely', 'Maybe', 'No, probably not', 'No, never'],
                    datasets: [{
                        data: [22, 24, 6, 3],
                        backgroundColor: ['#059669', '#d97706', '#b91c1c', '#7f1d1d'],
                        borderColor: '#0f172a',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { 
                        legend: { 
                            position: 'bottom', 
                            labels: { 
                                boxWidth: 12, 
                                font: { size: 10 },
                                color: '#94a3b8'
                            } 
                        } 
                    }
                }
            });

            // Chart 5: Preferred Toppings
            new Chart(document.getElementById('chartToppings'), {
                type: 'bar',
                data: {
                    labels: ['Cheese Sauce', 'Bacon', 'Extra Chs', 'Sour Crm', 'G.Pork', 'Nacho Chs', 'Hot Sauce', 'Salsa', 'Jalapeño'],
                    datasets: [{
                        label: 'Votes %',
                        data: [72.2, 57.4, 48.1, 44.4, 40.7, 35.2, 33.3, 31.5, 27.8],
                        backgroundColor: '#d97706',
                        borderRadius: 4
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: { 
                        x: { 
                            max: 100,
                            grid: gridConfig,
                            ticks: { color: '#94a3b8' }
                        },
                        y: {
                            grid: { display: false },
                            ticks: { color: '#94a3b8' }
                        }
                    }
                }
            });

            // Chart 6: Event Dislikes / Complaints
            new Chart(document.getElementById('chartDislikes'), {
                type: 'bar',
                data: {
                    labels: ['Long Wait', 'Runs Out', 'Expensive', 'Small Portions', 'Choices', 'Quality'],
                    datasets: [{
                        label: '% Mentioned',
                        data: [81.1, 37.7, 26.4, 24.5, 15.1, 15.1],
                        backgroundColor: '#ef4444',
                        borderRadius: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: { 
                        y: { 
                            max: 100,
                            grid: gridConfig,
                            ticks: { color: '#94a3b8' }
                        },
                        x: {
                            grid: { display: false },
                            ticks: { color: '#94a3b8' }
                        }
                    }
                }
            });
        }

        // EXPORT REPLACEMENTS (TXT DOWNLOADS)
        function exportShoppingList() {
            let txt = `==================================================\n`;
            txt += ` JOHN PORK TACOS INVENTORY SHOPPING LIST & CALCULATIONS\n`;
            txt += ` Generated for Grade 9 Entrepreneurship Challenge\n`;
            txt += ` Planned Servings: ${simulationVolume}\n`;
            txt += `==================================================\n\n`;
            
            txt += `INGREDIENTS TO PURCHASE:\n`;
            ingredients.forEach(item => {
                const totalReq = item.servingAmount * simulationVolume;
                const packsReq = item.buyQty > 0 ? (totalReq / item.buyQty) : 0;
                txt += `- ${item.name}: Required Total ${totalReq.toFixed(1)} ${item.unit} (~${packsReq.toFixed(1)} packs)\n`;
            });

            txt += `\nPACKAGING MATERIALS TO PURCHASE:\n`;
            packaging.forEach(item => {
                const totalReq = item.servingAmount * simulationVolume;
                const packsReq = item.buyQty > 0 ? (totalReq / item.buyQty) : 0;
                txt += `- ${item.name}: Required Total ${totalReq.toFixed(1)} ${item.unit} (~${packsReq.toFixed(1)} packs)\n`;
            });

            downloadTxtFile('john_pork_tacos_shopping_list.txt', txt);
            showNotification('Shopping list
