# newecommerce<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>JKS All-In-One Grocery & Food Ordering</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f8ff;
      margin: 0; padding: 0;
      color: #1a458b;
    }
    header, nav, main, footer {
      padding: 10px 20px;
    }
    header {
      background: #87ceeb;
      color: white;
      font-size: 24px;
      font-weight: bold;
      text-align: center;
    }
    nav {
      background: #d3ecff;
      display: flex;
      gap: 15px;
      justify-content: center;
    }
    nav button {
      background: #3498db;
      border: none;
      color: white;
      padding: 10px 15px;
      cursor: pointer;
      border-radius: 4px;
      font-weight: 600;
    }
    nav button:hover {
      background: #2471a3;
    }
    .grid-images {
      display: grid;
      grid-template-columns: repeat(auto-fill,minmax(150px,1fr));
      gap: 15px;
      margin-top: 15px;
      border-radius: 6px;
    }
    .grid-images img {
      width: 100%;
      height: 100px;
      object-fit: cover;
      border-radius: 6px;
    }
    .folder-section {
      margin-top: 20px;
      text-align: center;
    }
    .category-list {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      justify-content: center;
      margin-top: 8px;
    }
    .category-list button {
      padding: 10px 12px;
      border: 1.5px solid #3498db;
      color: #3498db;
      background: white;
      cursor: pointer;
      border-radius: 4px;
      font-weight: 600;
      user-select: none;
      transition: background-color 0.3s, color 0.3s;
    }
    .category-list button.active {
      background: #3498db;
      color: white;
    }
    form {
      margin-top: 20px;
      max-width: 400px;
      margin-left: auto;
      margin-right: auto;
    }
    form label {
      display: block;
      margin-top: 10px;
      font-weight: bold;
      color: #1a458b;
    }
    form input, form textarea {
      width: 100%;
      padding: 8px;
      margin-top: 4px;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }
    form textarea {
      resize: vertical;
      min-height: 60px;
    }
    form button {
      margin-top: 15px;
      padding: 12px 15px;
      background: #3498db;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 4px;
      font-weight: bold;
      font-size: 16px;
      width: 100%;
    }
    form button:hover {
      background: #2471a3;
    }
    .error-message {
      color: red;
      display: none;
      margin-top: 4px;
      font-size: 12px;
    }
    footer {
      background: #87ceeb;
      color: white;
      text-align: center;
      padding: 10px 20px;
      margin-top: 40px;
      font-weight: 600;
      font-size: 14px;
    }
    /* Camera video styling */
    #camera video {
      width: 100%;
      max-width: 400px;
      height: auto;
      border-radius: 6px;
      background: black;
      margin-bottom: 10px;
    }
    #camera-controls {
      text-align: center;
      margin-bottom: 20px;
    }
    #camera-controls button {
      margin: 6px 8px;
      padding: 10px 18px;
      font-weight: bold;
      border-radius: 6px;
      border: none;
      background-color: #3498db;
      color: white;
      cursor: pointer;
    }
    #camera-controls button:hover {
      background-color: #2471a3;
    }
    /* Google Maps */
    #map {
      width: 100%;
      height: 400px;
      border-radius: 6px;
    }
  </style>
</head>
<body>
<header>JKS Online Grocery & Food Ordering</header>
<nav>
  <button onclick="showPage('home')">Home</button>
  <button onclick="showPage('camera')">Camera</button>
  <button onclick="showPage('maps')">Google Maps</button>
  <button onclick="showPage('orders')">Orders</button>
</nav>

