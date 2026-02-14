<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Valentine</title>
  <style>
    body {
      font-family: Arial;
      background: #ffe6ea;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    .box {
      background: white;
      padding: 30px;
      border-radius: 15px;
      text-align: center;
    }
    button {
      padding: 12px 20px;
      margin: 10px;
      font-size: 16px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
    }
    #yes { background: #ff4d6d; color: white; }
    #no { background: #ddd; }
  </style>
</head>
<body>
  <div class="box">
    <h1>Will you be my Valentine?</h1>
    <button onclick="yes()">Yes</button>
    <button onclick="no()">No</button>
    <p id="msg"></p>
  </div>

  <script>
    function yes() {
      document.getElementById("msg").innerHTML = "Yay! I love you!";
    }
    function no() {
      document.getElementById("msg").innerHTML = "No is not an option :)";
    }
  </script>
</body>
</html>
