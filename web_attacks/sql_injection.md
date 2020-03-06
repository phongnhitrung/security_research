Data is one of the most vital components of information systems. 
Database powered web applications are used by the organization to get data from customers. 
SQL is the acronym for Structured Query Language. 
It is used to retrieve and manipulate data in the database.

# 1. What is a SQL Injection?
SQL Injection is an attack that poisons dynamic SQL statements to comment out certain parts of the statement or appending a condition that will always be true. 
It takes advantage of the design flaws in poorly designed web applications to exploit SQL statements to execute malicious SQL code.

# 2. How SQL Injection Works
The types of attacks that can be performed using SQL injection vary depending on the type of database engine. 
The attack works on dynamic SQL statements. 
A dynamic statement is a statement that is generated at run time using parameters password from a web form or URI query string.

Let’s consider a simple web application with a login form. 
The code for the HTML form is shown below.

```
<form action=‘index.php’ method="post">
<input type="email" name="email" required="required"/>
<input type="password" name="password"/>
<input type="checkbox" name="remember_me" value="Remember me"/>
<input type="submit" value="Submit"/>
</form>
```
