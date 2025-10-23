
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>ProShop — eCommerce Template</title>
  <meta name="description" content="Responsive professional eCommerce template (HTML, CSS, JavaScript) — product grid, cart, product modal, search & filtering">
  <style>
    :root{
      --bg:#0f1724; --card:#0b1220; --muted:#9aa4b2; --accent:#06b6d4; --glass: rgba(255,255,255,0.04);
      --radius:12px; --maxw:1200px; --gap:18px;
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{margin:0;background:linear-gradient(180deg,#07111a 0%, #08131a 100%);color:#e6eef6;display:flex;align-items:flex-start;justify-content:center;padding:28px}
    .container{width:100%;max-width:var(--maxw);}

    /* Header */
    header{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:22px}
    .brand{display:flex;align-items:center;gap:12px}
    .logo{width:46px;height:46px;border-radius:10px;background:linear-gradient(135deg,var(--accent),#7c3aed);display:flex;align-items:center;justify-content:center;font-weight:700}
    .brand h1{font-size:18px;margin:0}
    nav{display:flex;gap:12px;align-items:center}
    nav a{color:var(--muted);text-decoration:none;padding:8px 12px;border-radius:8px}
    nav a:hover{color:#fff;background:var(--glass)}

    /* Search & cart */
    .controls{display:flex;gap:12px;align-items:center}
    .search{display:flex;align-items:center;background:var(--glass);padding:8px;border-radius:10px;gap:8px}
    .search input{background:transparent;border:0;color:inherit;outline:none;width:220px}
    .cart-btn{position:relative;background:transparent;border:1px solid rgba(255,255,255,0.06);padding:8px 12px;border-radius:10px;cursor:pointer}
    .cart-badge{position:absolute;top:-6px;right:-6px;background:#ff6b6b;color:#100;min-width:20px;height:20px;border-radius:999px;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700}

    /* Layout */
    .hero{display:flex;align-items:center;justify-content:space-between;gap:18px;margin-bottom:22px}
    .hero-left{max-width:56%}
    .hero h2{margin:0;font-size:28px}
    .hero p{color:var(--muted);margin-top:8px}
    .hero-right img{width:260px;border-radius:16px;box-shadow:0 8px 30px rgba(0,0,0,0.6)}

    /* Grid */
    .toolbar{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
    .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:var(--gap)}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:14px;border-radius:var(--radius);border:1px solid rgba(255,255,255,0.03)}
    .card img{width:100%;height:140px;object-fit:cover;border-radius:10px}
    .card h3{margin:10px 0 6px;font-size:16px}
    .price-row{display:flex;align-items:center;justify-content:space-between}
    .price{font-weight:700}
    .add{background:var(--accent);color:#042; border:none;padding:8px 10px;border-radius:8px;cursor:pointer}

    /* Cart sidebar */
    .cart-panel{position:fixed;right:24px;top:80px;width:360px;max-width:90%;transform:translateX(110%);transition:transform .28s ease;background:linear-gradient(180deg,#09121a,#061016);border-radius:14px;padding:14px;border:1px solid rgba(255,255,255,0.04);box-shadow:0 12px 40px rgba(0,0,0,0.6)}
    .cart-panel.open{transform:translateX(0)}
    .cart-items{max-height:420px;overflow:auto;margin-top:8px}
    .cart-item{display:flex;gap:10px;align-items:center;padding:8px;border-radius:10px}
    .cart-item img{width:64px;height:48px;object-fit:cover;border-radius:8px}
    .cart-footer{display:flex;justify-content:space-between;align-items:center;margin-top:12px}
    .btn{background:transparent;border:1px solid rgba(255,255,255,0.06);padding:8px 12px;border-radius:8px;color:var(--muted);cursor:pointer}

    /* Modal */
    .modal{position:fixed;left:0;top:0;width:100%;height:100%;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,0.6);visibility:hidden;opacity:0;transition:opacity .18s ease}
    .modal.open{visibility:visible;opacity:1}
    .modal-card{background:linear-gradient(180deg,#07111a,#0b1620);padding:18px;border-radius:12px;max-width:900px;width:96%;display:flex;gap:18px}
    .modal-card img{width:320px;height:220px;object-fit:cover;border-radius:10px}

    /* Footer */
    footer{margin-top:30px;padding:18px;border-radius:12px;background:transparent;color:var(--muted);text-align:center}

    /* Responsive */
    @media (max-width:800px){
      .hero{flex-direction:column;align-items:flex-start}
      .hero-right img{width:100%}
      .hero-left{max-width:100%}
      nav{display:none}
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">PS</div>
        <div>
          <h1>ProShop</h1>
          <div style="font-size:12px;color:var(--muted)">Professional eCommerce Template</div>
        </div>
      </div>

      <nav>
        <a href="#">Home</a>
        <a href="#products">Products</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
      </nav>

      <div class="controls">
        <div class="search" role="search">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" aria-hidden><path d="M21 21l-4.35-4.35" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"></path><circle cx="11" cy="11" r="6" stroke="currentColor" stroke-width="1.6"></circle></svg>
          <input id="searchInput" placeholder="Search products..." aria-label="Search products">
        </div>
        <button class="cart-btn" id="cartToggle" aria-label="Open cart">Cart <span class="cart-badge" id="cartCount">0</span></button>
      </div>
    </header>

    <section class="hero">
      <div class="hero-left">
        <h2>Quality products. Clean UI. Fast checkout.</h2>
        <p>Modern, responsive eCommerce demo built with semantic HTML, sleek CSS, and vanilla JavaScript — perfect for portfolios and prototypes.</p>
      </div>
      <div class="hero-right"><img src="https://picsum.photos/seed/hero/600/400" alt="Hero product"></div>
    </section>

    <div class="toolbar">
      <div id="resultCount" style="color:var(--muted)">Showing <span id="ncount">0</span> products</div>
      <div style="display:flex;gap:8px;align-items:center">
        <select id="sort" class="btn">
          <option value="default">Sort: Popular</option>
          <option value="price-asc">Price: Low → High</option>
          <option value="price-desc">Price: High → Low</option>
        </select>
      </div>
    </div>

    <main id="products" class="grid" aria-live="polite"></main>

    <div id="noResults" style="display:none;color:var(--muted);margin-top:18px">No products found.</div>

    <footer id="about">
      <small>© <span id="year"></span> ProShop • Built with HTML, CSS & JavaScript</small>
    </footer>
  </div>

  <!-- Cart panel -->
  <aside class="cart-panel" id="cartPanel" aria-hidden="true">
    <h3>Cart</h3>
    <div class="cart-items" id="cartItems"></div>
    <div class="cart-footer">
      <div style="font-weight:700">Total: ₹<span id="cartTotal">0</span></div>
      <div style="display:flex;gap:8px">
        <button class="btn" id="clearCart">Clear</button>
        <button class="add" id="checkout">Checkout</button>
      </div>
    </div>
  </aside>

  <!-- Modal -->
  <div class="modal" id="modal">
    <div class="modal-card" role="dialog" aria-modal="true">
      <img id="modalImg" src="" alt="Product image">
      <div>
        <h3 id="modalTitle"></h3>
        <p id="modalDesc" style="color:var(--muted)"></p>
        <div style="margin-top:12px" class="price-row">
          <div style="font-size:18px" class="price">₹<span id="modalPrice"></span></div>
          <div>
            <button class="add" id="modalAdd">Add to cart</button>
            <button class="btn" id="modalClose">Close</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script>
    // Demo product data
    const products = [
      {id:1,title:'Wireless Headphones',price:2499,desc:'Comfortable over-ear wireless headphones with long battery life.',img:'https://picsum.photos/seed/p1/600/400'},
      {id:2,title:'Smartwatch Pro',price:4999,desc:'Feature-rich smartwatch with heart-rate monitoring and GPS.',img:'https://picsum.photos/seed/p2/600/400'},
      {id:3,title:'Minimal Lamp',price:899,desc:'Elegant desk lamp with adjustable brightness and touch control.',img:'https://picsum.photos/seed/p3/600/400'},
      {id:4,title:'Portable Speaker',price:1599,desc:'Compact Bluetooth speaker with rich bass and water resistance.',img:'https://picsum.photos/seed/p4/600/400'},
      {id:5,title:'Ergonomic Mouse',price:699,desc:'Precision optical mouse designed for comfortable long use.',img:'https://picsum.photos/seed/p5/600/400'},
      {id:6,title:'Backpack 20L',price:1299,desc:'Durable lightweight backpack suitable for daily commute and travel.',img:'https://picsum.photos/seed/p6/600/400'},
      {id:7,title:'Noise-cancel Earbuds',price:1999,desc:'True wireless earbuds with active noise cancellation.',img:'https://picsum.photos/seed/p7/600/400'},
      {id:8,title:'Fitness Band',price:799,desc:'Slim fitness band with sleep tracking and step counter.',img:'https://picsum.photos/seed/p8/600/400'}
    ];

    // App state
    let cart = JSON.parse(localStorage.getItem('proshop_cart') || '[]');

    const productsEl = document.getElementById('products');
    const ncount = document.getElementById('ncount');
    const cartCount = document.getElementById('cartCount');
    const cartPanel = document.getElementById('cartPanel');
    const cartItemsEl = document.getElementById('cartItems');
    const cartTotalEl = document.getElementById('cartTotal');
    const searchInput = document.getElementById('searchInput');
    const sortSelect = document.getElementById('sort');
    const noResults = document.getElementById('noResults');

    // Render products
    function renderProducts(list){
      productsEl.innerHTML = '';
      if(!list.length){ noResults.style.display='block'; ncount.textContent = 0; return }
      noResults.style.display='none';
      ncount.textContent = list.length;
      list.forEach(p=>{
        const card = document.createElement('article'); card.className='card';
        card.innerHTML = `
          <img loading="lazy" src="${p.img}" alt="${p.title}">
          <h3>${p.title}</h3>
          <div style="color:var(--muted);font-size:13px">${p.desc}</div>
          <div class="price-row" style="margin-top:8px">
            <div class="price">₹${p.price}</div>
            <div>
              <button class="btn" data-id="${p.id}" aria-label="View">View</button>
              <button class="add" data-add="${p.id}" aria-label="Add to cart">Add</button>
            </div>
          </div>
        `;
        productsEl.appendChild(card);
      })
    }

    // Initial render
    renderProducts(products);

    // Event delegation for product actions
    productsEl.addEventListener('click', e=>{
      const view = e.target.closest('button[aria-label="View"]');
      const add = e.target.closest('button[data-add]');
      if(view){
        const id = +view.dataset.id; openModal(products.find(x=>x.id===id));
      }
      if(add){
        const id = +add.dataset.add; addToCart(id); animateAdd(e.target);
      }
    })

    // Modal logic
    const modal = document.getElementById('modal');
    const modalImg = document.getElementById('modalImg');
    const modalTitle = document.getElementById('modalTitle');
    const modalDesc = document.getElementById('modalDesc');
    const modalPrice = document.getElementById('modalPrice');
    const modalAdd = document.getElementById('modalAdd');
    let activeProduct = null;

    function openModal(p){
      activeProduct = p;
      modalImg.src = p.img; modalTitle.textContent = p.title; modalDesc.textContent = p.desc; modalPrice.textContent = p.price;
      modal.classList.add('open');
    }
    document.getElementById('modalClose').addEventListener('click', ()=> modal.classList.remove('open'));
    modal.addEventListener('click', e=>{ if(e.target===modal) modal.classList.remove('open') });
    modalAdd.addEventListener('click', ()=>{ if(activeProduct) addToCart(activeProduct.id); modal.classList.remove('open') });

    // Cart functions
    function addToCart(id){
      const item = products.find(p=>p.id===id);
      const found = cart.find(c=>c.id===id);
      if(found){ found.qty +=1 } else { cart.push({id:item.id,title:item.title,price:item.price,img:item.img,qty:1}) }
      saveCart(); renderCart();
    }
    function saveCart(){ localStorage.setItem('proshop_cart', JSON.stringify(cart)); }
    function renderCart(){
      cartItemsEl.innerHTML = '';
      let total=0; let count=0;
      cart.forEach(ci=>{
        total += ci.price*ci.qty; count += ci.qty;
        const el = document.createElement('div'); el.className='cart-item';
        el.innerHTML = `<img src="${ci.img}" alt="${ci.title}"><div style="flex:1"><div style="font-weight:700">${ci.title}</div><div style="color:var(--muted);font-size:13px">₹${ci.price} × ${ci.qty}</div></div><div style="display:flex;flex-direction:column;gap:6px"><button class="btn" data-dec="${ci.id}">−</button><button class="add" data-inc="${ci.id}">+</button></div>`;
        cartItemsEl.appendChild(el);
      })
      cartCount.textContent = count;
      cartTotalEl.textContent = total.toFixed(0);
      // hide if empty
      cartItemsEl.style.display = cart.length ? 'block' : 'none';
    }

    // Cart controls
    cartItemsEl.addEventListener('click', e=>{
      const dec = e.target.closest('button[data-dec]');
      const inc = e.target.closest('button[data-inc]');
      if(dec){ const id=+dec.dataset.dec; changeQty(id, -1) }
      if(inc){ const id=+inc.dataset.inc; changeQty(id, +1) }
    })
    function changeQty(id, delta){ const it = cart.find(c=>c.id===id); if(!it) return; it.qty += delta; if(it.qty<1) cart = cart.filter(x=>x.id!==id); saveCart(); renderCart(); }

    document.getElementById('cartToggle').addEventListener('click', ()=>{ cartPanel.classList.toggle('open'); cartPanel.setAttribute('aria-hidden', cartPanel.classList.contains('open') ? 'false':'true') });
    document.getElementById('clearCart').addEventListener('click', ()=>{ cart=[]; saveCart(); renderCart(); });
    document.getElementById('checkout').addEventListener('click', ()=>{ if(!cart.length){ alert('Cart is empty') } else { alert('Checkout — demo only. Integrate payment gateway for production.') } });

    // Search & sort
    searchInput.addEventListener('input', ()=> applyFilters());
    sortSelect.addEventListener('change', ()=> applyFilters());

    function applyFilters(){
      const q = searchInput.value.trim().toLowerCase();
      let out = products.filter(p=> p.title.toLowerCase().includes(q) || p.desc.toLowerCase().includes(q));
      const s = sortSelect.value;
      if(s==='price-asc') out = out.sort((a,b)=>a.price-b.price);
      if(s==='price-desc') out = out.sort((a,b)=>b.price-a.price);
      renderProducts(out);
    }

    // little add-to-cart animation (subtle)
    function animateAdd(btn){
      btn.animate([{transform:'scale(1)'},{transform:'scale(.96)'},{transform:'scale(1)'}],{duration:180});
    }

    // init
    document.getElementById('year').textContent = new Date().getFullYear();
    renderCart();

    // accessibility: keyboard close modal
    document.addEventListener('keydown', e=>{
      if(e.key==='Escape'){ modal.classList.remove('open'); cartPanel.classList.remove('open') }
    });
  </script>
</body>
</html>
