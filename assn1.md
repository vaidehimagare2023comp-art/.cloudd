I // commands to type in virtual machine terminal to show web connectivity for EC2
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl status httpd

//for database connectivity
sudo yum install mariadb105-server -y
sudo systemctl start mariadb
sudo systemctl enable mariadb
sudo systemctl status mariadb
sudo mysql
CREATE DATABASE studentdb; 
USE studentdb; 
CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    department VARCHAR(50)
); 
INSERT INTO students VALUES
(1,'Vaidehi','Computer'),
(2,'Rahul','IT');
SELECT * FROM students;
EXIT;
