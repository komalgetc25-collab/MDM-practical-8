<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Student Registration</title>

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
</head>

<body class="bg-gray-100">

    <div class="max-w-md mx-auto mt-10 bg-white p-6 rounded-lg shadow-lg">

        <h1 class="text-2xl font-bold text-center text-blue-600 mb-6">
            Student Registration
        </h1>

        <form id="registrationForm">

            <!-- Name -->
            <label class="block font-semibold mb-1">
                Name
            </label>

            <input
                type="text"
                id="name"
                class="w-full border p-2 rounded mb-2"
                placeholder="Enter your name"
            >

            <p id="nameError" class="text-red-500 text-sm mb-3"></p>


            <!-- Email -->
            <label class="block font-semibold mb-1">
                Email
            </label>

            <input
                type="text"
                id="email"
                class="w-full border p-2 rounded mb-2"
                placeholder="Enter your email"
            >

            <p id="emailError" class="text-red-500 text-sm mb-3"></p>


            <!-- Mobile -->
            <label class="block font-semibold mb-1">
                Mobile Number
            </label>

            <input
                type="text"
                id="mobile"
                class="w-full border p-2 rounded mb-2"
                placeholder="Enter 10-digit mobile number"
            >

            <p id="mobileError" class="text-red-500 text-sm mb-3"></p>


            <!-- Password -->
            <label class="block font-semibold mb-1">
                Password
            </label>

            <input
                type="password"
                id="password"
                class="w-full border p-2 rounded mb-2"
                placeholder="Enter password"
            >

            <p id="passwordError" class="text-red-500 text-sm mb-3"></p>


            <!-- Submit -->
            <button
                type="submit"
                class="w-full bg-blue-600 text-white py-2 rounded
                       hover:bg-blue-700"
            >
                Register
            </button>

        </form>

        <!-- Success Message -->
        <p id="success" class="text-green-600 text-center font-bold mt-4"></p>

    </div>


    <script>

        const form = document.getElementById("registrationForm");

        form.addEventListener("submit", function(event) {

            event.preventDefault();

            // Get values
            let name = document.getElementById("name").value.trim();
            let email = document.getElementById("email").value.trim();
            let mobile = document.getElementById("mobile").value.trim();
            let password = document.getElementById("password").value;

            // Error elements
            document.getElementById("nameError").innerText = "";
            document.getElementById("emailError").innerText = "";
            document.getElementById("mobileError").innerText = "";
            document.getElementById("passwordError").innerText = "";
            document.getElementById("success").innerText = "";

            let valid = true;

            // Name validation
            if (name === "") {
                document.getElementById("nameError").innerText =
                    "Name is required.";
                valid = false;
            }

            // Email validation
            let emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;

            if (email === "") {
                document.getElementById("emailError").innerText =
                    "Email is required.";
                valid = false;
            }
            else if (!emailPattern.test(email)) {
                document.getElementById("emailError").innerText =
                    "Enter a valid email.";
                valid = false;
            }

            // Mobile validation
            let mobilePattern = /^[0-9]{10}$/;

            if (mobile === "") {
                document.getElementById("mobileError").innerText =
                    "Mobile number is required.";
                valid = false;
            }
            else if (!mobilePattern.test(mobile)) {
                document.getElementById("mobileError").innerText =
                    "Enter a valid 10-digit mobile number.";
                valid = false;
            }

            // Password validation
            if (password === "") {
                document.getElementById("passwordError").innerText =
                    "Password is required.";
                valid = false;
            }
            else if (password.length < 6) {
                document.getElementById("passwordError").innerText =
                    "Password must contain at least 6 characters.";
                valid = false;
            }

            // Successful submission
            if (valid) {

                document.getElementById("success").innerText =
                    "Registration successful!";

                form.reset();
            }

        });

    </script>

</body>
</html>
