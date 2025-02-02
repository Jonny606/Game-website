<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Grade Input System</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 20px;
    }
    h1 {
      text-align: center;
    }
    .form-container {
      max-width: 600px;
      margin: 0 auto;
      background-color: #fff;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    .form-group {
      margin-bottom: 15px;
    }
    label {
      display: block;
      font-weight: bold;
      margin-bottom: 5px;
    }
    input[type="number"] {
      width: 100%;
      padding: 10px;
      margin: 5px 0;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    button {
      display: block;
      width: 100%;
      padding: 10px;
      background-color: #28a745;
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover {
      background-color: #218838;
    }
    .result {
      margin-top: 20px;
      text-align: center;
    }
  </style>
</head>
<body>
  <h1>Grade Input System</h1>
  <div class="form-container">
    <div class="form-group">
      <label for="productGrade">Product Grade:</label>
      <input type="number" id="productGrade" placeholder="Enter Product Grade (0-100)">
    </div>
    <div class="form-group">
      <label for="processGrade">Process Grade:</label>
      <input type="number" id="processGrade" placeholder="Enter Process Grade (0-100)">
    </div>
    <div class="form-group">
      <label for="serviceGrade">Service Grade:</label>
      <input type="number" id="serviceGrade" placeholder="Enter Service Grade (0-100)">
    </div>
    <button onclick="calculateGrade()">Calculate Final Grade</button>

    <div class="result" id="result"></div>
  </div>

  <script>
    function calculateGrade() {
      // Get grades from inputs
      let productGrade = parseFloat(document.getElementById('productGrade').value);
      let processGrade = parseFloat(document.getElementById('processGrade').value);
      let serviceGrade = parseFloat(document.getElementById('serviceGrade').value);

      // Ensure values are valid numbers between 0-100
      if (isNaN(productGrade) || isNaN(processGrade) || isNaN(serviceGrade) ||
          productGrade < 0 || productGrade > 100 ||
          processGrade < 0 || processGrade > 100 ||
          serviceGrade < 0 || serviceGrade > 100) {
        document.getElementById('result').innerHTML = "Please enter valid grades between 0 and 100.";
        return;
      }

      // Calculate the average grade
      let finalGrade = (productGrade + processGrade + serviceGrade) / 3;

      // Display the final grade with appropriate formatting
      document.getElementById('result').innerHTML = `Your Final Grade: <strong>${finalGrade.toFixed(2)}</strong>`;
    }
  </script>
</body>
</html>
