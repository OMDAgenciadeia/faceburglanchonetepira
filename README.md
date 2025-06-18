<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Face Burg - Delivery 18h-1h</title>
    <base target="_self">
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/@preline/preline@2.0.0/dist/preline.min.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#FF6B00',
                        secondary: '#FFD700',
                        dark: '#1E1E1E',
                    }
                }
            }
        }
    </script>
    <style>
        .cart-item-enter {
            opacity: 0;
            transform: translateY(20px);
        }
        .cart-item-enter-active {
            opacity: 1;
            transform: translateY(0);
            transition: all 300ms ease-out;
        }
        .cart-item-exit {
            opacity: 1;
        }
        .cart-item-exit-active {
            opacity: 0;
            transform: translateY(20px);
            transition: all 300ms ease-in;
        }
        .menu-category {
            scroll-margin-top: 100px;
        }
    </style>
</head>
<body class="bg-gray-50 dark:bg-dark text-gray-800 dark:text-gray-200 transition-colors duration-300">
    <header class="sticky top-0 z-50 bg-white dark:bg-gray-900 shadow-md">
        <div class="container mx-auto px-4 py-3 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <i class="fas fa-hamburger text-2xl text-primary"></i>
                <h1 class="text-xl font-bold">FACE BURG</h1>
            </div>
            <div class="flex items-center space-x-4">
                <button id="cart-toggle" class="relative p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-800">
                    <i class="fas fa-shopping-cart text-xl"></i>
                    <span id="cart-count" class="absolute -top-1 -right-1 bg-primary text-white text-xs font-bold rounded-full h-5 w-5 flex items-center justify-center">0</span>
                </button>
                <button id="theme-toggle" class="p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-800">
                    <i class="fas fa-moon dark:hidden"></i>
                    <i class="fas fa-sun hidden dark:block"></i>
                </button>
            </div>
        </div>
        <div class="bg-primary text-white py-2 text-center">
            <p class="text-sm font-medium">Delivery das 18h às 1h | Segunda a Domingo</p>
        </div>
    </header>

    <main class="container mx-auto px-4 py-6">
        <div class="flex flex-col lg:flex-row gap-6">
            <!-- Menu Section -->
            <div class="lg:w-3/4">
                <div class="mb-8">
                    <h2 class="text-2xl font-bold mb-4 text-primary border-b pb-2">HAMBÚRGUERES</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="burgers">
                        <!-- Burgers will be inserted here by JS -->
                    </div>
                </div>

                <div class="mb-8 menu-category" id="adicionais">
                    <h2 class="text-2xl font-bold mb-4 text-primary border-b pb-2">ADICIONAIS</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="adicionais-items">
                        <!-- Additional items will be inserted here by JS -->
                    </div>
                </div>

                <div class="mb-8 menu-category" id="bebidas">
                    <h2 class="text-2xl font-bold mb-4 text-primary border-b pb-2">BEBIDAS</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="bebidas-items">
                        <!-- Drinks will be inserted here by JS -->
                    </div>
                </div>

                <div class="mb-8 menu-category" id="fries">
                    <h2 class="text-2xl font-bold mb-4 text-primary border-b pb-2">FRITAS</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="fries-items">
                        <!-- Fries will be inserted here by JS -->
                    </div>
                </div>

                <div class="mb-8 menu-category" id="acai">
                    <h2 class="text-2xl font-bold mb-4 text-primary border-b pb-2">AÇAÍ (COPOS E TIGELAS)</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="acai-items">
                        <!-- Açai items will be inserted here by JS -->
                    </div>
                </div>

                <div class="mb-8 menu-category" id="combos">
                    <h2 class="text-2xl font-bold mb-4 text-primary border-b pb-2">COMBOS</h2>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="combo-items">
                        <!-- Combos will be inserted here by JS -->
                    </div>
                </div>
            </div>

            <!-- Cart Sidebar -->
            <div class="lg:w-1/4">
                <div id="cart-sidebar" class="hidden lg:block fixed lg:sticky top-24 right-0 lg:right-auto w-full lg:w-auto lg:max-w-xs bg-white dark:bg-gray-800 shadow-lg rounded-lg p-4 h-[calc(100vh-150px)] overflow-y-auto transition-all duration-300 transform translate-x-full lg:translate-x-0">
                    <div class="flex justify-between items-center mb-4">
                        <h3 class="text-lg font-bold">Seu Pedido</h3>
                        <button id="close-cart" class="lg:hidden p-1 rounded-full hover:bg-gray-100 dark:hover:bg-gray-700">
                            <i class="fas fa-times"></i>
                        </button>
                    </div>
                    
                    <div id="cart-items" class="mb-4 space-y-3">
                        <!-- Cart items will be inserted here by JS -->
                        <div class="text-center py-8 text-gray-500" id="empty-cart-message">
                            <i class="fas fa-shopping-cart text-4xl mb-2"></i>
                            <p>Seu carrinho está vazio</p>
                        </div>
                    </div>
                    
                    <div class="border-t border-gray-200 dark:border-gray-700 pt-4">
                        <div class="flex justify-between font-bold mb-2">
                            <span>Total:</span>
                            <span id="cart-total">R$ 0,00</span>
                        </div>
                        
                        <div class="mb-4">
                            <label for="customer-name" class="block text-sm font-medium mb-1">Nome*</label>
                            <input type="text" id="customer-name" class="w-full px-3 py-2 border rounded-lg dark:bg-gray-700 dark:border-gray-600" placeholder="Seu nome completo">
                        </div>
                        
                        <div class="mb-4">
                            <label for="customer-address" class="block text-sm font-medium mb-1">Endereço*</label>
                            <textarea id="customer-address" rows="3" class="w-full px-3 py-2 border rounded-lg dark:bg-gray-700 dark:border-gray-600" placeholder="Endereço completo para entrega"></textarea>
                        </div>
                        
                        <button id="send-order" disabled class="w-full bg-gray-400 text-white py-3 rounded-lg font-bold transition-colors duration-300 flex items-center justify-center space-x-2">
                            <span>ENVIAR PEDIDO</span>
                            <i class="fas fa-whatsapp"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <script>
        // Menu Data
        const menuItems = {
            burgers: [
                { name: "SUPREMO", price: 31.00 },
                { name: "F-PICANHA", price: 35.00 },
                { name: "F-PICANHA DUPLO", price: 45.00 },
                { name: "F-ANGUS", price: 35.00 },
                { name: "F-ANGUS DUPLO", price: 45.00 },
                { name: "F-AMERICANO", price: 31.00 },
                { name: "F-AUSTRALIANO", price: 29.00 },
                { name: "F-SALADA", price: 17.00 },
                { name: "F-BACON", price: 26.00 },
                { name: "F-BURGUER", price: 16.00 },
                { name: "F-CALABRESA", price: 25.00 },
                { name: "F-EGG", price: 19.00 },
                { name: "F-EGG BACON", price: 27.00 },
                { name: "F-FILÉ", price: 31.00 },
                { name: "F-FRANGO", price: 25.00 },
                { name: "F-LOMBO", price: 24.00 },
                { name: "F-TUDO", price: 33.00 },
                { name: "FACEBURG", price: 29.00 },
                { name: "FRANBACON", price: 29.00 },
                { name: "MISTO QUENTE", price: 8.00 },
                { name: "VEGETARIANO", price: 27.00 }
            ],
            adicionais: [
                { name: "BACON ADICIONAL", price: 5.00 },
                { name: "BIFE ARTESANAL", price: 0.00 },
                { name: "HAMBÚRGUER 56G ADICIONAL", price: 2.50 },
                { name: "HAMBÚRGUER ARTESANAL 180G", price: 6.50 },
                { name: "HAMBÚRGUER DE PICANHA 90G ADICIONAL", price: 4.50 },
                { name: "CALABRESA ADICIONAL", price: 5.00 },
                { name: "CREME CHEDDAR ADICIONAL", price: 5.00 },
                { name: "FILÉ ADICIONAL", price: 8.00 },
                { name: "LOMBO ADICIONAL", price: 5.00 },
                { name: "FRANGO ADICIONAL", price: 6.00 },
                { name: "OVO ADICIONAL", price: 2.00 },
                { name: "PRESUNTO ADICIONAL", price: 2.50 },
                { name: "QUEIJO MUSSARELA ADICIONAL", price: 2.00 },
                { name: "SALSICHA ADICIONAL", price: 2.00 }
            ],
            bebidas: [
                { name: "REFRIGERANTE LATA (Coca-Cola)", price: 7.00 },
                { name: "REFRIGERANTE LATA (Fanta Laranja)", price: 7.00 },
                { name: "REFRIGERANTE LATA (Fanta Uva)", price: 7.00 },
                { name: "REFRIGERANTE LATA (Guaraná Antártica)", price: 7.00 },
                { name: "REFRIGERANTE LATA (Sprite)", price: 7.00 },
                { name: "COCA-COLA ZERO 350ML", price: 7.00 }
            ],
            fries: [
                { name: "FRITAS", price: 10.00 }
            ],
            acai: [
                { name: "FACE OREO", price: 24.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Bis)", price: 21.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Delícia)", price: 21.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Brasil)", price: 21.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Kids)", price: 21.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Ninho)", price: 21.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Ouro)", price: 21.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Tropical)", price: 21.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face dos Sonhos)", price: 22.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Especial)", price: 23.00 },
                { name: "COPO DE AÇAÍ MONTADO 500ML (Face Nutella)", price: 24.00 },
                { name: "TIGELA DE AÇAÍ CASADINHO 1L", price: 37.00 },
                { name: "TIGELA DE AÇAÍ TRADICIONAL 1L", price: 37.00 },
                { name: "TIGELA DE AÇAÍ CASADINHO 300ML", price: 18.00 },
                { name: "TIGELA DE AÇAÍ TRADICIONAL 300ML", price: 18.00 },
                { name: "TIGELA DE AÇAÍ CASADINHO 500ML", price: 21.00 },
                { name: "TIGELA DE AÇAÍ TRADICIONAL 500ML", price: 21.00 }
            ],
            combos: [
                { name: "FACE COMBO 1 AMERI", price: 26.00 },
                { name: "FACE COMBO 2 AUSTRA", price: 25.00 },
                { name: "FACE COMBO 4 BACON", price: 23.50 },
                { name: "COMBO F-CALABRESA", price: 27.50 },
                { name: "COMBO F-BACON", price: 27.50 },
                { name: "COMBO F-PICANHA C/ FRITAS", price: 34.99 },
                { name: "F-BACON + FRITAS + REFRI LATA", price: 30.00 }
            ]
        };

        // Cart State
        let cart = [];
        let cartVisible = false;

        // DOM Elements
        const cartSidebar = document.getElementById('cart-sidebar');
        const cartToggle = document.getElementById('cart-toggle');
        const closeCart = document.getElementById('close-cart');
        const cartItemsContainer = document.getElementById('cart-items');
        const emptyCartMessage = document.getElementById('empty-cart-message');
        const cartCount = document.getElementById('cart-count');
        const cartTotal = document.getElementById('cart-total');
        const sendOrderBtn = document.getElementById('send-order');
        const customerName = document.getElementById('customer-name');
        const customerAddress = document.getElementById('customer-address');
        const themeToggle = document.getElementById('theme-toggle');

        // Initialize the page
        document.addEventListener('DOMContentLoaded', () => {
            renderMenu();
            updateCart();
            setupEventListeners();
            checkThemePreference();
        });

        // Render menu items
        function renderMenu() {
            // Render burgers
            const burgersContainer = document.getElementById('burgers');
            menuItems.burgers.forEach(item => {
                burgersContainer.appendChild(createMenuItemCard(item));
            });

            // Render adicionais
            const adicionaisContainer = document.getElementById('adicionais-items');
            menuItems.adicionais.forEach(item => {
                adicionaisContainer.appendChild(createMenuItemCard(item));
            });

            // Render bebidas
            const bebidasContainer = document.getElementById('bebidas-items');
            menuItems.bebidas.forEach(item => {
                bebidasContainer.appendChild(createMenuItemCard(item));
            });

            // Render fries
            const friesContainer = document.getElementById('fries-items');
            menuItems.fries.forEach(item => {
                friesContainer.appendChild(createMenuItemCard(item));
            });

            // Render açaí
            const acaiContainer = document.getElementById('acai-items');
            menuItems.acai.forEach(item => {
                acaiContainer.appendChild(createMenuItemCard(item));
            });

            // Render combos
            const combosContainer = document.getElementById('combo-items');
            menuItems.combos.forEach(item => {
                combosContainer.appendChild(createMenuItemCard(item));
            });
        }

        // Create menu item card
        function createMenuItemCard(item) {
            const card = document.createElement('div');
            card.className = 'bg-white dark:bg-gray-800 rounded-lg shadow-md overflow-hidden hover:shadow-lg transition-shadow duration-300';
            
            card.innerHTML = `
                <div class="p-4">
                    <h3 class="font-bold text-lg mb-1">${item.name}</h3>
                    <div class="flex justify-between items-center">
                        <span class="text-primary font-bold">R$ ${item.price.toFixed(2).replace('.', ',')}</span>
                        <button class="add-to-cart bg-primary text-white px-3 py-1 rounded-full text-sm hover:bg-orange-700 transition-colors duration-300" data-name="${item.name}" data-price="${item.price}">
                            <i class="fas fa-plus mr-1"></i> Adicionar
                        </button>
                    </div>
                </div>
            `;
            
            return card;
        }

        // Setup event listeners
        function setupEventListeners() {
            // Cart toggle
            cartToggle.addEventListener('click', () => {
                cartVisible = !cartVisible;
                if (cartVisible) {
                    cartSidebar.classList.remove('hidden');
                    setTimeout(() => {
                        cartSidebar.classList.remove('translate-x-full');
                    }, 10);
                } else {
                    cartSidebar.classList.add('translate-x-full');
                    setTimeout(() => {
                        cartSidebar.classList.add('hidden');
                    }, 300);
                }
            });

            // Close cart on mobile
            closeCart.addEventListener('click', () => {
                cartVisible = false;
                cartSidebar.classList.add('translate-x-full');
                setTimeout(() => {
                    cartSidebar.classList.add('hidden');
                }, 300);
            });

            // Add to cart buttons
            document.addEventListener('click', (e) => {
                if (e.target.classList.contains('add-to-cart') || e.target.closest('.add-to-cart')) {
                    const button = e.target.classList.contains('add-to-cart') ? e.target : e.target.closest('.add-to-cart');
                    const name = button.dataset.name;
                    const price = parseFloat(button.dataset.price);
                    
                    addToCart(name, price);
                    
                    // Animation feedback
                    button.innerHTML = '<i class="fas fa-check mr-1"></i> Adicionado';
                    button.classList.remove('bg-primary', 'hover:bg-orange-700');
                    button.classList.add('bg-green-500', 'hover:bg-green-600');
                    
                    setTimeout(() => {
                        button.innerHTML = '<i class="fas fa-plus mr-1"></i> Adicionar';
                        button.classList.remove('bg-green-500', 'hover:bg-green-600');
                        button.classList.add('bg-primary', 'hover:bg-orange-700');
                    }, 1000);
                }
            });

            // Remove item from cart
            cartItemsContainer.addEventListener('click', (e) => {
                if (e.target.classList.contains('remove-item') || e.target.closest('.remove-item')) {
                    const button = e.target.classList.contains('remove-item') ? e.target : e.target.closest('.remove-item');
                    const index = parseInt(button.dataset.index);
                    removeFromCart(index);
                }
            });

            // Customer info validation
            [customerName, customerAddress].forEach(input => {
                input.addEventListener('input', validateOrderButton);
            });

            // Send order
            sendOrderBtn.addEventListener('click', sendOrder);

            // Theme toggle
            themeToggle.addEventListener('click', toggleTheme);
        }

        // Cart functions
        function addToCart(name, price) {
            const existingItem = cart.find(item => item.name === name);
            
            if (existingItem) {
                existingItem.quantity += 1;
            } else {
                cart.push({
                    name,
                    price,
                    quantity: 1
                });
            }
            
            updateCart();
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            updateCart();
        }

        function updateCart() {
            // Update cart items display
            cartItemsContainer.innerHTML = '';
            
            if (cart.length === 0) {
                emptyCartMessage.classList.remove('hidden');
            } else {
                emptyCartMessage.classList.add('hidden');
                
                cart.forEach((item, index) => {
                    const cartItem = document.createElement('div');
                    cartItem.className = 'flex justify-between items-center bg-gray-50 dark:bg-gray-700 p-3 rounded-lg';
                    
                    cartItem.innerHTML = `
                        <div>
                            <h4 class="font-medium">${item.name}</h4>
                            <div class="flex items-center mt-1">
                                <button class="remove-item text-xs text-red-500 hover:text-red-700 dark:hover:text-red-400" data-index="${index}">
                                    <i class="fas fa-trash mr-1"></i> Remover
                                </button>
                            </div>
                        </div>
                        <div class="text-right">
                            <div class="font-bold">R$ ${(item.price * item.quantity).toFixed(2).replace('.', ',')}</div>
                            <div class="text-sm text-gray-500 dark:text-gray-400">${item.quantity}x R$ ${item.price.toFixed(2).replace('.', ',')}</div>
                        </div>
                    `;
                    
                    cartItemsContainer.appendChild(cartItem);
                });
            }
            
            // Update cart count
            const totalItems = cart.reduce((sum, item) => sum + item.quantity, 0);
            cartCount.textContent = totalItems;
            
            // Update total
            const total = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);
            cartTotal.textContent = `R$ ${total.toFixed(2).replace('.', ',')}`;
            
            // Validate order button
            validateOrderButton();
        }

        function validateOrderButton() {
            const nameValid = customerName.value.trim().length > 0;
            const addressValid = customerAddress.value.trim().length > 0;
            const cartValid = cart.length > 0;
            
            if (nameValid && addressValid && cartValid) {
                sendOrderBtn.disabled = false;
                sendOrderBtn.classList.remove('bg-gray-400');
                sendOrderBtn.classList.add('bg-green-500', 'hover:bg-green-600');
            } else {
                sendOrderBtn.disabled = true;
                sendOrderBtn.classList.remove('bg-green-500', 'hover:bg-green-600');
                sendOrderBtn.classList.add('bg-gray-400');
            }
        }

        function sendOrder() {
            if (cart.length === 0) return;
            
            const name = customerName.value.trim();
            const address = customerAddress.value.trim();
            
            if (!name || !address) return;
            
            // Format WhatsApp message
            let message = `Olá, este é o meu pedido de hoje!\n\n`;
            message += `*NOME:* ${name}\n`;
            message += `*ENDEREÇO:* ${address}\n\n`;
            message += `*ITENS DO PEDIDO:*\n`;
            
            cart.forEach(item => {
                message += `- ${item.name} (${item.quantity}x) - R$ ${(item.price * item.quantity).toFixed(2).replace('.', ',')}\n`;
            });
            
            message += `\n*TOTAL:* R$ ${cart.reduce((sum, item) => sum + (item.price * item.quantity), 0).toFixed(2).replace('.', ',')}\n\n`;
            message += `*HORÁRIO:* ${new Date().toLocaleString('pt-BR')}`;
            
            // Encode for URL
            const encodedMessage = encodeURIComponent(message);
            const whatsappUrl = `https://wa.me/5538998722422?text=${encodedMessage}`;
            
            // Open WhatsApp
            window.open(whatsappUrl, '_blank');
            
            // Reset cart and form
            cart = [];
            customerName.value = '';
            customerAddress.value = '';
            updateCart();
            
            // Show success message
            alert('Pedido enviado com sucesso! Você será redirecionado para o WhatsApp.');
        }

        // Theme functions
        function checkThemePreference() {
            if (localStorage.getItem('theme') === 'dark' || (!localStorage.getItem('theme') && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
                document.documentElement.classList.add('dark');
            } else {
                document.documentElement.classList.remove('dark');
            }
        }

        function toggleTheme() {
            if (document.documentElement.classList.contains('dark')) {
                document.documentElement.classList.remove('dark');
                localStorage.setItem('theme', 'light');
            } else {
                document.documentElement.classList.add('dark');
                localStorage.setItem('theme', 'dark');
            }
        }
    </script>
</body>
</html>
