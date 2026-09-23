# Day3-Assignment_Software-Engineering-Essentials
Akidor Erot Julias
Task 1: Flutter & Dart Environment Setup
1. Verify Flutter Installation
I opened the terminal and ran the following command:
flutter doctor

Flutter Doctor Output


The flutter doctor command checks whether Flutter, Dart, Android development tools, connected devices, and other required components are correctly installed and configured.

2. Create a New Flutter Application
I created a new Flutter application named my_first_app using:
flutter create my_first_app

I then navigated into the project folder:
cd my_first_app

To list the available target devices, I ran:
flutter devices

Available Devices

The flutter devices command displays the devices and platforms available for running the Flutter application, such as Android devices, Chrome, Windows, or other supported platforms.

3. Hot Reload vs Hot Restart
Hot Reload updates the running Flutter application with changes made to the source code without restarting the entire application. It normally preserves the current application state, making it useful when changing the user interface, styling, widgets, or layout during development.
Hot Restart completely restarts the Flutter application and resets its current state. It is useful when changes affect application startup, initialization, or state that cannot be properly updated using Hot Reload.
Simple Difference
Hot Reload
Hot Restart
Updates code quickly
Restarts the application
Usually preserves app state
Resets app state
Faster
Slower than Hot Reload
Useful for UI and small code changes
Useful when a full restart is needed

In short: Use Hot Reload for quick development changes while keeping the current state. Use Hot Restart when you need the application to start again from its initial state.

Task 2: MySQL Database Management
1. Create and Manage the School Database
I logged into my local MySQL server as the root user from the terminal using:
mysql -u root -p

After entering my MySQL password, I executed the following SQL commands:
CREATE DATABASE school;

USE school;

CREATE TABLE students (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(150) UNIQUE,
    enrolled_on DATE
);

INSERT INTO students (name, email, enrolled_on)
VALUES
    ('Alice Johnson', 'alice@example.com', '2026-09-01'),
    ('Brian Smith', 'brian@example.com', '2026-09-05');

SELECT * FROM students;

2. SELECT Query Results
The SELECT * FROM students; command retrieves all records from the students table.
Terminal Output


I would include a screenshot of the terminal showing the SELECT * FROM students; command and its results as evidence.

3. Security Reflection
Using the MySQL root account directly from an application backend is poor security practice because root has extensive privileges over the entire MySQL server. If the application's credentials are stolen or the application is compromised, an attacker could potentially modify or delete databases, create users, or access other sensitive data. A dedicated application account should therefore be created with only the permissions required by that application.
For example, I can create a dedicated user and grant it access only to the school database:
CREATE USER 'school_app'@'localhost'
IDENTIFIED BY 'Use-A-Strong-Unique-Password';

GRANT SELECT, INSERT, UPDATE, DELETE
ON school.*
TO 'school_app'@'localhost';

FLUSH PRIVILEGES;

The application should then connect using school_app instead of root.
The GRANT command follows the principle of least privilege because the application user receives permissions only for the school database and only for the operations it needs. The root account should be reserved for administrative tasks rather than normal application database connections.
For example, if the application only needs to read student information, its permissions can be reduced further:
CREATE USER 'school_readonly'@'localhost'
IDENTIFIED BY 'Another-Strong-Unique-Password';

GRANT SELECT
ON school.*
TO 'school_readonly'@'localhost';

FLUSH PRIVILEGES;

This provides a more restrictive account because the user can read data but cannot insert, update, or delete records.
Task 3: Python Environment & Dependency Isolation
1. Create the Project Directory
I created a project directory named python_setup_lab using:
mkdir python_setup_lab
cd python_setup_lab

2. Create and Activate the Virtual Environment
I created an isolated virtual environment named venv inside the project folder:
python -m venv venv

I activated the virtual environment using:
source venv/Scripts/activate

After activation, (venv) appeared at the beginning of my terminal prompt, confirming that the virtual environment was active.
3. Install and Verify Requests
I installed the requests library with:
python -m pip install requests

I verified the installed packages using:
python -m pip list

The package list showed the requests library and its installed version.
I then exported the environment's installed packages to requirements.txt using:
python -m pip freeze > requirements.txt

I checked the contents of the file with:
cat requirements.txt

4. Exact Terminal Commands Used
mkdir python_setup_lab
cd python_setup_lab
python -m venv venv
source venv/Scripts/activate
python -m pip install requests
python -m pip list
python -m pip freeze > requirements.txt
cat requirements.txt

Project Structure
After completing the setup, the project contains:
python_setup_lab/
├── venv/
└── requirements.txt

The venv directory contains the isolated Python environment, while requirements.txt records the packages and versions installed in the environment.
Task 4: VS Code Workspace Configuration
I installed the required VS Code extensions: Flutter, Dart, Python, Pylance, and MySQL. I then opened the python_setup_lab project in VS Code and selected the Python interpreter located inside the project's venv directory.
The selected Python interpreter is:
python_setup_lab/venv/Scripts/python.exe

I activated the virtual environment in the VS Code integrated terminal. The terminal displayed (venv), confirming that the virtual environment was active.
I also verified that the VS Code status bar displayed the selected venv Python interpreter.
A full-screen screenshot was taken showing the installed extensions in the Extensions panel, the active (venv) terminal prompt, and the selected Python interpreter in the VS Code status bar.



