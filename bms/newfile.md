Areas Examined: Visualizing a real-world problem into a software/database System.
Caltex Medical Store is a health firm with main offices located in Mbarara town near Centenary bank. According to the company sales manager Mr. Odongo Marks, Caltex is an international company capable of rendering health-related services to its clients. The company has branches in over seven parts of the world. The company services are provided in different departments i.e., the health product sales department, the consultation department, the guidance, and counseling department, the clinic department, and others. Marks further says that the sales department is responsible for selling health products to the company’s clients.  The company has long-time clients and the day to clients who come to access services.  He continued to inform us that the company currently used a manual way of managing the day-to-day operations as well as storing the company information. The main organs where information is collected and managed at Caltex are branches, departments, health products stock, cosmetics, sales, customers/clients, employees, and suppliers. As a student of database programming, use the briefly provided Caltex Information to respond to the following.
A)	Prepare a presentation to the top management of Caltex. In this presentation, you will be required to show the team the importance of using a database-based system to simply manage transactions and store information at Caltex. (3 marks)

**Answer:**
A database-based system will streamline the management of transactions and information storage at Caltex by:
1. Improving data accuracy and consistency.
2. Enhancing data security and access control.
3. Facilitating real-time data access and reporting.

B)	 Suggest the name of the database system that you will develop for Caltex and Why?. (2 mark)

**Answer:**
The suggested name for the database system is "Caltex Health Management System (CHMS)". This name reflects the system's purpose of managing health-related services and operations efficiently.

C)	Provide a list of 3 functional and 2 non-functional requirements of the suggested system. (5 marks)

**Answer:**
Functional Requirements:
1. User authentication and authorization.
2. Inventory management for health products.
3. Appointment scheduling and management.

Non-Functional Requirements:
1. System should be highly available and reliable.
2. System should be scalable to handle increasing data and user load.

D)	Explain the steps that you plan to go through to make sure the suggested system is fully functional and accessible on a distributed network. (5 marks)

**Answer:**
1. Requirements gathering and analysis.
2. System design and architecture planning.
3. Development and unit testing.
4. Integration and system testing.
5. Deployment on a distributed network.
6. Continuous monitoring and maintenance.

E)	How would you ensure that the suggested system is up and running without any failure after its implementation on a distributed network? (3 marks)

**Answer:**
1. Implementing redundancy and failover mechanisms.
2. Regular system backups and disaster recovery planning.
3. Continuous monitoring and performance tuning.

F)	Draw a well-structured flow chart showing how the performance of the system will flow.  Use a software tool to draw this flow chart. (5 marks)
```mermaid
flowchart TD
    A[Start] --> B[User Authentication]
    B --> C[Inventory Management]
    C --> D[Appointment Scheduling]
    D --> E[Data Storage]
    E --> F[Generate Reports]
    F --> G[End]
```
**Answer:**
*Flow chart to be created using a software tool like Microsoft Visio or Lucidchart.*

G)	Draw a context diagram to show how external entities will interact with the system. (4 marks)


```mermaid
graph TD
    Client -->|Requests| System
    System -->|Provides Services| Client
    System -->|Reports| Management
    Supplier -->|Supplies| System
    Employee -->|Uses| System

```
**Answer:**
*Context diagram to be created using a software tool like Microsoft Visio or Lucidchart.*

H)	Using MySQL Workbench, draw a well normalized enhanced entity relationship diagram with at least 5 tables to show the logical structure of the system database. (4 marks)

**Answer:**
*ER diagram to be created using MySQL Workbench.*



```mermaid
erDiagram
    CLIENT {
        int id(pk)
        string name
        string contact
    }
    EMPLOYEE {
        int id(pk)
        string name
        string position
    }
    PRODUCT {
        int id
        string name
        float price
        int stock
    }
    APPOINTMENT {
        int id
        date date
        int client_id
        int employee_id
    }
    SALE {
        int id
        int product_id
        int client_id
        int quantity
        date date
    }
    CLIENT ||--o{ APPOINTMENT : books
    EMPLOYEE ||--o{ APPOINTMENT : attends
    CLIENT ||--o{ SALE : makes
    PRODUCT ||--o{ SALE : includes
```
I)	Explain two software requirements that you will use to design and develop the required web system. (2 marks)

**Answer:**
1. Web server software (e.g., Apache or Nginx) to host the web application.
2. Database management system (e.g., MySQL) to store and manage data.

J)	Explain four languages that you will use to develop the required web system. (2marks)

**Answer:**
1. HTML for structuring web pages.
2. CSS for styling web pages.
3. JavaScript for client-side scripting.
4. PHP for server-side scripting.

K)	Using a server-side language script of your choice, write a configuration file script that you will use to connect to the database. (3 marks)

**Answer:**
```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "caltex_db";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
echo "Connected successfully";
?> 
```

L) Write a code snippet that will log in users into the system service. (2marks)
```php 
<?php
session_start();
include 'db.php';

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $username = $_POST['username'];
    $password = $_POST['password'];

    $sql = "SELECT id FROM users WHERE username = '$username' and password = '$password'";
    $result = $conn->query($sql);

    if ($result->num_rows > 0) {
        $_SESSION['login_user'] = $username;
        header("location: dashboard.php");
    } else {
        $error = "Your Login Name or Password is invalid";
    }
}
?>
```
