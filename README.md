
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIVA TV - Streaming de Canais, Filmes e Séries</title>
    
    <!-- FontAwesome para ícones -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#5D5CDE',
                        secondary: '#ff3a6b',
                        dark: '#0f0f1a',
                        light: '#FFFFFF'
                    }
                }
            }
        }
    </script>
    
    <!-- Email JS -->
    <script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
    
    <style> 
        :root { 
            --primary: #5D5CDE; 
            --secondary: #ff3a6b; 
            --dark: #0f0f1a; 
            --light: #FFFFFF; 
        }
        /* Dark mode support */
        .dark {
            --primary: #6665e7;
            --secondary: #ff5286;
            --dark: #0f0f1a;
            --light: #1e1e30;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--dark);
            color: var(--light);
            overflow-x: hidden;
        }
        
        .dark body {
            background-color: var(--dark);
            color: #f1f1f1;
        }
        
        .hero {
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.85)), url('https://images.unsplash.com/photo-1594908900066-3f47337549d8?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            position: relative;
        }
        
        .logo {
            text-transform: uppercase;
            font-weight: 900;
            letter-spacing: 2px;
            text-shadow: 0 0 15px rgba(93, 92, 222, 0.8);
            position: relative;
        }
        
        .logo::before {
            content: '';
            position: absolute;
            width: 40px;
            height: 40px;
            background: var(--secondary);
            border-radius: 5px;
            transform: rotate(45deg);
            z-index: -1;
            left: -10px;
            top: -8px;
            opacity: 0.7;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { transform: rotate(45deg) scale(1); opacity: 0.7; }
            50% { transform: rotate(45deg) scale(1.1); opacity: 0.9; }
            100% { transform: rotate(45deg) scale(1); opacity: 0.7; }
        }
        
        .btn-pulse {
            animation: btn-pulse 1.5s infinite;
            box-shadow: 0 0 0 rgba(255,58,107, 0.4);
            transition: all 0.3s ease;
        }
        
        @keyframes btn-pulse {
            0% { box-shadow: 0 0 0 0 rgba(255,58,107, 0.4); }
            70% { box-shadow: 0 0 0 15px rgba(255,58,107, 0); }
            100% { box-shadow: 0 0 0 0 rgba(255,58,107, 0); }
        }
        
        .btn-pulse:hover {
            transform: scale(1.05);
        }
        
        .device-icon {
            transition: all 0.3s ease;
        }
        
        .device-icon:hover {
            transform: translateY(-10px);
        }
        
        .card {
            transition: all 0.3s ease;
            background: rgba(255,255,255,0.03);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.1);
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 30px rgba(0,0,0,0.3);
        }
        
        .floating-whatsapp {
            position: fixed;
            bottom: 30px;
            right: 30px;
            z-index: 100;
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        .movie-background {
            background: linear-gradient(rgba(15,15,26,0.7), rgba(15,15,26,1)), url('https://images.unsplash.com/photo-1626814026160-2237a95fc5a0?ixlib=rb-1.2.1&auto=format&fit=crop&w=1350&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
        }
        
        input, textarea {
            background: rgba(255,255,255,0.05) !important;
            border: 1px solid rgba(255,255,255,0.1) !important;
            color: white !important;
        }
        
        input:focus, textarea:focus {
            border-color: var(--primary) !important;
            box-shadow: 0 0 0 3px rgba(93, 92, 222, 0.3) !important;
        }
        
        .testimonial-slider {
            overflow: hidden;
            position: relative;
        }
        
        .slider-container {
            display: flex;
            animation: slide 20s infinite linear;
        }
        
        @keyframes slide {
            0% { transform: translateX(0); }
            100% { transform: translateX(-100%); }
        }
        
        .warning-badge {
            background-color: #ff3a6b;
            color: white;
            padding: 8px 15px;
            border-radius: 50px;
            font-weight: bold;
            font-size: 0.9rem;
            display: inline-block;
            box-shadow: 0 4px 12px rgba(255, 58, 107, 0.4);
            animation: attention 2s infinite;
        }
        
        @keyframes attention {
            0% { transform: scale(1); }
            5% { transform: scale(1.1); }
            10% { transform: scale(1); }
            15% { transform: scale(1.1); }
            20% { transform: scale(1); }
            100% { transform: scale(1); }
        }
        
        .channel-slider {
            overflow: hidden;
        }
        
        .channel-slider-container {
            display: flex;
            animation: slideChannels 30s infinite linear;
        }
        
        @keyframes slideChannels {
            0% { transform: translateX(0); }
            100% { transform: translateX(-100%); }
        }
        
        .channel-logo {
            height: 60px;
            margin: 0 20px;
            opacity: 0.7;
            transition: all 0.3s ease;
            filter: grayscale(100%);
        }
        
        .channel-logo:hover {
            opacity: 1;
            filter: grayscale(0%);
            transform: scale(1.2);
        }
    </style>
</head>
<body>
<nav class="bg-dark py-4">
    <div class="container mx-auto px-4 flex justify-between items-center">
        <div class="logo text-2xl font-bold text-white">
            <span class="text-white">VIVA</span>
            <span class="text-secondary">TV</span>
        </div>
        <div class="hidden md:flex space-x-6">
            <a href="#benefits" class="text-white hover:text-secondary transition-colors">Benefícios</a>
            <a href="#devices" class="text-white hover:text-secondary transition-colors">Dispositivos</a>
            <a href="#pricing" class="text-white hover:text-secondary transition-colors">Preços</a>
            <a href="#contact" class="text-white hover:text-secondary transition-colors">Contato</a>
        </div>
        <a href="https://wa.me/5511911379757" target="_blank" class="bg-secondary hover:bg-opacity-90 text-white px-4 py-2 rounded-full font-medium text-sm">
            <i class="fab fa-whatsapp mr-1"></i> WhatsApp
        </a>
    </div>
</nav>
<header class="hero min-h-screen flex items-center justify-center relative">
    <div class="container mx-auto px-4 flex flex-col items-center justify-center z-10 py-20">
        <h1 class="text-5xl md:text-7xl font-bold text-center mb-6">
            <span class="logo">
                <span class="text-white">VIVA</span>
                <span class="text-secondary">TV</span>
            </span>
        </h1>
        <p class="text-xl md:text-2xl text-center mb-8 max-w-3xl">Tenha acesso a milhares de canais, filmes e séries em um único lugar. A melhor experiência de streaming para toda a família!</p>
        <div class="warning-badge mb-8">
            <i class="fas fa-exclamation-circle mr-2"></i>Não oferecemos teste grátis!
        </div>
        <a href="https://wa.me/5511911379757" target="_blank" class="btn-pulse bg-secondary text-white text-xl px-8 py-4 rounded-full font-bold mb-8 inline-block">
            Assine Agora <i class="fas fa-arrow-right ml-2"></i>
        </a>
        <p class="text-xl opacity-80">+ de 100.000 conteúdos liberados!</p>
    </div>
    
    <div class="absolute bottom-0 left-0 w-full overflow-hidden" style="height: 70px;">
        <svg viewBox="0 0 500 150" preserveAspectRatio="none" style="height: 100%; width: 100%;">
            <path d="M0.00,49.98 C150.00,150.00 349.20,-50.00 500.00,49.98 L500.00,150.00 L0.00,150.00 Z" style="stroke: none; fill: #0f0f1a;"></path>
        </svg>
    </div>
</header>
<!-- Channels Slider -->
<section class="py-16 bg-gradient-to-b from-dark to-gray-900">
    <div class="container mx-auto px-4">
        <h2 class="text-3xl md:text-4xl font-bold text-center mb-12">Canais e Conteúdos Populares</h2>
        
        <div class="channel-slider">
            <div class="channel-slider-container">
                <!-- Generated channel logos -->
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">HBO</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Netflix</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Disney+</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Globo</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">SBT</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Record</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">ESPN</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Fox</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Warner</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Paramount</div>
                <!-- Duplicate logos for continuous scrolling -->
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">HBO</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Netflix</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Disney+</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Globo</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">SBT</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Record</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">ESPN</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Fox</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Warner</div>
                <div class="channel-logo bg-gray-800 rounded-md flex items-center justify-center">Paramount</div>
            </div>
        </div>
    </div>
</section>
<!-- Benefits -->
<section id="benefits" class="py-20 movie-background">
    <div class="container mx-auto px-4">
        <h2 class="text-3xl md:text-4xl font-bold text-center mb-16">Por Que Escolher a VIVA TV?</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <div class="card rounded-xl p-8 text-center">
                <div class="w-20 h-20 bg-secondary bg-opacity-20 rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fas fa-tv text-3xl text-secondary"></i>
                </div>
                <h3 class="text-2xl font-bold mb-4">+100.000 Conteúdos</h3>
                <p class="text-gray-300">Acesso a um catálogo massivo com mais de 100 mil títulos entre canais, filmes e séries.</p>
            </div>
            
            <div class="card rounded-xl p-8 text-center">
                <div class="w-20 h-20 bg-secondary bg-opacity-20 rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fas fa-film text-3xl text-secondary"></i>
                </div>
                <h3 class="text-2xl font-bold mb-4">Filmes em Lançamento</h3>
                <p class="text-gray-300">Assista aos maiores lançamentos do cinema logo quando são disponibilizados.</p>
            </div>
            
            <div class="card rounded-xl p-8 text-center">
                <div class="w-20 h-20 bg-secondary bg-opacity-20 rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fas fa-mobile-alt text-3xl text-secondary"></i>
                </div>
                <h3 class="text-2xl font-bold mb-4">Múltiplos Dispositivos</h3>
                <p class="text-gray-300">Assista em qualquer dispositivo: Smart TVs, celulares, tablets, computadores e muito mais.</p>
            </div>
            
            <div class="card rounded-xl p-8 text-center">
                <div class="w-20 h-20 bg-secondary bg-opacity-20 rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fas fa-money-bill-wave text-3xl text-secondary"></i>
                </div>
                <h3 class="text-2xl font-bold mb-4">Sem Fidelidade</h3>
                <p class="text-gray-300">Cancele quando quiser, sem burocracia. Não há contratos de fidelidade.</p>
            </div>
            
            <div class="card rounded-xl p-8 text-center">
                <div class="w-20 h-20 bg-secondary bg-opacity-20 rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fas fa-users text-3xl text-secondary"></i>
                </div>
                <h3 class="text-2xl font-bold mb-4">Para Toda Família</h3>
                <p class="text-gray-300">Conteúdo para todas as idades e gostos, garantindo diversão para toda a família.</p>
            </div>
            
            <div class="card rounded-xl p-8 text-center">
                <div class="w-20 h-20 bg-secondary bg-opacity-20 rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fas fa-credit-card text-3xl text-secondary"></i>
                </div>
                <h3 class="text-2xl font-bold mb-4">Sem Taxa de Adesão</h3>
                <p class="text-gray-300">Não cobramos taxa de adesão. Apenas o valor mensal da assinatura, sem surpresas.</p>
            </div>
            
            <!-- Novo card de benefício de fidelidade -->
            <div class="card rounded-xl p-8 text-center">
                <div class="w-20 h-20 bg-secondary bg-opacity-20 rounded-full flex items-center justify-center mx-auto mb-6">
                    <i class="fas fa-percent text-3xl text-secondary"></i>
                </div>
                <h3 class="text-2xl font-bold mb-4">Programa de Fidelidade</h3>
                <p class="text-gray-300">Ganhe 20% de desconto automático nas renovações realizadas dentro do prazo. Economia garantida para assinantes fiéis!</p>
            </div>
        </div>
        
        <div class="text-center mt-16">
            <a href="https://wa.me/5511911379757" target="_blank" class="btn-pulse bg-secondary text-white text-xl px-8 py-4 rounded-full font-bold inline-block">
                Quero Assinar Agora <i class="fas fa-arrow-right ml-2"></i>
            </a>
        </div>
    </div>
</section>
<!-- Compatible Devices -->
<section id="devices" class="py-20 bg-gradient-to-b from-gray-900 to-dark">
    <div class="container mx-auto px-4">
        <h2 class="text-3xl md:text-4xl font-bold text-center mb-16">Compatível Com Seus Dispositivos</h2>
        
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mb-12">
            <div class="text-center">
                <div class="device-icon w-20 h-20 bg-gray-800 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-tv text-3xl text-secondary"></i>
                </div>
                <h3 class="text-xl font-bold mb-2">Smart TV</h3>
                <p class="text-gray-400">Samsung, LG, Sony, etc.</p>
            </div>
            
            <div class="text-center">
                <div class="device-icon w-20 h-20 bg-gray-800 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fab fa-android text-3xl text-secondary"></i>
                </div>
                <h3 class="text-xl font-bold mb-2">TV Android</h3>
                <p class="text-gray-400">Qualquer TV com Android</p>
            </div>
            
            <div class="text-center">
                <div class="device-icon w-20 h-20 bg-gray-800 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-mobile-alt text-3xl text-secondary"></i>
                </div>
                <h3 class="text-xl font-bold mb-2">Celulares</h3>
                <p class="text-gray-400">Android e iOS</p>
            </div>
            
            <div class="text-center">
                <div class="device-icon w-20 h-20 bg-gray-800 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-tablet-alt text-3xl text-secondary"></i>
                </div>
                <h3 class="text-xl font-bold mb-2">Tablets</h3>
                <p class="text-gray-400">Android e iPad</p>
            </div>
            
            <div class="text-center">
                <div class="device-icon w-20 h-20 bg-gray-800 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-desktop text-3xl text-secondary"></i>
                </div>
                <h3 class="text-xl font-bold mb-2">Computadores</h3>
                <p class="text-gray-400">Windows, Mac, Linux</p>
            </div>
            
            <div class="text-center">
                <div class="device-icon w-20 h-20 bg-gray-800 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-laptop text-3xl text-secondary"></i>
                </div>
                <h3 class="text-xl font-bold mb-2">Notebooks</h3>
                <p class="text-gray-400">Qualquer marca</p>
            </div>
            
            <div class="text-center">
                <div class="device-icon w-20 h-20 bg-gray-800 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fab fa-xbox text-3xl text-secondary"></i>
                </div>
                <h3 class="text-xl font-bold mb-2">Xbox</h3>
                <p class="text-gray-400">Consoles Xbox</p>
            </div>
            
            <div class="text-center">
                <div class="device-icon w-20 h-20 bg-gray-800 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i class="fas fa-box text-3xl text-secondary"></i>
                </div>
                <h3 class="text-xl font-bold mb-2">TV Box</h3>
                <p class="text-gray-400">Qualquer TV Box</p>
            </div>
        </div>
        
        <div class="text-center">
            <a href="https://wa.me/5511911379757" target="_blank" class="inline-block bg-gray-800 hover:bg-gray-700 text-white font-bold py-3 px-6 rounded-lg transition-all">
                Verificar Compatibilidade <i class="fas fa-chevron-right ml-2"></i>
            </a>
        </div>
    </div>
</section>
<!-- Pricing -->
<section id="pricing" class="py-20 movie-background">
    <div class="container mx-auto px-4">
        <h2 class="text-3xl md:text-4xl font-bold text-center mb-6">Preço Imbatível</h2>
        <p class="text-xl text-center mb-16 max-w-3xl mx-auto">Acesso ilimitado a mais de 100.000 conteúdos por um valor acessível</p>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-4xl mx-auto">
            <!-- Plano Mensal -->
            <div class="card rounded-2xl p-8 border-2 border-secondary transform transition-all hover:scale-105">
                <div class="absolute -top-5 left-1/2 transform -translate-x-1/2 bg-secondary text-white px-6 py-2 rounded-full font-bold text-lg">
                    Mais Popular
                </div>
                <h3 class="text-2xl font-bold text-center mb-2 mt-4">Assinatura Mensal</h3>
                <div class="text-center mb-6">
                    <span class="text-5xl font-bold">R$ 24,99</span>
                    <span class="text-xl">/mês</span>
                </div>
                
                <ul class="space-y-4 mb-8">
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Mais de 100.000 conteúdos</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Canais ao vivo liberados</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Filmes em lançamento</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Séries completas</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Sem fidelidade</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Sem taxa de adesão</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Compatível com múltiplos dispositivos</span>
                    </li>
                    <li class="flex items-center text-secondary font-bold">
                        <i class="fas fa-gift text-secondary mr-3"></i>
                        <span>20% OFF nas renovações em dia (apenas R$19,99)</span>
                    </li>
                </ul>
                
                <div class="warning-badge w-full text-center mb-6">
                    <i class="fas fa-exclamation-circle mr-1"></i>Não oferecemos teste grátis!
                </div>
                
                <a href="https://wa.me/5511911379757" target="_blank" class="btn-pulse block w-full bg-secondary text-white text-center py-3 rounded-lg font-bold text-lg">
                    Assinar Agora <i class="fas fa-arrow-right ml-2"></i>
                </a>
            </div>
            
            <!-- Plano Trimestral -->
            <div class="card rounded-2xl p-8 border-3 border-primary transform transition-all hover:scale-105">
                <div class="absolute -top-5 left-1/2 transform -translate-x-1/2 bg-primary text-white px-6 py-2 rounded-full font-bold text-lg">
                    Melhor Custo-Benefício
                </div>
                <h3 class="text-2xl font-bold text-center mb-2 mt-4">Pacote Trimestral</h3>
                <div class="text-center mb-2">
                    <span class="text-5xl font-bold">R$ 69,99</span>
                    <span class="text-xl">/3 meses</span>
                </div>
                <div class="text-center mb-6">
                    <span class="text-lg text-green-500 font-bold">Economize R$ 5,98 por mês!</span>
                </div>
                
                <ul class="space-y-4 mb-8">
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Todos os benefícios do plano mensal</span>
                    </li>
                    <li class="flex items-center font-bold">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Valor equivalente a R$ 23,33/mês</span>
                    </li>
                    <li class="flex items-center font-bold">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Economia de 22% em relação ao plano mensal</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Prioridade no suporte técnico</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Sem preocupações com pagamentos mensais</span>
                    </li>
                    <li class="flex items-center">
                        <i class="fas fa-check-circle text-green-500 mr-3"></i>
                        <span>Proteção contra aumento de preços</span>
                    </li>
                    <li class="flex items-center text-secondary font-bold">
                        <i class="fas fa-gift text-secondary mr-3"></i>
                        <span>20% OFF nas renovações em dia (apenas R$55,99)</span>
                    </li>
                </ul>
                
                <a href="https://wa.me/5511911379757" target="_blank" class="btn-pulse block w-full bg-primary text-white text-center py-3 rounded-lg font-bold text-lg">
                    Economizar Agora <i class="fas fa-arrow-right ml-2"></i>
                </a>
            </div>
        </div>
    </div>
</section>
<!-- Contact form -->
<section id="contact" class="py-20 bg-gradient-to-b from-dark to-gray-900">
    <div class="container mx-auto px-4">
        <h2 class="text-3xl md:text-4xl font-bold text-center mb-6">Entre em Contato</h2>
        <p class="text-xl text-center mb-16 max-w-2xl mx-auto">Tem dúvidas ou precisa de ajuda? Preencha o formulário abaixo ou entre em contato pelo WhatsApp.</p>
        
        <div class="max-w-xl mx-auto">
            <form id="contact-form" class="space-y-6">
                <div>
                    <label for="name" class="block mb-2 font-medium">Nome</label>
                    <input type="text" id="name" name="name" required class="w-full bg-gray-800 border border-gray-700 rounded-lg py-3 px-4 text-base focus:outline-none focus:ring-2 focus:ring-secondary">
                </div>
                
                <div>
                    <label for="email" class="block mb-2 font-medium">Email</label>
                    <input type="email" id="email" name="email" required class="w-full bg-gray-800 border border-gray-700 rounded-lg py-3 px-4 text-base focus:outline-none focus:ring-2 focus:ring-secondary">
                </div>
                
                <div>
                    <label for="phone" class="block mb-2 font-medium">Telefone (opcional)</label>
                    <input type="tel" id="phone" name="phone" class="w-full bg-gray-800 border border-gray-700 rounded-lg py-3 px-4 text-base focus:outline-none focus:ring-2 focus:ring-secondary">
                </div>
                
                <div>
                    <label for="message" class="block mb-2 font-medium">Mensagem</label>
                    <textarea id="message" name="message" rows="4" required class="w-full bg-gray-800 border border-gray-700 rounded-lg py-3 px-4 text-base focus:outline-none focus:ring-2 focus:ring-secondary"></textarea>
                </div>
                
                <div class="flex justify-between items-center">
                    <button type="submit" class="bg-secondary text-white font-bold py-3 px-8 rounded-lg hover:bg-opacity-90 transition-all">
                        Enviar Mensagem
                    </button>
                    
                    <a href="https://wa.me/5511911379757" target="_blank" class="flex items-center text-white hover:text-secondary transition-colors">
                        <i class="fab fa-whatsapp text-2xl mr-2"></i> WhatsApp
                    </a>
                </div>
                
                <div id="form-status" class="text-center hidden"></div>
            </form>
        </div>
    </div>
</section>
<!-- Footer -->
<footer class="bg-gray-900 py-12">
    <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row justify-between items-center mb-8">
            <div class="mb-6 md:mb-0">
                <div class="logo text-3xl md:text-4xl font-bold text-white mb-4">
                    <span class="text-white">VIVA</span>
                    <span class="text-secondary">TV</span>
                </div>
                <p class="text-gray-400">Uma empresa do grupo Moura Tech Soluções em Tecnologia</p>
            </div>
            
            <div class="flex flex-col md:flex-row space-y-4 md:space-y-0 md:space-x-6">
                <a href="#benefits" class="text-gray-400 hover:text-white transition-colors">Benefícios</a>
                <a href="#devices" class="text-gray-400 hover:text-white transition-colors">Dispositivos</a>
                <a href="#pricing" class="text-gray-400 hover:text-white transition-colors">Preços</a>
                <a href="#contact" class="text-gray-400 hover:text-white transition-colors">Contato</a>
            </div>
        </div>
        
        <hr class="border-gray-800 mb-8">
        
        <div class="text-center text-gray-500 text-sm">
            <p>© 2023 VIVA TV. Todos os direitos reservados.</p>
            <p class="mt-2">Desenvolvido por Moura Tech Soluções em Tecnologia</p>
        </div>
    </div>
</footer>

<!-- FloatingWhatsApp Button -->
<a href="https://wa.me/5511911379757" target="_blank" class="floating-whatsapp bg-green-500 text-white p-4 rounded-full shadow-lg">
    <i class="fab fa-whatsapp text-2xl"></i>
</a>
<script>
    // Dark mode detection
    if (window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches) {
        document.documentElement.classList.add('dark');
    }
    
    window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', event => {
        if (event.matches) {
            document.documentElement.classList.add('dark');
        } else {
            document.documentElement.classList.remove('dark');
        }
    });
    
    // Contact form
    document.getElementById('contact-form').addEventListener('submit', function(e) {
        e.preventDefault();
        
        const formStatus = document.getElementById('form-status');
        formStatus.className = 'text-center mt-4';
        formStatus.innerHTML = '<p class="text-yellow-400"><i class="fas fa-spinner fa-spin mr-2"></i>Enviando mensagem...</p>';
        formStatus.classList.remove('hidden');
        
        const formData = {
            name: document.getElementById('name').value,
            email: document.getElementById('email').value,
            phone: document.getElementById('phone').value,
            message: document.getElementById('message').value,
            recipient: 'vivasortedan@gmail.com'
        };
        
        // Simulate form submission (in a real implementation, you'd send this to a server)
        setTimeout(() => {
            formStatus.innerHTML = '<p class="text-green-400"><i class="fas fa-check-circle mr-2"></i>Mensagem enviada com sucesso!</p>';
            document.getElementById('contact-form').reset();
            
            setTimeout(() => {
                formStatus.classList.add('hidden');
            }, 5000);
        }, 1500);
    });
    
    // Smooth scrolling for anchor links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function (e) {
            e.preventDefault();
            
            const targetId = this.getAttribute('href');
            if (targetId === '#') return;
            
            const targetElement = document.querySelector(targetId);
            if (targetElement) {
                window.scrollTo({
                    top: targetElement.offsetTop,
                    behavior: 'smooth'
                });
            }
        });
    });
</script>
</body>
</html>
