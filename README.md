# 2- shopping cart
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Shopping Cart</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 40px;
    }
    h1 {
      color: #333;
    }
    ul {
      line-height: 1.6;
    }
    .total {
      margin-top: 20px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>Shopping Cart Calculator</h1>
  <ul id="item-list"></ul>
  <p class="total" id="total-value"></p>

  <script>
    const cart = [
      { name: "Pen", price: 20, quantity: 3 },
      { name: "Notebook", price: 50, quantity: 2 },
      { name: "Pencil", price: 10, quantity: 5 }
    ];

    // 1. Calculate total price for each item
    const cartWithTotal = cart.map(item => ({
      ...item,
      total: item.price * item.quantity
    }));

    // 2. Generate new array of item descriptions
    const itemDescriptions = cart.map(item => `${item.name} - ₱${item.price}`);

    // 3. Compute total cart value using reduce
    const totalCartValue = cart.reduce((sum, item) => sum + (item.price * item.quantity), 0);

    // 4. Display item descriptions on the page
    const itemList = document.getElementById('item-list');
    itemDescriptions.forEach(desc => {
      const li = document.createElement('li');
      li.textContent = desc;
      itemList.appendChild(li);
    });

    // 5. Display total cart value
    const totalValue = document.getElementById('total-value');
    totalValue.textContent = `Total Cart Value: ₱${totalCartValue}`;
  </script>
</body>
</html>
