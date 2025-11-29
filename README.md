
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NexGen Ultra | Advanced Interactive Template</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Tailwind Config -->
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: {
                            50: '#eff6ff', 100: '#dbeafe', 500: '#3b82f6', 600: '#2563eb', 700: '#1d4ed8', 900: '#1e3a8a',
                        },
                        secondary: {
                            500: '#ec4899', 600: '#db2777',
                        },
                        dark: {
                            800: '#1e293b', 900: '#0f172a'
                        }
                    },
                    animation: {
                        'bounce-slow': 'bounce 3s infinite',
                        'fade-in-up': 'fadeInUp 0.8s ease-out forwards',
                        'float': 'float 6s ease-in-out infinite',
                        'pulse-glow': 'pulseGlow 2s ease-in-out infinite alternate',
                        'gradient': 'gradient 15s ease infinite',
                    },
                    keyframes: {
                        fadeInUp: {
                            '0%': { opacity: '0', transform: 'translateY(20px)' },
                            '100%': { opacity: '1', transform: 'translateY(0)' },
                        },
                        float: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-10px)' },
                        },
                        pulseGlow: {
                            '0%': { boxShadow: '0 0 5px rgba(59, 130, 246, 0.5)' },
                            '100%': { boxShadow: '0 0 20px rgba(59, 130, 246, 0.8)' },
                        },
                        gradient: {
                            '0%': { backgroundPosition: '0% 50%' },
                            '50%': { backgroundPosition: '100% 50%' },
                            '100%': { backgroundPosition: '0% 50%' },
                        }
                    },
                    backgroundSize: {
                        'gradient': '200% 200%',
                    }
                }
            }
        }
    </script>
    <!-- Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 10px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; }
        .dark ::-webkit-scrollbar-track { background: #1f2937; }
        ::-webkit-scrollbar-thumb { background: #3b82f6; border-radius: 5px; }
        ::-webkit-scrollbar-thumb:hover { background: #2563eb; }

        /* Glassmorphism */
        .glass {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
        }
        .dark .glass {
            background: rgba(17, 24, 39, 0.85);
        }

        /* Chat Widget Animation */
        .chat-open { transform: scale(1); opacity: 1; pointer-events: auto; }
        .chat-closed { transform: scale(0.9); opacity: 0; pointer-events: none; }

        /* Loader */
        .typing-dot {
            animation: typing 1.4s infinite ease-in-out both;
        }
        .typing-dot:nth-child(1) { animation-delay: -0.32s; }
        .typing-dot:nth-child(2) { animation-delay: -0.16s; }
        @keyframes typing {
            0%, 80%, 100% { transform: scale(0); }
            40% { transform: scale(1); }
        }

        /* Gradient Text */
        .gradient-text {
            background: linear-gradient(90deg, #3b82f6, #8b5cf6, #ec4899);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: gradient 4s linear infinite;
        }

        /* Enhanced Button Styles */
        .btn-glow {
            box-shadow: 0 4px 14px 0 rgba(59, 130, 246, 0.4);
            transition: all 0.3s ease;
        }
        .btn-glow:hover {
            box-shadow: 0 6px 20px rgba(59, 130, 246, 0.6);
            transform: translateY(-2px);
        }

        /* Card Hover Effects */
        .card-hover {
            transition: all 0.3s ease;
        }
        .card-hover:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
        }

        /* Particle Background */
        .particles-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -1;
        }
        .particle {
            position: absolute;
            border-radius: 50%;
            background: rgba(59, 130, 246, 0.2);
            animation: float 15s infinite linear;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-900 dark:bg-gray-950 dark:text-gray-100 transition-colors duration-300 font-sans selection:bg-primary-500 selection:text-white">

    <!-- Preloader -->
    <div id="preloader" class="fixed inset-0 bg-white dark:bg-gray-950 z-[100] flex items-center justify-center transition-opacity duration-500">
        <div class="text-center">
            <div class="w-16 h-16 border-4 border-primary-500 border-t-transparent rounded-full animate-spin mx-auto mb-4"></div>
            <h2 class="text-xl font-bold">NexGen Ultra</h2>
            <p class="text-gray-500 mt-2">Loading next generation experience...</p>
        </div>
    </div>

    <!-- Scroll Progress Bar -->
    <div class="fixed top-0 left-0 h-1 bg-gradient-to-r from-primary-500 to-secondary-500 z-[60]" id="scroll-progress" style="width: 0%"></div>

    <!-- Navigation -->
    <nav class="fixed w-full z-50 glass border-b border-gray-200 dark:border-gray-800 transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <!-- Logo -->
                <div class="flex items-center gap-2 cursor-pointer group" onclick="window.scrollTo(0,0)">
                    <div class="bg-primary-600 text-white p-1.5 rounded-lg group-hover:rotate-12 transition-transform">
                        <i data-lucide="layers" class="h-6 w-6"></i>
                    </div>
                    <span class="font-bold text-xl tracking-tight">NexGen<span class="text-primary-600">Ultra</span></span>
                </div>

                <!-- Desktop Menu -->
                <div class="hidden md:flex items-center space-x-8">
                    <a href="#stats" class="hover:text-primary-600 transition-colors relative group">
                        Stats
                        <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-primary-600 group-hover:w-full transition-all duration-300"></span>
                    </a>
                    <a href="#portfolio" class="hover:text-primary-600 transition-colors relative group">
                        Portfolio
                        <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-primary-600 group-hover:w-full transition-all duration-300"></span>
                    </a>
                    <a href="#pricing" class="hover:text-primary-600 transition-colors relative group">
                        Pricing
                        <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-primary-600 group-hover:w-full transition-all duration-300"></span>
                    </a>
                    <a href="#features" class="hover:text-primary-600 transition-colors relative group">
                        Features
                        <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-primary-600 group-hover:w-full transition-all duration-300"></span>
                    </a>
                    <a href="#faq" class="hover:text-primary-600 transition-colors relative group">
                        FAQ
                        <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-primary-600 group-hover:w-full transition-all duration-300"></span>
                    </a>
                    
                    <button id="theme-toggle" class="p-2 rounded-full hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors">
                        <i data-lucide="sun" class="h-5 w-5 dark:hidden"></i>
                        <i data-lucide="moon" class="h-5 w-5 hidden dark:block"></i>
                    </button>

                    <button onclick="scrollToSection('contact')" class="btn-glow bg-primary-600 hover:bg-primary-700 text-white px-5 py-2 rounded-full font-medium transition-all">
                        Get Quote
                    </button>
                </div>

                <!-- Mobile Menu Button -->
                <div class="md:hidden flex items-center gap-4">
                    <button id="theme-toggle-mobile" class="p-2 rounded-full hover:bg-gray-200 dark:hover:bg-gray-800">
                        <i data-lucide="sun" class="h-5 w-5 dark:hidden"></i>
                        <i data-lucide="moon" class="h-5 w-5 hidden dark:block"></i>
                    </button>
                    <button id="mobile-menu-btn" class="p-2 rounded-md hover:bg-gray-200 dark:hover:bg-gray-800">
                        <i data-lucide="menu" class="h-6 w-6"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white dark:bg-gray-900 border-b border-gray-200 dark:border-gray-800 absolute w-full">
            <div class="px-4 py-4 space-y-3">
                <a href="#stats" onclick="toggleMobileMenu()" class="block text-lg font-medium hover:text-primary-600 transition-colors">Stats</a>
                <a href="#portfolio" onclick="toggleMobileMenu()" class="block text-lg font-medium hover:text-primary-600 transition-colors">Portfolio</a>
                <a href="#pricing" onclick="toggleMobileMenu()" class="block text-lg font-medium hover:text-primary-600 transition-colors">Pricing</a>
                <a href="#features" onclick="toggleMobileMenu()" class="block text-lg font-medium hover:text-primary-600 transition-colors">Features</a>
                <a href="#faq" onclick="toggleMobileMenu()" class="block text-lg font-medium hover:text-primary-600 transition-colors">FAQ</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section with Typewriter -->
    <section class="pt-32 pb-20 px-4 text-center max-w-7xl mx-auto min-h-[80vh] flex flex-col justify-center items-center relative overflow-hidden">
        <!-- Animated Background -->
        <div class="particles-container" id="particles-container"></div>
        
        <div class="animate-fade-in-up relative z-10">
            <span class="inline-block py-1 px-3 rounded-full bg-primary-100 dark:bg-primary-900 text-primary-600 dark:text-primary-300 text-sm font-semibold mb-6">
                v2.0 Now Available
            </span>
            <h1 class="text-5xl md:text-7xl font-extrabold tracking-tight mb-6">
                We Build <span id="typewriter" class="gradient-text"></span><span class="animate-pulse">|</span>
            </h1>
            <p class="text-xl text-gray-600 dark:text-gray-300 mb-10 max-w-2xl mx-auto leading-relaxed">
                Experience the next generation of web interaction. Fully responsive, dark-mode ready, and packed with advanced features.
            </p>
            <div class="flex flex-col sm:flex-row justify-center gap-4">
                <button onclick="scrollToSection('portfolio')" class="btn-glow px-8 py-4 rounded-full bg-primary-600 text-white font-bold hover:bg-primary-700 transition-all flex items-center justify-center gap-2 group">
                    View Work <i data-lucide="arrow-right" class="group-hover:translate-x-1 transition-transform"></i>
                </button>
                <button onclick="openVideoModal()" class="px-8 py-4 rounded-full border border-gray-300 dark:border-gray-700 hover:bg-gray-100 dark:hover:bg-gray-800 transition-colors font-bold flex items-center justify-center gap-2">
                    <i data-lucide="play-circle" class="h-5 w-5"></i> Live Demo
                </button>
            </div>
        </div>
        
        <!-- Floating Elements Background (Decoration) -->
        <div class="absolute top-1/4 left-10 w-24 h-24 bg-primary-500/10 rounded-full blur-2xl animate-float -z-10"></div>
        <div class="absolute bottom-1/4 right-10 w-32 h-32 bg-secondary-500/10 rounded-full blur-2xl animate-float -z-10" style="animation-delay: 2s"></div>
        <div class="absolute top-1/2 left-1/3 w-20 h-20 bg-purple-500/10 rounded-full blur-2xl animate-float -z-10" style="animation-delay: 4s"></div>
        
        <!-- Scroll Indicator -->
        <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce">
            <i data-lucide="chevron-down" class="h-6 w-6 text-gray-400"></i>
        </div>
    </section>

    <!-- Animated Stats Section -->
    <section id="stats" class="py-16 bg-gradient-to-br from-primary-600 via-purple-600 to-secondary-600 text-white relative overflow-hidden">
        <div class="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PGNpcmNsZSBjeD0iMiIgY3k9IjIiIHI9IjIiIGZpbGw9InJnYmEoMjU1LDI1NSwyNTUsMC4xKSIvPjwvc3ZnPg==')] opacity-20"></div>
        <div class="max-w-7xl mx-auto px-4 grid grid-cols-2 md:grid-cols-4 gap-8 text-center relative z-10">
            <div class="p-4 transform transition-all hover:scale-105">
                <div class="text-4xl md:text-5xl font-bold mb-2 count-up" data-target="250">0</div>
                <div class="text-primary-100">Projects Done</div>
            </div>
            <div class="p-4 transform transition-all hover:scale-105">
                <div class="text-4xl md:text-5xl font-bold mb-2 count-up" data-target="98">0</div>
                <div class="text-primary-100">% Satisfaction</div>
            </div>
            <div class="p-4 transform transition-all hover:scale-105">
                <div class="text-4xl md:text-5xl font-bold mb-2 count-up" data-target="15">0</div>
                <div class="text-primary-100">Awards Won</div>
            </div>
            <div class="p-4 transform transition-all hover:scale-105">
                <div class="text-4xl md:text-5xl font-bold mb-2 count-up" data-target="1200">0</div>
                <div class="text-primary-100">Happy Clients</div>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section id="features" class="py-20 bg-white dark:bg-gray-900 transition-colors">
        <div class="max-w-7xl mx-auto px-4">
            <div class="text-center mb-16">
                <h2 class="text-3xl font-bold mb-4">Advanced Features</h2>
                <p class="text-gray-600 dark:text-gray-400 max-w-2xl mx-auto">Our templates come packed with cutting-edge features that set them apart from the competition.</p>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Feature 1 -->
                <div class="card-hover bg-gray-50 dark:bg-gray-800 p-6 rounded-xl">
                    <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 text-primary-600 rounded-lg flex items-center justify-center mb-4">
                        <i data-lucide="zap" class="h-6 w-6"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Lightning Fast</h3>
                    <p class="text-gray-600 dark:text-gray-400">Optimized for performance with minimal code and efficient animations.</p>
                </div>
                
                <!-- Feature 2 -->
                <div class="card-hover bg-gray-50 dark:bg-gray-800 p-6 rounded-xl">
                    <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 text-primary-600 rounded-lg flex items-center justify-center mb-4">
                        <i data-lucide="smartphone" class="h-6 w-6"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Fully Responsive</h3>
                    <p class="text-gray-600 dark:text-gray-400">Looks perfect on all devices from mobile to desktop.</p>
                </div>
                
                <!-- Feature 3 -->
                <div class="card-hover bg-gray-50 dark:bg-gray-800 p-6 rounded-xl">
                    <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 text-primary-600 rounded-lg flex items-center justify-center mb-4">
                        <i data-lucide="moon" class="h-6 w-6"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Dark Mode</h3>
                    <p class="text-gray-600 dark:text-gray-400">Automatic dark mode with system preference detection.</p>
                </div>
                
                <!-- Feature 4 -->
                <div class="card-hover bg-gray-50 dark:bg-gray-800 p-6 rounded-xl">
                    <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 text-primary-600 rounded-lg flex items-center justify-center mb-4">
                        <i data-lucide="code" class="h-6 w-6"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Clean Code</h3>
                    <p class="text-gray-600 dark:text-gray-400">Well-structured, commented code that's easy to customize.</p>
                </div>
                
                <!-- Feature 5 -->
                <div class="card-hover bg-gray-50 dark:bg-gray-800 p-6 rounded-xl">
                    <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 text-primary-600 rounded-lg flex items-center justify-center mb-4">
                        <i data-lucide="palette" class="h-6 w-6"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">Customizable</h3>
                    <p class="text-gray-600 dark:text-gray-400">Easy to customize colors, fonts, and layouts to match your brand.</p>
                </div>
                
                <!-- Feature 6 -->
                <div class="card-hover bg-gray-50 dark:bg-gray-800 p-6 rounded-xl">
                    <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 text-primary-600 rounded-lg flex items-center justify-center mb-4">
                        <i data-lucide="shield" class="h-6 w-6"></i>
                    </div>
                    <h3 class="text-xl font-bold mb-2">SEO Optimized</h3>
                    <p class="text-gray-600 dark:text-gray-400">Built with SEO best practices to help you rank higher.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Filterable Portfolio -->
    <section id="portfolio" class="py-20 px-4 max-w-7xl mx-auto bg-gray-50 dark:bg-gray-800/50 transition-colors">
        <div class="text-center mb-12">
            <h2 class="text-3xl font-bold mb-4">Our Creative Work</h2>
            <p class="text-gray-600 dark:text-gray-400 max-w-2xl mx-auto mb-8">Explore our portfolio of cutting-edge projects across different industries and technologies.</p>
            <div class="flex flex-wrap justify-center gap-4 mt-8">
                <button class="filter-btn active px-6 py-2 rounded-full border border-primary-600 bg-primary-600 text-white transition-all" data-filter="all">All</button>
                <button class="filter-btn px-6 py-2 rounded-full border border-gray-300 dark:border-gray-600 hover:border-primary-600 hover:text-primary-600 transition-all" data-filter="web">Web Design</button>
                <button class="filter-btn px-6 py-2 rounded-full border border-gray-300 dark:border-gray-600 hover:border-primary-600 hover:text-primary-600 transition-all" data-filter="app">Mobile Apps</button>
                <button class="filter-btn px-6 py-2 rounded-full border border-gray-300 dark:border-gray-600 hover:border-primary-600 hover:text-primary-600 transition-all" data-filter="brand">Branding</button>
            </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8" id="portfolio-grid">
            <!-- Items (Mock Data) -->
            <!-- Item 1: Web -->
            <div class="portfolio-item group relative rounded-xl overflow-hidden aspect-video shadow-lg cursor-pointer card-hover" data-category="web" onclick="openImageModal(this)">
                <img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?auto=format&fit=crop&w=800&q=80" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110" alt="Web Project">
                <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                    <span class="text-primary-400 text-sm font-bold uppercase">Web Design</span>
                    <h3 class="text-white text-xl font-bold">Fintech Dashboard</h3>
                </div>
            </div>
            <!-- Item 2: App -->
            <div class="portfolio-item group relative rounded-xl overflow-hidden aspect-video shadow-lg cursor-pointer card-hover" data-category="app" onclick="openImageModal(this)">
                <img src="https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?auto=format&fit=crop&w=800&q=80" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110" alt="App Project">
                <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                    <span class="text-secondary-400 text-sm font-bold uppercase">Mobile App</span>
                    <h3 class="text-white text-xl font-bold">Fitness Tracker</h3>
                </div>
            </div>
            <!-- Item 3: Brand -->
            <div class="portfolio-item group relative rounded-xl overflow-hidden aspect-video shadow-lg cursor-pointer card-hover" data-category="brand" onclick="openImageModal(this)">
                <img src="https://images.unsplash.com/photo-1542744173-8e7e53415bb0?auto=format&fit=crop&w=800&q=80" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110" alt="Brand Project">
                <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                    <span class="text-green-400 text-sm font-bold uppercase">Branding</span>
                    <h3 class="text-white text-xl font-bold">Eco Agency</h3>
                </div>
            </div>
             <!-- Item 4: Web -->
             <div class="portfolio-item group relative rounded-xl overflow-hidden aspect-video shadow-lg cursor-pointer card-hover" data-category="web" onclick="openImageModal(this)">
                <img src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?auto=format&fit=crop&w=800&q=80" class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110" alt="Web Project">
                <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex flex-col justify-end p-6">
                    <span class="text-primary-400 text-sm font-bold uppercase">Web Design</span>
                    <h3 class="text-white text-xl font-bold">Corporate Portal</h3>
                </div>
            </div>
        </div>
    </section>

    <!-- Pricing with Toggle -->
    <section id="pricing" class="py-20 bg-white dark:bg-gray-900 transition-colors">
        <div class="max-w-7xl mx-auto px-4 text-center">
            <h2 class="text-3xl font-bold mb-6">Flexible Pricing</h2>
            <p class="text-gray-600 dark:text-gray-400 max-w-2xl mx-auto mb-12">Choose the plan that fits your needs. All plans include our core features with no hidden fees.</p>
            
            <!-- Toggle -->
            <div class="flex items-center justify-center gap-4 mb-12">
                <span class="text-gray-600 dark:text-gray-400 font-medium">Monthly</span>
                <button id="billing-toggle" class="w-14 h-8 bg-gray-300 dark:bg-gray-600 rounded-full p-1 transition-colors relative focus:outline-none" onclick="toggleBilling()">
                    <div id="toggle-circle" class="w-6 h-6 bg-white rounded-full shadow-md transform transition-transform duration-300"></div>
                </button>
                <span class="text-gray-900 dark:text-gray-100 font-bold">Yearly <span class="text-xs text-green-500 ml-1">-20%</span></span>
            </div>

            <div class="grid md:grid-cols-3 gap-8">
                <!-- Basic -->
                <div class="card-hover bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg border border-gray-200 dark:border-gray-700 transition-all">
                    <h3 class="text-xl font-bold mb-2">Freelancer</h3>
                    <div class="text-4xl font-extrabold mb-6 flex justify-center items-end">
                        $<span class="price-amount" data-monthly="29" data-yearly="24">29</span>
                        <span class="text-base text-gray-500 dark:text-gray-400 font-normal mb-1">/mo</span>
                    </div>
                    <ul class="space-y-4 mb-8 text-left text-gray-600 dark:text-gray-400">
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> 5 Projects</li>
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> Basic Analytics</li>
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> Email Support</li>
                        <li class="flex gap-2"><i data-lucide="x" class="text-gray-400 h-5 w-5"></i> Advanced Features</li>
                    </ul>
                    <button class="w-full py-3 rounded-lg bg-primary-100 dark:bg-gray-700 text-primary-700 dark:text-white font-bold hover:bg-primary-200 dark:hover:bg-gray-600 transition-colors">Select Plan</button>
                </div>

                <!-- Pro -->
                <div class="card-hover bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-xl border-2 border-primary-500 transform md:-translate-y-4 animate-pulse-glow">
                    <div class="bg-primary-500 text-white text-xs font-bold px-3 py-1 rounded-full inline-block mb-4">MOST POPULAR</div>
                    <h3 class="text-xl font-bold mb-2">Agency</h3>
                    <div class="text-4xl font-extrabold mb-6 flex justify-center items-end">
                        $<span class="price-amount" data-monthly="99" data-yearly="79">99</span>
                        <span class="text-base text-gray-500 dark:text-gray-400 font-normal mb-1">/mo</span>
                    </div>
                    <ul class="space-y-4 mb-8 text-left text-gray-600 dark:text-gray-400">
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> Unlimited Projects</li>
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> Priority Support</li>
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> Advanced SEO</li>
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> Custom Domains</li>
                    </ul>
                    <button class="btn-glow w-full py-3 rounded-lg bg-primary-600 text-white font-bold hover:bg-primary-700 transition-colors">Select Plan</button>
                </div>

                <!-- Enterprise -->
                <div class="card-hover bg-white dark:bg-gray-800 p-8 rounded-2xl shadow-lg border border-gray-200 dark:border-gray-700 transition-all">
                    <h3 class="text-xl font-bold mb-2">Enterprise</h3>
                    <div class="text-4xl font-extrabold mb-6 flex justify-center items-end">
                        $<span class="price-amount" data-monthly="299" data-yearly="239">299</span>
                        <span class="text-base text-gray-500 dark:text-gray-400 font-normal mb-1">/mo</span>
                    </div>
                    <ul class="space-y-4 mb-8 text-left text-gray-600 dark:text-gray-400">
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> Custom Solutions</li>
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> 24/7 Dedicated Support</li>
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> White-label Options</li>
                        <li class="flex gap-2"><i data-lucide="check" class="text-primary-500 h-5 w-5"></i> API Access</li>
                    </ul>
                    <button class="w-full py-3 rounded-lg bg-primary-100 dark:bg-gray-700 text-primary-700 dark:text-white font-bold hover:bg-primary-200 dark:hover:bg-gray-600 transition-colors">Select Plan</button>
                </div>
            </div>
        </div>
    </section>

    <!-- FAQ Accordion -->
    <section id="faq" class="py-20 max-w-3xl mx-auto px-4 bg-gray-50 dark:bg-gray-800/50 transition-colors">
        <h2 class="text-3xl font-bold text-center mb-10">Frequently Asked Questions</h2>
        <div class="space-y-4" id="faq-container">
            <!-- FAQ Item 1 -->
            <div class="border border-gray-200 dark:border-gray-700 rounded-lg overflow-hidden bg-white dark:bg-gray-800 transition-colors">
                <button class="w-full flex justify-between items-center p-4 bg-white dark:bg-gray-800 hover:bg-gray-50 dark:hover:bg-gray-700 transition-colors text-left font-medium" onclick="toggleAccordion(this)">
                    <span>Do you provide source code?</span>
                    <i data-lucide="chevron-down" class="transition-transform duration-300"></i>
                </button>
                <div class="hidden bg-gray-50 dark:bg-gray-900 p-4 text-gray-600 dark:text-gray-300 border-t border-gray-200 dark:border-gray-700">
                    Yes! All plans include full access to the source code. You can modify it, extend it, and use it for commercial projects without restrictions.
                </div>
            </div>
            <!-- FAQ Item 2 -->
            <div class="border border-gray-200 dark:border-gray-700 rounded-lg overflow-hidden bg-white dark:bg-gray-800 transition-colors">
                <button class="w-full flex justify-between items-center p-4 bg-white dark:bg-gray-800 hover:bg-gray-50 dark:hover:bg-gray-700 transition-colors text-left font-medium" onclick="toggleAccordion(this)">
                    <span>Is this optimized for SEO?</span>
                    <i data-lucide="chevron-down" class="transition-transform duration-300"></i>
                </button>
                <div class="hidden bg-gray-50 dark:bg-gray-900 p-4 text-gray-600 dark:text-gray-300 border-t border-gray-200 dark:border-gray-700">
                    Absolutely. The structure uses semantic HTML5 tags, fast loading speeds (thanks to minimal JS), and follows all modern web vitals guidelines.
                </div>
            </div>
             <!-- FAQ Item 3 -->
             <div class="border border-gray-200 dark:border-gray-700 rounded-lg overflow-hidden bg-white dark:bg-gray-800 transition-colors">
                <button class="w-full flex justify-between items-center p-4 bg-white dark:bg-gray-800 hover:bg-gray-50 dark:hover:bg-gray-700 transition-colors text-left font-medium" onclick="toggleAccordion(this)">
                    <span>Can I cancel anytime?</span>
                    <i data-lucide="chevron-down" class="transition-transform duration-300"></i>
                </button>
                <div class="hidden bg-gray-50 dark:bg-gray-900 p-4 text-gray-600 dark:text-gray-300 border-t border-gray-200 dark:border-gray-700">
                    Yes, there are no lock-in contracts. You can cancel your subscription from your dashboard at any moment.
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Form Section -->
    <section id="contact" class="py-20 bg-gradient-to-br from-primary-600 via-purple-600 to-secondary-600 text-white relative overflow-hidden">
        <div class="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjAiIGhlaWdodD0iMjAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PGNpcmNsZSBjeD0iMiIgY3k9IjIiIHI9IjIiIGZpbGw9InJnYmEoMjU1LDI1NSwyNTUsMC4xKSIvPjwvc3ZnPg==')] opacity-20"></div>
        <div class="max-w-4xl mx-auto px-4 flex flex-col md:flex-row gap-12 items-center relative z-10">
            <div class="md:w-1/2">
                <h2 class="text-3xl font-bold mb-4">Let's start a project</h2>
                <p class="text-primary-100 mb-8">Ready to take your business to the next level? Fill out the form and we will get back to you within 24 hours.</p>
                <div class="space-y-4">
                    <div class="flex items-center gap-3">
                        <div class="p-2 bg-primary-500 rounded-lg"><i data-lucide="mail" class="h-5 w-5"></i></div>
                        <span>hello@nexgenultra.com</span>
                    </div>
                    <div class="flex items-center gap-3">
                        <div class="p-2 bg-primary-500 rounded-lg"><i data-lucide="map-pin" class="h-5 w-5"></i></div>
                        <span>123 Tech Street, Silicon Valley</span>
                    </div>
                    <div class="flex items-center gap-3">
                        <div class="p-2 bg-primary-500 rounded-lg"><i data-lucide="phone" class="h-5 w-5"></i></div>
                        <span>+1 (555) 123-4567</span>
                    </div>
                </div>
            </div>
            <div class="md:w-1/2 w-full bg-white dark:bg-gray-900 text-gray-900 dark:text-gray-100 p-8 rounded-2xl shadow-2xl">
                <form onsubmit="handleContact(event)" class="space-y-4">
                    <div>
                        <label class="block text-sm font-medium mb-1">Name</label>
                        <input type="text" required class="w-full px-4 py-2 rounded-lg border border-gray-300 dark:border-gray-700 bg-gray-50 dark:bg-gray-800 focus:ring-2 focus:ring-primary-500 outline-none transition-all">
                    </div>
                    <div>
                        <label class="block text-sm font-medium mb-1">Email</label>
                        <input type="email" required class="w-full px-4 py-2 rounded-lg border border-gray-300 dark:border-gray-700 bg-gray-50 dark:bg-gray-800 focus:ring-2 focus:ring-primary-500 outline-none transition-all">
                    </div>
                    <div>
                        <label class="block text-sm font-medium mb-1">Message</label>
                        <textarea rows="4" required class="w-full px-4 py-2 rounded-lg border border-gray-300 dark:border-gray-700 bg-gray-50 dark:bg-gray-800 focus:ring-2 focus:ring-primary-500 outline-none transition-all"></textarea>
                    </div>
                    <button type="submit" class="btn-glow w-full bg-primary-600 text-white py-3 rounded-lg font-bold hover:bg-primary-700 transition-colors">Send Message</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-gray-400 py-12 border-t border-gray-800">
        <div class="max-w-7xl mx-auto px-4 text-center">
            <div class="flex items-center justify-center gap-2 mb-4">
                <i data-lucide="layers" class="h-6 w-6 text-primary-500"></i>
                <span class="text-white font-bold text-lg">NexGen Ultra</span>
            </div>
            <p class="mb-8">Designed for the future.</p>
            <div class="flex justify-center gap-6 mb-8">
                <a href="#" class="hover:text-white transition-colors transform hover:scale-110"><i data-lucide="twitter"></i></a>
                <a href="#" class="hover:text-white transition-colors transform hover:scale-110"><i data-lucide="github"></i></a>
                <a href="#" class="hover:text-white transition-colors transform hover:scale-110"><i data-lucide="linkedin"></i></a>
                <a href="#" class="hover:text-white transition-colors transform hover:scale-110"><i data-lucide="instagram"></i></a>
            </div>
            <p class="text-sm text-gray-600">&copy; 2024 NexGen Ultra. All rights reserved.</p>
        </div>
    </footer>

    <!-- WIDGETS & OVERLAYS -->

    <!-- 1. Floating Chat Widget -->
    <div class="fixed bottom-6 right-6 z-40">
        <!-- Chat Window -->
        <div id="chat-window" class="chat-closed absolute bottom-16 right-0 w-80 bg-white dark:bg-gray-800 rounded-2xl shadow-2xl border border-gray-200 dark:border-gray-700 overflow-hidden transition-all duration-300 origin-bottom-right flex flex-col">
            <div class="bg-primary-600 p-4 text-white flex justify-between items-center">
                <div class="flex items-center gap-2">
                    <div class="w-2 h-2 bg-green-400 rounded-full"></div>
                    <span class="font-bold">Support Bot</span>
                </div>
                <button onclick="toggleChat()" class="hover:bg-primary-700 p-1 rounded"><i data-lucide="x" class="h-4 w-4"></i></button>
            </div>
            <div id="chat-messages" class="h-64 overflow-y-auto p-4 space-y-3 bg-gray-50 dark:bg-gray-900">
                <div class="flex items-start gap-2">
                    <div class="w-8 h-8 rounded-full bg-primary-100 flex items-center justify-center text-primary-600 text-xs font-bold">Bot</div>
                    <div class="bg-white dark:bg-gray-800 p-2 rounded-lg rounded-tl-none shadow-sm text-sm border border-gray-200 dark:border-gray-700">
                        Hello! How can I help you today?
                    </div>
                </div>
            </div>
            <div class="p-3 border-t border-gray-200 dark:border-gray-700 bg-white dark:bg-gray-800 flex gap-2">
                <input type="text" id="chat-input" placeholder="Type a message..." class="flex-1 text-sm bg-gray-100 dark:bg-gray-900 rounded-full px-3 py-2 outline-none focus:ring-1 focus:ring-primary-500" onkeypress="handleChatEnter(event)">
                <button onclick="sendChatMessage()" class="p-2 bg-primary-600 text-white rounded-full hover:bg-primary-700 transition-colors"><i data-lucide="send" class="h-4 w-4"></i></button>
            </div>
        </div>
        <!-- Toggle Button -->
        <button onclick="toggleChat()" class="btn-glow w-14 h-14 bg-primary-600 hover:bg-primary-700 text-white rounded-full shadow-lg flex items-center justify-center transition-all">
            <i data-lucide="message-circle" class="h-6 w-6"></i>
        </button>
    </div>

    <!-- 2. Toast Notification Container -->
    <div id="toast-container" class="fixed top-24 right-5 z-[70] flex flex-col gap-2 pointer-events-none"></div>

    <!-- 3. Cookie Consent Banner -->
    <div id="cookie-banner" class="fixed bottom-0 left-0 w-full bg-gray-900/95 backdrop-blur text-white p-4 z-[80] transform translate-y-full transition-transform duration-500">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-4">
            <p class="text-sm">We use cookies to enhance your experience. By continuing to visit this site you agree to our use of cookies.</p>
            <div class="flex gap-3">
                <button onclick="acceptCookies()" class="px-4 py-2 bg-primary-600 rounded-lg text-sm font-bold hover:bg-primary-500 transition-colors">Accept</button>
                <button onclick="acceptCookies()" class="px-4 py-2 bg-gray-700 rounded-lg text-sm hover:bg-gray-600 transition-colors">Decline</button>
            </div>
        </div>
    </div>

    <!-- 4. Image Modal -->
    <div id="image-modal" class="fixed inset-0 z-[90] bg-black/90 hidden flex items-center justify-center p-4 backdrop-blur-sm" onclick="closeImageModal()">
        <img id="modal-img" src="" class="max-w-full max-h-[90vh] rounded-lg shadow-2xl transform scale-95 transition-transform duration-300">
        <button class="absolute top-4 right-4 text-white p-2 hover:bg-white/20 rounded-full transition-colors"><i data-lucide="x" class="h-8 w-8"></i></button>
    </div>

    <!-- 5. Scroll to Top Button -->
    <button id="scroll-top" onclick="window.scrollTo(0,0)" class="fixed bottom-6 left-6 w-12 h-12 bg-primary-600 text-white rounded-full shadow-lg flex items-center justify-center transition-all opacity-0 pointer-events-none z-40">
        <i data-lucide="chevron-up" class="h-5 w-5"></i>
    </button>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // --- 1. Initialization ---
        lucide.createIcons();
        
        // Remove preloader after page loads
        window.addEventListener('load', function() {
            setTimeout(() => {
                document.getElementById('preloader').style.opacity = '0';
                setTimeout(() => {
                    document.getElementById('preloader').style.display = 'none';
                }, 500);
            }, 1000);
        });

        // Create particle background
        function createParticles() {
            const container = document.getElementById('particles-container');
            const particleCount = 30;
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.classList.add('particle');
                
                // Random properties
                const size = Math.random() * 60 + 20;
                const posX = Math.random() * 100;
                const posY = Math.random() * 100;
                const delay = Math.random() * 15;
                const duration = Math.random() * 10 + 10;
                
                particle.style.width = `${size}px`;
                particle.style.height = `${size}px`;
                particle.style.left = `${posX}%`;
                particle.style.top = `${posY}%`;
                particle.style.animationDelay = `${delay}s`;
                particle.style.animationDuration = `${duration}s`;
                
                container.appendChild(particle);
            }
        }
        createParticles();

        // Theme Logic
        const html = document.documentElement;
        const toggleBtns = [document.getElementById('theme-toggle'), document.getElementById('theme-toggle-mobile')];
        
        function initTheme() {
            if (localStorage.theme === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
                html.classList.add('dark');
            } else {
                html.classList.remove('dark');
            }
        }
        initTheme();

        toggleBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                html.classList.toggle('dark');
                localStorage.theme = html.classList.contains('dark') ? 'dark' : 'light';
            });
        });

        // --- 2. Scroll Progress Bar & Scroll to Top Button ---
        window.onscroll = function() {
            let winScroll = document.body.scrollTop || document.documentElement.scrollTop;
            let height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            let scrolled = (winScroll / height) * 100;
            document.getElementById("scroll-progress").style.width = scrolled + "%";
            
            // Navbar Glass effect on scroll
            const nav = document.getElementById('navbar');
            if (winScroll > 50) {
                nav.classList.add('shadow-md');
            } else {
                nav.classList.remove('shadow-md');
            }
            
            // Show/hide scroll to top button
            const scrollTopBtn = document.getElementById('scroll-top');
            if (winScroll > 500) {
                scrollTopBtn.classList.remove('opacity-0', 'pointer-events-none');
                scrollTopBtn.classList.add('opacity-100', 'pointer-events-auto');
            } else {
                scrollTopBtn.classList.remove('opacity-100', 'pointer-events-auto');
                scrollTopBtn.classList.add('opacity-0', 'pointer-events-none');
            }
        };

        // --- 3. Typewriter Effect ---
        const words = ["Websites", "Mobile Apps", "Brands", "Experiences"];
        let wordIndex = 0;
        let charIndex = 0;
        let isDeleting = false;
        const typeTarget = document.getElementById('typewriter');

        function type() {
            const currentWord = words[wordIndex];
            
            if (isDeleting) {
                typeTarget.textContent = currentWord.substring(0, charIndex - 1);
                charIndex--;
            } else {
                typeTarget.textContent = currentWord.substring(0, charIndex + 1);
                charIndex++;
            }

            let typeSpeed = isDeleting ? 50 : 150;

            if (!isDeleting && charIndex === currentWord.length) {
                isDeleting = true;
                typeSpeed = 2000; // Pause at end
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                wordIndex = (wordIndex + 1) % words.length;
                typeSpeed = 500;
            }

            setTimeout(type, typeSpeed);
        }
        type(); // Start

        // --- 4. Animated Stats Counter ---
        const observerOptions = { threshold: 0.5 };
        const statsObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    const counters = entry.target.querySelectorAll('.count-up');
                    counters.forEach(counter => {
                        const target = +counter.getAttribute('data-target');
                        const duration = 2000; // 2 seconds
                        const increment = target / (duration / 16);
                        
                        let current = 0;
                        const updateCount = () => {
                            current += increment;
                            if (current < target) {
                                counter.innerText = Math.ceil(current);
                                requestAnimationFrame(updateCount);
                            } else {
                                counter.innerText = target + (target > 100 ? '+' : '');
                            }
                        };
                        updateCount();
                    });
                    statsObserver.unobserve(entry.target);
                }
            });
        }, observerOptions);
        
        statsObserver.observe(document.getElementById('stats'));

        // --- 5. Portfolio Filtering ---
        const filterBtns = document.querySelectorAll('.filter-btn');
        const items = document.querySelectorAll('.portfolio-item');

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                // Active class logic
                filterBtns.forEach(b => {
                    b.classList.remove('bg-primary-600', 'text-white', 'border-primary-600');
                    b.classList.add('border-gray-300', 'hover:text-primary-600'); 
                });
                
                // Re-add active styles to clicked
                btn.classList.remove('border-gray-300', 'hover:text-primary-600');
                btn.classList.add('bg-primary-600', 'text-white', 'border-primary-600');

                const filterValue = btn.getAttribute('data-filter');

                items.forEach(item => {
                    if (filterValue === 'all' || item.getAttribute('data-category') === filterValue) {
                        item.style.display = 'block';
                        setTimeout(() => item.style.opacity = '1', 50);
                    } else {
                        item.style.opacity = '0';
                        setTimeout(() => item.style.display = 'none', 300);
                    }
                });
            });
        });

        // --- 6. Pricing Toggle ---
        let isYearly = false;
        function toggleBilling() {
            isYearly = !isYearly;
            const toggleCircle = document.getElementById('toggle-circle');
            const toggleBtn = document.getElementById('billing-toggle');
            
            // Move circle
            toggleCircle.style.transform = isYearly ? 'translateX(24px)' : 'translateX(0)';
            toggleBtn.classList.toggle('bg-primary-500', isYearly);
            toggleBtn.classList.toggle('bg-gray-300', !isYearly);

            // Update Prices
            document.querySelectorAll('.price-amount').forEach(el => {
                const newVal = isYearly ? el.getAttribute('data-yearly') : el.getAttribute('data-monthly');
                // Simple animation
                el.style.opacity = 0;
                setTimeout(() => {
                    el.textContent = newVal;
                    el.style.opacity = 1;
                }, 200);
            });
        }

        // --- 7. FAQ Accordion ---
        function toggleAccordion(button) {
            const content = button.nextElementSibling;
            const icon = button.querySelector('i');
            
            // Toggle current
            content.classList.toggle('hidden');
            icon.style.transform = content.classList.contains('hidden') ? 'rotate(0deg)' : 'rotate(180deg)';
        }

        // --- 8. Chat Widget Logic ---
        function toggleChat() {
            const win = document.getElementById('chat-window');
            if (win.classList.contains('chat-closed')) {
                win.classList.remove('chat-closed');
                win.classList.add('chat-open');
                document.getElementById('chat-input').focus();
            } else {
                win.classList.remove('chat-open');
                win.classList.add('chat-closed');
            }
        }

        function handleChatEnter(e) {
            if (e.key === 'Enter') sendChatMessage();
        }

        function sendChatMessage() {
            const input = document.getElementById('chat-input');
            const msg = input.value.trim();
            const container = document.getElementById('chat-messages');
            
            if (!msg) return;

            // User Message
            const userDiv = document.createElement('div');
            userDiv.className = 'flex items-center justify-end gap-2';
            userDiv.innerHTML = `
                <div class="bg-primary-600 text-white p-2 rounded-lg rounded-tr-none shadow-sm text-sm">${msg}</div>
            `;
            container.appendChild(userDiv);
            input.value = '';
            container.scrollTop = container.scrollHeight;

            // Bot Typing Simulation
            const typingDiv = document.createElement('div');
            typingDiv.id = 'bot-typing';
            typingDiv.className = 'flex items-start gap-2 mt-2';
            typingDiv.innerHTML = `
                <div class="w-8 h-8 rounded-full bg-primary-100 flex items-center justify-center text-primary-600 text-xs font-bold">Bot</div>
                <div class="bg-white dark:bg-gray-800 p-3 rounded-lg rounded-tl-none shadow-sm text-sm border border-gray-200 dark:border-gray-700 flex gap-1">
                    <div class="w-1.5 h-1.5 bg-gray-400 rounded-full typing-dot"></div>
                    <div class="w-1.5 h-1.5 bg-gray-400 rounded-full typing-dot"></div>
                    <div class="w-1.5 h-1.5 bg-gray-400 rounded-full typing-dot"></div>
                </div>
            `;
            container.appendChild(typingDiv);
            container.scrollTop = container.scrollHeight;

            // Bot Reply
            setTimeout(() => {
                document.getElementById('bot-typing').remove();
                const botDiv = document.createElement('div');
                botDiv.className = 'flex items-start gap-2 animate-fade-in-up';
                botDiv.innerHTML = `
                    <div class="w-8 h-8 rounded-full bg-primary-100 flex items-center justify-center text-primary-600 text-xs font-bold">Bot</div>
                    <div class="bg-white dark:bg-gray-800 p-2 rounded-lg rounded-tl-none shadow-sm text-sm border border-gray-200 dark:border-gray-700">
                        Thanks for reaching out! We will get back to you shortly.
                    </div>
                `;
                container.appendChild(botDiv);
                container.scrollTop = container.scrollHeight;
            }, 1500);
        }

        // --- 9. Toast Notifications ---
        function showToast(message) {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = 'bg-gray-800 text-white px-6 py-4 rounded-lg shadow-xl flex items-center gap-3 transform translate-x-full transition-transform duration-300 pointer-events-auto';
            toast.innerHTML = `<i data-lucide="check-circle" class="text-green-400"></i> ${message}`;
            
            container.appendChild(toast);
            lucide.createIcons();
            
            // Slide in
            requestAnimationFrame(() => {
                toast.classList.remove('translate-x-full');
            });

            setTimeout(() => {
                toast.classList.add('translate-x-full', 'opacity-0');
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // --- 10. Utils (Form, Mobile Menu, Cookie, Image Modal) ---
        function handleContact(e) {
            e.preventDefault();
            const btn = e.target.querySelector('button');
            const oldText = btn.innerText;
            btn.innerText = 'Sending...';
            btn.disabled = true;
            
            setTimeout(() => {
                btn.innerText = oldText;
                btn.disabled = false;
                e.target.reset();
                showToast('Message sent successfully!');
            }, 1500);
        }

        function toggleMobileMenu() {
            document.getElementById('mobile-menu').classList.toggle('hidden');
        }

        function scrollToSection(id) {
            document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
        }

        // Cookie Consent
        setTimeout(() => {
            if(!localStorage.cookiesAccepted) {
                document.getElementById('cookie-banner').classList.remove('translate-y-full');
            }
        }, 1000);

        function acceptCookies() {
            document.getElementById('cookie-banner').classList.add('translate-y-full');
            localStorage.cookiesAccepted = "true";
        }

        // Image Modal
        function openImageModal(element) {
            const src = element.querySelector('img').src;
            const modal = document.getElementById('image-modal');
            const img = document.getElementById('modal-img');
            img.src = src;
            modal.classList.remove('hidden');
            setTimeout(() => img.classList.remove('scale-95'), 10);
        }

        function closeImageModal() {
            const modal = document.getElementById('image-modal');
            const img = document.getElementById('modal-img');
            img.classList.add('scale-95');
            setTimeout(() => modal.classList.add('hidden'), 200);
        }

        // Video Modal
        function openVideoModal() {
            showToast('Video demo feature would open a modal with a product walkthrough');
        }
    </script>
</body>
</html>
can you make this kind of code for me with other topic