<main id="contentArea">
  <!-- Home page -->
  <section id="home" class="page">
    <h1>Welcome to JKS Online Grocery & Food</h1>
    <p>Explore our categories and place your order via WhatsApp.</p>
    <div class="grid-images">
      <img src="https://source.unsplash.com/150x100/?groceries" alt="Grocery" />
      <img src="https://source.unsplash.com/150x100/?fruits" alt="Fruits" />
      <img src="https://source.unsplash.com/150x100/?vegetables" alt="Vegetables" />
      <img src="https://source.unsplash.com/150x100/?milk" alt="Milk" />
      <img src="https://source.unsplash.com/150x100/?meat" alt="Meat" />
      <img src="https://source.unsplash.com/150x100/?pizza" alt="Pizza" />
      <img src="https://source.unsplash.com/150x100/?ice-cream" alt="Ice Cream" />
      <img src="https://source.unsplash.com/150x100/?tiffin" alt="Tiffin" />
      <img src="https://source.unsplash.com/150x100/?flowers" alt="Flowers" />
      <img src="https://source.unsplash.com/150x100/?medicine" alt="Medicine" />
    </div>
    <div class="folder-section">
      <h2>Folders:</h2>
      <button onclick="openFolder('groceries')">Groceries</button>
      <button onclick="openFolder('food')">Food</button>
      <button onclick="openFolder('pharmacy')">Pharmacy</button>
    </div>
  </section>

  <!-- Groceries page -->
  <section id="groceries" class="page" style="display:none;">
    <h2>Groceries</h2>
    <div class="category-list">
      <button onclick="selectGroceriesCategory('milk')">Milk</button>
      <button onclick="selectGroceriesCategory('meat')">Meat</button>
      <button onclick="selectGroceriesCategory('fruits')">Fruits</button>
      <button onclick="selectGroceriesCategory('vegetables')">Vegetables</button>
      <button onclick="selectGroceriesCategory('flowers')">Flowers</button>
      <button onclick="selectGroceriesCategory('others')">Others</button>
    </div>
    <div id="groceries-category-content"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Food page -->
  <section id="food" class="page" style="display:none;">
    <h2>Food</h2>
    <div class="category-list">
      <button onclick="selectFoodCategory('biriyani')">Biriyani</button>
      <button onclick="selectFoodCategory('tiffins')">Tiffins</button>
      <button onclick="selectFoodCategory('icecream')">Ice Cream</button>
      <button onclick="selectFoodCategory('pizza')">Pizza</button>
      <button onclick="selectFoodCategory('burgers')">Burgers</button>
      <button onclick="selectFoodCategory('rolls')">Rolls</button>
    </div>
    <div id="food-category-content"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Pharmacy page -->
  <section id="pharmacy" class="page" style="display:none;">
    <h2>Pharmacy</h2>
    <div id="pharmacy-content"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Camera page -->
  <section id="camera" class="page" style="display:none;">
    <h2>Camera</h2>
    <div id="camera-controls">
      <button onclick="switchCamera()">Switch Camera</button>
      <button onclick="capturePhoto()">Capture Photo</button>
    </div>
    <video id="video" autoplay muted playsinline></video>
    <canvas id="canvas" style="display:none;"></canvas>
    <div id="capturedPhotoContainer" style="text-align:center; margin-top:10px;"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Maps page -->
  <section id="maps" class="page" style="display:none;">
    <h2>Google Maps</h2>
    <div id="map"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Orders page -->
  <section id="orders" class="page" style="display:none;">
    <h2>Your Orders</h2>
    <p>No orders yet.</p>
    <button onclick="showPage('home')">Back to Home</button>
  </section>
</main>

<footer>
  Contact us: <a href="tel:+918977143043">+91 89771 43043</a> | WhatsApp: <a href="https://wa.me/918977143043" target="_blank">+91 89771 43043</a>
</footer>

