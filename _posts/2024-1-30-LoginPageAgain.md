---
toc: true
comments: true
layout: post
title: BadandFakeLogin
type: hacks
courses: { compsci: {week: 9} }
---

<html lang="en">

<head>
<script>
    function login_user() {
      const enteredUid = document.getElementById("uid").value;
      const enteredPassword = document.getElementById("password").value;
      console.log("Uid = " + enteredUid)
      console.log("Password = " + enteredPassword)
      const signupHeaders = new Headers();
      signupHeaders.set('111', '222');
      signupHeaders.set("Accept", "*/*");
      signupHeaders.set("Accept-Language", "en-US,en;q=0.9");
      signupHeaders.set("Content-Type", "application/json");
      login_api(enteredUid,enteredPassword)
    }
    function login_api(uid, pw){
      var myHeaders = new Headers();
      myHeaders.append("Accept", "*/*");
      myHeaders.append("Accept-Language", "en-US,en;q=0.9");
      myHeaders.append("Content-Type", "application/json");
      }

      var raw = JSON.stringify({
          "uid": enteredUid,
          "password": enteredPassword
        });

      var requestOptions = {
          method: 'POST',
          headers: myHeaders,
          body: raw,
          redirect: 'follow'
        };

      fetch("http://127.0.0.1:8086/api/users/authenticate", requestOptions)
          .then(response => {
            if (response.ok) {
                console.log("User logged in successfully");
                window.location.href = "http://127.0.0.1:4200/student/2024/02/06/DataBase"
              } else {
                console.error("User login failed");
                // You can handle failed login attempts here
                const errorMessageDiv = document.getElementById('errorMessage');
                errorMessageDiv.innerHTML = '<label style="color: red;">User Login Failed</label>';
              }
          })
          .then(result => { 
            console.log(result);
            
            })
          .catch(error => console.log('error', error));
          

      
      //return response
  </script>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Login Page</title>
  <link rel="stylesheet" href="styles.css"> <!-- Include the compiled CSS file -->
</head>

<body>
  <!-- Your HTML login form -->
  <div id="errorMessage"></div>
  <form action="javascript:login_user()">
    <p><label for="uid">User ID:</label>
      <input type="text" name="uid" id="uid" required>
    </p>
    <p><label for="password">Password:</label>
      <input type="password" name="password" id="password" required>
    </p>
    <p>
     <button class="button-spacing">Log In</button>
     <button onClick = "window.location.href ='https://tanav-kambhampati.github.io/student2/'" class="button-spacing" >Sign Up</button>

      
    </p>
  </form>

  <!-- Your JavaScript code -->
  
</body>

</html>