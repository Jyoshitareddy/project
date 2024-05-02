<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Agroconnect</title>
    <style>
        /* Styles for both pages */
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 0;
            padding: 0;
        }

        #main {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
        }

        input {
            width: 100%;
            padding: 8px;
            margin: 5px 0;
            box-sizing: border-box;
        }

        button {
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        .hidden {
            display: none;
        }

        #space {
            margin: 10px;
        }

        /* Styles for shopping cart */
        .container {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
        }

        .item {
            margin: 20px;
            text-align: center;
        }

        img {
            width: 200px;
            height: 200px;
            object-fit: cover;
            margin-bottom: 10px;
        }

        select {
            margin-bottom: 10px;
        }

        #cart {
            background-color: #f9f9f9;
            padding: 20px;
            margin-top: 20px;
        }

        #cartItems {
            list-style-type: none;
            padding: 0;
        }

        li {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <!DOCTYPE html>
<html lang="en">
  
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>
      Agroconnect
    </title>
    <style>
      body { font-family: Arial, sans-serif; text-align: center; margin: 0;
      padding: 0; } #main { max-width: 600px; margin: 0 auto; padding: 20px;
      } input { width: 100%; padding: 8px; margin: 5px 0; box-sizing: border-box;
      } button { padding: 10px 20px; background-color: #4CAF50; color: white;
      border: none; cursor: pointer; } button:hover { background-color: #45a049;
      } .hidden { display: none; } #space{ margin:10px; }
    </style>
  </head>
  
  <body>
    <div id="main">
      <h1>
        Agroconnect
      </h1>
      <div id="loginSection">
        <input type="text" id="username" placeholder="Username">
        <br>
        <input type="password" id="loginpassword" placeholder="Password">
        <br>
		<a href="file:///C:/Users/addis/Desktop/iop/new6.html">
    <button onclick="login()">>login</button>
</a>
        <br>
        <p id="forgotPassword" onclick="showForgotPassword()">
          Forgotten password?
        </p>
        <div id="forgotPasswordSection" class="hidden">
          
          <input type="text" id="usernameofuser" placeholder="Username">
          <input type="phone" id="newphonenumber" placeholder="Enter registered phonenumber">
          
          <input type="password" id="newPassword" placeholder="Enter New Password">
          <br>
          <button onclick="updatePassword()">
            Submit
          </button>
        </div>
      </div>
      
      <div id="space">
        </div?>
        <button onclick="showCreateAccount()">
          Create New Account
        </button>
        <div id="createAccountSection" class="hidden">
          <input type="text" id="name" placeholder="Name">
          <br>
          <input type="password" id="password" placeholder="Password">
          <br>
          <input type="tel" id="phone" placeholder="Phone Number">
          <br>
          <button onclick="createAccount()">
            Submit
          </button>
          <p id="successMessage" class="hidden">
            Account created successfully!
          </p>
        </div>
      </div>
      <script>
        let userobj = {};
        function login() {
          var username = document.getElementById('username').value;
          var password = document.getElementById('loginpassword').value;console.log(username);console.log(password);
          var users = JSON.parse(localStorage.getItem('users')) || [];
          var user = users.find(u =>u.name === username && u.password === password);
          if (user) {
            alert('Login successful!');
          } else {
            alert('Invalid username or password.');
          }document.getElementById('username').value = "";
          document.getElementById('loginpassword').value = "";
        }
        function showForgotPassword() {
          document.getElementById('forgotPasswordSection').classList.toggle('hidden');
        }
        function updatePassword() {
          var username = document.getElementById('usernameofuser').value;
          var newPassword = document.getElementById('newPassword').value;
          var newphonenumber = document.getElementById('newphonenumber').value;
          var users = JSON.parse(localStorage.getItem('users')) || [];
          var userIndex = users.findIndex(u =>u.name === username && u.phone === newphonenumber); 
		  if (userIndex !== -1) {
            users[userIndex].password = newPassword;
            localStorage.setItem('users', JSON.stringify(users));
            alert('Password updated successfully!');
          } else {
            alert('Invalid username or password.');
          }document.getElementById('usernameofuser').value = "";
          document.getElementById('newPassword').value = "";
          document.getElementById('newphonenumber').value = "";
        }
        function showCreateAccount() {
          document.getElementById('createAccountSection').classList.toggle('hidden');
        }
        function createAccount() {
          var name = document.getElementById('name').value;
          var password = document.getElementById('password').value;
          var phone = document.getElementById('phone').value;
          if (name.trim() === '' || password.trim() === '' || phone.trim() === '') {
            alert('Please fill in all fields.');
            return;
          }
          if (!/^\d{10}$/.test(phone)) {
            alert('Phone number must be 10 digits.');
            return;
          }
          var users = JSON.parse(localStorage.getItem('users')) || [];
          users.push({
            name: name,
            password: password,
            phone: phone
          });
          localStorage.setItem('users', JSON.stringify(users));
          document.getElementById('successMessage').classList.remove('hidden');
          setTimeout(function() {
            document.getElementById('successMessage').classList.add('hidden');
            document.getElementById('createAccountSection').classList.add('hidden');
          },
          1000);userobj = localStorage.getItem("users");console.log(userobj);document.getElementById('name').value = "";
          document.getElementById('password').value = "";
          document.getElementById('phone').value = "";
        }
      </script>
  </body>

</html>
