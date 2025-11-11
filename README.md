#<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Tazamall – Shop by Reagan Omondi</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: #f5f5f5;
      color: #333;
    }

    header {
      background: white;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      padding: 0.8rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 100;
    }

    .logo {
      font-size: 1.8rem;
      font-weight: bold;
      color: #e74c3c;
    }

    .search-bar {
      flex: 1;
      margin: 0 2rem;
    }

    .search-bar input {
      width: 100%;
      padding: 0.6rem 1rem;
      border: 1px solid #ddd;
      border-radius: 20px;
      font-size: 1rem;
    }

    .cart-icon {
      font-size: 1.6rem;
      color: #2c3e50;
      position: relative;
      cursor: pointer;
    }

    .cart-count {
      position: absolute;
      top: -8px;
      right: -8px;
      background: #e74c3c;
      color: white;
      border-radius: 50%;
      width: 18px;
      height: 18px;
      font-size: 0.7rem;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* Cart Sidebar */
    #cart-sidebar {
      position: fixed;
      top: 0;
      right: -400px;
      width: 380px;
      height: 100vh;
      background: white;
      box-shadow: -2px 0 15px rgba(0,0,0,0.1);
      z-index: 1000;
      transition: right 0.3s ease;
      padding: 1.5rem;
      overflow-y: auto;
    }

    #cart-sidebar.open {
      right: 0;
    }

    .close-cart {
      text-align: right;
      margin-bottom: 1rem;
      font-size: 1.5rem;
      cursor: pointer;
      color: #7f8c8d;
    }

    .cart-item {
      display: flex;
      justify-content: space-between;
      padding: 0.8rem 0;
      border-bottom: 1px solid #eee;
    }

    .cart-item-name {
      font-weight: bold;
    }

    .remove-btn {
      color: #e74c3c;
      background: none;
      border: none;
      cursor: pointer;
      font-weight: bold;
      font-size: 1.2rem;
    }

    .cart-total {
      font-size: 1.4rem;
      font-weight: bold;
      margin: 1.5rem 0;
      color: #2c3e50;
      text-align: right;
    }

    .checkout-btn {
      width: 100%;
      padding: 0.8rem;
      background: #2ecc71;
      color: white;
      border: none;
      border-radius: 6px;
      font-size: 1.1rem;
      font-weight: bold;
      cursor: pointer;
      margin-top: 1rem;
    }

    .checkout-btn:hover {
      background: #27ae60;
    }

    .categories {
      background: white;
      padding: 0.8rem 2rem;
      overflow-x: auto;
      white-space: nowrap;
      border-bottom: 1px solid #eee;
    }

    .category {
      display: inline-block;
      padding: 0.5rem 1rem;
      margin-right: 1rem;
      background: #f8f9fa;
      border-radius: 8px;
      cursor: pointer;
      color: #2c3e50;
    }

    .category:hover {
      background: #e74c3c;
      color: white;
    }

    .hero {
      background: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('https://images.unsplash.com/photo-1523275335684-37898b6baf30?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80') center/cover;
      height: 250px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 2rem;
      font-weight: bold;
      margin: 1rem 0;
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 1.2rem;
    }

    .section-title {
      font-size: 1.5rem;
      margin: 1.5rem 0 1rem;
      color: #2c3e50;
      padding-left: 0.5rem;
      border-left: 4px solid #e74c3c;
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
      gap: 1.2rem;
      margin-bottom: 2rem;
    }

    .product-card {
      background: white;
      border-radius: 10px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.08);
      overflow: hidden;
      transition: transform 0.2s;
    }

    .product-card:hover {
      transform: scale(1.02);
    }

    .product-image {
      width: 100%;
      height: 160px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #f9f9f9;
    }

    .product-image img {
      width: 80%;
      height: auto;
      object-fit: contain;
    }

    .product-info {
      padding: 0.8rem;
    }

    .product-title {
      font-size: 0.95rem;
      margin-bottom: 0.4rem;
      color: #2c3e50;
    }

    .product-price {
      font-weight: bold;
      color: #e74c3c;
      font-size: 1rem;
    }

    .add-to-cart-btn {
      width: 100%;
      margin-top: 0.5rem;
      padding: 0.4rem;
      background: #3498db;
      color: white;
      border: none;
      border-radius: 4px;
      font-size: 0.85rem;
      cursor: pointer;
    }

    .add-to-cart-btn:hover {
      background: #2980b9;
    }

    .creator-tag {
      display: flex;
      align-items: center;
      margin-top: 0.6rem;
      font-size: 0.75rem;
      color: #7f8c8d;
    }

    .creator-photo {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      object-fit: cover;
      margin-right: 5px;
      border: 1px solid #3498db;
    }

    footer {
      text-align: center;
      padding: 2rem;
      color: #7f8c8d;
      font-size: 0.9rem;
      border-top: 1px solid #eee;
      margin-top: 2rem;
    }

    @media (max-width: 768px) {
      .logo { font-size: 1.4rem; }
      .search-bar { margin: 0 0.8rem; }
      .hero { height: 180px; font-size: 1.5rem; }
      .products-grid { grid-template-columns: repeat(auto-fill, minmax(140px, 1fr)); }
      #cart-sidebar { width: 300px; }
    }
  </style>
