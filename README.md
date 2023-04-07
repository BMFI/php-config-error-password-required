# php-config-error-password-required
Password required yes error in php
Here is the original code that throws the error:
<?php 
    //Start Session
    session_start();
    ob_start();	


    //Create Constants to Store Non Repeating Values
    define('SITEURL', 'http://localhost/food-order-1/');
    define('LOCALHOST', 'localhost');
    define('DB_USERNAME', 'root');
    define('DB_PASSWORD', ' ');
    define('DB_NAME', 'food');
    
    $conn = mysqli_connect(LOCALHOST, DB_USERNAME, ' ') or die(mysqli_error()); //Database Connection
    $db_select = mysqli_select_db($conn, DB_NAME) or die(mysqli_error()); //SElecting Database


?>
Here is the error:
https://stackoverflow.com/questions/71954572/connection-to-the-database-mysql-and-php-whats-the-solution-to-below-error

Fatal error: Uncaught mysqli_sql_exception: Access denied for user 'root'@'localhost' (using password: YES) in C:\xampp-1\htdocs\food-order-1\config\constants.php:14 Stack trace: #0 C:\xampp-1\htdocs\food-order-1\config\constants.php(14): mysqli_connect('localhost', 'root', ' ') #1 C:\xampp-1\htdocs\food-order-1\partials-front\menu.php(1): include('C:\\xampp-1\\htdo...') #2 C:\xampp-1\htdocs\food-order-1\index.php(1): include('C:\\xampp-1\\htdo...') #3 {main} thrown in C:\xampp-1\htdocs\food-order-1\config\constants.php on line 14

Here is the good code that fixed the errors on my xampp with the latest version of php:
<?php 
 //Create Constants to Store Non Repeating Values
    define('SITEURL', 'http://localhost/food-order-1/');
    define('LOCALHOST', 'localhost');
    define('DB_USERNAME', 'root');
    define('DB_PASSWORD', ' ');
    define('DB_NAME', 'food');

$conn= new mysqli('localhost','root','','food')or die("Could not connect to mysql".mysqli_error($con));
if(mysqli_connect_errno()) 
{
	echo "Failed to connect: " . mysqli_connect_errno();
}

?>
