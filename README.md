<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>College Student Info</title>
    <style>
        body,
        html {
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
            max-width: 150px;
            margin-bottom: 20px;
            box-shadow: 8px 8px 15px black;
        }

        #splash-screen h1 {
            font-size: 24px;
            text-shadow: 2px 2px 4px #000;
            text-align: center;
        }

        #splash-screen.hide {
            opacity: 0;
            visibility: hidden;
        }

        .container {
            display: none;
            text-align: center;
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            width: 90%;
            max-width: 400px;
            transform: translateY(20px);
            transition: opacity 1s ease, transform 1s ease;
            overflow-y: auto;
            max-height: 70%;
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

        select,
        input[type="text"] {
            padding: 10px;
            border: 2px solid #ddd;
            border-radius: 5px;
            margin-bottom: 20px;
            width: 100%;
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
            overflow-y: auto;
            max-height: 70vh;/* Allows scrolling if content is taller than 70% of the viewport height */
            width:100%;
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
            flex-wrap: wrap;
        }

        .info span {
            font-size: 14px;
            max-width: 60%;
            word-wrap: break-word;
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

        .student-entry {
            margin-bottom: 20px;
        }

        hr {
            border: 0;
            height: 1px;
            background: #ddd;
            margin: 20px 0;
        }

        @media (max-width: 600px) {
            #splash-screen img {
                max-width: 120px;
            }

            #splash-screen h1 {
                font-size: 20px;
            }

            h2 {
                font-size: 20px;
            }

            .info span {
                font-size: 12px;
                max-width: 100%;
            }

            .student-entry {
                margin-bottom: 15px;
            }
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
            <option value="CSE">IT</option>
            <option value="IT">CSE</option>
            <option value="CSE(AI)">CSE(AI)</option>
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
        <div id="student-details"></div>
    </div>

    <script>
        const students = [
            { name: "Papana Yalamanda Rao", rollNumber: "22471A1239", studentMobile: "+91-7416546101", parentMobile: "+91-9603484788" },
            { name: "Kottu Sangeeth Kumar", rollNumber: "22471A1243", studentMobile: "+91-7416546101", parentMobile: "+91-9603484788" },
            { name: "Shaik Appapuram Firoz", rollNumber: "22471A1244", studentMobile: "+91-7416546101", parentMobile: "+91-9603484788" },
            { name: "Shaik Ismail", rollNumber: "22471A1245", studentMobile: "+91-8123456789", parentMobile: "+91-9123456789" },
            { name: "Shaik Nagur Vali", rollNumber: "22471A1248", studentMobile: "+91-7987654321", parentMobile: "+91-8987654321" },
            { name: "Shaik Saida Vali", rollNumber: "22471A1249", studentMobile: "+91-7416546101", parentMobile: "+91-9603484788" },
            // Add more students here
        ];

        // Extend the students array to include 70 students
        for (let i = 4; i <= 70; i++) {
            students.push({
                name: `Student ${i}`,
                rollNumber: `22471A12${i}`,
                studentMobile: `+91-123456789${i % 10}`,
                parentMobile: `+91-987654321${i % 10}`
            });
        }

        function displayStudentInfo() {
            const container = document.getElementById('student-details');
            container.innerHTML = '';

            students.forEach((student, index) => {
                const studentInfo = `
                    <div class="student-entry">
                        <h3>Student ${index + 1}</h3>
                        <div class="info">
                            <span><strong>Name:</strong> ${student.name}</span>
                        </div>
                        <div class="info">
                            <span><strong>Roll Number:</strong> ${student.rollNumber}</span>
                        </div>
                        <div class="info">
                            <span><strong>Student Mobile:</strong> ${student.studentMobile}</span>
                            <div class="icons">
                                <img src="https://img.icons8.com/ios-filled/50/000000/phone.png" alt="Call" onclick="makeCall('${student.studentMobile}')">
                                <img src="https://img.icons8.com/ios-filled/50/000000/sms.png" alt="Message" onclick="sendMessage('${student.studentMobile}')">
                            </div>
                        </div>
                        <div class="info">
                            <span><strong>Parent Mobile:</strong> ${student.parentMobile}</span>
                            <div class="icons">
                                <img src="https://img.icons8.com/ios-filled/50/000000/phone.png" alt="Call" onclick="makeCall('${student.parentMobile}')">
                                <img src="https://img.icons8.com/ios-filled/50/000000/sms.png" alt="Message" onclick="sendMessage('${student.parentMobile}')">
                            </div>
                        </div>
                        <hr>
                    </div>`;
                container.innerHTML += studentInfo;
            });

            document.getElementById('selectionForm').style.display = 'none';
            document.getElementById('student-info').style.display = 'block';
        }

        function makeCall(number) {
            window.location.href = `tel:${number}`;
        }

        function sendMessage(number) {
            window.location.href = `sms:${number}?body=Your child is absent for today's session.`;
        }

        // Hide the splash screen after 2 seconds
        window.addEventListener('load', () => {
            setTimeout(() => {
                document.getElementById('splash-screen').classList.add('hide');
                document.getElementById('selectionForm').classList.add('show');
            }, 2000);
        });
    </script>
</body>

</html>
