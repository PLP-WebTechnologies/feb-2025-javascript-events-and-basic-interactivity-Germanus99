# feb-2025-avasjcript-events-and-basic-interactivity

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Form and Validation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .form-container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
        }

        .form-container h2 {
            text-align: center;
        }

        .form-container input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .form-container button {
            width: 100%;
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .form-container button:hover {
            background-color: #45a049;
        }

        .error-message {
            color: red;
            font-size: 12px;
            display: none;
        }

        .success-message {
            color: green;
            font-size: 12px;
            display: none;
        }
    </style>
</head>
<body>

    <div class="form-container">
        <h2>Sign Up</h2>
        <form id="signupForm">
            <input type="text" id="username" placeholder="Enter your username" required>
            <div id="usernameError" class="error-message">Username is required.</div>

            <input type="email" id="email" placeholder="Enter your email" required>
            <div id="emailError" class="error-message">Please enter a valid email.</div>

            <input type="password" id="password" placeholder="Enter your password" required>
            <div id="passwordError" class="error-message">Password is required.</div>

            <button type="submit">Sign Up</button>
            <div id="formSuccess" class="success-message">Form submitted successfully!</div>
        </form>
    </div>

    <script>
        // Get form elements
        const form = document.getElementById('signupForm');
        const username = document.getElementById('username');
        const email = document.getElementById('email');
        const password = document.getElementById('password');
        const usernameError = document.getElementById('usernameError');
        const emailError = document.getElementById('emailError');
        const passwordError = document.getElementById('passwordError');
        const formSuccess = document.getElementById('formSuccess');

        // Event listener for form submission
        form.addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form submission for validation

            // Clear previous error messages
            usernameError.style.display = 'none';
            emailError.style.display = 'none';
            passwordError.style.display = 'none';
            formSuccess.style.display = 'none';

            // Form validation
            let isValid = true;

            // Check if username is empty
            if (username.value.trim() === "") {
                usernameError.style.display = 'block';
                isValid = false;
            }

            // Check if email is valid
            const emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
            if (!emailPattern.test(email.value)) {
                emailError.style.display = 'block';
                isValid = false;
            }

            // Check if password is empty
            if (password.value.trim() === "") {
                passwordError.style.display = 'block';
                isValid = false;
            }

            // If form is valid, show success message
            if (isValid) {
                formSuccess.style.display = 'block';
            }
        });

        // Event listener for input focus
        username.addEventListener('focus', function() {
            usernameError.style.display = 'none'; // Hide error on focus
        });
        email.addEventListener('focus', function() {
            emailError.style.display = 'none'; // Hide error on focus
        });
        password.addEventListener('focus', function() {
            passwordError.style.display = 'none'; // Hide error on focus
        });
    </script>

</body>
</html>