</head>
<body>

  <header>
    <div class="logo">Tazamall</div>
    <div class="search-bar">
      <input type="text" placeholder="Search for fashion, electronics, home...">
    </div>
    <div class="cart-icon" onclick="openCart()">🛒 <span id="cart-count" class="cart-count">0</span></div>
  </header>

  <!-- Cart Sidebar -->
  <div id="cart-sidebar">
    <div class="close-cart" onclick="closeCart()">✕</div>
    <h2>Your Shopping Cart</h2>
    <div id="cart-items">
      <p id="cart-empty">Your cart is empty.</p>
    </div>
    <div class="cart-total">Total: $<span id="cart-total">0.00</span></div>

    <!-- REAL PAYPAL CHECKOUT -->
    <form id="paypal-form" action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_top">
      <input type="hidden" name="cmd" value="_cart">
      <input type="hidden" name="upload" value="1">
      <!-- 🔄 REPLACE THE EMAIL BELOW WITH YOUR PAYPAL BUSINESS EMAIL -->
      <input type="hidden" name="business" value="your-paypal-email@example.com">
      <input type="hidden" name="currency_code" value="USD">
      <input type="hidden" name="return" value="https://yourwebsite.com/success.html">
      <input type="hidden" name="cancel_return" value="https://yourwebsite.com/cancel.html">
      <div id="paypal-items"></div>
      <button type="submit" class="checkout-btn">✅ Pay with PayPal</button>
    </form>
    <p style="font-size:0.8rem;color:#7f8c8d;margin-top:10px;">
      Secure checkout • PayPal protects your info
    </p>
  </div>

  <!-- Categories -->
  <div class="categories">
    <div class="category">All</div>
    <div class="category">Fashion</div>
    <div class="category">Electronics</div>
    <div class="category">Home & Kitchen</div>
    <div class="category">Beauty</div>
    <div class="category">Accessories</div>
  </div>

  <div class="hero">
    Welcome to Tazamall – Curated by Reagan Omondi
  </div>

  <div class="container">

    <h2 class="section-title">👗 Fashion</h2>
    <div class="products-grid" id="fashion"></div>

    <h2 class="section-title">📱 Electronics</h2>
    <div class="products-grid" id="electronics"></div>

    <h2 class="section-title">🏠 Home & Kitchen</h2>
    <div class="products-grid" id="home"></div>

    <h2 class="section-title">💄 Beauty</h2>
    <div class="products-grid" id="beauty"></div>

  </div>

  <footer>
    <p>&copy; 2025 Tazamall – Every product proudly created and curated by <strong>Reagan Omondi</strong></p>
    <p style="margin-top:8px;font-size:0.85rem;">Based in Kenya • Worldwide Shipping</p>
  </footer>

  <script>
    // ✅ ALL PRODUCTS – 12 ITEMS ACROSS CATEGORIES
    const products = {
      fashion: [
        { id: 1, name: "Graphic Cotton T-Shirt", price: 19.99, img: "https://images.unsplash.com/photo-1521572163474-6864f9cf17ab?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" },
        { id: 2, name: "Denim Jacket", price: 45.00, img: "https://images.unsplash.com/photo-1591047139829-d91aecb6caea?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" },
        { id: 3, name: "Casual Sneakers", price: 52.99, img: "https://images.unsplash.com/photo-1549298916-b41d501d3772?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" },
        { id: 4, name: "Summer Dress", price: 38.50, img: "https://images.unsplash.com/photo-1525507119028-ed4c629a60a3?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" },
         
      ],
      electronics: [
        { id: 5, name: "Wireless Earbuds", price: 29.99, img: "https://images.unsplash.com/photo-1572569511254-d8f925fe2cbb?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" },
        { id: 6, name: "Smart Watch", price: 79.99, img: "smart.jpeg" },
        { id: 7, name: "Phone Stand", price: 12.50, img: "https://images.unsplash.com/photo-1609821868300-73c47602a926?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" },
        { id: 8, name: "LED Desk Lamp", price: 24.99, img: "https://images.unsplash.com/photo-1593696140880-40b3e4f3a4a5?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" }
      ],
      home: [
        { id: 9, name: "Ceramic Coffee Mug", price: 14.99, img: "https://images.unsplash.com/photo-1578985545062-69928b1d9587?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" },
        { id: 10, name: "Scented Candle Set", price: 18.75, img: "https://images.unsplash.com/photo-1607083551265-e9a1625c5a90?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" }
      ],
      beauty: [
        { id: 11, name: "Natural Face Serum", price: 22.00, img: "https://images.unsplash.com/photo-1595341888016-a392ef81b7de?ixlib=rb-4.0.3&auto=format&fit=crop&w=150&h=150&q=80" },
        { id: 12, name: "Organic Lip Balm", price: 8.99, img: "lip.jpg" }
        
      ]
    };

    let cart = [];

    // Render all sections
    function renderProducts() {
      Object.keys(products).forEach(section => {
        const container = document.getElementById(section);
        if (!container) return;
        container.innerHTML = products[section].map(p => `
          <div class="product-card">
            <div class="product-image">
              <img src="${p.img}" alt="${p.name}" loading="lazy">
            </div>
            <div class="product-info">
              <div class="product-title">${p.name}</div>
              <div class="product-price">$${p.price.toFixed(2)}</div>
              <button class="add-to-cart-btn" onclick="addToCart(${p.id}, '${p.name.replace(/'/g, "\\'")}', ${p.price})">Add to Cart</button>
              <div class="creator-tag">
                <img src="reagan.jpg" class="creator-photo" 
                     onerror="this.src='https://ui-avatars.com/api/?name=Reagan+Omondi&background=3498db&color=fff&size=24'">
                Reagan Omondi
              </div>
            </div>
          </div>
        `).join('');
      });
    }

    // Cart Functions
    function addToCart(id, name, price) {
      cart.push({ id, name, price });
      updateCart();
    }

    function removeFromCart(index) {
      cart.splice(index, 1);
      updateCart();
    }

    function updateCart() {
      const countEl = document.getElementById('cart-count');
      const totalEl = document.getElementById('cart-total');
      const itemsEl = document.getElementById('cart-items');
      const emptyEl = document.getElementById('cart-empty');
      const paypalItems = document.getElementById('paypal-items');

      countEl.textContent = cart.length;
      const total = cart.reduce((sum, item) => sum + item.price, 0);
      totalEl.textContent = total.toFixed(2);

      if (cart.length === 0) {
        emptyEl.style.display = 'block';
        itemsEl.innerHTML = '';
        paypalItems.innerHTML = '';
      } else {
        emptyEl.style.display = 'none';
        itemsEl.innerHTML = cart.map((item, i) => `
          <div class="cart-item">
            <div>
              <div class="cart-item-name">${item.name}</div>
              <div>$${item.price.toFixed(2)}</div>
            </div>
            <button class="remove-btn" onclick="removeFromCart(${i})">×</button>
          </div>
        `).join('');

        paypalItems.innerHTML = cart.map((item, i) => 
          `<input type="hidden" name="item_name_${i+1}" value="${item.name}">
           <input type="hidden" name="amount_${i+1}" value="${item.price.toFixed(2)}">
           <input type="hidden" name="quantity_${i+1}" value="1">`
        ).join('');
      }
    }

    // Cart UI
    function openCart() {
      document.getElementById('cart-sidebar').classList.add('open');
    }

    function closeCart() {
      document.getElementById('cart-sidebar').classList.remove('open');
    }

    // Initialize
    renderProducts();
    updateCart();
  </script>
</body>
</html> Tazamall-
A shopping website 
