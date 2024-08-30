<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>College Student Info</title>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, #89f7fe, #66a6ff);
        }

        #splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #66a6ff;
            color: #fff;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            opacity: 1;
            transition: opacity 1s ease-in-out;
        }

        #splash-screen img {
            max-width: 200px;
            margin-bottom: 20px;
            box-shadow: 8px 8px 15px black;
        }

        #splash-screen h1 {
            font-size: 30px;
            text-shadow: 2px 2px 4px #000;
        }

        #splash-screen.hide {
            opacity: 0;
            visibility: hidden;
        }

        .container {
            display: none;
            text-align: center;
            background-color: #fff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            width: 90%;
            max-width: 500px;
            transform: translateY(20px);
            transition: opacity 1s ease, transform 1s ease;
        }

        .container.show {
            display: block;
            opacity: 1;
            transform: translateY(0);
        }

        h2 {
            color: #333;
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 10px;
            font-weight: bold;
            color: #555;
        }

        select, input[type="text"] {
            padding: 10px;
            border: 2px solid #ddd;
            border-radius: 5px;
            margin-bottom: 20px;
            width: 100%;
            max-width: 400px;
            box-sizing: border-box;
        }

        button {
            padding: 10px 20px;
            background-color: #66a6ff;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s;
        }

        button:hover {
            background-color: #5480cb;
            transform: scale(1.05);
        }

        #student-info {
            text-align: left;
            display: none;
        }

        #student-info h3 {
            color: #333;
            margin-bottom: 10px;
        }

        .info {
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .info span {
            font-size: 18px;
        }

        .icons {
            display: flex;
            gap: 10px;
        }

        .icons img {
            width: 24px;
            height: 24px;
            cursor: pointer;
            transition: transform 0.2s;
        }

        .icons img:hover {
            transform: scale(1.2);
        }
    </style>
</head>
<body>

    <div id="splash-screen">
        <img src="https://camo.githubusercontent.com/db4c7f852ac5951515814bba18551cd7aeb48c4271df6f9ab1519bb8f49b4866/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f7468756d622f322f32312f4e65632e706e672e6a70672f32323070782d4e65632e706e672e6a7067" alt="College Logo">
        <h1>Welcome to NEC(IT) Portal</h1>
    </div>

    <div class="container" id="selectionForm">
        <h2>Student Details</h2>
        <label for="branch">Select Branch:</label>
        <select id="branch">
            <option value="CSE">CSE</option>
            <option value="CSE">IT</option>
            <option value="CSE">CSE(AI)</option>
            <option value="ECE">ECE</option>
            <option value="EEE">EEE</option>
            <option value="MECH">MECH</option>
            <option value="CIVIL">CIVIL</option>
        </select>
        <label for="year">Select Year:</label>
        <select id="year">
            <option value="1st">1st Year</option>
            <option value="2nd">2nd Year</option>
            <option value="3rd">3rd Year</option>
            <option value="4th">4th Year</option>
        </select>
        <label for="section">Select Section:</label>
        <select id="section">
            <option value="A">A</option>
            <option value="B">B</option>
            <option value="C">C</option>
            <option value="D">D</option>
            <option value="E">E</option>
            
        </select>
        <button onclick="displayStudentInfo()">Submit</button>
    </div>

    <div class="container" id="student-info">
        <h2>Student Information</h2>
        <div class="info">
            <span>Student Name: Shaik Appapuram Firoz</span>
        </div>
        <div class="info">
            <span>Roll Number: 22471A1244</span>
        </div>
        <div class="info">
            <span>Student Mobile: +91-7416546101</span>
            <div class="icons">
                <img src="https://img.icons8.com/ios-filled/50/000000/phone.png" alt="Call" onclick="makeCall('7416546101')">
                <img src="https://img.icons8.com/ios-filled/50/000000/sms.png" alt="Message" onclick="sendMessage('9603484788')">
            </div>
        </div>
        <div class="info">
            <span>Parent Mobile: +91-9603484788</span>
            <div class="icons">
                <img src="https://img.icons8.com/ios-filled/50/000000/phone.png" alt="Call" onclick="makeCall('9603484788')">
                <img src="https://img.icons8.com/ios-filled/50/000000/sms.png" alt="Message" onclick="sendMessage('9603484788')">
            </div>
        </div>
    </div>

    <script>
        window.onload = function() {
            setTimeout(function() {
                document.getElementById('splash-screen').classList.add('hide');
                document.getElementById('selectionForm').classList.add('show');
            }, 1500);
        };

        function displayStudentInfo() {
            document.getElementById('selectionForm').style.display = 'none';
            document.getElementById('student-info').style.display = 'block';
        }

        function makeCall(number) {
            window.location.href = `tel:${number}`;
        }

        function sendMessage(number) {
            window.location.href = `sms:${number}?body=Your child is absent for today's session.`;
        }
    </script>
</body>
</html>