<script>
  function showPage(pageId) {
    document.querySelectorAll('.page').forEach(p => p.style.display = 'none');
    document.getElementById(pageId).style.display = 'block';

    if (pageId === 'camera') {
      startCamera();
    }
    if (pageId === 'maps') {
      if (!window.mapInitialized) {
        initMap();
        window.mapInitialized = true;
      }
    }
  }

  // --- Groceries, Food, Pharmacy Data and Functions ---
  const groceriesCategories = {
    milk: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?milk,${i}`) },
    meat: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?meat,${i}`) },
    fruits: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?fruit,${i}`) },
    vegetables: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?vegetable,${i}`) },
    flowers: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?flower,${i}`) },
    others: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?grocery,${i}`) }
  };

  const foodCategories = {
    biriyani: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?biriyani,${i}`) },
    tiffins: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?tiffin,${i}`) },
    icecream: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?icecream,${i}`) },
    pizza: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?pizza,${i}`) },
    burgers: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?burger,${i}`) },
    rolls: { images: [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?roll,${i}`) }
  };

  const pharmacyImages = [...Array(10).keys()].map(i => `https://source.unsplash.com/300x200/?pharmacy,${i}`);

  function clearContent(id) {
    document.getElementById(id).innerHTML = '';
  }

  function openFolder(folderName) {
    showPage(folderName);
    clearCategoryContent(folderName);
    if (folderName === 'groceries') loadGroceriesCategory('milk');
    if (folderName === 'food') loadFoodCategory('biriyani');
    if (folderName === 'pharmacy') loadPharmacy();
  }

  function clearCategoryContent(folderName) {
    if (folderName === 'groceries') clearContent('groceries-category-content');
    if (folderName === 'food') clearContent('food-category-content');
    if (folderName === 'pharmacy') clearContent('pharmacy-content');
  }

  function loadGroceriesCategory(category) {
    const content = document.getElementById('groceries-category-content');
    content.innerHTML = '';
    if (!groceriesCategories[category]) return;

    content.appendChild(renderImages(groceriesCategories[category].images));
    content.appendChild(createOrderForm(category));
  }

  function loadFoodCategory(category) {
    const content = document.getElementById('food-category-content');
    content.innerHTML = '';
    if (!foodCategories[category]) return;

    content.appendChild(renderImages(foodCategories[category].images));
    content.appendChild(createOrderForm(category));
  }

  function loadPharmacy() {
    const content = document.getElementById('pharmacy-content');
    content.innerHTML = '';
    content.appendChild(renderImages(pharmacyImages));
    content.appendChild(createOrderForm('Pharmacy'));
  }

  function renderImages(images) {
    const grid = document.createElement('div');
    grid.className = 'grid-images';
    images.forEach(src => {
      let img = document.createElement('img');
      img.src = src;
      grid.appendChild(img);
    });
    return grid;
  }

  function createOrderForm(category) {
    const form = document.createElement('form');
    form.onsubmit = e => {
      e.preventDefault();
      submitOrder(form, category);
    };
    form.innerHTML = `
      <label>Name:</label>
      <input type="text" name="name" required />
      <label>Mobile Number:</label>
      <input type="tel" name="phone" maxlength="10" pattern="[6-9][0-9]{9}" required />
      <span class="error-message">Enter valid 10-digit number starting with 6-9</span>
      <label>Order Item:</label>
      <textarea name="orderItem" rows="3" required></textarea>
      <label>Delivery Address:</label>
      <textarea name="deliveryAddress" rows="3" required></textarea>
      <button type="submit">Place Order via WhatsApp</button>
    `;
    // Validation message logic
    const phoneInput = form.querySelector('input[name="phone"]');
    const errorMessage = form.querySelector('.error-message');
    phoneInput.addEventListener('input', () => {
      errorMessage.style.display = phoneInput.validity.patternMismatch ? 'block' : 'none';
    });
    return form;
  }

  function submitOrder(form, category) {
    const name = form.name.value.trim();
    const phone = form.phone.value.trim();
    const orderItem = form.orderItem.value.trim();
    const deliveryAddress = form.deliveryAddress.value.trim();

    if (!name || !phone || !orderItem || !deliveryAddress) {
      alert('Please fill all fields.');
      return;
    }

    const whatsappNumber = '918977143043';
    const msgText = encodeURIComponent(
      `Order from JKS Online Store\nCategory: ${category}\nName: ${name}\nMobile: ${phone}\nOrder: ${orderItem}\nDelivery Address: ${deliveryAddress}`
    );
    const waLink = `https://wa.me/${whatsappNumber}?text=${msgText}`;
    window.open(waLink, '_blank');
    form.reset();
  }

  // Camera functionality
  let currentStream = null;
  let usingFrontCamera = true;

  function startCamera() {
    const constraints = {
      video: { facingMode: usingFrontCamera ? "user" : "environment" }
    };
    navigator.mediaDevices.getUserMedia(constraints).then(stream => {
      currentStream = stream;
      const video = document.getElementById('video');
      video.srcObject = stream;
      video.play();
    }).catch(e => alert('Camera access denied or not available.'));
  }

  function switchCamera() {
    if(currentStream){
      currentStream.getTracks().forEach(track => track.stop());
    }
    usingFrontCamera = !usingFrontCamera;
    startCamera();
  }

  function capturePhoto() {
    const video = document.getElementById('video');
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');
    canvas.width = video.videoWidth;
    canvas.height = video.videoHeight;
    ctx.drawImage(video, 0, 0, canvas.width, canvas.height);
    const photoContainer = document.getElementById('capturedPhotoContainer');
    photoContainer.innerHTML = '';
    const img = document.createElement('img');
    img.src = canvas.toDataURL('image/png');
    img.style.maxWidth = '100%';
    img.style.borderRadius = '6px';
    photoContainer.appendChild(img);
  }

  // Google Maps init
  function initMap() {
    const center = {lat: 17.3850, lng: 78.4867};
    const map = new google.maps.Map(document.getElementById('map'), {
      center: center,
      zoom: 13
    });
  }
</script>
<script async defer 
  src="https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_MAPS_API_KEY&callback=initMap">
</script>
<script>
  function showPage(pageId) {
    document.querySelectorAll('.page').forEach(p => p.style.display = 'none');
    document.getElementById(pageId).style.display = 'block';
    if(pageId === 'camera'){
      startCamera();
    }
  }
</script>
</body>
</html>
