<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tienda de Ropa</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    /* Animación para el botón flotante */
    .whatsapp-float {
      position: fixed;
      bottom: 20px;
      right: 20px;
      background-color: #25D366;
      color: white;
      border-radius: 50%;
      width: 60px;
      height: 60px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 28px;
      box-shadow: 0px 4px 10px rgba(0,0,0,0.3);
      z-index: 1000;
      transition: transform 0.3s ease;
    }
    .whatsapp-float:hover {
      transform: scale(1.1);
      background-color: #20b358;
    }
  </style>
</head>
<body class="bg-gray-100 font-sans">

  <!-- Header -->
  <header class="bg-white shadow-md sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4 py-4 flex justify-between items-center">
      <h1 class="text-2xl font-bold text-gray-800">Mi Ropa</h1>
      <nav class="flex items-center space-x-6">
        <a href="#productos" class="text-gray-600 hover:text-black">Productos</a>
        <a href="#contacto" class="text-gray-600 hover:text-black">Contacto</a>
        <button id="cartBtn" class="relative">
          🛒
          <span id="cartCount" class="absolute -top-2 -right-2 bg-red-500 text-white text-xs font-bold px-2 py-0.5 rounded-full">0</span>
        </button>
      </nav>
    </div>
  </header>

  <!-- Hero -->
  <section class="bg-cover bg-center h-[70vh] flex items-center justify-center text-center text-white"
    style="background-image: url('https://images.unsplash.com/photo-1521334884684-d80222895322?auto=format&fit=crop&w=1350&q=80');">
    <div class="bg-black bg-opacity-50 p-8 rounded-xl">
      <h2 class="text-4xl font-bold mb-4">Nueva Colección 2025</h2>
      <p class="mb-6">Descubrí los estilos más frescos y modernos</p>
      <a href="#productos" class="bg-white text-black px-6 py-3 rounded-lg font-semibold hover:bg-gray-200">Ver Productos</a>
    </div>
  </section>

  <!-- Productos -->
  <section id="productos" class="max-w-6xl mx-auto px-4 py-12">
    <h2 class="text-3xl font-bold text-center mb-10">Nuestros Productos</h2>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8">

      <div class="bg-white rounded-xl shadow-lg overflow-hidden">
        <img src="https://images.unsplash.com/photo-1523381210434-271e8be1f52b?auto=format&fit=crop&w=800&q=80" alt="Campera Denim" class="w-full h-64 object-cover">
        <div class="p-4">
          <h3 class="font-bold text-lg">Campera Denim</h3>
          <p class="text-gray-600">$45.000</p>
          <button onclick="addToCart('Campera Denim', 45000)" class="mt-4 bg-black text-white px-4 py-2 rounded-lg w-full hover:bg-gray-800">Agregar al carrito</button>
        </div>
      </div>

      <div class="bg-white rounded-xl shadow-lg overflow-hidden">
        <img src="https://images.unsplash.com/photo-1520975918311-7ce48d7b99a0?auto=format&fit=crop&w=800&q=80" alt="Vestido Casual" class="w-full h-64 object-cover">
        <div class="p-4">
          <h3 class="font-bold text-lg">Vestido Casual</h3>
          <p class="text-gray-600">$38.000</p>
          <button onclick="addToCart('Vestido Casual', 38000)" class="mt-4 bg-black text-white px-4 py-2 rounded-lg w-full hover:bg-gray-800">Agregar al carrito</button>
        </div>
      </div>

      <div class="bg-white rounded-xl shadow-lg overflow-hidden">
        <img src="https://images.unsplash.com/photo-1512436991641-6745cdb1723f?auto=format&fit=crop&w=800&q=80" alt="Remera Oversize" class="w-full h-64 object-cover">
        <div class="p-4">
          <h3 class="font-bold text-lg">Remera Oversize</h3>
          <p class="text-gray-600">$25.000</p>
          <button onclick="addToCart('Remera Oversize', 25000)" class="mt-4 bg-black text-white px-4 py-2 rounded-lg w-full hover:bg-gray-800">Agregar al carrito</button>
        </div>
      </div>

    </div>
  </section>

  <!-- Modal Carrito -->
  <div id="cartModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
    <div class="bg-white rounded-xl shadow-lg max-w-md w-full p-6 relative">
      <h2 class="text-2xl font-bold mb-4">🛒 Carrito</h2>
      <ul id="cartItems" class="space-y-2"></ul>
      <p id="cartTotal" class="font-bold mt-4">Total: $0</p>

      <!-- Datos del cliente -->
      <div class="mt-4 space-y-2">
        <input id="clientName" type="text" placeholder="Tu Nombre" class="w-full p-2 border rounded">
        <input id="clientAddress" type="text" placeholder="Tu Dirección" class="w-full p-2 border rounded">
      </div>

      <button onclick="checkout()" class="bg-green-600 text-white px-4 py-2 rounded-lg mt-4 w-full hover:bg-green-700">
        Finalizar compra por WhatsApp
      </button>
      <button onclick="closeCart()" class="absolute top-3 right-3 text-gray-600 hover:text-black">✖</button>
    </div>
  </div>

  <!-- Contacto -->
  <section id="contacto" class="bg-black text-white py-12">
    <div class="max-w-4xl mx-auto px-4 text-center">
      <h2 class="text-3xl font-bold mb-6">Contáctanos</h2>
      <p class="mb-4">¿Querés saber más? Envianos un mensaje</p>
      <form class="grid gap-4">
        <input type="text" placeholder="Tu Nombre" class="p-3 rounded-lg text-black">
        <input type="email" placeholder="Tu Email" class="p-3 rounded-lg text-black">
        <textarea placeholder="Tu Mensaje" class="p-3 rounded-lg text-black"></textarea>
        <button class="bg-white text-black px-6 py-3 rounded-lg font-semibold hover:bg-gray-200">Enviar</button>
      </form>
    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-gray-900 text-white py-6 text-center">
    <p>© 2025 Mi Ropa - Todos los derechos reservados</p>
  </footer>

  <!-- Botón flotante de WhatsApp -->
  <a id="whatsappBtn" href="#" target="_blank" class="whatsapp-float">💬</a>

  <!-- JS Carrito -->
  <script>
    let cart = [];
    const phoneNumber = "5492324562513"; 

    function addToCart(product, price) {
      cart.push({ product, price });
      updateCart();
    }

    function updateCart() {
      document.getElementById("cartCount").textContent = cart.length;
      const cartItems = document.getElementById("cartItems");
      cartItems.innerHTML = "";
      let total = 0;
      cart.forEach((item, index) => {
        total += item.price;
        cartItems.innerHTML += `
          <li class="flex justify-between">
            <span>${item.product} - $${item.price}</span>
            <button onclick="removeFromCart(${index})" class="text-red-600">Eliminar</button>
          </li>`;
      });
      document.getElementById("cartTotal").textContent = "Total: $" + total;
    }

    function removeFromCart(index) {
      cart.splice(index, 1);
      updateCart();
    }

    function checkout() {
      if(cart.length === 0){
        alert("Tu carrito está vacío 🛒");
        return;
      }

      const name = document.getElementById("clientName").value.trim();
      const address = document.getElementById("clientAddress").value.trim();

      if(name === "" || address === ""){
        alert("Por favor, completá tu nombre y dirección 📦");
        return;
      }

      let mensaje = `Hola! Quiero hacer un pedido:%0A`;
      cart.forEach(item => {
        mensaje += `- ${item.product} - $${item.price}%0A`;
      });
      const total = cart.reduce((sum, item) => sum + item.price, 0);
      mensaje += `%0ATotal: $${total}%0A%0A📌 Datos del cliente:%0ANombre: ${name}%0ADirección: ${address}`;

      window.open(`https://wa.me/${phoneNumber}?text=${mensaje}`, "_blank");
    }

    document.getElementById("cartBtn").addEventListener("click", () => {
      document.getElementById("cartModal").classList.remove("hidden");
    });

    function closeCart() {
      document.getElementById("cartModal").classList.add("hidden");
    }

    // Botón flotante (WhatsApp directo)
    document.getElementById("whatsappBtn").href = `https://wa.me/${phoneNumber}?text=Hola! Quiero más información sobre la tienda 👕`;
  </script>

</body>
</html>
