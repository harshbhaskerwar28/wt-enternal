# Online Bookstore Code Documentation

This repository contains various HTML, CSS, and JavaScript files that together create an online bookstore application. Below you'll find documentation for each key component.

## Table of Contents
1. [Frames](#1-frames)
2. [Registration with Forgot Password](#2-registration-with-forgot-password)
3. [Dynamic Content Loading](#3-dynamic-content-loading)
4. [Add to Cart Functionality](#4-add-to-cart-functionality)
5. [XML Online Store Catalog](#5-xml-online-store-catalog)
6. [XML User Data](#6-xml-user-data)

## 1. Frames

The frames structure divides the page into header, navigation, content, and footer sections.

### index.html
```html
<!DOCTYPE html>
<html>
<head>
  <title>Online Book Store</title>
</head>
<frameset rows="80px,*,40px">
  <frame src="header.html" name="headerFrame" noresize scrolling="no">
  <frameset cols="200px,*">
    <frame src="nav.html" name="navFrame" noresize>
    <frame src="content.html" name="contentFrame">
  </frameset>
  <frame src="footer.html" name="footerFrame" noresize scrolling="no">
</frameset>
</html>
```

### header.html
```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header><h1>Online Bookstore</h1></header>
</body>
</html>
```

### nav.html
```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <nav>
    <h3>Categories</h3>
    <ul>
      <li><a href="aids.html" target="contentFrame">AI & DS</a></li>
      <li><a href="ds.html" target="contentFrame">Data Science</a></li>
      <li><a href="cybersecurity.html" target="contentFrame">Cybersecurity</a></li>
    </ul>
  </nav>
</body>
</html>
```

### aids.html (Sample Content)
```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <main>
    <h2>AI & DS Books</h2>
    <p><b>AI for Beginners</b> by John Doe</p>
    <p><b>Machine Learning 101</b> by Jane Smith</p>
  </main>
</body>
</html>
```

### footer.html
```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <footer><p>&copy; 2025 Online Bookstore</p></footer>
</body>
</html>
```

### styles.css
```css
body {
  margin: 0;
  font-family: Arial, sans-serif;
  font-size: 14px;
}

header, nav, main, footer {
  padding: 10px;
}

header {
  background-color: lightblue;
  text-align: center;
}

nav {
  background-color: #f0f0f0;
}

ul {
  list-style: none;
  padding-left: 0;
}

a {
  text-decoration: none;
  color: black;
}
```

## 2. Registration with Forgot Password

A user registration form with forgot password functionality.

### rigjs.html
```html
<!DOCTYPE html>
<html>
<body style="text-align:center;font-family:sans-serif;margin-top:50px">
<style>
  input, button {
    margin: 5px;
    padding: 8px;
    border-radius: 5px;
    border: 1px solid gray;
  }
  #f, #b { 
    background: none; 
    color: blue; 
    border: none; 
    cursor: pointer; 
    text-decoration: underline;
  }
</style>

<h2 id="t">Register</h2>

<!-- Registration Form -->
<form id="r" onsubmit="return v()">
  <input id="u" placeholder="Username"><br>
  <input id="p" type="password" placeholder="Password"><br>
  <input id="cp" type="password" placeholder="Confirm Password"><br>
  <button>Register</button><br>
  <button type="button" id="f" onclick="s(1)">Forgot Password?</button>
</form>

<!-- Forgot Form -->
<form id="fp" style="display:none" onsubmit="return f()">
  <input id="e" placeholder="Email"><br>
  <button>Reset</button><br>
  <button type="button" id="b" onclick="s(0)">Back to Register</button>
</form>

<script>
let emails=["a@x.com","b@y.com"]

function v(){
  let u=document.getElementById('u').value
  let p=document.getElementById('p').value
  let c=document.getElementById('cp').value
  if(u.length<5)return alert("User"),!1
  if(p.length<8)return alert("Pass"),!1
  if(p!=c)return alert("No Match"),!1
  alert("OK")
  return!1
}

function f(){
  let e=document.getElementById('e').value
  let r=/^[^@]+@[^@]+\.[^@]+$/
  if(!r.test(e))return alert("Bad Email"),!1
  if(!emails.includes(e))return alert("No User"),!1
  alert("Check Mail")
  return!1
}

function s(x){
  document.getElementById('r').style.display=x?"none":"block"
  document.getElementById('fp').style.display=x?"block":"none"
  document.getElementById('t').innerText=x?"Forgot Password":"Register"
}
</script>
</body>
</html>
```

## 3. Dynamic Content Loading

This page dynamically loads book details when a navigation link is clicked.

### dynamic.html
```html
<!DOCTYPE html>
<html>
<head>
  <title>Online Bookstore</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      color: #333;
      max-width: 1000px;
      margin: 0 auto;
      padding: 20px;
      background-color: #f9f9f9;
    }

    h2 {
      color: #2c3e50;
      margin-bottom: 20px;
      text-align: center;
      border-bottom: 2px solid #3498db;
      padding-bottom: 10px;
    }

    h3 {
      color: #2c3e50;
      margin: 20px 0;
    }


    #nav {
      background-color: #3498db;
      border-radius: 5px;
      padding: 10px;
      margin-bottom: 20px;
    }

    #nav ul {
      list-style-type: none;
      display: flex;
      justify-content: space-around;
    }

    #nav li {
      display: inline;
    }

    #nav a {
      color: white;
      text-decoration: none;
      font-weight: bold;
      padding: 5px 10px;
    }

    #nav a:hover {
      background-color: #2980b9;
      border-radius: 3px;
    }


    #content {
      background-color: white;
      padding: 20px;
      border-radius: 5px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    #bookDetails {
      padding: 15px;
      line-height: 1.8;
    }

    #bookDetails img {
      display: block;
      margin: 20px auto;
      border: 1px solid #ddd;
      border-radius: 5px;
    }

    #bookDetails h4 {
      color: #3498db;
      font-size: 24px;
      margin-bottom: 10px;
    }

    #bookDetails p {
      margin-bottom: 15px;
    }
  </style>
</head>
<body>
  <h2>Bookstore Navigation</h2>

  <div id="nav">
    <ul>
      <li><a href="#" onclick="loadBook('book1')">Book One</a></li>
      <li><a href="#" onclick="loadBook('book2')">Book Two</a></li>
      <li><a href="#" onclick="loadBook('book3')">Book Three</a></li>
    </ul>
  </div>

  <div id="content">
    <h3>Book Details</h3>
    <div id="bookDetails">Select a book to see details here.</div>
  </div>

  <script>
    const books = {
      book1: {
        title: "📘 Book One",
        description: "A thrilling adventure through time.",
        image: "https://via.placeholder.com/200x250?text=Book+One"
      },
      book2: {
        title: "📕 Book Two",
        description: "A heartwarming tale of friendship.",
        image: "https://via.placeholder.com/200x250?text=Book+Two"
      },
      book3: {
        title: "📗 Book Three",
        description: "Discover the secrets of the universe.",
        image: "https://via.placeholder.com/200x250?text=Book+Three"
      }
    };

    function loadBook(bookId) {
      const book = books[bookId];
      const content = `
        <h4>${book.title}</h4>
        <p>${book.description}</p>
        <img src="${book.image}" alt="${book.title}">
      `;
      document.getElementById("bookDetails").innerHTML = content;
    }
  </script>
</body>
</html>
```

## 4. Add to Cart Functionality

Shopping cart implementation for the bookstore.

### add-cart.html
```html
<!DOCTYPE html>
<html>
<head>
  <title>Bookstore Cart</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f2f2f2;
      padding: 20px;
    }

    h2 {
      text-align: center;
      color: #333;
    }

    #books, #cart {
      float: left;
      width: 45%;
      margin: 2%;
      background-color: white;
      padding: 15px;
      border-radius: 8px;
      box-shadow: 0 0 5px #ccc;
    }

    ul {
      list-style: none;
      padding: 0;
    }

    li {
      padding: 5px 0;
    }

    button {
      margin-top: 5px;
      padding: 5px 10px;
      background-color: #4CAF50;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }

    button:hover {
      background-color: #45a049;
    }

    .clear-button {
      background-color: #f44336;
      margin-top: 10px;
    }

    .clear-button:hover {
      background-color: #d32f2f;
    }

    p {
      font-size: 16px;
      color: #333;
    }
  </style>
</head>
<body>

  <h2>Online Bookstore</h2>

  <div id="books">
    <h3>Available Books</h3>
    <ul>
      <li>
        📘 Book One - $10 
        <br><button onclick="addToCart('Book One', 10)">Add to Cart</button>
      </li>
      <li>
        📕 Book Two - $15 
        <br><button onclick="addToCart('Book Two', 15)">Add to Cart</button>
      </li>
      <li>
        📗 Book Three - $12 
        <br><button onclick="addToCart('Book Three', 12)">Add to Cart</button>
      </li>
    </ul>
  </div>

  <div id="cart">
    <h3>Your Cart</h3>
    <ul id="cartItems">
      <li>No items in cart.</li>
    </ul>
    <p><strong>Total: $<span id="total">0</span></strong></p>
    <button class="clear-button" onclick="clearCart()">Clear Cart</button>
  </div>

  <script>
    const cart = [];
    
    function addToCart(title, price) {
      cart.push({ title, price });
      updateCart();
    }

    function updateCart() {
      const cartList = document.getElementById("cartItems");
      const totalDisplay = document.getElementById("total");
      cartList.innerHTML = "";

      let total = 0;

      cart.forEach(item => {
        const li = document.createElement("li");
        li.textContent = `${item.title} - $${item.price}`;
        cartList.appendChild(li);
        total += item.price;
      });

      if (cart.length === 0) {
        cartList.innerHTML = "<li>No items in cart.</li>";
      }

      totalDisplay.textContent = total;
    }

    function clearCart() {
      cart.length = 0;
      updateCart();
    }
  </script>

</body>
</html>
```

## 5. XML Online Store Catalog

XML file containing book catalog data.

### xml-online.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<catalog>
  <book id="b001">
    <title>Book One</title>
    <author>Jane Doe</author>
    <genre>Adventure</genre>
    <price>10.99</price>
    <availability>In Stock</availability>
  </book>

  <book id="b002">
    <title>Book Two</title>
    <author>John Smith</author>
    <genre>Fiction</genre>
    <price>14.50</price>
    <availability>Out of Stock</availability>
  </book>

  <book id="b003">
    <title>Book Three</title>
    <author>Emily Clark</author>
    <genre>Science</genre>
    <price>12.00</price>
    <availability>In Stock</availability>
  </book>
</catalog>
```

## 6. XML User Data

XML file containing user data and purchase history.

### xml-user.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<users>
  <user id="u001">
    <username>booklover99</username>
    <password hash="SHA-256">5e884898da28047151d0e56f8dc6...</password>
    <email>booklover99@example.com</email>
    
    <purchaseHistory>
      <purchase>
        <bookTitle>Book One</bookTitle>
        <date>2025-03-12</date>
        <price>10.99</price>
      </purchase>
      <purchase>
        <bookTitle>Book Two</bookTitle>
        <date>2025-04-01</date>
        <price>14.50</price>
      </purchase>
    </purchaseHistory>
  </user>

  <user id="u002">
    <username>reader123</username>
    <password hash="SHA-256">6b3a55e0261b0304143f805a249f...</password>
    <email>reader123@example.com</email>
    
    <purchaseHistory>
      <purchase>
        <bookTitle>Book Three</bookTitle>
        <date>2025-02-20</date>
        <price>12.00</price>
      </purchase>
    </purchaseHistory>
  </user>
</users>
```
