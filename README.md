<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Quán Cà Phê Online</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f9f9f9;
      padding: 20px;
    }
    h1 {
      color: #8B4513;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-bottom: 20px;
    }
    th, td {
      border: 1px solid #ddd;
      padding: 12px;
      text-align: left;
    }
    th {
      background-color: #d2b48c;
      color: white;
    }
    input[type="number"] {
      width: 60px;
    }
    #receipt {
      background: #fff;
      padding: 15px;
      border: 1px solid #ccc;
    }
    .total {
      font-weight: bold;
      font-size: 18px;
      color: #B22222;
    }
  </style>
</head>
<body>

  <h1>☕ Quán Cà Phê Online</h1>

  <form id="coffeeForm">
    <table>
      <tr>
        <th>Tên món</th>
        <th>Giá (VND)</th>
        <th>Số lượng</th>
      </tr>
      <tr>
        <td>Cà phê đen</td>
        <td>15000</td>
        <td><input type="number" name="Cà phê đen" value="0" min="0"></td>
      </tr>
      <tr>
        <td>Cà phê sữa</td>
        <td>18000</td>
        <td><input type="number" name="Cà phê sữa" value="0" min="0"></td>
      </tr>
      <tr>
        <td>Bạc xỉu</td>
        <td>20000</td>
        <td><input type="number" name="Bạc xỉu" value="0" min="0"></td>
      </tr>
      <tr>
        <td>Cappuccino</td>
        <td>30000</td>
        <td><input type="number" name="Cappuccino" value="0" min="0"></td>
      </tr>
      <tr>
        <td>Latte</td>
        <td>28000</td>
        <td><input type="number" name="Latte" value="0" min="0"></td>
      </tr>
    </table>

    <button type="button" onclick="calculateTotal()">🧾 Tính hóa đơn</button>
  </form>

  <div id="receipt"></div>

  <script>
    const prices = {
      "Cà phê đen": 15000,
      "Cà phê sữa": 18000,
      "Bạc xỉu": 20000,
      "Cappuccino": 30000,
      "Latte": 28000
    };

    function calculateTotal() {
      const form = document.getElementById("coffeeForm");
      const receipt = document.getElementById("receipt");
      let total = 0;
      let receiptHtml = "<h2>🧾 Hóa đơn:</h2><ul>";

      for (let item in prices) {
        const qty = parseInt(form.elements[item].value);
        if (qty > 0) {
          const itemTotal = prices[item] * qty;
          total += itemTotal;
          receiptHtml += `<li>${item} x${qty} = ${itemTotal.toLocaleString()} VND</li>`;
        }
      }

      receiptHtml += `</ul><p class="total">💵 Tổng cộng: ${total.toLocaleString()} VND</p>`;
      receipt.innerHTML = receiptHtml;
    }
  </script>

</body>
</html># Ban_cafe.htlm
