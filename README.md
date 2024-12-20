# Progress-Plans-Project
progress plans portal/website 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Springboard Client Progress Portal</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0fff4;
        }
        header {
            background-color: #28a745;
            color: white;
            padding: 1rem;
            text-align: center;
        }
        header img {
            height: 50px;
            margin-bottom: -15px;
        }
        .container {
            width: 80%;
            margin: auto;
            padding: 2rem;
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        h2 {
            color: #333;
        }
        label {
            display: block;
            margin-top: 1rem;
        }
        input, select, textarea {
            width: 100%;
            padding: 0.5rem;
            margin-top: 0.5rem;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .button-container {
            margin-top: 2rem;
            text-align: center;
        }
        button {
            padding: 0.75rem 1.5rem;
            color: white;
            background-color: #28a745;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        .tabs {
            margin-top: 2rem;
            display: flex;
            justify-content: space-around;
        }
        .tab {
            padding: 1rem;
            background-color: #f0fff4;
            border: 1px solid #ddd;
            border-radius: 4px;
            text-align: center;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        .tab:hover {
            background-color: #e2ffe4;
        }
        .tab-content {
            display: none;
            margin-top: 2rem;
        }
        .active {
            display: block;
        }
        .form-builder {
            margin-top: 1rem;
        }
        .form-field {
            margin-bottom: 1rem;
        }
        .form-storage {
            margin-top: 1rem;
            border: 1px solid #ccc;
            padding: 1rem;
            background-color: #f9f9f9;
        }
    </style>
</head>
<body>
    <header>
        <img src="springboard-logo.png" alt="Springboard Logo">
        <h1>Springboard Client Progress Portal</h1>
    </header>

    <div class="container" id="login-container">
        <h2>Log In</h2>
        <form id="login-form">
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>

            <label for="password">Password:</label>
            <input type="password" id="password" name="password" required>

            <div class="button-container">
                <button type="submit">Log In</button>
            </div>
        </form>
    </div>

    <div class="tabs" id="tabs" style="display: none;">
        <div class="tab" id="forms-tab">Forms</div>
        <div class="tab" id="templates-tab">Templates</div>
        <div class="tab" id="form-storage-tab">Form Storage</div>
        <div class="tab" id="analytics-tab">Analytics</div>
        <div class="tab" id="admin-permissions-tab">Admin Permissions</div>
    </div>

    <div class="tab-content" id="forms-content">
    <h2>Form Builder</h2>
    <div id="form-builder" class="form-builder">
        <div class="form-field">
            <label>Question:</label>
            <input type="text" class="question" placeholder="Enter question">
        </div>
        <div class="form-field">
            <label>Answer Type:</label>
            <select class="answer-type">
                <option value="text">Text</option>
                <option value="checkbox">Checkbox</option>
                <option value="radio">Multiple Choice</option>
                <option value="file">File Upload</option>
                <option value="date">Date</option>
            </select>
        </div>
        <div class="form-field">
            <label>Attach Media (Optional):</label>
            <input type="file" class="media-upload" accept="image/*,video/*">
        </div>
        <button onclick="addFormField()">Add Another Question</button>
    </div>
    <div class="button-container">
        <button onclick="previewForm()">Preview Form</button>
        <button onclick="saveFormData()">Save Form</button>
    </div>
    <div id="form-preview" class="form-preview">
        <h3>Form Preview:</h3>
        <p>No preview available.</p>
    </div>
</div>

<script>
    function previewForm() {
        const previewContainer = document.getElementById('form-preview');
        previewContainer.innerHTML = '<h3>Form Preview:</h3>';
        const questions = document.querySelectorAll('.question');
        const answerTypes = document.querySelectorAll('.answer-type');
        questions.forEach((question, index) => {
            const questionDiv = document.createElement('div');
            questionDiv.innerHTML = `<p><strong>${index + 1}. ${question.value}</strong> (${answerTypes[index].value})</p>`;
            previewContainer.appendChild(questionDiv);
        });
    }

    function addFormField() {
        const formBuilder = document.getElementById('form-builder');
        const fieldHTML = `
            <div class="form-field">
                <label>Question:</label>
                <input type="text" class="question" placeholder="Enter question">
                <label>Answer Type:</label>
                <select class="answer-type">
                    <option value="text">Text</option>
                    <option value="checkbox">Checkbox</option>
                    <option value="radio">Multiple Choice</option>
                    <option value="file">File Upload</option>
                    <option value="date">Date</option>
                </select>
                <label>Attach Media (Optional):</label>
                <input type="file" class="media-upload" accept="image/*,video/*">
            </div>`;
        formBuilder.insertAdjacentHTML('beforeend', fieldHTML);
    }
</script>
    </div>

    <div class="tab-content" id="form-storage-content">
        <h2>Form Storage</h2>
        <div id="form-storage" class="form-storage">
            <p>No forms stored yet.</p>
        </div>
        <div class="button-container">
            <button onclick="exportToExcel">Export to Excel</button>
        </div>
    </div>

    <div class="tab-content" id="admin-permissions-content">
        <h2>Admin Permissions</h2>
        <div id="admin-permissions">
            <h3>Manage Users</h3>
            <form id="add-user-form">
                <label for="new-email">Email:</label>
                <input type="email" id="new-email" name="new-email" required>

                <label for="new-password">Password:</label>
                <input type="password" id="new-password" name="new-password" required>

                <label for="new-role">Role:</label>
                <select id="new-role">
                    <option value="admin">Admin</option>
                    <option value="staff">Staff</option>
                    <option value="parent">Parent</option>
                </select>

                <div class="button-container">
                    <button type="button" onclick="addUser()">Add User</button>
                </div>
            </form>

            <h3>Existing Users</h3>
            <div id="user-list">
                <p>No users found.</p>
            </div>
        </div>
    </div>

    <script>
        const users = [
            { email: 'tim@curtis.services', password: 'password123', level: 'admin' },
            { email: 'staff@example.com', password: 'staff123', level: 'staff' },
            { email: 'parent@example.com', password: 'parent123', level: 'parent' }
        ];

        const forms = [];

        document.getElementById('login-form').addEventListener('submit', function(event) {
            event.preventDefault();

            const email = document.getElementById('email').value;
            const password = document.getElementById('password').value;

            const user = users.find(u => u.email === email && u.password === password);

            if (user) {
                document.getElementById('login-container').style.display = 'none';
                document.getElementById('tabs').style.display = 'flex';
                activateTab(document.getElementById('forms-tab'));
            } else {
                alert('Invalid email or password!');
            }
        });

        const tabs = document.querySelectorAll('.tab');
        const tabContents = document.querySelectorAll('.tab-content');

        tabs.forEach(tab => {
            tab.addEventListener('click', () => activateTab(tab));
        });

        function activateTab(tab) {
            tabs.forEach(t => t.classList.remove('active'));
            tabContents.forEach(content => content.classList.remove('active'));

            tab.classList.add('active');
            const contentId = tab.id.replace('-tab', '-content');
            document.getElementById(contentId).classList.add('active');
        }

        function addFormField() {
            const formBuilder = document.getElementById('form-builder');
            const fieldHTML = `
                <div class="form-field">
                    <label>Question:</label>
                    <input type="text" class="question" placeholder="Enter question">
                    <label>Answer Type:</label>
                    <select class="answer-type">
                        <option value="text">Text</option>
                        <option value="checkbox">Checkbox</option>
                        <option value="radio">Multiple Choice</option>
                    </select>
                </div>`;
            formBuilder.insertAdjacentHTML('beforeend', fieldHTML);
        }

        function saveFormData() {
            const questions = document.querySelectorAll('.question');
            const answerTypes = document.querySelectorAll('.answer-type');
            const formData = [];

            questions.forEach((question, index) => {
                formData.push({
                    question: question.value,
                    type: answerTypes[index].value
                });
            });

            forms.push(formData);
            displayForms();
        }

        function displayForms() {
            const formStorage = document.getElementById('form-storage');
            formStorage.innerHTML = '';
            forms.forEach((form, formIndex) => {
                const formDiv = document.createElement('div');
                formDiv.classList.add('form-storage-item');
                formDiv.innerHTML = `<h3>Form ${formIndex + 1}</h3>`;
                form.forEach(field => {
                    const fieldDiv = document.createElement('div');
                    fieldDiv.innerHTML = `<p><strong>${field.question}</strong> (${field.type})</p>`;
                    formDiv.appendChild(fieldDiv);
                });
                formStorage.appendChild(formDiv);
            });
        }

        function exportToExcel() {
            const rows = [
                ['Form Index', 'Question', 'Answer Type']
            ];

            forms.forEach((form, formIndex) => {
                form.forEach(field => {
                    rows.push([formIndex + 1, field.question, field.type]);
                });
            });

            let csvContent = 'data:text/csv;charset=utf-8,' + rows.map(row => row.join(',')).join('\n');
            const link = document.createElement('a');
            link.href = encodeURI(csvContent);
            link.download = 'form_data.csv';
            link.click();
        }

        function addUser() {
            const email = document.getElementById('new-email').value;
            const password = document.getElementById('new-password').value;
            const role = document.getElementById('new-role').value;

            users.push({ email, password, level: role });
            displayUsers();
        }

        function displayUsers() {
            const userList = document.getElementById('user-list');
            userList.innerHTML = '';

            users.forEach(user => {
                const userDiv = document.createElement('div');
                userDiv.innerHTML = `<p>${user.email} (${user.level})</p>`;
                userList.appendChild(userDiv);
            });
        }

        displayUsers();
    </script>
</body>
</html>
