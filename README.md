<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tech and Mech - Sign Up</title>
    <style>
        /* Global Styles */
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
            color: #333;
        }

        header {
            background-color: #4e73df;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .navbar {
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .navbar a {
            color: white;
            text-decoration: none;
            margin: 0 20px;
            font-size: 18px;
        }

        .navbar a:hover {
            text-decoration: underline;
        }

        /* Form Container */
        .form-container {
            width: 400px;
            margin: 50px auto;
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        h2 {
            text-align: center;
            margin-bottom: 20px;
            font-size: 24px;
            color: #4e73df;
        }

        label {
            font-size: 16px;
            margin-bottom: 8px;
            display: block;
            font-weight: bold;
        }

        input {
            width: 100%;
            padding: 12px;
            margin: 10px 0 15px;
            border: 2px solid #ddd;
            border-radius: 5px;
            box-sizing: border-box;
        }

        input:focus {
            border-color: #4e73df;
            outline: none;
        }

        .error {
            color: red;
            font-size: 12px;
        }

        .submit-btn {
            width: 100%;
            padding: 15px;
            background-color: #4e73df;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 18px;
            cursor: pointer;
        }

        .submit-btn:hover {
            background-color: #224abe;
        }

        /* Thank You Message Styles */
        .thank-you-message {
            text-align: center;
            margin-top: 50px;
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .thank-you-message h3 {
            color: #4e73df;
            font-size: 30px;
        }

        .thank-you-message p {
            color: #333;
            font-size: 18px;
        }

        footer {
            text-align: center;
            background-color: #4e73df;
            color: white;
            padding: 15px;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>

    <header>
        <div class="navbar">
            <h1>Tech and Mech</h1>
            <nav>
                <a href="#">Home</a>
                <a href="#">About Us</a>
                <a href="#">Contact</a>
            </nav>
        </div>
    </header>

    <!-- Form Container -->
    <section id="formSection" class="form-container">
        <h2>Create an Account</h2>
        <form id="signupForm">
            <label for="firstName">First Name</label>
            <input type="text" id="firstName" name="firstName" required>
            <div id="errorFirstName" class="error"></div>

            <label for="lastName">Last Name</label>
            <input type="text" id="lastName" name="lastName" required>
            <div id="errorLastName" class="error"></div>

            <label for="email">Email Address</label>
            <input type="email" id="email" name="email" required>
            <div id="errorEmail" class="error"></div>

            <label for="phone">Phone Number</label>
            <input type="text" id="phone" name="phone" required>
            <div id="errorPhone" class="error"></div>

            <label for="address">Address</label>
            <input type="text" id="address" name="address" required>
            <div id="errorAddress" class="error"></div>

            <label for="password">Password</label>
            <input type="password" id="password" name="password" required>
            <div id="errorPassword" class="error"></div>

            <label for="confirmPassword">Confirm Password</label>
            <input type="password" id="confirmPassword" name="confirmPassword" required>
            <div id="errorConfirmPassword" class="error"></div>

            <label for="dob">Date of Birth</label>
            <input type="date" id="dob" name="dob" required>
            <div id="errorDob" class="error"></div>

            <button type="submit" class="submit-btn">Sign Up</button>
        </form>
    </section>

    <!-- Thank You Message Container -->
    <section id="thankYouSection" class="thank-you-message" style="display: none;">
        <h3>Thank You for Signing Up!</h3>
        <p>We appreciate your interest in Tech and Mech. You will hear from us soon.</p>
    </section>

    <footer>
        <p>&copy; 2025 Tech and Mech. All Rights Reserved.</p>
    </footer>

    <script>
        document.getElementById('signupForm').addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent the form from submitting

            let isValid = true;

            // Clear previous error messages
            document.querySelectorAll('.error').forEach(function (error) {
                error.innerHTML = '';
            });

            // Validate First Name
            const firstName = document.getElementById('firstName').value;
            if (firstName.trim() === "") {
                document.getElementById('errorFirstName').innerHTML = 'First Name is required';
                isValid = false;
            }

            // Validate Last Name
            const lastName = document.getElementById('lastName').value;
            if (lastName.trim() === "") {
                document.getElementById('errorLastName').innerHTML = 'Last Name is required';
                isValid = false;
            }

            // Validate Email
            const email = document.getElementById('email').value;
            const emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
            if (!emailPattern.test(email)) {
                document.getElementById('errorEmail').innerHTML = 'Please enter a valid email address';
                isValid = false;
            }

            // Validate Phone Number
            const phone = document.getElementById('phone').value;
            const phonePattern = /^[0-9]{10}$/;
            if (!phonePattern.test(phone)) {
                document.getElementById('errorPhone').innerHTML = 'Please enter a valid phone number (10 digits)';
                isValid = false;
            }

            // Validate Address
            const address = document.getElementById('address').value;
            if (address.trim() === "") {
                document.getElementById('errorAddress').innerHTML = 'Address is required';
                isValid = false;
            }

            // Validate Password
            const password = document.getElementById('password').value;
            if (password.length < 8) {
                document.getElementById('errorPassword').innerHTML = 'Password must be at least 8 characters long';
                isValid = false;
            }

            // Validate Confirm Password
            const confirmPassword = document.getElementById('confirmPassword').value;
            if (confirmPassword !== password) {
                document.getElementById('errorConfirmPassword').innerHTML = 'Passwords do not match';
                isValid = false;
            }

            // Validate Date of Birth
            const dob = document.getElementById('dob').value;
            if (!dob) {
                document.getElementById('errorDob').innerHTML = 'Date of Birth is required';
                isValid = false;
            }

            // If form is valid, hide the form and show the thank you message
            if (isValid) {
                document.getElementById('formSection').style.display = 'none'; // Hide the form
                document.getElementById('thankYouSection').style.display = 'block'; // Show the thank you message
            }
        });
    </script>

</body>
</html>

